# Should I use SharePoint REST or Microsoft Graph API in Power Automate?

When working with Microsoft 365, we see a lot of overlapping tools and features and we will need (to provide) a lot of guidance around 'when to use what' for users. Wile most comparisons address users, I want to cover some more IT related scenarios in this blog post. Specifically, I want to compare two different RESTful APIs, which we can both use in Power Automate and also Azure Logic Apps to send HTTP requests. If you are not familiar with that, don't fret, just continue to read my blog post about [how to get started with http requests in Power Automate](https://m365princess.com/how-to-get-started-with-http-requests-in-power-automate/), I will grab a coffee ☕ in the meanwhile.

Back again? Cool. Let me introduce you to our 

## use case

Let's say, we want create a new SharePoint list and add some columns to a it based on user's input using Power Automate or Azure Logic Apps. When we look at the different available SharePoint actions in Power Automate, we will see, that there is no 'create a list' and no 'add column to SharePoint list' action, but that we could try out something with ['send an HTTP request to SharePoint'](https://docs.microsoft.com/en-us/sharepoint/dev/business-apps/power-automate/guidance/working-with-send-sp-http-request)

### Option No. 1: SharePoint REST

The 'send an HTTP request to SharePoint' action uses SharePoint REST API. To create a list, we can look up [working with lists and lists items](https://docs.microsoft.com/en-us/sharepoint/dev/sp-add-ins/working-with-lists-and-list-items-with-rest#working-with-lists-by-using-rest) and see, that we need to send a POST request to the `https://{site_url}/_api/web/lists` endpoint and specify in the body of our list should look like. We can define title and description of the list and also [set the Basetemplate](https://techcommunity.microsoft.com/t5/sharepoint/near-complete-list-of-sharepoint-list-types-and-templates-a-k-a/m-p/220550) (in case you want to do the same with a library etc.): 

    POST https://{site_url}/_api/web/lists
    Authorization: "Bearer " + accessToken
    Accept: "application/json;odata=verbose"
    Content-Type: "application/json"
    Content-Length: {length of request body as integer}
    X-RequestDigest: "{form_digest_value}"

    {
       "__metadata": {
    "type": "SP.List"
      },
      "AllowContentTypes": true,
      "BaseTemplate": 100,
      "ContentTypesEnabled": true,
      "Description": "My list description",
      "Title": "Test"
     }

Now how do we do this in Power Automate without writing much code? 

#### mobile flow button

To make things easier, I will use the mobile flow trigger with three text inputs: 

![mobile flow trigger with two text inputfields](https://github.com/LuiseFreese/blog/blob/main/media/sharepointrest-or-graph/mobileflowtrigger.png)

Of course you can also trigger the flow from a list, a form, an app, a bot or whatever suits your use case. 

#### Send an HTTP request to SharePoint - create a list

Now we need to add the 'send an HTTP request to SharePoint' action: 

* Select the site of your choice from the dropdown menu
* Select method **Post**
* enter `_api/web/lists/` as URI
* enter Headers as follows:
  * `Content-type` : `application/json;odata=verbose`
  * `accept`:`application/json;odata=verbose`
* enter 

```{
  "__metadata": {
    "type": "SP.List"
  },
  "AllowContentTypes": true,
  "BaseTemplate": 100,
  "ContentTypesEnabled": true,
  "Description": "@{triggerBody()['text_1']}",
  "Title": "@{triggerBody()['text']}"
  }
  ```
  
 as Body- make sure you replace the placeholder by Dynamic Content:
 
![send an http request to SharePoint](https://github.com/LuiseFreese/blog/blob/main/media/sharepointrest-or-graph/sendhttprequest.png)

#### Parse JSON

Now we want to add a column. Let's have a look [into the documentation](https://docs.microsoft.com/en-us/sharepoint/dev/sp-add-ins/working-with-lists-and-list-items-with-rest#working-with-lists-by-using-rest), how we can do this. 

```
POST https://{site_url}/_api/web/lists(guid'{list_guid}')/Fields
Authorization: "Bearer " + accessToken
Accept: "application/json;odata=verbose"
Content-Type: "application/json"
Content-Length: {length of request body as integer}
X-RequestDigest: "{form_digest_value}"

{
  "__metadata": {
    "type": "SP.Field"
  },
  "Title": "field title",
  "FieldTypeKind": FieldType value,
  "Required": "true/false",
  "EnforceUniqueValues": "true/false",
  "StaticName": "field name"
}
```

We need another 'send an HTTP request to SharePoint action, and we need the **list Guid**. To get the list Guid, we need to add a **Parse JSON** action. If you are not familiar with that - blogged about it: [How to use Parse JSON action in Power Automate](https://m365princess.com/how-to-use-parse-json-action-in-power-automate/)

#### Parse JSON

* Let your flow run - just the mobile trigger and the 'send an HTTP request to SharePoint' action
* Go to your flow run history
* Copy the Outputs from the 'send an HTTP request to SharePoint' action
* add a 'Parse JSON' action to your flow
* select `body` from the 'send an HTTP request to SharePoint'action as **Content**
* click **Generate from sample**
* paste the copied JSON code in here
* click **Done**

When we now have a look into our Dynamic Content, we will see a lot of more options, also the list Guid, which is named **Id** here. 

#### Send an HTTP request to SharePoint 2 - add a column

Now we add another 'send an HTTP request to SharePoint' action which will create us a column: 

* Select the site of your choice from the dropdown menu
* Select method **Post**
* enter `_api/web/lists(guid'@{body('Parse_JSON')?['d']?['Id']}')/Fields`as URI (replace the placeholder with Dynamic content)
* enter Headers as follows:
  * `Content-type` : `application/json;odata=verbose`
  * `accept`:`application/json;odata=verbose`
enter in the Body: 

```
{
  "__metadata": {
    "type": "SP.Field"
  },
  "Title": "@{triggerBody()['text_2']}",
  "FieldTypeKind": 2,
  "Required": "false",
  "EnforceUniqueValues": "false",
  "StaticName": "@{triggerBody()['text_2']}"
}
```
* Please replace again all placeholder by Dynamic content

![Send an HTTP request to SharePoint 2](https://github.com/LuiseFreese/blog/blob/main/media/sharepointrest-or-graph/sendhttprequest2.png)

Should you stumble upon the FieldTypeKind, please find reference [here](https://docs.microsoft.com/en-us/previous-versions/office/sharepoint-csom/ee540543(v=office.15)) - 2 means 'single line of text'. 

If you now want to run your flow, please think about changing the list name, because you already created a list! 

If we control in our new created SharePoint list, we will see, that our new column doesn't show up in the default view, but that we need to enable the column- bummer! 

#### Send an HTTP request to SharePoint 3 - add column to view

To have the column in the default view (or another view), we need to add another 'send an HTTP request to SharePoint' action: 

* Select the site of your choice from the dropdown menu
* Select method **Post**
* enter `_api/web/Lists/getByTitle('@{triggerBody()['text']}')/views/getByTitle('All Items')/ViewFields/addViewField('@{triggerBody()['text_2']}')`as URI 
* (replace the placeholder with Dynamic content)
* enter Headers as follows:
  * `Content-type` : `application/json;odata=verbose`
  * `accept`:`application/json;odata=verbose`
* Body is empty

![send an HTTP request to SharePoint 3](https://github.com/LuiseFreese/blog/blob/main/media/sharepointrest-or-graph/senhttp3.png)

#### Advantages of this solution

* no need to register an application in Azure AD
* send an HTTP request to SharePoint is not a premium connector, which means that you won't need a Power Automate Standalone license 

#### Disadvantages of this solution: 

* with an 'http request to SharePoint' action you have - compared to the power of Microsoft Graph API - limited options, as you can only send requests to SharePoint, but not to other services in Microsoft 365-
* to add the new column to our default view, we need a third request - which makes the flow unnessarily more complex

### Option No. 2: Microsoft Graph API
 
Let's see, how we can create a SharePoint list or library and columns in it using Microsoft Graph. Microsoft Graph is a super powerful set of APIs that gives you a consistent experience for authentication, documentation and samples. You can try it out on [Microsoft Graph Explorer](https://developer.microsoft.com/en-us/graph/graph-explorer). For full documentation please continue [here](https://docs.microsoft.com/en-us/graph/overview). If you are not familiar with using Microsoft Graph in Power Automate, [please continue to read here](https://m365princess.com/how-to-get-started-with-http-requests-in-power-automate/)... time for another coffee for me then :-)

#### mobile flow trigger

Again, to make things easy, we will use the same trigger as in Option No. 1.: 

![mobile flow trigger](https://github.com/LuiseFreese/blog/blob/main/media/sharepointrest-or-graph/mobileflowtrigger.png)

#### HTTP action

Now that we registered our app in Azure AD, we can continue with the HTTP action in Power Automate. We will insert it and fill it as follows: 



####
To create a list, we will look up [documentation here](https://docs.microsoft.com/en-us/graph/api/list-create?view=graph-rest-1.0&tabs=http) and see, that we will need to send a POST request to 

`https://graph.microsoft.com/v1.0/sites/{site-id}/lists`

and that we will need to add permissions to be able to call this API. Our HTTP request needs authentication, which can be done via Azure Active Directory OAuth, but we will first need to have a representation of our app (yes, this flow that calls Microsoft Graph is an application) in Azure AD.

We will follow these steps to register an app in Azure AD:

* Go to portal.azure.com and log in
* Click app registrations
* Click New App registration
* Give your app a nice name
* Save tenant ID and Client(app) ID somewhere (notepad or similar)
* Click **API PERMISSIONS** and select Microsoft Graph

Now look up the permissions needed for this action: [Create a new list](https://docs.microsoft.com/en-us/graph/api/list-create?view=graph-rest-1.0&tabs=http):

| Permission type | Permissions (from least to most privileged)|
| ------- |:-----:|
|Application|Sites.ReadWrite.All|

* Select all these permissions
* Grant Admin consent
* Click **Certificates & secrets** 
* Click **New client secret** 
* Type in a description
* Click **Add**
* Copy the value and save it in your notepad (you will need that later) 

Add an HTTP (not 'send an HTTP request to SharePoint action) action to your flow and fill out as follows: 

* Method: Post


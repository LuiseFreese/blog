# Should I use SharePoint REST or Microsoft Graph API in Power Automate?

When working with Microsoft 365, we see a lot of overlapping tools and features and we will need (to provide) a lot of guidance around 'when to use what' for users. Wile most comparisons address users, I want to cover some more IT related scenarios in this blog post. Specifically, I want to compare two different RESTful APIs, which we can both use in Power Automate and also Azure Logic Apps to send HTTP requests. If you are not familiar with that, don't fret, just continue to read [my blog post about how to get started with http requests in Power Automate](https://m365princess.com/how-to-get-started-with-http-requests-in-power-automate/), I will grab a coffee ☕ in the meanwhile.

Back again? Cool. Let me introduce you to our 

## use case

Let's say, we want create a new SharePoint list and add some columns to a it based on user's input using Power Automate or Azure Logic Apps. When we look at the different available SharePoint actions, we will see, that there is no 'create a list' and no 'add column to SharePoint list' action, but that we could try out something with ['send an HTTP request to SharePoint'](https://docs.microsoft.com/en-us/sharepoint/dev/business-apps/power-automate/guidance/working-with-send-sp-http-request)

### Option No. 1: SharePoint REST

The 'send an HTTP request to SharePoint' action uses SharePoint REST API. To create a list, we can look up [working with lists and lists items](https://docs.microsoft.com/en-us/sharepoint/dev/sp-add-ins/working-with-lists-and-list-items-with-rest#working-with-lists-by-using-rest) and see, that we need to send a POST request to the `https://{site_url}/_api/web/lists` endpoint and specify in the body of our list should look like. We can define title and description of the list and also [set the Basetemplate](https://techcommunity.microsoft.com/t5/sharepoint/near-complete-list-of-sharepoint-list-types-and-templates-a-k-a/m-p/220550) (in case you want to do the same with a library etc.): 

`POST https://{site_url}/_api/web/lists
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
}` 

Now how do we do this in Power Automate without writing nmuch code? 

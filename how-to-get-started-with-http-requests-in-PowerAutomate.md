# How to get started with HTTP requests in Power Automate

If you ever wondered what is an HTTP request and why you would want to know how this works - this post is made for you. 

## What is a HTTP request and why would I need it?

HTTP requests are a super powerful thing - not only in Power Automate so we will first need to understand what this is in order to determine why we would like to know how to use them. But wait - HTTP? 

### What is HTTP? 

Let's first get us all an the same page. HTTP is the acronym for **Hypertext Transfer Protocol**. Its purpose is to structure requests and responses over the internet (yeah, you heard of that one 😇) - Data needs to be transferred from Point A to Point B over the network. 

The transfer of resources (like html files, images, videos etc) happens with TCP - which again is acronym, for **Transmission Control Protocol**. When you read this blog post, TCP manages the channels between your browser (hope you are using Microsoft Edge) and the server. TCP is used a lot for scenarios in which one computer sends something to another. Now what has TCP to do with HTTP? Think of HTTP as the command language for both computers so they are able to communicate. 

When you type a URL like **https://www.m365princess.com** into the address bar of your browser, your computer establishes first a TCP connection and then makes a request. We will call your computer now **client**. The request is a **HTTP GET** request, as we nicely ask to retrieve the website that the browser shall display. And as we send a nicely request, the server (site that you requested) will send a response and close the TCP connection. Of course, there are more methods than just the **GET** method, you will learn later more about methods **POST, PUT, PATCH, DELETE**. 

Now that we know what an HTTP request does, we want to learn what it could do in Power Automate

## What can HTTP requests do in Power Automate?

Power Automate offers you a huge variety of connectors and within those connectors, many actions which you can use to automate your processes. But although we have so many options, this won't cover everything you need or taht you might want to build in Power Automate, which is why we have an HTTP action in Power Automate as well. With the HTTP action we can invoke a REST API. 

### What is a REST API? 

Wait but what? Ok, let's slow down a little bit. What is a REST API and would we want to invoke that? 

API is -yet again- an acronym for **application programming interface** and with it is a set of rules and mechanisms. By these an app or component interacts with others. RESTful APIs (REST means **representational state transfer**) can return data that you need for your app in a convenient format (for example JSON or XML). By using the **HTTP** action in Power Automate we can *invoke/call* an API by using methods **GET** (read), **POST** (write), **PUT** (update), **PATCH** (update, but only partially) or **DELETE** (remove). The same way as our browser made a call towards a website and getting a response using HTTP, we now use HTTP to send a request to a service. In my example, I will use Microsoft Graph. Microsoft Graph is a RESTful API that enables you to access Microsoft Cloud service resources. It is literally THE way to read, create, update and delete resources (like files, teams, meetings etc.).

Microsoft provides us with an amazing tool to try out Microsoft Graph, it's the [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).

## How to create a HTTP request in Power Automate

Now how do we create an HTTP reuqets in Power Automate? First let me introduce everyone to our little 

### Use case
We want to use Power Automate to create a Team with some predefined content in it. To make things easier, we will use the mobile trigger and ask for Team Name, Team Description, and if a user wants a channel for **Learning** and wants to pin training material (a website) as a tab to this channel
![manual trigger of flow](https://github.com/LuiseFreese/blog/blob/main/media/how-to-get-started-with-http-requests-in-PowerAutomate/manually-trigger.png)

We will now add actions to create the team and the first channel (technically it's the second channel as the first channel **General** will be created by default): 

![create the Team and add a channel](https://github.com/LuiseFreese/blog/blob/main/media/how-to-get-started-with-http-requests-in-PowerAutomate/create-team.png)

Now we add a conditions: if user wants Learning material, we want to pin a website to the **Learning** channel.

Unfortunatley, there are no actions "pin a website to a channel in Teams" in Power Automate. Fortunately, we can still do this by making an HTTP request towards Microsoft Graph. This is why I added the HTTP action into the flow: 

![HTTP request](https://github.com/LuiseFreese/blog/blob/main/media/how-to-get-started-with-http-requests-in-PowerAutomate/condition1.png)

You can see a lot of fields in that HTTP action, so I will make you understand them. 

### What do we need to make a successfull HTTP request? 

💡 It is a very good idea to open documentation on [docs.microsoft.com](https://docs.microsoft.com/en-us/graph/api/overview?toc=.%2Fref%2Ftoc.json&view=graph-rest-1.0) buiding your flows that call Microsoft Graph. You will find in nearly all pages 4 things, that we need to consider when doing an HTTP request: 

#### Endpoint

First things first, if we want to call an API with HTTP, we need to know the right endpoint. Think of an endpoint like a phonenumber that you want to call. You need to know it, because otherwise you won't reach the right person.

An endpoint is a URL like this: `https://graph.microsoft.com/v1.0/{resource}?[query_parameters]` and we will later use `https://graph.microsoft.com/v1.0/teams/{team-id}/channels/{channel-id}/tabs` to create those tabs. 

#### Method

Second thing we need to know is which method we want to use. As already explained, 

| Method | Meaning|
| ------- |:-----:|
| GET     |📖 read|
| POST    |✍ create|
| PUT | 📰 update|
| PATCH | ✒ update|
| DELETE | 🗑 remove|

If we now open the dropdown menu for the **Method** field in the HTTP action, we will see a representation of that: 
![different methods in HTTP action](https://github.com/LuiseFreese/blog/blob/main/media/how-to-get-started-with-http-requests-in-PowerAutomate/methods.png)

As we want to *create* a new tab in a channel, we will use **POST**.

#### Headers

Headers are not mandatory for all requests, but look like this: `Content-type: application/json` - If they are needed, documentation will tell you. 

#### Data (or body)

If we call an endpoint, it's not enough to specify the URL the request needs to make to, but we will also need to post some addiutional info into the body of our requests. Most GET requests though don't need information in the body, as they will only list the requested resources. 

### Fill in the HTTP action

If we carefully follow the docs, we will see that we should do this: 

`POST https://graph.microsoft.com/v1.0/teams/{team-id}/channels/{channel-id}/tabs`



>{

> "displayName": "M365Princess Blog","teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/com.microsoft.teamspace.tab.web", 
>"configuration": {
>      "contentUrl": "https://m365princess.com",
>     "websiteUrl": "https://m365princess.com"
>  }

>}


while for websites this applies: 

Some remarks on that: 

1. Choose Method **POST** - we already figured that out
2. https://graph.microsoft.com/v1.0/teams/{team-id}/channels/{channel-id}/tabs is our URL, but we will need to replace `{team-id}` and `{channel-id}` with the actual dynamic content
3. choose a `displayName` for the Tab as you wish
4. `"teamsApp@odata.bind"` is "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/com.microsoft.teamspace.tab.web"
4. both `websiteUrl` and `contentUrl` are the full URL of the website you want to pin including `https://`. If your website is only `http://` you can't use that inside of Teams. 
5. we don't need `removeUrl` and `entityID`. 

In total, this looks like this:

![http request without auth](https://github.com/LuiseFreese/blog/blob/main/media/how-to-get-started-with-http-requests-in-PowerAutomate/http-without-auth.png)

#### Authentication in Azure AD
We are almost there, but some critucal parts are missing. As you can see in the last image, there is a **Show advanced options** link in the HTTP action and we need to click on it. Our HTTP request need authentication. We can authenticate via Azure Active Directory OAuth, but we will first need to have a representation of our app (yes, this flow that calls Graph is an application) in Azure AD. 

We will follow these steps to register an app in Azure AD: 

* go to portal.azure.com and log in
* click **app registrations**
* click **New App registration**
* Gice your app a nice name
* save tenant ID and Client(app) ID somewhere (notepad or similar)
* click **API PERMISSIONS** and select **Microsoft Graph**
* Now look up the permissions needed for this action: [Add tabs to a channel(https://docs.microsoft.com/en-us/graph/api/channel-post-tabs?view=graph-rest-1.0):


| Permission type | Permissions (from least to most privileged)|
| ------- |:-----:|
|Delegated (work or school account)|TeamsTab.Create, TeamsTab.ReadWriteForTeam, TeamsTab.ReadWrite.All, Group.ReadWrite.All, Directory.ReadWrite.All|

* select all these permissions
* grant Admin consent
* Click **Certificates & secrets** 
* Click **New client secret** 
* Type in a description
* Click **Add**
* Copy the value and save it in your notepad (you will need that later) 















## Resources that might help you

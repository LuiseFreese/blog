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

## How to create a HTTP request in Power Automate

Now how do we create an HTTP reuqets in Power Automate? First let me introduce everyone to our little 

### Use case
We want to use Power Automate to create a Team with some predefined content in it. To make things easier, we will use the mobile trigger and ask for Team Name, Team Description, name of first channel and if a user wants us to pin Training Material (a document library with a lot of docs and presentations) to that channel and/or just a pinned document as a quick start guide). 
![manual trigger of flow](https://github.com/LuiseFreese/blog/blob/main/media/how-to-get-started-with-http-requests-in-PowerAutomate/manually-trigger.png)

We will now add actions to create the team and the first channel (technically it's the second channel as the first channel **General** will be created ny default): 

![create the Team and add a channel](https://github.com/LuiseFreese/blog/blob/main/media/how-to-get-started-with-http-requests-in-PowerAutomate/create-team.png)

Now we add 2 conditions: if user wants Learning material, we want to pin a document libary (that sits on another site than the site that backs up this Team) to the new channel and if user wants a quick start guide, we want to pin this document as a tab to the new channel. 

Unfortunatley, there are no actions "pin a document to a channel in Teams" in Power Automate. Fortunately, we can still do this by making an HTTP request towards Microsoft Graph. This is why I added the HTTP action into the flow: 

![HTTP request](https://github.com/LuiseFreese/blog/blob/main/media/how-to-get-started-with-http-requests-in-PowerAutomate/condition1.png)

You can see a lot of fields in that HTTP action, so I will make you understand them. 

### What do we need to make a successfull HTTP request? 

#### Endpoint

First things first, if we want to call an API with HTTP, we need to know the right endpoint. Think of an endpoint like a phonenumber that you want to call. You need to know it, because otherwise you won't reach the right person.

An endpoint is a URL like this: `https://graph.microsoft.com/v1.0/{resource}?[query_parameters]` and we will later use `https://graph.microsoft.com/v1.0/teams/{team-id}/channels/{channel-id}/tabs` to create those tabs. 

#### method

Second thing we need to know is which method we want to use. As already explained, 

| Method | Meaning|
| ------- |:-----:|
| GET     |📖 read|
| POST    |✍ write|
| PUT | 📰 update|
| PATCH | ✒ update|
| DELETE | 🗑 remove|

If we now open the dropdown menu for the **Method** field in the HTTP action, we will see a representation of that: 
![different methods in HTTP action](https://github.com/LuiseFreese/blog/blob/main/media/how-to-get-started-with-http-requests-in-PowerAutomate/methods.png)

For an endpoint
#### headers
#### data (or body)







## Resources that might help you

# Doing Microsoft Graph Fundamentals learning path on MS Learn - Part 2

Welcome back to my series about the [Microsoft Graph Fundamentals learning path](https://docs.microsoft.com/en-us/learn/paths/m365-msgraph-fundamentals/) on Microsoft Learn. This is part 2, if you did not read [part 1](https://m365princess.com/microsoft-graph-fundamentals-learning-path-module-1/) yet, this is your chance to catch up! I will stay here and wait for you with a coffee ☕. 

This module is called **Configure a JavaScript application to retrieve Microsoft 365 data using Microsoft Graph** and we start with an

## intro

We are still sticking to the business scenario from module 1: We want to create an app that can access email, chats, files, meetings. To authenticate users, Microsoft 365 uses Microsoft Identity and we will need to use Microsoft Identity and Microsoft Graph to get the data we want to display in our app by using Microsoft Authentication Library (MSAL).

Wait, what? Don't worry, if you did not completely understand this. We will do this step-by-step.

## Understand the role of Azure Actiove Directory with Microsoft Graph

OK, we already understood that Microsoft Graph is THE API to access data in Microsoft 365 - but of course this data needs to be secured because we don't want everyone to access them, right? This is what we need Microsoft Identity platform for. Microsoft identity ensures that only authorized users (delegated permissions) and apps (application permisions) access data stored in Microsoft 365. The challenge now is to link Microsoft Identity (of which we will use Azure Active Directory) to our Microsoft Graph powered app. The module explains in detail how you register your app in Azure AD and retrieve your application ID. Later on, you will add this ID into the MSAL (Microsoft Authentication Library)'s code of your app to link to your Azure Active directory. 

But before we actually do this in an exercise, we will learn some theoretical stuff that we need later on. 

## Understand Microsoft Graph permissions and consent

Crucial to understand that a user or admin needs to consent before the app requests permission to access Microsoft 365 data via Graph, which is why we need to know a little bit more about:

### Scopes

All resources have specificic scopes, like *User.Read* (lets you read the profile of the signed in user) or *User.Read.All* lets you read the profiles of all users present in this directory. Of course you will want to only allow scopes that are necessary for the application. You can look up scopes for each request in the [official documentation](https://docs.microsoft.com/en-us/graph/api/overview?toc=.%2Fref%2Ftoc.json&view=graph-rest-1.0) and also learn about them while trying out requests in [Graph Explorer](https://aka.ms/ge).

### Permission types

We can perform requests on behalf of a user (delegated permission) and we can run background processes like creating, reading, updadting or deleting events of all calendars without the requirement of a signed-in user. This means, that an admin will need to pre-consent to these permissions. 

### Access tokens 

The module also describes how the magic with an access token works - and uses an awesome comparison for that! An access token is like a movie ticket - but your application gives it to Graph to show it has permission to access the requested data in Microsoft 365. LOVE this explanation so much! 

![Graph Access Token](https://github.com/LuiseFreese/blog/blob/main/media/GraphFun/GraphAccessTokenTicket.png)

We use this movie ticket/access token in the Authorization header of our HTTP request. 

## Register an application with Azure Active Directory

in this unit you learn which account type you can select when registering an app in AD and that web and single -page appls will require a redirect URI so that identity platform redirects ans sends security tokens after authentication. 

In case you wondered: There is a big difference between authentication and authorization. 

![Authentication and Authoruization](https://github.com/LuiseFreese/blog/blob/main/media/GraphFun/GraphFunAuth.png)

## Exercise - Register an application with Azure Active Directory

This exercise walks us step by step throufgh registering an app in Azure AD- highly recommend to follow this unit if you never registered an application before:

![app registration](https://github.com/LuiseFreese/blog/blob/main/media/GraphFun/appreg.png)

Let's now 

## Retrieve an access token using MSAL

MSAL will make Token interaction easier for you because with it we can acquire tokens from the identity platform to authenticate users and to access Microsoft Graph. 

![authentication flow](https://github.com/LuiseFreese/blog/blob/main/media/GraphFun/auth.gif)

Now that we understood the authentication flow, it's time to get our hands dirty with

## Exercise - Retrieve an access token using MSAL

To geth this straight - you will clone a repository either using git or by downloading a zip file. After opening this in Visual Studio Code (or any other editor) you will need to replace two placeholder with tenant ID and app ID from your Azure app registration. 

The unit walks you through some crucial parts of your app and lets you map this code to the authentication flow. 

![your Graph App 🚀](https://github.com/LuiseFreese/blog/blob/main/media/GraphFun/GraphApp.png)

Congratz! - you made it!

![Graph Fundamentals - You did it](https://github.com/LuiseFreese/blog/blob/main/media/GraphFun/GraphFun-didit2.png)




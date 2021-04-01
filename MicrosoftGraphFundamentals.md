# Doing Microsoft Graph Fundamentals learning path on MS Learn

![Microsoft Graph Fundamentals LearningPath](https://github.com/LuiseFreese/blog/blob/main/media/GraphFun/GraphFun.png)

This blog post will summarize how I did the brand new [Microsoft Graph Fundamentals Learning path](https://docs.microsoft.com/en-us/learn/paths/m365-msgraph-fundamentals/) . Microsoft Graph Fundamentals consists of 3 modules

1. What is Microsoft Graph - lets you understand the Graph services , and shows you how you can access user information from Graph using their learning playground called Graph Explorer. You will do a short exercise on that as well .

2. Configure a JavaScript application to retrieve Microsoft 365 data using Microsoft Graph - lets you understand how app registration works in Azure AD with permissions for Microsoft Graph powered apps and closes with 2 exercises using MSAL - making authentication easy. 
	
3. Access user photo information with Microsoft Graph - in this module you continue with the application you built in module 2 and learn how to retrieve a user photo and do an exercise about it. 

The whole learning path is estimated to be completed in ~75 minutes. Let's see how it goes :-) 

To be very honest: I worked with Graph before - see my blog posts here: [Microsoft Graph – M365 Princess](https://m365princess.com/category/microsoft-graph/) - but it's the first time I do this guided learning on Microsoft Learn. 

## What is Microsoft Graph

In super short: Microsoft Graph is a set of APIs that lets you access data in Microsoft 365 and use it for custom coded and low code applications. With this, Microsoft Graph is your key to data. Here are 3 super nice advantages of it: 

* across all Microsoft services, you can use one endpoint https://graph.microsoft.com - which makes it pretty straightforward
* documentation is awesome and there is a ton of learning material - like this learning path or the upcoming [Learn Together- Building apps with Microsoft Graph event ](https://learntogether-graph.splashthat.com/)
* you can try out Graph in [Graph Explorer](https://aka.ms/ge) - if you like to read more about that, read my blog post on [how to get started with Graph Explorer](https://m365princess.com/how-to-get-started-with-graph-explorer/)
* Microsoft Graph Toolkit (you will learn more about it later) makes authentication (my personal kryptonite) easy

For this module you will need to be global admin in a Microsoft 365 tenant. easiest way to have this is to [join the Microsoft 365 developer program](https://developer.microsoft.com/en-us/microsoft-365/dev-program) and get a free E5 subscription. If you are not familiar with this, go read [Julie Turner's article about it ](https://techcommunity.microsoft.com/t5/microsoft-365-pnp-blog/what-is-a-dev-tenant-and-why-would-you-want-one/ba-p/2036610), at least some basic JavaScript understanding and you should know what Azure Active Directory does. You will also need to have Node.js installed. 

The learning module introduces you to a business scenario so that it is easier for you to imagine which kind of applications we are talking about. In this scenario we want to bring together messages from chat and email, attended meetings, notes, key contact and relevant files. 




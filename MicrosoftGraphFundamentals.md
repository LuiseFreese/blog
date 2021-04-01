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

* across all Microsoft services, you can use one endpoint https://graph.microsoft.com - which makes development straightforward as you don't need to learn all the different APIs for mail and calendar and files and so on
* documentation is awesome and there is a ton of learning material - like this learning path or the upcoming [Learn Together- Building apps with Microsoft Graph event ](https://learntogether-graph.splashthat.com/)
* you can try out Graph in [Graph Explorer](https://aka.ms/ge) - if you like to read more about that, read my blog post on [how to get started with Graph Explorer](https://m365princess.com/how-to-get-started-with-graph-explorer/)
* Microsoft Graph Toolkit (you will learn more about it later) makes authentication (my personal kryptonite) easy

### intro - what is Graph?
For this module you will need to be global admin in a Microsoft 365 tenant. easiest way to have this is to [join the Microsoft 365 developer program](https://developer.microsoft.com/en-us/microsoft-365/dev-program) and get a free E5 subscription. If you are not familiar with this, go read [Julie Turner's article about it ](https://techcommunity.microsoft.com/t5/microsoft-365-pnp-blog/what-is-a-dev-tenant-and-why-would-you-want-one/ba-p/2036610), at least some basic JavaScript understanding and you should know what Azure Active Directory does. You will also need to have Node.js installed. 

The learning module introduces you to a business scenario so that it is easier for you to imagine which kind of applications we are talking about. In this scenario we want to bring together messages from chat and email, attended meetings, notes, key contact and relevant files. 

Our application could also grow later on and bring in data from more services like Windows 10 services or Enterprise Mobility and Security Services. We will not build this in total in this learning path, but we get a perspective, what we can develop, based on the needs of our organization.

### Understand Microsoft Graph Services

At the very heart of Graph we will find users and groups. In our application, we will need to both access data from personal scope of a single user (mail, messages, events) and from a group scope (teamwork). 

The module introduces you to some Microsoft Graph API calls and also shows you how the response will look like. Alls responses will be in JSON - in case you want to learn morwe about it, read this article by Bob German on [Introduction to JSON](https://techcommunity.microsoft.com/t5/microsoft-365-pnp-blog/introduction-to-json/ba-p/2049369)

Now to the even more interesting part: Apart from making direct API calls, Microsoft provides us with the Graph SDK (Software developer Kit) and we can use the client Graph SFK client libraries to even more easily call the Graph API. 

### Access user information from Microsoft Graph using Graph Explorer

This chapter introduces you to Graph Explorer -easily access it at [aka.ms/ge](https://aka.ms/ge), try out some sample queries! My blog post on [how to get started with Graph Explorer](https://m365princess.com/how-to-get-started-with-graph-explorer/) explains that in detail. 

#### Exercise - Access user information from Microsoft Graph using Graph Explorer

Time to access your own data! I strongly recommend to not play in your production tenant- especially if you do not only want to read data with **GET** requests but also want to write, update or delete data with **POST, PATCH, UPDATE, or DELETE** requests. Get yourself a Microsoft 365 developer tenant and use this. 

THis chapter teaches you how to modify permissions in Graph explorer and how tips help you. 

You will learn how to send a message to Teams via Graph - this is not a test, it will really appear in Teams 🚀

Let us 1'up this cool experience. Besides using this beautiful UI Graph Explorer provides you with 
* Access tokens used for authentication (recognizing who is a user) and authorization (looking up the correct privileges)
* code snippets for 3 different languages so that you can copy-paste them in your applications
* Microsoft Graph Toolkit components - coolest thing ever! If you are not familiar with MGT [go check it out ](https://www.youtube.com/watch?v=TbAZHvB5NEk)
* Adaptive cards snippets so you can easily build UI components for your apps

You see, this is the 'absolutely carefree package' provided by Microsoft Graph team. 

### conclusion

Not only is Microsoft Graph THE door opener to access all kinds of information and data across Microsoft 365 for developers and makers, the team also provides us with this amazing learning playground aka Graph explorer in which we can try out, learn, explore and get snippets for all kinds of development scenarios. After introducing you to some basic concepts on Microsoft Graph, you learn on a real world example how to use Microsoft Graph before we will continue to access data via Graph in a JavaScript application.

![Microsoft Graph Fundamentals - You did it](https://github.com/LuiseFreese/blog/blob/main/media/GraphFun/GraphFun-youdidit1.png)



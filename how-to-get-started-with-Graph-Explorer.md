# How to get started with Graph Explorer

Don't know what is the Microsoft Graph Explorer?Or have you already heard about it, but were not sure, how to get started and how this would help you as a developer and maker? In this post, I will show you, what Graph Explorer is, where are the benefits and how I use it. 

## What is Microsoft Graph

To understand what is the Graph Explorer, it is necessary to understad what is Microsoft Graph. 

> Microsoft Graph is the gateway to data and intelligence in Microsoft 365. It provides a unified programmability model that you can use to access the tremendous amount of data 
> in Microsoft 365, Windows 10, and Enterprise Mobility + Security. Use the wealth of data in Microsoft Graph to build apps for organizations and consumers that interact with ?
> millions of users. - [Read more here](https://docs.microsoft.com/en-us/graph/overview)

## What is Graph Explorer

Graph offers us a single endpoint https://graph.microsoft.com to access data in Microsoft 365, Windows 10 and Enterprise Mobility and Security and can be used by makers and developers. To get started to use the Graph API, Graph Team offers us a very cool tool called **Graph Explorer**. What does it do? Well, it lets us explore Graph! It's a learning playground in which we can try out requests, get responses, learn about permission scopes and more. 

To access Graph Explorer, visit [aka.ms/ge](https://aka.ms/ge) and make yourself familiar with it: 

![Overview of Graph Explorer](https://github.com/LuiseFreese/blog/blob/main/media/GraphExplorer/overview.png)

### Authentication

you can decide if you want to sign in or if you want to try out with sample data provided by Microsoft. I recommend 'playing' in your developer tenant; if you don't have one, [learn here how to join the Microsoft 365 developer program and get a developer tenant](https://techcommunity.microsoft.com/t5/microsoft-365-pnp-blog/what-is-a-dev-tenant-and-why-would-you-want-one/ba-p/2036610) The benefit of signing ion with your (developer) account is, that you can execute all requests including POST and DELETE requests, which is not possible in the sample account. 

When you click the gear-icon, you will find a short cut to the Microsoft 365 developer program website (to get your sandbox with sample data) and you can change the theme as it suits your needs best. I like dark mode most 🖤. 

![Microsoft Graph Gear](https://github.com/LuiseFreese/blog/blob/main/media/GraphExplorer/gear.png)

### Sample queries

Right below authentication, you will find sample queries - some may be disabled if you are not logged in. If you click on a sample, like I did in the screenshot below, Graph Explorer will send this HTTP request to Microsoft Graph - and get my joined teams. 

![Get my joined Teams](https://github.com/LuiseFreese/blog/blob/main/media/GraphExplorer/teams-channel.png)

Let's say I now want create a channel called 'Microsoft Graph' in the Team 'Insidious Word Domination Plans'. I first copy the ID of the Team from the response of that request and then use this ID in the next sample I try out, which is: 

![post a channel](https://github.com/LuiseFreese/blog/blob/main/media/GraphExplorer/post-teams-channel.png)

I then replace the `{teams-id}` placeholder with the copied ID value from the previous request and change the body to my needs: 

![post a channel to my team](https://github.com/LuiseFreese/blog/blob/main/media/GraphExplorer/post-teams-channel-replace.png)

In the **Modify permissions** tab I can learn about - and consent to permissions needed to execute this request





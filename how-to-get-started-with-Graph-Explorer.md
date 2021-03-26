# How to get started with Graph Explorer

Don't know what the Microsoft Graph Explorer is? Or have you already heard about it, but were not sure, how to get started and how this would help you? This post will show you what Graph Explorer is, the benefits, and how to use it. 

## What is Microsoft Graph Explorer

Microsoft Graph offers us a single endpoint https://graph.microsoft.com to access data in Microsoft 365, Windows 10, and Enterprise Mobility and Security and can be used by makers and developers. To get started to use the Graph API, the Graph Team offers us a very fantastic tool called **Graph Explorer**. 

What does it do? Well, it lets us explore Graph! It's a learning playground where we can try out requests, get responses, learn about permission scopes, and more. To access Graph Explorer, visit [aka.ms/ge](https://aka.ms/ge) and make yourself familiar with it: 

![Overview of Graph Explorer](https://github.com/LuiseFreese/blog/blob/main/media/GraphExplorer/overview.png)

### Authentication

You can decide if you want to sign in or if you want to try out with sample data provided by Microsoft. I recommend 'playing' in your developer tenant; if you don't have one, [learn here how to join the Microsoft 365 developer program and get a developer tenant](https://techcommunity.microsoft.com/t5/microsoft-365-pnp-blog/what-is-a-dev-tenant-and-why-would-you-want-one/ba-p/2036610). The benefit of signing in with your (developer) account is, that you can execute all requests including POST and DELETE requests, which is not possible in the sample account. 

When you click the gear icon, you will find a shortcut to the Microsoft 365 developer program website (to get your sandbox with sample data), and you can change the theme as it suits your needs best. I like dark mode most 🖤. 

![Microsoft Graph Gear](https://github.com/LuiseFreese/blog/blob/main/media/GraphExplorer/gear.png)

### Sample queries

You will find sample queries below authentication - some may be disabled if you are not logged in. If you click on a sample, like I did in the screenshot below, Graph Explorer will send this HTTP request to Microsoft Graph - and get my joined teams. We can see this in the request area (upper part) and the response area (lower part): 

![Get my joined Teams](https://github.com/LuiseFreese/blog/blob/main/media/GraphExplorer/teams-channel.png)

We now want to create a channel called 'Microsoft Graph' in the Team 'Insidious Word Domination Plans'. We first copy the ID of the Team from the response of that request and then use this ID in the next sample we try out, which is: 

![post a channel](https://github.com/LuiseFreese/blog/blob/main/media/GraphExplorer/post-teams-channel.png)

We then replace the `{teams-id}` placeholder with the copied ID value from the previous request and change the body to our needs: 

![post a channel to my team](https://github.com/LuiseFreese/blog/blob/main/media/GraphExplorer/post-teams-channel-replace.png)

In the **Modify permissions** tab, we can learn about - and consent to permissions needed to execute this request:

![modify permissions](https://github.com/LuiseFreese/blog/blob/main/media/GraphExplorer/modify-permissions.png)

But the awesomeness of this tool doesn't stop here - we get ready-to-use code snippets in different languages to insert them into our applications:

![code snippet](https://github.com/LuiseFreese/blog/blob/main/media/GraphExplorer/code-snippet-js.png)

And for some GET requests, we even get Adaptive Cards:

![Adaptive Card JSON](https://github.com/LuiseFreese/blog/blob/main/media/GraphExplorer/adaptivecards-json.png)

We can also try out Microsoft Graph Toolkit components right here, although I would personally recommend doing this in the dedicated [Microsoft Graph Toolkit Playground](https://mgt.dev). If you are unfamiliar with Microsoft Graph Toolkit, you can read how I started to use it - in my [blog series about MGT](https://m365princess.com/exploring-microsoft-graph-toolkit-lap-as-non-developer/) - I also recommend having a look at the beautiful [Microsoft Graph component](https://developer.microsoft.com/en-us/graph/components ) browser. 

Last but not least: Documentation to every sample is nicely tied in - click on the pop-out icon next to the sample queries: 
![pop-out that links to docs](https://github.com/LuiseFreese/blog/blob/main/media/GraphExplorer/pop-out-docs.png)

## How does Graph Explorer help building apps? 

I use Microsoft Graph in Power Apps with custom connectors or in Power Automate and Azure Logic Apps with the HTTP action to execute actions that are not present (yet). If you never did that but want to learn about it, here are two blog posts that will get you started: 

* [How to use a custom connector](https://m365princess.com/how-to-use-a-custom-connector-in-power-automate/)
* [How to get started with HTTP requests in Power Automate](https://m365princess.com/how-to-get-started-with-http-requests-in-power-automate/)

To get from the rough idea to a working up, I follow this process: 

1. Read the docs. I mean, seriously. learn, which endpoint you will need to call, which permissions you will need. 
2. Try out in Graph Explorer; when it works, proceed to step 3, in case it doesn't, go back to step 1 :')
3. Register your application in Azure AD with the permission scope that was needed for the request in Graph Explorer
4. Try out the flow/the action of your custom connector in a basic sample flow/app. 
5. Now replace all hard-coded values like a Teams ID with Dynamic Content from within your flow

You see, Graph Explorer is an amazing tool to learn and try out - it gets you a step closer to a working solution, but you do not need to worry upfront about app registration, permissions etc. It's a cool way to do a proof of concept - trying out if you can get, post, patch, update or delete the resources you like to before you start building your app. 

## Feedback and what's next? 

I am curious - which other tools help you developing with Microsoft Graph? Recently, [Elio Struyf published a VSCode extension](https://marketplace.visualstudio.com/items?itemName=eliostruyf.vscode-msgraph-autocomplete), that auto-completes Graph URLs for you, read more about it [here](https://techcommunity.microsoft.com/t5/microsoft-365-pnp-blog/new-vscode-extension-for-autocompleting-your-microsoft-graph/ba-p/2231013). Also, please share below what you build with Microsoft Graph? And how you use Graph Explorer? If you like to contribute to Graph Explorer, you can [check it out on GitHub](https://github.com/microsoftgraph/microsoft-graph-explorer-v4). I am looking forward to your feedback! 

❤ Sharing is Caring



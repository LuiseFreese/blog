# 10 things you should think about before you build an app

With Power Apps, we can rapidly build custom business applications that connect to our business data in a low code manner. This means, that not only professional developers can build applications, but that a lot more people will be able to make apps that fit their use specific use cases. 

But as development is not only writing code, there are certainly some things we should do before we actually hit [make.powerapps.com](https://make.powerapps.com). This post will list 10 things, that we should think about before we start building our app. 

## which problem does the app solve? 

This sounds obvious, that one would first do a proper analysis of value proposition and if the app they have in mind is actually a must-have solution to a specific business case or if its more or less 'yet another thing to use', although there are working alternatives in place. 

### understand your market 

Take some time segment your market and understand who (even if you build for your colleagues) needs your app. There will be roles, that will rely on your app, so it will become mission critical to them. Others will have already found applications that do similar things or the app doesn't solve a problem that is relevant to them. You can try to specifically look at underserved groups, such as blue collar workers and see if you can address their needs. Becoming obsessed with solving specific needs without assumptions is key here. This means, that you will need to validate the need that you have in mind. Even if you consider yourself a business user/power user /citizen developer, doesn't necessarily mean that you are your user. 

### psychological strain vs. energy of change

We've heard it probably before: To make users love an app, you will need to not only solve their pains or adress their needs, but also make it not too hard for them to change their behavior. If the energy they will need to change their behavior is higher than the psychological strain they face right now, they will not adapt your app, it's unfortunately as simple as that. 

## calculate value

Now you have a fair idea of who will use your app for which use cases and also know what users are doing now: 

* abuse other tools
* work on paper
* purchase 3rd party tools
* use unapproved shadow IT tools

and to which results this leads

* be busy with tasks that don't add value
* lose information
* cause additional costs
* severe risks in terms of data security, governance, compliance etc. 

tl;dr: more costs, less value. 

But take the effort to actually calculate the higher costs in terms of money and time and make an estimation for 12 or 24 months.

If the app you have in mind doesn't create value: take this as a learning opportunity. Of course, you can build apps 'for fun' or because you want to learn, or 'just because you can', but you should carefully distinguish those apps from apps that you want to internally pitch and 'sell'. 

## scope

The mother of all questions: Does it scale? Will you app be something for your personal productivity? Ease a workload for a small team? Or do we talk mission critical process? And even if you start with a small group of users to try out, is there a way where a broader audience could want to use it? Carefully indentify the scope of your app, as this will impact a lot of decisions. 

## data model

let's talk about your data model. Which datasource will you need to get data, in which services will you write data into? Which dependencies do you have, which other apps, flows, bots will be part of solution? Of course, the consultant answer on when to use what, will always be an 'it depends', but there are probably more reasons to look into different data sources as you are aware of

### licensing

As this is a pretty emotionally driven subject, we should handle this some more cool-headed. The idea of first understanding which needs your apps solves, who would benefot from it and how much money and time all users would save together by using it, is the counterpart of the licensing discussion. Of course, organizations tend to not want to pay for additional licenses, but the idea, that one could deliver great business value without any costs is somehow romanticized. Incorporate licensing costs for premium connectors (as you need them) in your calculation and if the app still delivers more value than it costs, you will probably get approval/green lights for it. 

### performance

The data sources we choose have not only impact on the licensing model, but also on the performance of our apps. For instance, if data needs to travel through an on-premises data gateway to a SQL server, most probably our app will not be as fast as if the data sits in Dataverse. For an elaborated comparison on this and other datasources such as Excel, SharePoint and more please read this article about [Considerations for optimized performance in Power Apps](https://powerapps.microsoft.com/en-us/blog/considerations-for-optimized-performance-in-power-apps/)

### developer and user experience

We can also see an impact on the experience you as a developer will have while building the app, depending on the datasource. If you ever 'loved' to deal with for example lookup columns from a SharePoint list, you will agree, that you didn't choose the easiest way to build an app. If you need to find workarounds as a developer, this will impact your user as well, which means, that their experience won't be as good as it could be. 

## lifecycle and delivery

Let's say, you are about to hit [make.powerapps.com](https://make.powerapps.com) and you have a fair idea what to do there to make an app. You will publish your app, share it, and mentally move on to something different. Now who cares for that app? Who will maintain your app? Things can easily change when we create apps on top of cloud services. This can easily become a not to be underestimated workload and probably you as a business user won't have capacity to cover that. And even if we are not talking about adjusting to things that changed: Who will support your app? Who will answer questions? Who will implement new feautures?

Delivery of a software should not only contain code (and yes, this applies to Power Apps as well), but also proper documentation, so that your organization does not rely on you for their mission critical process that you build in an app. Share knowledge about your app (what did you use, inputs, outputs, dependencies, licensing, data model, accessibility, feautures etc.) very early and best practice: Write it down to enable those, who need to maintain and support your solution. 



* mock up your app

* what is your mvp?


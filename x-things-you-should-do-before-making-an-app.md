# 10 things you should think about before you build an app

With Power Apps, we can rapidly build custom business applications that connect to our business data in a low code manner. This means, that not only professional developers can build applications, but that a lot more people will be able to make apps that fit their use specific use cases. 

But as sdevelopment is not only writing code, there are certainly some things we should do before we actually hit [make.powerapps.com](https://make.powerapps.com). A lot of developers will agree, that development is 20% about writing code and 80% about communications (meetings, gathering requirements, adjusting things). 

> If we now introduce 'low code development', we work on these 20%, not on those 80%. 

The issue with that is, that the narrative of 'everyone should make apps' doesn't reflect, that there is a lot of content out there to teach business users how to use controls, components, connectors and ask community when in doubt which function they should use. But there is about near to zero guidance around how to make better decisions about apps to build, and that apps, deliverd by power users, need to be documented properly, and that someone needs to offer support for that. 

These are things that pro-developers are very aware of, as DevOps is what most of them live and breathe every single day. But apart from IT departments, who will need to care about governance, application lifecycle management, etc., there are some things on business user side, that we should consider. 

This post will list 10 things, that we should think about before we start building our apps

## 1- which problem does the app solve? 

This sounds obvious, that one would first do a proper analysis of value proposition and if the app they have in mind is actually a must-have solution to a specific business case or if its more or less 'yet another thing to use', although there are working alternatives in place. 

### understand your market 

Let us take some time to segment our market and understand who (even if we build for our colleagues) needs our app. There will be roles, that will rely on our app, so it will become mission critical to them. Others will have already found applications that do similar things or the app doesn't solve a problem that is relevant to them. We can try to specifically look at underserved groups, such as blue collar workers and see if we can address their needs. Becoming obsessed with solving specific needs without assumptions is key here. This means, that we will need to validate the need that we have in mind. Even if we consider ourselves a business user/power user /citizen developer, doesn't necessarily mean that we are our user and specifically know what they need. 

### psychological strain vs. energy of change

To make users love an app, we will need to not only solve their pains or adress their needs, but also make it not too hard for them to change their behavior. If the energy they will need to change their behavior is higher than the psychological strain they face right now, they will not adapt your app, it's unfortunately as simple as that. 

## 2- calculate value

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

> tl;dr: it costs time & money

But we need to make the effort to actually calculate the higher costs in terms of money and time and make an estimation for the next 12 or 24 months in order. This will also help with any kind of approval process/ get funding. 

If the app we have in mind doesn't create (enough) value, we can take this as a learning opportunity to become better at meeting the needs of our (internal) customers. 

> The goal is to provide more value, not to deliver a poorly designed app which costs a little less. Of course, we can build apps 'for fun' or because we want to learn, or 'just because we can', but we should carefully distinguish those apps from apps that we want to internally pitch and 'sell'. 

## 3- scope

The mother of all questions: Does it scale? Will our app be something for our personal productivity? Ease a workload for a small team? Or do we talk about a mission critical process? And even if we start with a small group of users to try out, is there a way where a broader audience could want to use it? We need to carefully identify the scope of our app, as this will impact a lot of decisions. 

## 4- data model

Let's talk about our data model. Which datasource will you need to get data, in which services will you write data into? Which dependencies do you have, which other apps, flows, bots will be part of solution? Of course, the consultant answer on when to use what, will always be an 'it depends', but there are probably more reasons to look into different data sources as you are aware of:

### licensing

As this is a pretty emotionally driven subject, we should handle this some more cool-headed. The idea of first understanding which needs your app solves, who would benefit from it and how much money and time all users would save together by using it, is the counterpart of the licensing discussion. Of course, organizations tend to not want to pay for additional licenses, but the idea, that one could deliver great business value without any costs is somehow romanticized. Incorporate licensing costs for premium connectors (as you need them) in your calculation and if the app still delivers more value than it costs, we will probably get approval/green lights for it. 

> If the app isn't worth more than ~10$ per month and user, we should probably not be building it. 

### performance

The data sources we choose have not only impact on the licensing model, but also on the performance of our apps. For instance, if data needs to travel through an on-premises data gateway to a SQL server, most probably our app will not be as fast as if the data sits in Dataverse. For an elaborated comparison on this and other datasources such as Excel, SharePoint and more please read this article about [Considerations for optimized performance in Power Apps](https://powerapps.microsoft.com/en-us/blog/considerations-for-optimized-performance-in-power-apps/)

### developer and user experience

We can also see an impact on the experience you as a developer will have while building the app, depending on the datasource. If you ever 'loved' to deal with for example lookup columns from a SharePoint list, you will agree, that you didn't choose the easiest way to build an app. If you need to find work arounds as a developer, this will impact your user as well, which means, that their experience won't be as good as it could be. 

## 5- delivery

Let's say, we are about to hit [make.powerapps.com](https://make.powerapps.com) and we have a fair idea what to do there to make an app. We will publish our app, share it, and mentally move on to something different. Now who cares for that app? Who will maintain our app? Things can easily change when we create apps on top of cloud services. This can easily become a not to be underestimated workload and probably we as a business user won't have capacity to cover that. And even if we are not talking about adjusting to things that changed: Who will support our app? Who will answer questions? Who will implement new feautures?

Delivery of a software should not only contain code (and yes, this applies to Power Apps as well), but also proper documentation, so that your organization does not rely on you for their mission critical process that you build in an app. Sharing knowledge about our app (what did we use, inputs, outputs, dependencies, licensing, data model, accessibility, features etc.) very early by writing it down to enable those, who need to maintain and support our solution is important. Making it a habit to have a change log, where we document which features we add, remove or change, is crucial. If we think, that this is too time-consuming, we should be aware that someone will need to spend then even more time on fixing the lack of documentation for us. 

> A lack of documentation will create technical debt

## 6- what is your minimal l❤vable product?

Yes, I mean it! Define your minimal lovable product. If you only heard about a minimal viable product so far, please read this article [How to Build a Minimum Loveable Produc](https://medium.com/the-happy-startup-school/beyond-mvp-10-steps-to-make-your-product-minimum-loveable-51800164ae0c). In essence? Which features will we need to make users fall in love with our app? We will build this. We will not fall into the rabbit hole of delivering the whole software in one piece, but focus on the crucial parts. Once we published our first version, we gather feedback how we can improve it. Becoming comfortable with with a mindset, that a software is never finished can be a good idea as well. 

## 7- mock up your app

Finally- let's talk frontend - how shall our app look like? It's super tempting to actually start building screens an buttons and decide on colors etc., but we will get a better impression on the big picture of our app, if we first do a mock up. We may choose if we want to use a professional app for that or if we will draw something (I personally do this in OneNote). Defining which screens and buttons and forms and galleries you will need, will make the next steps easier. 

## 8- componetize your app

Reinventing the wheel is always painful, and to avoid this, we can should think about components in our apps, so that we reuse what we (or even other in this environment in the component library) build before. While controls are a good way to start learning and understanding how everything works, components are the way to not only accelerate our process of making apps, but making sure, that we easily adjust them and don't need to start over again for the next app we are making. It is also the low-code equivalent to the principle of ['Don't repeat yourself](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)'. Thinking upfront which controls we would repeatedly use and planning to componetize these will make sure that we don't need to start all over again. 

If you are not familiar with components you can watch [April Dunnams video about componetizing Power Apps](https://www.youtube.com/watch?v=RO6RMYauAlY) to get up to speed. Using component

## 9- accessiblity

Accessibility is nothing, that comes on top of a ready-to-publish app, but should be one of your core concepts straight from the beginning. The accessibility checker in Power Apps is a good start, but its always worth it to explore even more concepts. We can find lots of guidance how to ensure, that more people can benefit from our apps, if you need some inspiration, please read here [Microsoft Inclusive Design](https://www.microsoft.com/design/inclusive/).




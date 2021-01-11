# How to templatize a collaboration workshop as a Power App and provision the Teams that your organization will love

## intro

In my day to day life as a consultant, my customers need a lot of guidance on HOW to work with Microsoft Teams. After I educated them in what is Teams and everything in Microsoft 365 is interwoven, they ask: 

* which channels do we need?
* which apps and services should we pin in our channels?
* how many libraries do we need in SharePoint? And with which additional columns?
* how about lists? 
* and buckets in Planner? 
* who should be a Teams Owner? 

![it depends](https://github.com/LuiseFreese/blog/blob/main/media/itdepends.png "yes this is also a sticker")

My answer, as a consultant, will always be a "it depends". It depends on their objectives. To get them going, we would do a workshop to define their collaboration contract. In this workshop, I would provide them with knowledlege about tools and working behavior in Microsoft 365 and then give them some options what to do. We would write down everything and then someone would need to not only create the team and invite the members, but also:

* create channels
* create additional libraries and lists
* create columns
* create views
* pin the libraries to the teams channel they belong to
* create buckets in the Planner board
* pin learning resources for beginners into the channel general
* pin the collaboration contract
* delete the wiki tab

These workshops are very effective, as people

* gain knowledge
* reflect on their working behavior
* are enabled to make better decisions

But those workshops are not efficient as well, as they 

* are time consuming
* don't scale
* are expensive

Also, I got tired of asking and answering the same questions over and over again. Especially in this pandemic-driven world, which worked as an accelerator on Teams rollouts, I just got bored.  And whenever I get bored to do a certain thing, I will automate it. 

This blog post is about a work in progress. 

## solution & team up

My idea was to templatize those workshops as an app. The app should: 

* educate users about everything they should know to make decision that we would typically do in a collaboration contract
* get user's input on channel names, team members, metadata etc. 
* store all inputs in a list (SharePoint)

(You can also use a table in Dataverse for Teams or even an Excel Table (although I wouldn't recommend it)). 

To keep the app simple and adjustable I want to keep the whole logic in a flow (either Power Automate or Azure Logic Apps). For that, I teamed up with a rising star in the community, [Carmen Ysewijn](https://twitter.com/CarmenYsewijn). Carmen is a PowerPlatform Architect working at [Qubix](https://www.qubix.be/), Belgium and I met her last year in Warsaw at a Power Platform conference. I was more than impressed by her conciseness and #learnitall mindset. Carmen will help to transistion my Power Automate flow into Azure Logic Apps - she wanted to learn something new and we thought that an open source project would be a good idea to contribute to. 

## a simple PowerApp 

![Home screen of Teams Advisor App](https://github.com/LuiseFreese/blog/blob/main/media/TA-home.png "Purpose of this app is guide users through the art of teamwork and proviosion the team of their dreams for them")

Our Canvas App should be a simple interface to provide knowledge and get user's input, which is why we will have info-screens, which will display knowledge around a certain topic, like "What are channels" and process-screens, which will ask users with a form, what they want, like private or standard channels and which apps and sites and files should already be pinned to these channels. 

As this is a longer process we also want

* to guide users so that they know at which point of the app they are right now
* them to be able to go back and forth between screens and edit what they already put in
* show them a log which input they already gave

This makes sure that users stay motivated to proceed in the app. This gif illustrates what users will experience: 

![first steps of TeamsAdvisor App](https://github.com/LuiseFreese/blog/blob/main/media/TA-decision.gif "Guiding users through knowledge and decisions when it comes to create the teams of their dreams")

For each thing, we need to have a decision, I will follow these steps: 

1. provide knowledge
2. ask users in a form what they want to do
3. store input in variables

At the end of the whole process, I will update my SharePoint with a new item. 

## a complex system of flows

Now that I described the very straightforward app, it's time to have look at the logic. For my minimal lovable ♥ product, I decided to use Power Automate, but as already said in the intro, the goal is to transition to Azure Logic Apps. 

### Power Automate or Azure Logic Apps? 

Both systems have their pros and cons, but as much as it it easy to automate your personal work challenges in Power Automate, you shouldn't use it for organizational, business critical processes. Power Automate flows run in the context of a user, which means that we have the same challenges with files stored in OneDrive. People get different jobroles, leave the company or simply abandon this lovely pet project (which outgrew the sideproject level by far and should have been handed over to someone who can take better care of it). Also, we have better options to have the run history of a Logic App. 

Carmen had the very neat idea to split the huge flow (with 20+ API calls) into one parent flow and several child flows to make it easier for everyone to exactly pick what they need. 

This is only an exerpt of the flow to give you an idea that for most of the things I wanted to do, there are no predefined actions in Power Automate (nor in Logic Apps) but that we needed to define our http calls: 

![exerpt of the flow showing some http actions](https://github.com/LuiseFreese/blog/blob/main/media/TA-flow.png "a lot of https actions in a flow can make it a little confusing")

### HTTP request to SharePoint or Graph?

In our minimal lovable product, we use the SharePoint list item creation as a trigger and create channels, libraries, columns, views as requested by our user. I worked with both "send an HTTP request to SharePoint" actions and HTTP action towards Graph API (which I find better documented). The advantage of the HTTP reuqest to SharePoint is, that you do not need to register an app in Azure AD, but as we need that for all calls via Graph, this is not an argument anymore. 

### in complex flows, follow these steps 

1. Read the docs. Seriously. 
2. Try out your call in Graph Explorer. In case you don't know what this is, check out here: 
3. Try in a test flow
4. if it doesn't work, write a test protocol

## Next steps & Open Souce approach

Next steps to evolve from a minimal lovalble product to a good solution? 
1. Put some more work into the UI of the app
2. finish the Azure Logic Apps part

As we want to open source this solution, we will 

3. export app and flows
4. document everything and share it on GitHub 

This way, everyone can use it, share it, learn from it, and adapt it to their needs. We are open for all kind of feedback from you! 

3. write documentation
4. publish everything on GitHub

## Call to action

1. follow [Carmen Ysewijn](https://twitter.com/CarmenYsewijn) and myself on twitter
2. stay tuned, and give us feedback, we highly appreciate it!
3. If you want to watch me explaining the solution,  you can do this in episode 111 of PnPWeekly 

# How to templatize a collaboration workshop as a Power App and provision the Teams that your organization will love

## intro

In my day to day life as a consultant, my customers need a lot of guidance on HOW to work with Microsoft Teams. After I educated them in what is Teams and everything in Microsoft 365 is interwoven, they ask: 

* which channels do we need?
* which apps and services should we pin in our channels?
* how many libraries do we need in SharePoint? And with which additional colunmns?
* how about lists? 
* and buckets in Planner? 
* who should be a Teams Owner? 

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

## solution & team up

My idea was to templatize those workshops as an app. The app should: 

* educate users about everything they should know to make decision that we would typically do in a collaboration contract
* get user's input on channel names, team members, metadata etc. 
* store all inputs in a list (SharePoint)

(You can also use a table in Dataverse for Teams or even an Excel Table (although I wouldn't recommend it)). 

To keep the app simple and adjustable I want to keep the whole logic in a flow (either Power Automate or Azure Logic Apps). For that I teamed up with a rising star, Carmen Ysewijn. Carmen is a Functional Consultant working at Qubix, Belgium and I met her last year in Warsaw at a Power Platform conference. Carmen will help to transistion my Power Automate flow into an Azure Logic App - she wanted to learn something new and we thought that an open source project would be a good idea to contribute to. 

Oh, did I say open-source? Yes. The plan is to export app and flows, document everything and share it on GitHub so that everyone can use it, share it, learn from it and adapt it to their needs. 

## a simple PowerApp 

Our Canvas App should be a simple interface to provide knowledge and get user's input, which is why we will have info-screens, which will display knowledge around a certain topic, like "What are channels" and process-screens, which will ask users with a form, what they want, like private or standard channels and which apps and sites and files should already be pinned to these channels. 

# Power Platform Licensing

## Overview

This article shall give you a detailed and easy to understand overview about licensing/pricing regarding Power Platform. It won't replace all other bits posted across docs.microsoft.com but gives you a solid understanding which licenses you will need for your solutions. You will learn about Core Licensing Concepts and Levers and we will give you some guidance plus showcase some licensing scenarios. 

## Core Concepts

### Seeded vs Standalone

We distinguish between Power Apps for Office 365 License  and Power Apps Standalone License

#### Power Apps for Office 365 License
Power Apps and Power Automate for Office 365 means customizing and extending Office with low code. Users can build and run unlimited amount of apps and flows using SharePoint, Excel and dozens of other standard connectors. The license to use Power Apps and Power Automate for Office 365 are included in most Office 365 and Microsoft 365 licenses, which means that you don't need to purchase an additional license for Power Apps and Power Automate if you stay inside of the huge range of Standard Connectors . A list of Standard connectors can be found here: [insert link]. As soon as you want to use a premium connector (which is indicated by the word _Premium_ next to the Connector name, you will need a PowerApps Standalone license. Please note, that this Standalone license is not only required for the owner of that app but for everyone, that uses the app as well. Power Apps licensing has no "free consume concept". Microsoft will refer to the Power Apps for Office 365 license as "seeded license", as they are seeded in another license you already purchased. 

#### Power Apps Standalone License

As soon as you use a premium connector, you will need a Power Apps Standalone license, because the license seeded in your Microsoft 365 license won't be sufficient anymore. For Standalone license, we distinguish between Power Apps Standalone per user plan and Power Apps Standalone per app plan. 

##### Power Apps "per user" plan 

is the equivalent to an "All You Can Eat" Buffet. It means, that users can build and run as many apps using Premium Connectors as they wish. 

##### Power Apps "per app" plan

is the equivalent to an à la carte menu. It means, that users can build and run a single app.

Any Power Automate flow that’s working on the same data as the app, doesn’t require an additional license for the flow: We don’t need multiple licenses to run one use case.

### Dataverse and Dataverse for Teams

Dataverse (previously known as Common Data Services / CDS) is one of the Premium connectors that is not seeded in Microsoft 365 licenses and requires a Power Apps Standalone license (either per user plan or per apps plan depending on how many apps you want to run). 

[short paragraph on what is Dataverse] 

The required license resulted in a barrier when it came to empowering users to make good decisions where data should sit in their apps. They abused SharePoint lists and even Excel tables as backends for data, which wouldn't be the best choice to do [short paragraph or link why Excel and SP are not always the best choice]. As Microsoft Teams works as platform for millions of users and Microsoft wanted to give everyone the power create apps as part of that platform, they made an exception to Dataverse: If you want to use Dataverse for you your apps you build inside of Teams, you won't need a Power Apps Standalone license anymore. The license is then called "Dataverse for Teams" and is a seeded license in Microsoft 365, which means that you do not need to pay extra for that. 









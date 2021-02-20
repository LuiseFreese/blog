# Power Platform Licensing

## Overview

This article shall give a direct and easy to understand overview about licensing/pricing in Power Apps, Power Automate and Power Virtual Agents along with the key features and services associated with them. It won't replace all other material posted across docs.microsoft.com but gives you, the reader, a solid understanding as which licenses apply to your solutions. This article focuses on Core Licensing Concepts and Levers along with guidance and licensing scenarios. The goal is to provide the citizen developer with the bulk of the information to make decisions on the spot or mitigate the research effort and time to confirm nuance cases or specialized use cases.  

Please note that the scope of this article excludes as well as other licensing associated with third party connectors or services.  

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

## Guidance

Of course we do not want to encourage anyone to work around purchasing licenses, but to make best use of your seeded license, we advise you to 


### Do your Apps/flows in Teams wherever possible to be able to use Dataverse with no additional cost

If you need Dataverse, let your Power Automate flows and Power Apps live in Microsoft Teams, because this way you can use the power of Dataverse as Dataverse for Teams which means that the license is included in your Microsoft 365 license. You should pick Dataverse for Teams over other other premium connectors, especially in enterprise-scale applications, because it is the preferred way to store your data, see also [Considerations for optimized performance in Power Apps](https://powerapps.microsoft.com/de-de/blog/considerations-for-optimized-performance-in-power-apps/). When you are very experienced in Microsoft 365, you will probably consider to store data in SharePoint lists, also as SharePoint is a standadrd connector, which means that you don't need a Power Apps Standalone license, but Dataverse has more capability, is faster and doesn't have issues like "only 12 complex columns in one view", 5000 items threshold and more. 

### To learn Power Platform, use the Community Plan

There is a [free Community Plan to learn Power Platform](https://powerapps.microsoft.com/en-us/communityplan/). You are not allowed to use it in production, but can try out things and have access to all premium connectors. You can use this free community plan also in a free [Microsoft 365 developer tenant](https://developer.microsoft.com/en-us/microsoft-365/dev-program). 

### Think Governance early with COE

### Prepare for change
The license docs are updated often (lately its been monthly) Take time to review changes as often as you can to catch those not heavily publicized.
Think of your scale and what that is worth to you or your organization.









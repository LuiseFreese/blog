# Power Platform Licensing

## Overview

This article shall give a direct and easy to understand overview about licensing/pricing in Power Apps, Power Automate and Power Virtual Agents along with the key features and services associated with them. It won't replace all other material posted across docs.microsoft.com but gives you, the reader, a solid understanding as which licenses apply to your solutions. This article focuses on Core Licensing Concepts and Levers along with guidance and licensing scenarios. The goal is to provide the citizen developer with the bulk of the information to make decisions on the spot or mitigate the research effort and time to confirm nuance cases or specialized use cases.  

Please note that the scope of this article excludes as well as other licensing associated with third party connectors or services.

## Core Concepts

The last iteration of this article attempted to break down the original licensing guide into key concepts where important topics ended up being separated into the main applications in the same manner as the document itself and effectively duplicating information that was subject to frequent changes.  Rather than repeat published documentation, this section imparts initial guidance based on topics that span the three main Power Platform systems diving into some detail where they have impact on the others.  

The Core Concepts are as follows:

### Review the definitive licensing guide published monthly

Before going through the guidance, it is important to refer to the ultimate authority on licensing which has been updated on a monthly basis for several years now.  The licensing document may be download via links in Power Apps, Power Automate and Power Virtual agents' main pages and have maintained the following URL to point to the most current version for your language or region:

- <https://go.microsoft.com/fwlink/?linkid=2085130>

There are two important things to note in that PDF download.  

First is that changes from the previous versions will be noted in an appendix (currently appendix c) and should be the first point of reference after reading through articles such as this one or asking questions related to Apps, Flow or Bot changes since their implementation.  

The second item to note is that one will never see prices here as those will always be region specific in addition to being subject to specific customer licenses in general and directly with Microsoft or through a third party vendor. Prices and changes in prices will always reflect the underlying information contained in the download but be aware that not all tenants' Billing administrations screens will have a clear association as those screens may, for various reasons, contain important references to previous or depracated products.

### Seeded vs Standalone

The most important concept that potentially simplified most licensing questions is the one of "Is it included with my Office 365/Dynamics 365 License?".

"Seeded" in this case relates specifically for "inclusion" to another license type even though, tecnically, Power Platform systems will always run in context of an Office 365 tenant and have "limited use rights" which is a specification of what may be done at that level.  "Standalone" in this case means the license is not reliant on the other license type and it typically infers access to many more services that what is included with the main tenant.  

Since the rules for the temamt license type may change, it is recommended that a monthly review of Appendix B in the latest version of the license guide should be checked.  On that note, guidance offered as of this publication is that there has not been a significant change in the license types that are counted for inclusion and as of March 2021, the following license types are the main exceptions for general,limited use rights:

- Microsoft 365 F1
- Windows 10 Pro
- Windows Enterprise E3
- Windows Enteroruse E5

Dynamics 365 licenses, as a rule, have always counted for at least "limited use rights" while more premium services where noted in the guide are more powerful and inclusive of some but not all premium features.

The biggest and most significant change in 2020 was the introduction of Dataverse (formerly Common Data Service or CDS) in Microsoft Teams as a separate and size limited environment where its use is considered included with the Seeded license rather than a Premium service requiring the Standalone license or premium Dynamics 365 seat.  This change is made even more significant because now Power Virtual Agents, a service that requires the use of Dataverse, now has a scenario free of additional charge outside of its monthly, capacity based cost.  

 The conclusion of this core concept is that answering the "is it Seeded" question is one where at a glance, the cost for use may be immediately clear especially if usage revolves around Microsoft Teams.  From here, the levers for determination become a case of applying layers of nuance from the specific seat licenses, to ways of running the solutions and then through more direct elements such as capacity and features.

### Standard versus Premium Data Connectors

If there is a main point of guidance that may be delivered at this stage, it is the one recommending the design of solutions to "make the most" of what comes out of box or included with Office 365 or the basic level of Dynamics 365 which includes considering Microsoft Teams as the lynchpin application.  This may mean making compromises for some usability or conveninience but consider that the "cost" for avoiding the financial obligation for the organization or the users.

With that noted, business requirements and necessity will always drive the solution that is eventually used and the next question after the decision to use a Premium Connector will become the next nuance group around the scale of use by the specific Power Platform component. Also, keep in mind that some premium connectors, especially to third parties, may include their own costs for subscriptions or access.

### Power Apps "per app" versus "per user"

The question of scale in Power Apps is the difference of accomodating a single user to utilize a single app or unlimited apps. In the United States, the price point difference on a monthly basis is 4 times ($10/month/"one" app  versus $40/month/unlimited apps). Although there is a capactity limited which will be discussed later, the main nuance is that a "one app" package is actually two apps in any combination of canvas or model applications. This can make a major difference as one would be counting pairs of application for each license and certainly sway a decision where there are only a few applications actually required.  

The case of the "per user" license, sometimes called the "All you can eat Buffet" plan, now becomes a question whether the user will be one requiring more than 6 applications or if there is a need for more capacity or services such as the ability to access an "unlimited number" of custom portals or having more Dataverse space and make more API requests in a day.  The latest licensing guide will always clarify those differences as well as any new included features.  It is important to remember that per app or per user does not limit the number of premium connectors that may be used but costs specific to those connectors will still apply.

### Power App with Power Automate

In the original introduction of the new licensing and as a consequence of the older model, it was thought that a separate license would be required for a Power App to use A Power Automate Flow when, in fact, it is only the cost of the Power App that will apply even if the Premium connector is only accessed via the flow.  The key guidance here is to understand the use case of the flow itself whether it is created to service the app or if it is the type that is expected to be shared or used outside of the application as it will then be a case of selecting the appropriate Power Automate license.

### Dataverse

Dataverse (previously known as Common Data Services / CDS) is one of the Premium connectors that is not seeded in Microsoft 365 licenses and requires a Power Apps or Power Automate Standalone license. Dataverse is also required when using Power Virtual Agents as well as data features in Dynamics 365 and, is in fact, originally the data storage solution introduced with Dynamics.  

Dataverse was intended to fulfill many requirements behind the support of business data with minimal data developer interaction.  Dataverse tables come with built in fields and automated processes supported by Microsoft to alleviate may of the day to day Database Admininstrator (DBA) duties one would find in an organization using MS SQL Server or other database platform.  In its orginal form, it came ready to support the productivity and business information in Dynamics and may now be used by the organization for their own data requirements.  It's use was considered PREMIUM in the same manner as connecting to a SQL Server connector due to the power afforded by the access.

The Premium connector designation resulted in a barrier when it came to power platform design decisions for data access. The seeded license aspect tended to drive data to SharePoint Lists or Excel Files which did not support data management best practices in the manner of a true database platform. SharePoint Lists could not be linked and joined in relationships as natively as a database table and data in Excel are potentially locked when being accessed by an application or process. The difference was not just a case of paying for convenience but also in accommodating critical business requirements in appropriate and performant ways. In those cases, the choice to not use the Power Platform over another custom solution because of cost was quite common.

Microsoft has recognized this blocker and has chosen to leverage Microsoft Teams as their own "starter" environments to promote usage and to consequently further adoption and perhaps innovation as the entry point for implementation now aligns with the same entry point for other Power Apps and Power Automate solutions even bringing in Power Virtual Agents which itself starts at a fairly steep monthly charge.  This core concept becomes important because not only can guidance now point to more appropriate solutions but because adoption will certainly drive the need to handle cases where more capacity and scale will be required but this time in the same context as other storage and capacity decisions covered here.

### Power Automate "per flow" versus "per user"

There is a major distinction in Power Automate over Power Apps when looking at the licensing unit.  Where Apps look at usage in all cases, Flow licenses are split between the permission to CREATE unlimited flows per use or to Implement specific flows to SERVE unlimited users.  These are two very different bases where the first effectively gives a single user the "All you can Eat" power for the main licence while the other is the case of a SET of Flows packaged for the organization to be used anywhere and in any and all context.

The manner of how a Flow is TRIGGERED potentially makes the decision.  Flows triggered from a Power App are included in all cases as it assumes the premium connector will be part of the app itself.  Flows that do not touch premium connectors or who are triggered from non premium sources such as SharePoint lists and MS Forms will also not count for extra cost.  If none of these conditions apply, it is now a case of the person who created the flow as the designated licensee where the act of getting licensed effectively allows that user to create any number of flows they wish assuming the flows only serve the purpose of the user and is not shared with others.

A common question is if a Flow is created for a SharePoint List and many users interact with that list, will there be a cost for all the users.  The answer is if the flow does not use a premium connector such as call Dataverse in the full production environment and not the teams environment, the cost of the flow must either be for each user or a per flow license is used so that all users of the list may be serviced by it.  

As a guidance for the "per flow" cases, remember that the initial license starts with 5 flows and may be increase one flow at a time at a cost about 7 times to cost for an individual license.  The expectation is that larger organizations or solutions that affect many will benefit from the fixed monthly cost versus a comparable per use cost in a pure Azure function.

### Purchasing Capacity and Storage

The Power Platform is made very viable through the option of "the Add-in" where storage and capacity may be purchased to fill gaps in those areas.  The main difference for this type of A la Carte service over platforms like Azure is that the extras are purchased as a package rather than a case of "pay as you go" or as usage charges.  Power Virtual Agents provide capacity in the same block as its initial monthly license cost.  Power Apps and Power Automate are optimized by preset support expectations such as a daily limit on API calls or a reserved storage area.

This concept is the impetus for guidance recommending the reviewing usage and capacity from the Power Platform administration areas and to be at least familiar with the reports and dasboards if not adding the review to the regular course of operations.

Storage and Capacity are considered tenant wide resources and when deciding cost impact, they should be considered in those terms as they can make a difference if the user case is to support a single user's application versus one for the larger organization. On that point, add ins such as AI Builder work in the same way where the ability is added at the tenant level and where the benefit could be seen as one for the wole organization being served or for the organization to serve a specific need.  

### Trials and Free Services

A question that has arisen for users who want to evaluate or learn elements of the Power Platform is how much that effort may cost and it may sometimes be a hindrance to those outside the people specifically licensed.  It is important to note that there are always trials and services provided by Microsoft to mitigate this from direct 30 day trials using the Power Platform to implenting a personal environment via the technical community resources as well as to obtaining a personal Developer Tenant where the user has nearly all the power as an E5 tenant level organization.  The ability to move what has been learned or separately developed into the production organization is being enhanced constantly by Microsoft and the community, the latter of which provides not just samples but process knowledge and guidance. Checking in with a community contributor on whether a solution has a license impact is a good way to fast track decision making in this regard especially if significant time has passed since the contribution.

The important piece to note in this concept is that although there will always be ways to "try things out", those ways will have limitations, the least being time.  A Developer tenant user will still need to pay for the use of Power Platform after the specific trial period is over and even though the current policy for the tenant may be an automatic 90 day reneway based on usage.  Taking advantage of "free" services is certainly recommended but it is good to keep a close eye on articles like this to be prepared for costs that may have to be incurred.  

See the guidance section below on more information using the Community Plan.

### The Power Virtual Agent Subscription

Outside of MS Teams, a major concept in Power Platform is the one of the subscription which is similar to storage, capacity and Add-ins in that they are at a tenant level billed to the organization as a whole and not by individual.  Just like storage and capacity, there is a limit to usage where going over can be accommodated by purchasing capactity or another license which stacks on to the original.  There is some uncertainty, however, for Power Virtual Agents as to the exact manner it uses that capacity and although the licensing guide is very clear on the units of use, there is no current map or list that directly assigns an activity by the underlying AI system to a specific number of units.  It is because of that that usage analysis is very important especially at the end of a trial or single month but, at least for this time, on an on going, monthly basis with an eye on the bot solutions themselves.

Guidance at this stage reiterates implementation via MS Teams if that is the appropriate delivery host but if it is not, guidance calls for making the most of the enabled feature to being down the ROI costs.  Refer to the guidance section here for more on cost comparisons.

Finally on this concept, when looking at the information in the licensing document, note that there are storage and capacity assumptions when implementing this in either production or in a MS Teams environment so be sure to include that information in design decisions.  

## Guidance

Some guidance has been covered as part of the Core Concepts discussions of the previous sessions.  This section covers additional as well as contributed guidance notes that underscore or clarify key points for decisions based on licensing.

### Do your Apps/flows in Teams wherever possible to be able to use Dataverse with no additional cost

If you need Dataverse, let your Power Automate flows and Power Apps live in Microsoft Teams, because this way you can use the power of Dataverse as Dataverse for Teams which means that the license is included in your Microsoft 365 license. You should pick Dataverse for Teams over other other premium connectors, especially in enterprise-scale applications, because it is the preferred way to store your data, see also [Considerations for optimized performance in Power Apps](https://powerapps.microsoft.com/de-de/blog/considerations-for-optimized-performance-in-power-apps/). When you are very experienced in Microsoft 365, you will probably consider to store data in SharePoint lists, also as SharePoint is a standadrd connector, which means that you don't need a Power Apps Standalone license, but Dataverse has more capability, is faster and doesn't have issues like "only 12 complex columns in one view", 5000 items threshold and more.

### To learn Power Platform, use the Community Plan

There is a [free Community Plan to learn Power Platform](https://powerapps.microsoft.com/en-us/communityplan/). You are not allowed to use it in production, but can try out things and have access to all premium connectors. You can use this free community plan also in a free [Microsoft 365 developer tenant](https://developer.microsoft.com/en-us/microsoft-365/dev-program).

### Think Governance early with COE

The Center Of Excellence (COE) Solution available from Microsoft and support with input from the community is an excellent way to control and manage not just the solutions but the costs related to licensing.  It ironically requires a license to run since it uses and needs Dataverse outside of Microsoft Teams and although it could modified to mitigate the cost, the strong recommendation is use it as it is designed if your organization anticipates adoption beyond a few power users or key developers.  

### Deciding to use Premium Connectors over Standard Connectors - Pricing your solution

As noted earlier, all efforts to work within the Standard Connector list or within Teams in the context of Dataverse is highly recommended but as highlighted by the change Microsoft itself made to make Dataverse more accessible via teams, there will be use cases where the work around is more painful and potentially more expensive through added user effort (their time is money) or delicate processes where small errors or lost time can affect diret financial impact.  

A case in point would be a case where the act of avoiding the premium HTTP API connector to get critical information from a third party service just to avoid the per user or per app fee when creating the custom application to put the information into a dashboard in teams or SharePoint might cost more to develop and maintain or even to run as a "pay as you go" service in Azure.  With that hypothetical scenario, the key point is to know how to price the competing solutions.  The Licensing guidance for Power Platform is direct at giving cost for the organization while tools such as the Azure Calculator will help pin down infrastructure level costs. The Wild card is now the development cost for either creating the Power Platform solution with rapid development tools and lower developer cost or the enterprise developer team using premium tooling and techniques that would need separate Service Level Agreements that are part of the Power Platform licenses.

In this last point, guidance calls for looking at the complete picture and not just the license effect of a single implementation and a note that the tools to do so are readily available.

## Scenarios from the Field

This article is meant to be a living and growing document that includes contributions of the community to help with decisions and understanding.  Sometimes, inspite of core concepts and guidance, there are nuances that may be used to either drive home knowledge or give pause and provide additional even if nuanced factors for consideration. We welcome your contributions to help fill out this section while adding a last piece of guidance to return here as often as you need to update the main licensing document to stay ahead and on top of this topic.

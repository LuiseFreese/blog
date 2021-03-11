# 5 commands to try in CLI for Microsoft 365 to fall in love with it

After I blogged about [How to send Adaptive Cards with CLI for Microsoft 365](https://techcommunity.microsoft.com/t5/microsoft-365-pnp-blog/how-to-send-adaptive-cards-with-cli-microsoft-365/ba-p/2143466) and also used [CLI to compare different ways to create SharePoint lists](https://techcommunity.microsoft.com/t5/microsoft-365-pnp-blog/should-we-use-sharepoint-rest-or-microsoft-graph-api-in-power/ba-p/2182284), I found some more commands, that made me fall in love with it. CLI for Microsoft 365 has three main benefits from my point of view: 

* 💻 it's platform-agnostic and even works on [Azure Cloud Shell](https://azure.microsoft.com/en-us/features/cloud-shell/?&ef_id=Cj0KCQiAnKeCBhDPARIsAFDTLTIDlnMADqglDP6WLiQ_Yq23PQL7px3W9ElP7bBanGB6762ENh6DzScaAsTxEALw_wcB:G:s&OCID=AID2100049_SEM_Cj0KCQiAnKeCBhDPARIsAFDTLTIDlnMADqglDP6WLiQ_Yq23PQL7px3W9ElP7bBanGB6762ENh6DzScaAsTxEALw_wcB:G:s) so that every browser can be my admin machine 
* 💡 the syntax is easy and almost intuitive to use for me, although I only start to not use the UI for everything I want to manage in my Microsoft 365 tenant
* 🚀 documentation is clear and concise with amazing code samples. 

Bonus: 💖 Caring maintainers and awesome contributors 

In case you never used CLI for Microsoft 365 before, please first read [how to get started with CLI Microsoft 365](https://m365princess.com/how-to-get-started-with-cli-microsoft-365-and-adaptive-cards/#how-to-use-cli-microsoft-365) were I explain how to install the CLI. 

My screenshots will show that I work in PowerShell in Visual Studio Code, but you can use any other shell that you like to use. 

## Get a list of Power Apps

Wouldn't it be nice to get a list of apps? This is what I thought as well. Looking into the [CLI for Microsoft 365 documentation](https://pnp.github.io/cli-microsoft365/cmd/pa/app/app-list/) we will find the command to list all Power Apps in this tenant, which gives us an idea, what makers are doing to be able to offer help and support as well. 

After having installed CLI and logged in: 

Run `m365 pa app list`

which will get you exactly that list - with internal names and display names:

![m365 pa app list](https://github.com/LuiseFreese/blog/blob/main/media/5-commands-in-CLIMicrosoft365-to-fall-in-love-with/list-pa.png)

## Get an overview about custom connectors in an environment

If we allowed makers to build their own custom connectors to fulfill their very unique needs, we might want to have a look on that as well. If you never build a custom connector, you can read my blog post about [how to build a custom connector](https://m365princess.com/how-to-use-a-custom-connector-in-power-automate/).

Run `m365 pa environment get --name Default-<name of your default environment>`

Now where do we get this `<name of your default environment>`from? This is your tenant ID, which you can obtain from the URL of any Power App running in this environment or you can copy it from [portal.azure.com](https://portal.azure.com), where you will find it in Azure Active Directory as **Tenant ID**. 

![obtain environment name in PA URL](https://github.com/LuiseFreese/blog/blob/main/media/5-commands-in-CLIMicrosoft365-to-fall-in-love-with/url-powerapps.png)

* Copy this Tenant ID
* Replace `<name of your default environment>`with this Tenant ID
* Run the command

## Get a list of users

Obtaining a list of users on a specific SharePoint website will be helpful to get their IDs. 

Run `m365 spo user list --webUrl "https://m365princess.sharepoint.com/sites/m365princess"`by replacing my webUrl with the tenant you are logged in and a site URL you want to query. 

The response will be something like this: 

![list spo users](https://github.com/LuiseFreese/blog/blob/main/media/5-commands-in-CLIMicrosoft365-to-fall-in-love-with/list-spo-users.png)

## Get a list of external users

Another cool starting point is to get a list of external users. As internal users tend to invite a lot of guests, it could be helpful to have an overview on external users and see when these external users were created. You can also obtain the ID of of users. 

`m365 spo externaluser list`,

![get external users](https://github.com/LuiseFreese/blog/blob/main/media/5-commands-in-CLIMicrosoft365-to-fall-in-love-with/list-external.png)
 
## remove users 

With 

`m365 spo user remove --webUrl "https://contoso.sharepoint.com/sites/HR" --id 10 --confirm`

we can remove a users. 

Hope that you now got an idea how you can get started with CLI for Microsoft 365 :-) Still I am curious, what you would use it for? Which are the commands that you use every single day? Please comment below! 


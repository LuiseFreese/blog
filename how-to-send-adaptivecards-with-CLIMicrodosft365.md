# How to send Adaptive Cards with CLI Microsoft 365

In this blog post I want to explain how you can send an Adaptive Card with CLI Microsoft 365. I will guide you from zero to hero 🚀, so even if you don't know anything about  the CLI Microsoft 365 or about Adaptive cards, don't  stop reading, you will be able to do that in a few minutes- I promise! 

## What is CLI Microsoft 365?

Lets first get us all on the same page and clarify, what CLI Microsoft 365 is and why we should use it: It is a CLI (Command Line Interface) which let's us manage Microsoft 365 from any kind of OS: It doesn't matter if we work on Windows, MacOS or Linux. Previously, some configurations were only possible by PowerShell for Windows, which limited a lot of admins. Even if you work on Windows and are pretty fine with using PowerShell, CLI might be a nice alternative to try out. 

### How to use CLI Microsoft 365 

I will now describe your first steps:

#### Install Node.js

To use the CLI MIcrosoft 365, you will need to install Node.js - Please follow these steps: 

* go to https://nodejs.org/en/
* download the LTS version of Node.js
* install Node.js

> If in doubt, if you have the correct version installed or if you need to use different versions of Node.js, pleas read [Use Node Version Manager to develop your SPFx apps](https://techcommunity.microsoft.com/t5/microsoft-365-pnp-blog/use-node-version-manager-to-develop-your-spfx-apps/ba-p/2128393) [Toni Pohl](https://twitter.com/atwork)


#### Install CLI Microsoft 365

Now that you have Node.js installed, we can continue with installing the CLI Microsoft 365. You can choose if you want to use PowerShell or the Terminal in Visual Studio Code or any other CLI. I like to use the terminal in Visual Studio Code, because links are render to be clickable and this saves me copy/pasting links into nmew browser tabs. But if you don't have Visual Studio Code or if you like to use PowerShell, that is perfectly fine as well. To install CLI Microsoft 365, run the command: 


`npm i -g @pnp/cli-microsoft365`

In case you wonder: 

* the `i` is an alias for `install`
* the `-g` means that we want to install this package globally

#### Login

Now that we installed CLI Microsoft 365, it's time to actually do something here. But before we can get or post anything, we will need to log into our tenant. Pro Tip: You can use your [Developer Tenant](https://techcommunity.microsoft.com/t5/microsoft-365-pnp-blog/what-is-a-dev-tenant-and-why-would-you-want-one/ba-p/2036610) to do that! Run the following command: 

`m365 login`

In response you will be asked to open a webbrowser and login with a code. If you are using Visual Studio Code, you can click on the link, please copy the code upfront. If you use PowerShell, you will need to copy/paste the URL into a new Browser tab. 

![Login](https://github.com/LuiseFreese/blog/blob/main/media/how-to-send-adaptivecards-with-CLIMicrosoft365/login.png)

After you pasted the code, 

* click **Next**
* pick an account out of the list of accounts

You will be seeing this message and can close this browser tab- we won't need it anymore. 
![you are logged in](https://github.com/LuiseFreese/blog/blob/main/media/how-to-send-adaptivecards-with-CLIMicrosoft365/PnPmanagementShellOK.png)

You don't believe that? Let's check with CLI Microsoft 365 and run this command to get your status: 

`m365 status`

and it will get your status for you: 
 
![status logged in](https://github.com/LuiseFreese/blog/blob/main/media/how-to-send-adaptivecards-with-CLIMicrosoft365/status.png)
 
If you want some inspiration, what you could do now, run this command: 

`m365 help`

![help](https://github.com/LuiseFreese/blog/blob/main/media/how-to-send-adaptivecards-with-CLIMicrosoft365/help.png)
which gives you a list of things you can try, these are called command groups, as each of them can contain several commands.  When you now choose one of the command groups and run for example this one: 

`m365 outlook`

 you will get the commands, that are available to you in this command group. Just try them out! 

## What are Adaptive Cards?

Next 

## How do we send an Adaptive Card with CLI Microsoft 365? 

### Create the Webhook

### Author your Card

#### Adaptive cards Designer

#### Visual Studio Card Cards Previewer

### Run the command




# How to build an FAQ bot for Microsoft Teams with Power Virtual Agents in minutes

In this blog I want to show you, how you can build, test and publish an FAQ bot for Microsoft Teams within minutes. We will use the Power Virtual Agents for Teams, which means, that you will not need any additional license to your Microsoft 365 license, for reference see also [Power Virtual Agents for Microsoft Teams plan] (https://docs.microsoft.com/en-us/power-virtual-agents/requirements-licensing-subscriptions#power-virtual-agents-for-microsoft-teams-plan). 

## What is Power Virtual Agents?

Power Virtual Agents belongs like Power Apps, [Power Automate](https://flow.microsoft.com) and Power Bi to the Power Platform (wow, that was a powerFULL sentence 😇). You can create chatbots, which can interact with users in apps and websites, trigger workflows and more, without the need of writing code. You can choose if you want to use it in the [Power Virtual Agents standalone web app](https://powerva.microsoft.com) or as [app within Microsoft Teams](https://aka.ms/PVAForTeams).

## Let's build a bot

I will guide you how to create an FAQ bot. To feed our bot we will need some FAQ so that our can bot can learn them. I will use [FAQ regarding licensing](https://docs.microsoft.com/en-us/power-platform/admin/powerapps-flow-licensing-faq) 🤓, but you can choose any FAQ from a website or PDF or even Word file that you like. 

* Open Teams
* Click on the **Apps** icon
* Search for **Power Virtual Agents**

![Power Virtual Agents](https://github.com/LuiseFreese/blog/blob/main/media/how-to-build-a-faq-bot/pva-teams.png)

* Click **Add**

![Add Power Virtual Agents to Teams](https://github.com/LuiseFreese/blog/blob/main/media/how-to-build-a-faq-bot/add-pva.png)

* Select the Team you want your bot to join

![select a team](https://github.com/LuiseFreese/blog/blob/main/media/how-to-build-a-faq-bot/pva-create.png)

* Give your bot a name ans select a language that your bot shall understand (should be the same language as your FAQ)

![name your bot](https://github.com/LuiseFreese/blog/blob/main/media/how-to-build-a-faq-bot/pva-create2.png)

* Click **Chatbots** - here you get an overview of ALL your chatbots

![my Chatbots](https://github.com/LuiseFreese/blog/blob/main/media/how-to-build-a-faq-bot/my-chatbots.png)

### Add topics from any website

* Click **Topics**

![Topics](https://github.com/LuiseFreese/blog/blob/main/media/how-to-build-a-faq-bot/topics.png)

You see, that some basic topics are already created for you. You can take a look later. 

* Click **Suggested**

[suggested topics](https://github.com/LuiseFreese/blog/blob/main/media/how-to-build-a-faq-bot/suggested.png)

Now we want to work on feeding our bot with the FAQ from the website that we selected. 

* Copy the URL auf the FAQ website
* Paste the URL into the **Link to online content** field

![Get Faq](https://github.com/LuiseFreese/blog/blob/main/media/how-to-build-a-faq-bot/getfaq.png)

* Click **Add**
* Click **Start**

This may take now a couple of minutes. Grab a coffee in the meanwhile: ☕. Soon you will see the message that your new suggested topics are now in: 

![Success](https://github.com/LuiseFreese/blog/blob/main/media/how-to-build-a-faq-bot/success.png)

### Review & edit topics

You can now review and edit each topic: 

![Review and edit](https://github.com/LuiseFreese/blog/blob/main/media/how-to-build-a-faq-bot/edit-topics.png)

* Click **Save Topic**

After you are done with reviewing and editing your topics, you will need to turn on the topics

* Switch the toggle to **on**

![Turn on topics](https://github.com/LuiseFreese/blog/blob/main/media/how-to-build-a-faq-bot/turn-on.png)

> Train your bot by entering more trigger phrases. This way, it is more likely that the Chatbot understands users assking questions even if they don't exactly match the trigger phrases. 

Time to test the bot! 

![Test bot](https://github.com/LuiseFreese/blog/blob/main/media/how-to-build-a-faq-bot/end-conversation.png)

You can now review and edit your topics until you are happy with the results. 

### Publish your Bot to Microsoft Teams

* Click the **Publish** icon

![Publish](https://github.com/LuiseFreese/blog/blob/main/media/how-to-build-a-faq-bot/publish.png)

* Click **Add**

![Add Bot](https://github.com/LuiseFreese/blog/blob/main/media/how-to-build-a-faq-bot/add.png)

* Click **Add to Teams**

![Success](https://github.com/LuiseFreese/blog/blob/main/media/how-to-build-a-faq-bot/publish-bot.png)

* Use your bot

![Chat](https://github.com/LuiseFreese/blog/blob/main/media/how-to-build-a-faq-bot/chat.png)

## Conclusion & what's next

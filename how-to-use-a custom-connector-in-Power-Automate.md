# How to create a custom connector in Power Automate

Power Automate is a super cool tool, which gives us a lot of options. But sometimes, the built-in connectors, are not enough. In one of previous posts, I showed you [how to send HTTP requests to Microsoft Graph API](https://m365princess.com/how-to-get-started-with-http-requests-in-power-automate/). This time, I will show you how to connect to APIs outside of Microsoft 365 in Power Automate and even use an IOT button to trigger your flow. 

## Use case

To make things more approachable, here is a little use case for you: 

> I want to click an IOT button and this shall trigger a flow which tweets about the music I currently listen to on Spotify. 

The result will look like this: 

![tweet about spotify](https://github.com/LuiseFreese/blog/blob/main/media/how-to-use-custom-connectors-in-powerautomate/tweet.png)

## What we need

To achieve this, we will need a couple of things: 

1. an IOT button - I use a Flic Smart button for that- that triggers my flow
2. a flow that connects to our Spotify and to twitter

So lets have a look at 

### IOT button

I use a [Flic IOT button](https://flic.io/) to trigger my flow. This button works with bluetooth, which means that we will need a bluetooth enabled device to work with this button- either a smartphone or an IOT Hub. 

#### Set Up your IOT button

* download the app from your app store
* install the app
* register a new account
* connect your folic button by pressing it for ~10 seconds

If you like to, rename this button - please keep in mind, that one button can be used to trigger several flows, as we have three different event types: Click, Double-Click and Hold. 

### Spotify

In this flow we want to trigger by one or any event of the flic button and then tweet the song we are currently listening to on Spotify. Turns out, that there is no connector for Spotify, so why not building our own custom connector? 

> To be able to build custom actions, you will need an API for this service. Lucky us, that Spotify provides us with that API so that we can use this to build our custom connector. 

Of course we need to have at least a free Spotify account so that we can listen to music that then shall be tweeted about. 

Before we can build the connector, we will need to register for [Spotify's Developer program](https://developer.spotify.com/) - Once this is done, we can retrieve Spotify content such as album data, playlists and more though Spotify Web API. To get user-related data (like the song our user is playing right now) we need to authorize our application so that we are allowed to retrieve this information.

#### Register our application on Spotify

* Log into your brand new Spotify for Developers account 
* Go to your [Dashbaord](https://developer.spotify.com/dashboard/applications)
* Click **Create an App**
* Give your app a name and accept T&C
![Create a new app](https://github.com/LuiseFreese/blog/blob/main/media/how-to-use-custom-connectors-in-powerautomate/create-an-app.png)
* Click **Create**
* Copy the `Client ID` and the `Client Secret` 

#### Build the custom Connector

* Go to [flow.microsoft.com](https://flow.microsoft.com)
* Click **Data**
* Click **Custom connectors**
* Click **New Custom connector**, **Create from blank**\
* Add a name for your connector
* Click **Continue**
* If you like to, you can upload a connector icon, this step is optional
* enter `api.spotify.com` as **Host**

![Custom Connector - general](https://github.com/LuiseFreese/blog/blob/main/media/how-to-use-custom-connectors-in-powerautomate/cc-general.png)

You can find the values you need to fill in here in the [Spotify for developers documentation](https://developer.spotify.com/documentation/web-api/reference/#reference-index), but to make things easier for you, I will provide them for you. 

* Click on **Security**
* Select **OAuth2.0**
* Select **Generic Oath 2** as Identity Provider
* Paste in your Client ID and Client secret
* enter `https://accounts.spotify.com/authorize` as Authorization URL
* enter `https://accounts.spotify.com/api/token` as Token URL and Refresh URL
* enter `user-read-currently-playing` as scope
* Click **Create connector 
* Copy the Redirect URL
* go to your [Spotify app](https://developer.spotify.com/dashboard/applications)
* Click **Edit settings**
* past the Redirect URI into the field for Redirect URIs 
* Click **Add**
* Click **Save**

![edit settings](https://github.com/LuiseFreese/blog/blob/main/media/how-to-use-custom-connectors-in-powerautomate/edit%20settings.png)

Now go back to your Custom connector

* Click on **Definition**
* Click **New action**
* enter something like `GetSong` in Summary
* enter a description
* enter an operation ID like `getssong` - please note, that this ID shouldn't start with an upper case letter
![Custom Connector definition](https://github.com/LuiseFreese/blog/blob/main/media/how-to-use-custom-connectors-in-powerautomate/cc-definition-general.png)

* Click **import from sample**
* Select verb **Get*
* paste in `https://api.spotify.com/v1/me/player/currently-playing` as URL

(For reference: https://developer.spotify.com/console/get-users-currently-playing-track/)

* Click **Import** 
* Click **Update connector** 
* Click **Test**

To test our new connector, we need to select from an existing connection or create a new connection. 

* Click **New connection**

A new pop up window will appear and promt us to **Agree** - you as a user authorize your Spotify app to retrieve data related to your user account - such as the song currently playing. 

![custom connector authorization](https://github.com/LuiseFreese/blog/blob/main/media/how-to-use-custom-connectors-in-powerautomate/cc-authorization.png)

* Click **Agree**
* Click **Close**

### Use the custom connector in our flow

Now it's time to build our flow

#### Trigger flic

As already said, we want the flic button to be our trigger

![Power Automate flow with flic as a trigger](https://github.com/LuiseFreese/blog/blob/main/media/how-to-use-custom-connectors-in-powerautomate/flic.png)

You can choose, if you want this flow to be triggered by any event type or if you want to save the two other event types for other flows. 

Now we want to get the current song from our shiny new Custom connector: 

### Get current song

* Click on **Insert a new Step**
* Click on **Custom**
* Select the new custom connector for Spotify

Our intention now is to tweet something like "I am currently listenintg to {songname} by {artistname}, check it out {spotify URL}." But from our custom connector, we don't get the name of song and artist per se, we will need to first parse the JSON output. If you never heard of that before, don't worry, go read this article about [how to parse JSON in Power Automate](https://m365princess.com/how-to-get-started-with-http-requests-in-power-automate/), I will just wait here for you and drink a coffee. 

Back again? Cool! 

* Let your flow run
* Go to your run history
* Copy the output of the **Get current song** action
* Insert a **Parse JSON** action
* Click **Generate from sample**
* Paste into the new field
* Click **done**

Magic 🦄 - Now we can see all the output from our custom action as Dynamic content. Next thing up is to send the tweet. We can use the twitter connector for it, but Buffer works fine as well. 

* Add the **post a tweet** action

provide your tweet text with Dynamic content as you wish from your Parse JSON action. Don't be afraid when the flow adds **Apply to each** loops! Unfortunatley, both artist-name and -song-name are named `name`, so you will need to figure out which is which. 

* save your flow

## Run your flow

Open your flic app and select the new button, set the action that is triggered by the `click` event to **Microsoft Flow** (watch out, this is the old name of Power Automate, which is not refelcted in the Flic app). When you now click the button, this will trigger our flow, that listens to the **Click** event of that button, get the current song and tweet about it! 

## Conclusion and what's next

In this post I explained, how you can create a custom connector and call an API outside of Microsoft 365. You learned how to define actions and how to authorize your application so that you can retrieve the requested data. Which use cases do you have in mind? What would you like to build a custom connector for? Please share!








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
2. a flow that connects to my Spotify and to twitter

So lets have a look at 

### IOT button

I use an [IOT button](https://flic.io/) to trigger my flow. The button I use, works with bluetooth, which means that you will need a bluetooth enabled device to work with this button- either a smartphone or an IOT Hub. 

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
* Go to your [Dashbaord](https://developer.spotify.com/dashboard/applications)\
* Click **Create an App**
* *

#### Build the custom Connector

### Use the custom connectir in our flow





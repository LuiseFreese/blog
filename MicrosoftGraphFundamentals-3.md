# Doing Microsoft Graph Fundamentals learning path on MS Learn - Part 3

This is already the third part of my little series on what it takes to do the [Microsoft Graph Fundamentals Learning Path](https://docs.microsoft.com/en-us/learn/paths/m365-msgraph-fundamentals/) on Microsoft Learn. If you missed [part 1](https://m365princess.com/microsoft-graph-fundamentals-learning-path-module-1/) or [part 2](https://m365princess.com/microsoft-graph-fundamentals-learning-path-module-2/), it would be a good idea to catch up first, as the parts build upon each other. 

After we already saw how easily we can configure a JavaScript application to retrieve Microsoft 365 data using Microsoft Graph in the last module, we will focus this time on how to access user photo information by using Microsoft Graph. 

This module is supposed to only take 17 minutes to complete - timer set 😇. 

## intro

Our goal is to insert a user profile in our app that we already used in the last module. We will need to authenticate our user by using Microsoft identity and receive an access token and let the app call MIcrosoft Graph API with this token. - If you now wonder 'wait but why?' it's a good idea to read part 2 of my summary again or to actually do the last module. 

After making us aware WHY we should display a user picture, we learn that there are several ways to get profile picture information with Microsoft Graph, for example 
`GET https://graph.microsoft.com/v1.0/me/photo/$value` gets us the image of the signed-in user itself. I used the Graph Explorer to check that: 

![get user profile picture in Graph Explorer](https://github.com/LuiseFreese/blog/blob/main/media/GraphFun/GraphFun-image.png)

Let's do an excercise: 

## Exercise - Use Microsoft Graph in your web application to retrieve a user's profile photo

### build upon module 2

As we are building upon the last module, we will not need to clone the repository again. The unit quickly walks us through the 4 main files for our app `index.html`, `auth.js`, `graph.js` and `ui.js` to make us aware what they will do and repeats the steps we did in module 2 to insert tenant ID and application ID. 

### Now the new part

1. copy - paste two code snippets into the `index.html` file to create and style a button with an image element
2. add a function to the `graph.js` file to call Microsoft Graph API and retrieve the photo of the signed-in user
3. add a function to the `ui.js` file that displays the image that we got from Graph into the image element that we created and styled in step 1
4. copy -paste a snippet to show a button which a signed-in user can click on to view their profile picture. 

![6 lines to get the profile picture from Graph](https://github.com/LuiseFreese/blog/blob/main/media/GraphFun/get-pic.png)

### Time to run our app 

Like in Module 2, open your terminal (I use the built-in Powershell in Visual Studio Code) and type in `npm start`, which will open your browser with `localhost:8080`. 

* Click on **Sign in with Microsoft**
* Click the `show profile picture` button 
* see that profile pic? YAY - time for a happy dance- You made it!

![your MS Learn Trophy](https://github.com/LuiseFreese/blog/blob/main/media/GraphFun/tropy.png)


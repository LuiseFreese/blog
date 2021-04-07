# Doing Microsoft Graph Fundamentals learning path on MS Learn - Part 3

This is already the third part of my little series on what it takes to do the [Microsoft Graph Fundamentals Learning Path](https://docs.microsoft.com/en-us/learn/paths/m365-msgraph-fundamentals/) on Microsoft Learn. If you missed [part 1](https://m365princess.com/microsoft-graph-fundamentals-learning-path-module-1/) or [part 2](https://m365princess.com/microsoft-graph-fundamentals-learning-path-module-2/), it would be a good idea to catch up first, as the parts build upon each other. 

After we already saw how easily we can configure a JavaScript application to retrieve Microsoft 365 data using Microsoft Graph in the last module, we will focus this time on how to access user photo information by using Microsoft Graph. 

This module is supposed to only take 17 minutes to complete - timer set 😇. 

Our goal is to insert a user profile in our app that we already used in the last module. We will need to authenticate our user by using Microsoft identity and receive an access token and let the app call MIcrosoft Graph API with this token. - If you now wonder 'wait but why?' it's a good idea to read part 2 of my summary again or to actually do the last module. 

After making us aware WHY we should display a user picture, we learn that there are several ways to get profile picture information with Microsoft Graph, for example 
`GET https://graph.microsoft.com/v1.0/me/photo/$value` gets us the image itself. I used the Graph Explorer to check that: 

![get user profile picture in Graph Explorer]()


# How we use SharePoint list formats and Power Automate at PYOD

Together with [Elio Struyf](https://www.eliostruyf.com), I run an onlin sticker shop called [PYOD - pimpyourowndevice.com](https://pyod.shop). Elio described, how we use Power Platform and Azure Functions to keep the store up-to-date and to print the labels for our envelopes to send out the stickers. This post shall show, how we use SharePoint and Power Platform to market our products and make our day-to-day work even easier. 

## Posting a random sticker

We use a SharePoint list for our inventory. This means, that each sticker is an item in the list and that we have dedicated columns for all attributes like price, dimensions, material in that list. To automate sharing our sticker on socials, we added some more columns like twitter text, twitter hashtags and short link to this sticker in the store. I experimented a bit with Buffer to automate posting on Social Media, but I was not happy with it, as I couldn't find an easy way to post stickers in a certain rythm. My solution: building a Power Automate flow, which posts a random item from said SharePoint list every 15 hours. 

The flow looks like this: 

![PYOD-twitter](https://github.com/LuiseFreese/blog/blob/main/media/pyod-twitter-flow-full.png)

### How does this flow work? 

It is a scheduled cloud Power Automate flow, which runs every 15 hours and gets all items from the Inventory that are for sale. The compose action will generate get us a random item, because we do not want to post every item but only one. The expression is: `body('Get_items')?['value'][rand(1,length(body('Get_items')?['value']))]`. In the next step, I parse the JSON code from the Outputs of my compose action so that I get all keys and values as dynamic content in my flow. Now I will create an update in Buffer, with the title of my item, description, hashtags and the link to the shop. Finally, I share the created update from Buffer. Flow automatically creates n `Apply to Each` loop for me as it could be, that there is more than one update created. 

### why does this run every 15 hours? 

Well, there are timezones, and as this shop sells and ships worldwide it's beneficial to not always post at the same time to reach different people. I recreated the same flow for our different social media accounts and let each of them run with a delay of a couple of hours to maximize reach and visibility of the brand. 

## Ooops, something went wrong

Sometimes, we make mistakes, like broken links because of a typo in our list, for example. As this doesn't look, I created a **oops, something went wron** column in our SharePoint list and associated a flow with it: 

![tweet this item now](https://github.com/LuiseFreese/blog/blob/main/media/pyod-twitter-now.png)


### How does this flow work?

This fglow is very similar to the first one. I used the **For a selected Item** trigger, get the item of the list that matches the `ID` of the selected item and then update and create my update via Buffer as shown before. 

### How does this flow work in the SharePoint list?

To have a nice trigger in the list, I formatted the **oops, something went wron** column with [this sample](https://github.com/pnp/sp-dev-list-formatting/blob/master/column-samples/generic-start-flow/start-flow-button.json). 

To learn, how you can apply column samples to your SharePoint lists, you can read my blog about [SharePoint list formatting made easy](https://m365princess.com/sharepoint-list-formatting-made-easy/)

This particular sample will create a button in each row of your list which executes a flow. To know, which flow it needs to execute (as you can run several flow associated to the same list), you will need to provide the ID of the flow that you want to run. You can find it in URL of the flow. You can change text, backgroundcolor, icon next to the text and more, please use [Fluent UI Icons](https://developer.microsoft.com/en-us/fluentui#/styles/web/icons) for reference. 

Of course, we do not only use that for typos, but also if we get a question on socials about a certain sticker to easily tweet it. I created this flow two times for our different social media profiles and formatted the list columns accordingly

![SharePoint list with flow action](https://github.com/LuiseFreese/blog/blob/main/media/pyod-twitter-list.png)

## News by RSS

## Ideation and Decision making progress

Running a sticker business means, that all [cool ideas for new stickers](https://pimpyourowndevice.com/news/2021/01/how-we-started-pixelart-stickers/) need to have a decent home. Thats where our Ideas lists comes into play. Each idea is an item and we work each week through a defined process that is reflected in the **Status** and **Next Step** columns. We define, if we need to still work on the idea until it is ready to be printed, who will design the sticker or if we will discard it. To deternmine, how much we believe in the sticker, we use 3 columns: **Rating Elio**, **Rating Luise** and **Rating**. 

**RatingElio** and **RatingLuise** are Number Columns, with a nice rainbow-heart effect formatting. The column expects values between 1 (not very convinced) and 5 (super convinced) and shows emoji hearts instead of a number:

<script src="https://gist.github.com/LuiseFreese/feb49003c05e3d399bf4eaccf6cad142.js">rainbow Hearts</script>

**Rating** is a calculated column and will sum up **RatingElio** and **RatingLuise**
    
![PYOD ideas list](https://github.com/LuiseFreese/blog/blob/main/media/pyod-ideas-list-format.png)



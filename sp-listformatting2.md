# How we use SharePoint list formatting and Power Automate at PYOD to ease our marketing

Together with [Elio Struyf](https://www.eliostruyf.com), I run an online sticker shop called [PYOD - pimpyourowndevice.com](https://pyod.shop). Elio described, [how we use Power Platform and Azure Functions](https://www.eliostruyf.com/running-online-store-powerplatform-azure/) to keep the store up-to-date and to print the labels for our envelopes to send out the stickers. This blog post shows, how I use SharePoint and Power Platform to market our products and make our day-to-day work even easier. We strongly believe that low-code and custom code complement each perfectly and that we can achieve more together. 

## Posting a random sticker

We use a SharePoint list for our inventory. This means, that each sticker is an item in the list and that we have dedicated columns for all attributes like price, dimensions, material in that list. These attributes are of course reflected in the store. To automate sharing our stickers on socials, I added some more columns like twitter text, twitter hashtags, and a shortlink to this sticker in the store. I experimented a bit with Buffer to automate posting on Social Media, but I was not happy with it, as I couldn't find an easy way to post stickers in a certain rhythm. My solution: building a Power Automate flow, which posts a random item from said SharePoint list.

The flow looks like this: 

![PYOD-twitter](https://github.com/LuiseFreese/blog/blob/main/media/pyod-twitter-flow-full.png)

### How does this flow work? 

It is a scheduled cloud Power Automate flow, which runs every 15 hours and gets all items from the inventory that are for sale. The compose action will get a random item, because I do not want to post every item but only one. The expression is: 

`body('Get_items')?['value'][rand(1,length(body('Get_items')?['value']))]`

I use the rand() function to get a random value between 1 and the amount of list items in this list.

In the next step, I parse the JSON code from the Outputs of my compose action so that I get all keys as dynamic content in my flow. Now I will create an update in Buffer, with the title of my item, description, hashtags and the link to the shop. Finally, I share the created update from Buffer. The Flow [automagically 🦄](https://pimpyourowndevice.com/stickers/automagically-large/) creates an `Apply to Each` loop for me, as it could be, that there is more than one update created. 

### why does this run every 15 hours? 

Well, there are timezones, and as this shop sells and ships worldwide it's beneficial to not always post at the same time to reach different people. I recreated the same flow for our different social media accounts and let each of them run with a delay of a couple of hours to maximize reach and visibility of the brand. 

## Ooops, something went wrong

Sometimes, we make mistakes, like broken links because of a typo in our list, for example. As this doesn't look good, I created a **oops, something went wrong** column in our SharePoint list and associated a flow with it: 

![tweet this item now](https://github.com/LuiseFreese/blog/blob/main/media/pyod-twitter-now.png)

### How does this flow work?

This flow is very similar to the first one. I used the **For a selected Item** trigger, get the item of the list that matches the `ID` of the selected item and then update and create my update via Buffer as shown before. 

### How does this flow work in the SharePoint list?

To have a nice trigger in the list, I formatted the **oops, something went wrong** column with [this sample](https://github.com/pnp/sp-dev-list-formatting/blob/master/column-samples/generic-start-flow/start-flow-button.json). To learn, how you can apply column samples to your SharePoint lists, you can read my blog about [SharePoint list formatting made easy](https://m365princess.com/sharepoint-list-formatting-made-easy/)

This particular sample will create a button in each row of your list which executes a flow. To know, which flow it needs to execute (as you can run several flows associated to the same list), you will need to provide the ID of the flow that you want to run. You can find it in URL of the flow. You can change text, backgroundcolor, icon next to the text and more, please use [Fluent UI Icons](https://developer.microsoft.com/en-us/fluentui#/styles/web/icons) for reference. 

Of course, we do not only use that for typos, but also if we get a question on socials about a certain sticker to easily tweet it. I created this flow two times for our different social media profiles and formatted the list columns accordingly:

![SharePoint list with flow action](https://github.com/LuiseFreese/blog/blob/main/media/pyod-twitter-list.png)

## News by RSS

Blogging for me does not stop with my own blog and [my foodblog](https://www.thatkitchenprincess.com), but I also write stories on [PYOD News](https://pimpyourowndevice.com/news). Because I want to automatically tweet these micro blog posts, I build another flow to do exactly that, after Elio prepared an rss feed for the news site. 

![PYOD post rss](https://github.com/LuiseFreese/blog/blob/main/media/pyod-ideas-news-rss.png)

## Ideation and Decision making progress

Running a sticker business means, that all [cool ideas for new stickers](https://pimpyourowndevice.com/news/2021/01/how-we-started-pixelart-stickers/) need to have a decent home. That's where our Ideas lists comes into play. Each idea is an item and we work each week through a defined process that is reflected in the **Status** and **Next Step** columns. We define, if we need to still work on the idea until it is ready to be printed, who will design the sticker or if we will defer the idea. To determine, how much we believe in the sticker, we use 3 columns: **Rating Elio**, **Rating Luise** and **Rating**. 

**RatingElio** and **RatingLuise** are Number Columns, with a nice rainbow-heart-effect formatting. The column expects values between 1 (not very convinced) and 5 (super convinced) and shows emoji hearts instead of a number:

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/sp/v2/column-formatting.schema.json",
  "elmType": "div",
  "children": [
    {
      "elmType": "span",
      "txtContent": "💛",
      "style": {
        "display": "=if([$RatingElio] >= 1, 'inherit','none'"
      }
    },
    {
      "elmType": "span",
      "txtContent": "🧡",
      "style": {
        "display": "=if([$RatingElio] >= 2, 'inherit','none'"
      }
    },
    {
      "elmType": "span",
      "txtContent": "💖",
      "style": {
        "display": "=if([$RatingElio] >= 3, 'inherit','none'"
      }
    },
    {
      "elmType": "span",
      "txtContent": "💜",
      "style": {
        "display": "=if([$RatingElio] >= 4, 'inherit','none'"
      }
    },
    {
      "elmType": "span",
      "txtContent": "💙",
      "style": {
        "display": "=if([$RatingElio] >= 5, 'inherit','none'"
      }
    }
  ]
}
```

**Rating** is a calculated column and will sum up **RatingElio** and **RatingLuise**
    
![PYOD ideas list](https://github.com/LuiseFreese/blog/blob/main/media/pyod-ideas-list-format.png)

## Conclusion & Feedback

I love to automate everything AND to have awesome looking lists with rainbows, unicorns and special buttons that make my life easier as I don't need to care about all day-to-day tasks, but can focus on ideation and growing the business. I am curious for which use cases you use lists and flows? 

I would love to hear from you! 

*#SharingIsCaring ❤*



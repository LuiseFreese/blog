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

Sometimes, we make mistakes. Broken links because of a typo in our list, for example. 


## News by RSS

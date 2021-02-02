# How to create a Content plan for your Social Media activities and automate all the boring work

I love SharePoint and I am amazed by lists - regardless if I use them standalone as Microsoft Lists, in SharePoint or in Microsoft Teams. One thing, all my customers want to know, are calendar views. I run, together with [Elio Struyf](https://eliostruyf.be) a [sticker shop](https://pyod.shop) and we both do not only aim for delivering amazing stickers, but also continuesly improve our business. You could read in my last posts about list formatting [Part 1](https://m365princess.com/sharepoint-list-formatting-made-easy/) and [Part 2](https://m365princess.com/how-we-use-sharepoint-list-formatting-and-power-automate-at-pyod-to-ease-our-marketing/), how I automated some social media activities. In this post I will show you how to create a content calendar and also automate creating actionable tasks from that as well. 

## Create a list with calendar view

I created a list in SharePoint and added columns for date, tweettext, hashtags URL and additional actions. Important: The Column, that contains the date needs to be a date column. I created some list items and created a new view: 

* Click **All Items**
* Click **Create New View**
* Give your view a nice name
* Click **Show as `Calendar`**
* Click **Create**

![Create a list with calendar view](https://github.com/LuiseFreese/blog/blob/main/media/listformattingcalendarview.gif)

## automate creating tasks in Microsoft Planner

We use Microsoft Planner for our tasks, which is why I want the additional tasks, that come along with an event in this calendar to appear in our Planner board. Instead of copy-pasting everything manually, I built a flow that does exactly that for me automatically: 

![flow that creates tasks in plannner fromk list item](https://github.com/LuiseFreese/blog/blob/main/media/flowlisttoplanner.png)

This flow is triggered when a new item is created or modified and then checks if the column with additional tasks is not empty. If that condition returns `true`, it creates a task with a due date and assignes me to that task. After that, the flow updates that task with a description and a Link to the list item. 

## automate tweeting about the content from calendar

As I already have content in the list to be tweeted, I now want to post the tweets automatically on value in my `Date` column. I created a scheduled cloud flow, which runs every day and gets only the items from my list where the Date equals today's date. 

To achieve this, I used a Filter Query in the **Get items** action: `Date eq 'utcnow('yyyy-MM-dd')'` and then created and shared an update in Buffer: 

![flow that tweets a list item from if Date is today](https://github.com/LuiseFreese/blog/blob/main/media/flowlisttotwitterbybuffer.png)

## Conclusion & What's next?

With a list, a view and 2 flows I could automate another piece of contentmanagement and daily marketing in this small business scenario. I would love to know what you like to use calendar view for and what you want to automate.






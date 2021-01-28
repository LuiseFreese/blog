# Modern SharePoint list formatting

This article shall give you guidance and inspiration on how to turn your classic boring lists into interactive modern list experiences, which will wow your users, let them get information at first sight, and increase overall productivity. This post is not about the Microsoft 365 list templates; I will cover them in the next blog post. 

If you never heard anything about modern SharePoint list formatting, don't worry; I will guide you through this. 

## Why would we use SharePoint lists

First things first: Why should we use SharePoint lists and not use - for instance - an Excel spreadsheet? Because we don't need to hide information in cascading s, that should be at the user's fingertips. The beauty of lists lies in their simplicity and flexibility to organize work and track the information that matters most to our businesses. 

Creating, sharing, and tracking lists is easy and available on any device; everyone stays in the loop, and we can use lists for all kinds of purposes like tracking issues, assets, routines, contacts, inventory, and more. Lists can easily be customized to make them visually more appealing. 

## How can we turn on modern experience

Now that we are teased into modern lists and libraries in SharePoint, it's time to turn on modern experiences. We can do it like this in the classic experience:

* select **Library Settings** or **List Settings** on the ribbon
* select **Advanced settings** and select **List experience**
* select **New experience** 
* save with **Ok**

### How can we change the look and feel of a list in the UI

Lists can contain different columns, and each column has a certain column type, depending on the kind of value we want to store in that column like text, numbers, dates, choice, persons, locations, links, or images. As lists can contain much information, its brilliant if we emphasize crucial parts by formatting them in a way that they are 

* easier to read
* give a grasp on what is going on
* are mobile-friendly

Already built-in, we will find options to format columns and views. Formatting a view means modifying the way the entire list is displayed. Formatting a column means changing the way this particular column looks like. 

<img src="https://github.com/LuiseFreese/blog/blob/main/media/list-formatting-create.png" width="350">



#### Formatting Views

* We can change the format view 

<img src="https://github.com/LuiseFreese/blog/blob/main/media/list-formatting-format.png" width="350">

* and also display a gallery view

<img src="https://github.com/LuiseFreese/blog/blob/main/media/list-formatting-formatgallery.png" width="350">

#### Formatting columns

* If we want to change the column's appearance, we can do that very end-user-friendly directly in the UI:

<img src="https://github.com/LuiseFreese/blog/blob/main/media/list-formatting-formatcolumns.png" width="350">
* and even with rules like if - then - else: 

<img src="https://github.com/LuiseFreese/blog/blob/main/media/list-formatting-formatrules.png" width="350">

### How can I apply conditional formatting, aka rules

Rules are a powerful feature to determine how a column should look like. Let's say we want to apply a background color depending on a number value. If the number is below 30, the field should be red; between 30 and 70, it should yellow, and above 70, it should be green. Let's see how this looks like: 

![list formatting in action](https://github.com/LuiseFreese/blog/blob/main/media/list-formatting.gif)

### How can we change the look and feel of a list with JSON

Sometimes, even if those options are already cool, we need some more flexibility. 

<img src="https://github.com/LuiseFreese/blog/blob/main/media/whatif.jpg" width="350">

There is a way to format both columns and views beyond what is already offered, as seen above. Perhaps you might have noticed the little link `Advanced mode`? This is where we will find the cool tools to play with! 

<img src="https://github.com/LuiseFreese/blog/blob/main/media/advanced-mode.png" width="350">

This field expects you to put some JSON code in it to format this column. If you never heard about JSON, you can quickly get started with [Intro to JSON](https://techcommunity.microsoft.com/t5/microsoft-365-pnp-blog/introduction-to-json/ba-p/2049369) by Bob German, [this video](https://www.youtube.com/watch?v=iiADhChRriM), or you can learn more at [w3schools](https://www.w3schools.com/js/js_json_intro.asp). 

## Samples

We will browse to the [Microsoft 365 PnP List formatting repository on GitHub](https://github.com/pnp/sp-dev-list-formatting) and open the folder `column samples`. In here, we will find free-to-use samples to make our lists look fantastic. 

Instead of having a list like this: 

<img src="https://github.com/LuiseFreese/blog/blob/main/media/example%20list-BEFORE.png" width="1200">

we can now look at a list like that: 

<img src="https://github.com/LuiseFreese/blog/blob/main/media/example%20list.png" width="1200">

### How can we apply a sample?

* Get familiar with the samples that are available on GitHub
* regularly check for new ones / pin the repo
* select the one that is interesting for you
* read the `readme.md` file to know the requirements for your column. Some samples only work with choice, text, or number columns
* open the JSON file
* copy the code to your clipboard
* go to your SharePoint list
* go to column settings --> format this column
* click on **Advanced mode**
* paste the code
* click **Save**

![Use samples from M365 PnP repository](https://github.com/LuiseFreese/blog/blob/main/media/formatsplist.gif)

That's it! 

We will find [view samples](https://github.com/pnp/sp-dev-list-formatting/tree/master/view-samples) in the same GitHub repository. 

## Want to learn more? 

You can find helpful resources to learn more here: 

* [aka.ms/m365pnp](https://aka.ms/m365pnp]
* [Microsoft 365 PnP Community on TechCommunity](https://techcommunity.microsoft.com/t5/microsoft-365-pnp-blog/)
* [Microsoft 365 PnP List formatting repository on GitHub](https://github.com/pnp/sp-dev-list-formatting)

Have fun and happy Modern SharePoint list formatting - 
*#SharingIsCaring ❤*

# Modern SharePoint list formatting

This article shall give you guidance and inspiration how to turn your classic boring lists into interactive modern list experiences, which will wow your users, let them get information at first sight and increase overall productivity. This post is not about the Microsoft 365 list templates, I will cover them in the next blog post. 

If you never heard anything about modern SharePoint list formatting, don't worry, I will guide you through this. 

## why would I use SharePoint list

First things first: Why should you use SharePoint lists and not use - for instance - an Excel spreadsheet? Because we don't need to hide information in cascading folders, that should be at users fingertips. The beauty of lists lies in their simplicity and flexibility to organize work and track the information that matters most to your business. 

Creating, sharing and tracking lists is easy and available on any device, everyone stays in the loop and you can use lists for all kind of purposes like tracking issues, assets, routines, contacts, inventory, and more. Lists can easily be customized to make them visually more appealing and increase overall satisfaction. 

## How can I turn on modern experience

Now that I teased you into modern lists and libraries in SharePoint, it's time to turn on modern experiences. You can do it like this: 

in the classic experience
* select `Library Settings` or `List Settings` on the ribbon
* select `Advanced settings` and select `List experience`.
* select `New experience` 
* save with `ok`. 

### how can I change the look and feel of a list in the UI

Lists can contain different columns, and columns have a certain column type, depending on the kind of value you want to store in that column like text, number, date, choice, person, location, links or images. As lists can contain a lot of information, its very smart if we emphasize crucial parts by formatting them in a way that they are 

* more easy to read
* give a grasp on what is going on
* are mobile friendly

Already built-in we will find options to format columns and views. 
Formatting a view means modifying the way the entire list is displayed. Formatting a column means changing the way this column looks like. 

<img src="https://github.com/LuiseFreese/blog/blob/main/media/list-formatting-create.png" width="250">

#### Formatting Views

* We can change the format view 

<img src="https://github.com/LuiseFreese/blog/blob/main/media/list-formatting-format.png" width="250">

* and also display a gallery view

<img src="https://github.com/LuiseFreese/blog/blob/main/media/list-formatting-formatgallery.png" width="250">

#### Formatting columns

* If we want to change the columns appearance, we can do that very enduser-friendly directly in the UI:

<img src="https://github.com/LuiseFreese/blog/blob/main/media/list-formatting-formatcolumns.png" width="250">

* and even with rules like if - then - else: 

<img src="https://github.com/LuiseFreese/blog/blob/main/media/list-formatting-formatrules.png" width="250">

### how can I apply conditional formatting aka rules

Rules are a powerful feature to determine how a column should look like. Let's say we want to apply a background color depending on a number value. If the number is below 30, the field should be red, between 30 and 70 it should yellow and above 70 it should be green. Lets see how this looks like: 

![list formatting in action](https://github.com/LuiseFreese/blog/blob/main/media/list-formatting.gif)

### how can I change the look and feel of a list with JSON

Sometimes, even if those option are already cool, we need some more flexibility. 

<img src="https://github.com/LuiseFreese/blog/blob/main/media/whatif.jpg" width="250">

There is a way to format both columns and views beyond what is already offered as seen above. Perhaps you might have noticed the little link `Advanced mode`? This is where we will find the cool tools to play with! 

<img src="https://github.com/LuiseFreese/blog/blob/main/media/advanced-mode.png" width="250">

This field expects you to put some JSON code in it in order to format this column. If you never heard about JSON, you can easily get started with [Intro to JSON](https://techcommunity.microsoft.com/t5/microsoft-365-pnp-blog/introduction-to-json/ba-p/2049369) by Bob German, [this video](https://www.youtube.com/watch?v=iiADhChRriM), or you can learn more at [w3schools](https://www.w3schools.com/js/js_json_intro.asp). 

## samples

As we don't want to reinvent the wheel, we will browse to the [Microsoft 365 PnP List formatting repository on GitHub](https://github.com/pnp/sp-dev-list-formatting) and open the folder `column samples`. In here, we will find free-to-use samples to make our lists look awesome. 

Instead of having a list like this: 

<img src="https://github.com/LuiseFreese/blog/blob/main/media/example%20list-BEFORE.png" width="600">

we can now look at a list like that: 

<img src="https://github.com/LuiseFreese/blog/blob/main/media/example%20list.png" width="600">


### How can I apply a sample?

* get familiar with the samples that are available on GitHub
* check regularly for new ones / pin the repo
* select the one that is interesting for you
* read the readm.me file to know the requirements to your column. Some samples only work with choice, text or number columns
* open the JSON file
* copy the code to yoyr clipboard
* go to your SharePoint list
* go to column settings --> format this column
* click on `Advanced mode`
* paste the code
* click `Save`


### how to tweak samples

## awesome list experience

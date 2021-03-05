# How to create a table in Adaptive Cards with Power Automate

In this blog post we want to show how we can display a table in an Adaptive Card, pull data from a SharePoint list and use Power Automate to do that in one flow. 

## use case

We want to display items of a SharePoint list in an Adaptive Card as a table. The result should look like this: 

![Adaptive Card result](https://github.com/LuiseFreese/blog/blob/main/media/how-to-create-table-in-adaptive-cards/V2AdaptiveCard-Result.png) 

Purpose is to notify the Team each Monday about all Unicorns with a unicornibility index of less than 85 so that the team can take care of them. We do not only want to display 1 single item of our list with a factsheet but display as many items as match our query (unicornibility lt 85). We don’t want to hard-code any value in here to keep things flexible. 

## Let’s start building our Power Automate flow

### recurrence Trigger

We start with a **Recurrence** trigger, set the **interval** to `1` and the **Frequency** to `Week`. 

![recurrence trigger](https://github.com/LuiseFreese/blog/blob/main/media/how-to-create-table-in-adaptive-cards/recurrence.png)
 
### get Items (SharePoint)

Next action is getting the items from our SharePoint list. Set **Filter Query** to `unicornibility lt 85` to only get those items, that match our query – this will ensure a better performance than first pulling all list items and then working with conditions later. You can also limit how many items you want to retrieve. 

![get items](https://github.com/LuiseFreese/blog/blob/main/media/how-to-create-table-in-adaptive-cards/get-items.png)
 
### Preparations to bind data and JSON schema of the Adaptive Card

We want to get a table into an Adaptive Card, which is not supported natively, so we need to do a little trick. We will use variables to build the different pieces of the Adaptive Card JSON, that we will later need. 
The Code in total would look like this: 
 
```
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.2",
    "body": [
        {
            "type": "TextBlock",
            "text": "Hey Team- watch out! 🦄 need some extra 💖",
            "wrap": true,
            "weight": "Bolder"
        },
        {
            "type": "ColumnSet",
            "columns": [
                {
                    "type": "Column",
                    "items": [
                        {
                            "type": "TextBlock",
                            "weight": "Bolder",
                            "text": "Name"
                        },
                        {
                            "type": "TextBlock",
                            "separator": true,
                            "text": "UNICORN1"
                        },
                        {
                            "type": "TextBlock",
                            "separator": true,
                            "text": "UNICORN2"
                        }
                    ],
                    "width": "stretch"
                },
                {
                    "type": "Column",
                    "items": [
                        {
                            "type": "TextBlock",
                            "weight": "Bolder",
                            "text": "Unicornibility"
                        },
                        {
                            "type": "TextBlock",
                            "separator": true,
                            "text": "VALUE1"
                        },
                        {
                            "type": "TextBlock",
                            "separator": true,
                            "text": "VALUE2"
                        }
                    ],
                    "width": "auto"
                },
                {
                    "type": "Column",
                    "items": [
                        {
                            "type": "TextBlock",
                            "weight": "Bolder",
                            "text": "Party Readiness"
                        },
                        {
                            "type": "TextBlock",
                            "separator": true,
                            "text": "PValue1"
                        },
                        {
                            "type": "TextBlock",
                            "separator": true,
                            "text": "PValue2"
                        }
                    ],
                    "width": "stretch"
                }
            ]
        },
        {
            "type": "ActionSet",
            "actions": [
                {
                    "type": "Action.OpenUrl",
                    "title": "open here and care 💖"
                }
            ]
        }
    ]
}

```

Let’s break this into pieces: 

1. First variable will be the upper part of the Adaptive Card in which we define the schema, a title and create a column set. 
![initialize variable for card- upper part](https://github.com/LuiseFreese/blog/blob/main/media/how-to-create-table-in-adaptive-cards/varCard-initialize.png)
2. We initialize variables for the 3 Headers “Name”, “Unicornibility” and “Party Readiness Index”
* ![initialize var Column 1](https://github.com/LuiseFreese/blog/blob/main/media/how-to-create-table-in-adaptive-cards/varColumn1-initialize.png)
* ![initialize var Column 2](https://github.com/LuiseFreese/blog/blob/main/media/how-to-create-table-in-adaptive-cards/varColumn2-initialize.png)
* ![initialize var Column 3](https://github.com/LuiseFreese/blog/blob/main/media/how-to-create-table-in-adaptive-cards/varColumn3-initialize.png)
3. We create an **Apply to Each** and loop over the values of our SharePoint list for each column by appending our variables.
* ![initialize var Column 3](https://github.com/LuiseFreese/blog/blob/main/media/how-to-create-table-in-adaptive-cards/apply-to-each.png)
4. We append the upper part of our card by the 3 columns (consisting of the headers and rows) and the actionset plus end of the card
* ![append columns to card](https://github.com/LuiseFreese/blog/blob/main/media/how-to-create-table-in-adaptive-cards/append%20to%20Card.png)

In case you wonder why we needed to somehow unclean cut the JSON – this is a bug in Power Automate. Although we defined our variables as string, Power Automate asked us to provide valid JSON. We could not provide valid JSON though, because we needed to cut the JSON into pieces. We needed therefore to find a way to make Power Automate believe, that we are not storing JSON in a string variable, and apparently a `{` at the beginning was a trigger for Power Automate to check if JSON was valid (which was not, but on purpose!).

Our Code would look color coded like this: 
 
* ![color-coded](https://github.com/LuiseFreese/blog/blob/main/media/how-to-create-table-in-adaptive-cards/V2color-coded.png)

And if we now lay the color-code blocks over the Adaptive Card: 

* ![Adaptive Card color-coded](https://github.com/LuiseFreese/blog/blob/main/media/how-to-create-table-in-adaptive-cards/V2AdaptiveCard-result-color.png)
 
### Send Adaptive Card

You may choose if you want to send the Post as the Flow bot or as a user or if you want to send this into a 1:1 chat or into a Channel. The Adaptive Card is our card variable. 

![Adaptive Card](https://github.com/LuiseFreese/blog/blob/main/media/how-to-create-table-in-adaptive-cards/card.png)
 
## Conclusion and what's next
 
Although not natively supported, we can actually display a table in Adaptive Cards and bind this to a datasource. What's next? Find the limit how many rows we can display and what else we could do with Cards :') What would you like to figure out? I am curious, please reply below! 
 

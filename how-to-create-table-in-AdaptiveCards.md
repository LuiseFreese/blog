# How to create a table in Adaptive Cards with Power Automate
## use case
We want to display items of a SharePoint list in an Adaptive Card as a table. The result should look like this: 

 

Purpose is to notify the Team each Monday about all Unicorns with a unicornibility index of less than 85 so that the team can take care of them. We do not only want to display 1 single item of our list with a factsheet but display as many items as match our query (unicornibility lt 85). We don’t want to hard-code any value in here to keep things flexible. 
## Let’s start building our Power Automate flow
### recurrence Trigger
We start with a **Recurrence ** trigger, set the **interval** to `1` and the **Frequency** to `Week`. 
 
### get Items (SharePoint)\

Next action is getting the items from our SharePoint list. Set **Filter Query** to `unicornibility lt 85` to only get those items, that match our query – this will ensure a better performance than first pulling all list items and then working with conditions later. You can also limit how many items you want to retrieve. 
 

### Preparations to bind data and JSON schema of the Adaptive Card

We want to get a table into an Adaptive Card, which is not supported natively, so we need to do a little trick. We will use variables to build the different pieces of the Adaptive Card JSON, that we will later need. 
The Code in total would look like this: 
 
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.2",
    "body": [
        {
            "type": "TextBlock",
            "text": "Hey Team- watch out! 🦄 need some extra 💖",
            "wrap": true,
            "weight": "bolder"
        },
        {
            "type": "ColumnSet",
            "columns": [
                {
                    "type": "Column",
                    "items": [
                        {
                            "type": "TextBlock",
                            "weight": "bolder",
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
                            "text": "UNICORN3"
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
        }
    ]
}
 
Let’s break this into pieces: 

1. First variable will be the upper part of the adaptive card in which we define the schema, a title and create a column set. 
2. we initialize a variable for the 3 Headers “Name”, “Unicornibility” and “Party Readiness Index”
3. We create an **Apply to Each** and loop over the values of our SharePoint list for each column by appending our variables.
4. We append the upper part of our card by the 3 columns (consisting of the headers and rows)
5. We append the Card now again by the missing pieces – in case you wonder why we needed to somehow unclean cut the JSON – this is a bug in Power Automate. Although we defined our variables as string, Power Automate asked us to provide valid JSON, when we needed cut the JSON into pieces. We needed therefore to find a way to make Power Automate believe, that we are not storing JSON in a string variable, and apparently a `{` at the beginning was a trigger for Power Automate to check if JSON was valid (which was not, but on purpose!)

Our Code would look color coded like this: 
 

{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.2",
    "body": [
        {
            "type": "TextBlock",
            "text": "Hey Team- watch out! 🦄 need some extra 💖",
            "wrap": true,
            "weight": "bolder"
        },
        {
            "type": "ColumnSet",
            "columns": [
                {
                    "type": "Column",
                    "items": [
                        {
                            "type": "TextBlock",
                            "weight": "bolder",
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
        }
    ]
}

And if we now lay the color-code blocks over the Adaptive Card: 
 
### Send Adaptive Card
You may choose if you want to send the Post as the Flow bot or as a user or if you want to send this into a 1:1 chat or into a Channel. The Adaptive Card is our card variable. 
 

## Flow in full beauty
 
 
 
 


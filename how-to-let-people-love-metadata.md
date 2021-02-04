# How to let people love 💗 metadata in SharePoint and Microsoft Teams

I've been told since I started to work with SharePoint, that people hate metadata. They don't understand, why information architects need them, feel it's too time-consuming to maintain them and feel uncomfortable with using them as a method to retrieve information they need to find. 

The fact, that people only think about how finding documents works, when they desperately need to know where THE MOST IMPORTANT FILE OF THE UNIVERSE is saved, is not helpful as well. This leads to "let's stick to what we already know" aka "we've always done it like this before" thinking. And this means: 

## the evil trinity of bad information architecture

### copies of copies of copies of copies...

We know that most organizations have a problem with redundant content: copies of copies of copies of the same document in different locations. This originates in a massive abuse of email as a document management system. People attach copies without even realizing, that those emails cause a bigger problem: 

Let's say Person A sends an email with an attachment to Person B so he/she could change it and send it back. How many different copies would we now have created? Let's coun't: 

1 Original
2 A's Sent Items folder in Outlook
3 B's Inbox folder in Outlook
4 B saves the file in her/his file server
5 B makes changes to the file and saves as a separate file on her/his file server
6 B attaches the file to an email and sends this back to A
7 A's Inbox folder in Outlook
8 A saves the file as a separate copy on her/his file server

![sending copies of copies](https://github.com/LuiseFreese/blog/blob/main/media/copies.gif)

1 file - 7 additional copies.  What, if we don't play this ping-pong game with 2, but with 5 people and not one time back- and forth, but 3 times? You see, this is the ugly truth of "have been sitting in documents and email the whole day". Which one is the valid one? What is the final one? 

### awkward files names

To cope with that, people get creative and invent super awkward file names, like

**ProjectDeathstar_MasterplanGoLive_DV_21-02-04_V3_final2_FINAL.docx**

I mean, wow, what is that? Shouldn't they stick to a naming convention? 

![naming convention Dilbert](https://github.com/LuiseFreese/blog/blob/main/media/AML-25602_577155_mutable_color.gif)

What are people trying to do? They add some attributes of a file to its name so that they could more easily know what this document is about before they need to open it. Versions, status, name of people who created/modified the document (but maybe thats the name of a Project Manager, a role that needs to approve something?! We actually don't know), and, almost mandatory, a date. Is this a due date, the date of creation, last edit, last edit by this person? Again, nobody can know. We guesswork, we compare, we track changes and send even more emails.. *Could you please send me the LATEST version of that file?!*

![awkward file name contains metadata](https://github.com/LuiseFreese/blog/blob/main/media/metadata.gif)

To be able to cope with these akward file names, they try to segment information so that there is less items to scroll through:

### cascading folder structures

Creating a gazillion of cascading folders seems to be the holy grail in some organizations. They are used to work with folders when it comes to paperwork and applied the working methods from back then to their digital work. They did not evolve in their working behavior in the last (at least) 30 years. This is why they didn't find approaches that support retrievability of information but that map working with papers and that imitates as if they were still working on paper: 

A folder allows only one attribute for a file and people need to pick one out of several attributes and prioritize exactly this. Let's say our document belongs to Project DeathStar, is a Plan and is still a draft? Should we then file it under the Project folder, the Plan folder or the Draft Folder if those happen to be on the same level? What if we nest folders into other folders? Will this solve the problem? Well, let's see: An accounting department needs to store invoices, purchase notices and contracts. Shall we group those by type or by year? 

![cascading folder structures](https://github.com/LuiseFreese/blog/blob/main/media/folderstypeandyear.gif)

## How does this lead us to people out of a sudden loving metadata? 

Of course most of them know, that we can use metadata in SharePoint and Teams, but they will insist that it takes just too much time to fill in columns with data to describe what a file is about. But once we explain the evil trinity (copies of copies of copies, awkward file names, cascading folder structures) and show them how time-consuming this behavior is, they will open their minds and get it: yes, it WILL take some time to maintain metadata, but this will save everyone even more time because we can better filter and therefor faster retrieve what we were looking for in the first place. Plus: we will not have to deal with this tremendous amount of copies anymore, as SharePoint offers us version history. 

Please note, that a folder per se isn't evil, but that, if we overdo (3 levels and more) we will create an insane chaos. 

## Feedback and what's next? 

I would love to know what you do to convince people to choose metadata instead of folders? One of the blog posts could be around version history- what do you think? 





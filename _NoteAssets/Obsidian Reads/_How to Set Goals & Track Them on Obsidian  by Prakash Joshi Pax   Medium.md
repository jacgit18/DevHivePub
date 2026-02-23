---
tags: 
author: 
Status: Distilling
Started: 
EditDate: 
Relates:
---
## Easy setup guide

[

![Prakash Joshi Pax](https://miro.medium.com/v2/resize:fill:88:88/1*UCacEqoCWFjOOZHm-PdC2Q.png)



](https://beingpax.medium.com/?source=post_page-----5cf5702f0a3--------------------------------)

![set goals and track goals in obsidian](https://miro.medium.com/v2/resize:fit:700/1*McmW5vY6LNLaGYtCJ_zTVw.png)

Screenshot by author

If obsidian is your go-to tool, you would love to set goals and track them right from the obsidian dashboard, right?

If your answer is yes, read this article till the end. I’ll walk you through a beginner-friendly step-by-step guide to set goals and track them in obsidian.

Following are the tools that we need for finishing this setup:

-   Dataview Plugin
-   Minimal Theme
-   Kanban Board
-   MetaEdit Plugin
-   Templater Plugin

## #1: Download the Demo Vault

The first thing that you have to do is to [**download the demo vault**.](https://drive.google.com/file/d/1UkATljCfG8hDFdcRXxLz7dWG0Oi-vh70/view?usp=sharing) This vault includes all the files and settings that we need to download.

Here’s what the dashboard in my demo vault looks like. The multi-columns are achieved by using the **multi-column plugin**. Here’s a [**tutorial**](https://beingpax.medium.com/how-to-create-multiple-columns-on-obsidian-c88d220116f6) on how to use that plugin.

![Obsidian Goals tracker](https://miro.medium.com/v2/resize:fit:700/1*NYogG0796tbTfc4NE3tzNA.png)

Demo Vault

## #2: Copying the files in your vault

![](https://miro.medium.com/v2/resize:fit:700/1*MLH0qpH7LI3LyfJjMOh3hg.png)

Demo vault files

Now, copy the ‘**goal\_item\_template**’ file inside your **templates** folder specifically. Then copy the **‘dashboard.md’,** ‘**Goals.md’**, and **Views** and **Goals** Folder to your vault.

## #3: Installing and Configuration

Now you have to install the required themes and plugins and configure them.

-   **Primary theme:** The progress bar seems to work properly only with the primary theme.
-   **Dataview plugin:** After you have installed the plugin, go to its settings and enable the following options

![](https://miro.medium.com/v2/resize:fit:700/1*0G5zs1hqNnGS1Z1flyUCVw.png)

configuring dataview plugin

-   **Metaedit:** After installing, go to ‘Kanban Board Helper’, enable it and add the goals board.

![](https://miro.medium.com/v2/resize:fit:700/1*0jBfista96xEwS0b4vZaTA.png)

configuring metaedit plugin

-   **Templater:** I guess you are already using the templater plugin, if not, you will need to specify the templates folder and add a **hotkey** for a frictionless workflow.

![](https://miro.medium.com/v2/resize:fit:700/1*oW-G52Jk72-mMXIlVlTIIA.png)

Configuring templater plugin

-   **Kanban Board:** You need to change nothing here.
-   **Multi-column markdown:** If you want the dashboard to work properly, I suggest you use this plugin. If not you can edit the text after the tracker in the dashboard file.
-   **Disable readable length:**

![](https://miro.medium.com/v2/resize:fit:700/1*PlYyWzBOtCShHKKLZjim7g.png)

disable readable line length

**After you have finished installing and configuring these plugins, make sure you close your vault and restart it to see the results.**

The problem with using other themes rather than the primary theme is this:

![](https://miro.medium.com/v2/resize:fit:700/1*GUmfnuhVk_AFBmlofxcunA.png)

obsidian dashboard with default theme

It’s not a big issue, but it doesn’t look good to me. So we’ll switch to the primary theme. If you are so in love with another theme, you can also use its CSS snippets.

Only when you switch to the primary theme, your dashboard will look like this:

![Obsidian goal tracker dashboard](https://miro.medium.com/v2/resize:fit:700/1*Byc1bnoDgxCQzdsGnSlZFg.png)

Obsidian dashboard with minimal theme

If you go to your goals file, you will see a kanban view of all your goals.

![](https://miro.medium.com/v2/resize:fit:700/1*Az_Lq-nEj1ylVye94CJDjg.png)

Goals in kanban view

You can add a new goal. You can edit the headings. You can enable checkboxes. There are a lot of settings to play here, but we’ll not go over there.

## #4: Setting a New Goal

Follow the steps below to set your own goals and track them in obsidian.

-   Create a new file with a goal\_item template. Here’s what your file will look like in editing mode.

![](https://miro.medium.com/v2/resize:fit:700/1*VX1UlMImdk26kUw6B4EwDQ.png)

Creating a new goal

You can change the template if you want to. The text in between — — — is the metadata that is used for visualizing in the dashboard and goals board.

Following are the only values that you should change:

-   Progress
-   Target
-   Timespan
-   Creation Date
-   Deadline

Let’s say we created this goal to lose 10 kgs in two months. We edited the metadata values. And then we replaced the text between ‘’ with the goal name.

![](https://miro.medium.com/v2/resize:fit:700/1*a4HotY61qenw45HNdbRkMw.png)

**Important:**

## #5: Enabling goal tracker

If you go and see it in your dashboard and Goals kanban board, the goals will not be visible there, so let’s make it so.

## Making goals visible on the kanban board

The goal is not visible on the kanban board because we have not added it here. To do so, click on add a card and use wiki links for the goal name, and then hit enter.

![](https://miro.medium.com/v2/resize:fit:700/1*Rkz4Ojn5MPDXXUAtj0AQPw.png)

This is what the card will look like

![](https://miro.medium.com/v2/resize:fit:376/1*x6-zVUO1hubBTglaqITumA.png)

Goals in kanban view

## Making Goals Visible on Dashboard

If you have a good knowledge of how dataview plugin works then you are pretty good, but if not, here is a simple explanation. I’m not a coder, so correct me if I’m wrong.

![](https://miro.medium.com/v2/resize:fit:699/1*0txefE4B_jJHvVOmnAOelQ.png)

Here we have dataview queries from #goal and “Goals”. This means all the files that are linked to #goals and which are located inside the “goals” folder will be shown here.

Since our goal “Lose 10 Kgs” is inside the vault folder, it's not shown here. When we move it to the “Goals” folder, it will be shown in the dashboard with dataview plugin just like this.

![Tracking goals in obsidian](https://miro.medium.com/v2/resize:fit:700/1*3VkGIQFPjdfI_KhI-4xVug.png)

And finally, you have a goal tracker on your obsidian dashboard.

Credits to [bagerbach](https://twitter.com/chrisbbh) for originally creating this.

![Prakash Joshi Pax](https://miro.medium.com/v2/resize:fill:40:40/1*UCacEqoCWFjOOZHm-PdC2Q.png)

## Obsidian Ninja
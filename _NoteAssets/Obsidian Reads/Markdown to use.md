---
tags:
  - Markup
  - favorite
author:
  - jacgit18
Purpose: This documentation list Markdown syntax to use in obsidian.
Status: Done
Started: 2022-11-01
EditDate: 
Relates:
---


avoid question marks in page name or special characters

You can bookmark filters search  
  
Even headers  
  
Also attachment  
And all open tabs



| <img src="https://i.imgur.com/mHfA2Z7.png" alt="Image 1" width="300" height="200"> | <img src="https://i.imgur.com/vGJ8bhw.png" alt="Image 2" width="300" height="200"> |
|:------------------------------------------------------------:|:------------------------------------------------------------:|
|                      Priority                      |                      Picking DB                       |


^^ lets you pick anything 

^ one if you want to link to stuff in current note





Here's a sentence with a footnote. [^1]  
  
[^1]: This is the footnote.

Footnote ^[[Recent Dev Research](Recent%20Dev%20Research.md)]
Footnote ^[[[Manual To Automated#Supply & Demand| alias]]]  
Footnote ^[[[note^text]]]
Some content above the fold.
^[[[note^Text below the fold.]]] 
Some content below the fold.
[[Caret]] symbol meaning 

Here's a sentence with a footnote.^[This is the footnote.]


### My Great Heading {#custom-id}


term  
: definition




Some of these words <ins>will be underlined</ins>.


&nbsp;&nbsp;&nbsp;&nbsp;This is the first sentence of my indented paragraph.


<center>This text is centered.</center>

<p style="text-align: center; color: red;">Center this text with red font.</p>



> Dorothy followed her through many of the beautiful rooms in her castle.
>
> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.



> Dorothy followed her through many of the beautiful rooms in her castle.
>
>> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.
>



> #### The quarterly results look great!
>
> - Revenue was off the chart.
> - Profits were higher than ever.
>
>  *Everything* is going according to **plan**.









Here's a paragraph that will be visible.

[This is a comment that will be hidden.]: # 

And here's another paragraph above that is Invisible.




## [Admonitions](https://www.markdownguide.org/hacks/#admonitions)

Admonitions are frequently used in documentation to call attention to warnings, notes, and tips. Markdown doesn’t provide special syntax for admonitions, and most Markdown applications don’t provide support for admonitions (one exception is [MkDocs](https://www.markdownguide.org/tools/mkdocs/)).

However, if you need to add admonitions, you might be able to use [blockquotes](https://www.markdownguide.org/basic-syntax/#blockquotes-1) with [emoji](https://www.markdownguide.org/extended-syntax/#emoji) and [emphasis](https://www.markdownguide.org/basic-syntax/#emphasis) to create something that looks similar to the admonitions you see on other websites.


> ⚠**Warning:** Do not push the big red button.

> 📝 **Note:** Sunrises are beautiful.

> 💡 **Tip:** Remember to appreciate the little things in life.




-   Copyright (©) — `&copy;`
-   Registered trademark (®) — `&reg;`
-   Trademark (™) — `&trade;`
-   Euro (€) — `&euro;`
-   Left arrow (←) — `&larr;`
-   Up arrow (↑) — `&uarr;`
-   Right arrow (→) — `&rarr;`
-   Down arrow (↓) — `&darr;`
-   Degree (°) — `&#176;`
-   Pi (π) — `&#960;`


| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title |
| List        | Here's a list! <ul><li>Item one.</li><li>Item two.</li></ul> |
## [Subscript](https://www.markdownguide.org/extended-syntax/#subscript)

This isn’t common, but some Markdown processors allow you to use _subscript_ to position one or more characters slightly below the normal line of type. To create a subscript, use one tilde symbol (`~`) before and after the characters.


H~2~O

##### html
H<sub>2</sub>O



## [Superscript](https://www.markdownguide.org/extended-syntax/#superscript)

This isn’t common, but some Markdown processors allow you to use _superscript_ to position one or more characters slightly above the normal line of type. To create a superscript, use one caret symbol (`^`) before and after the characters.


X^2

##### html
X<sup>2</sup>


This is ~~strikethrough~~ text.


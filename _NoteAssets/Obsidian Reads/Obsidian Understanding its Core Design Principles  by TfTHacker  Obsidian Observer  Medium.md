---
tags: 
author: 
Status: Distilling
Started: 
EditDate: 
Relates:
---


[Obsidian](https://obsidian.md/) has become one of the most popular tools in the exciting and growing category of note-taking tools called “Tools for Thought.”

In this article, I want to lay out the core principles behind the design of this tool. This article is not about Obsidian features. It is about the building blocks that make up the foundation of Obsidian and why this can give you confidence in Obsidian as your long-term writing partner.

These core principles come from the information I have collected via forums where the makers of Obsidian visit. So, this article is from factual information gathered from those who make Obsidian and not on my conjecture.

In addition to the core principles that underlie the design of Obsidian, we will consider some secondary design considerations that contribute to Obsidian’s success.

![](https://miro.medium.com/v2/resize:fit:700/0*lROrj4SYt1lOFArz.png)

The Obsidian Application

## It all started in 2020

When the team behind Obsidian started working on this new note-taking tool, they began with three simple design principles:

-   Data will be **_local-first_** and **_plaintext_**
-   **_Links_** will be first-class citizens
-   The application will be **_extendable_** by others

This simple list of goals provided clarity in design and features. Also, this list of goals is what draws so many to use Obsidian who want long-term data ownership and creative control over their notes.

Besides these three core principles, there were secondary design principles that guided the developers of Obsidian:

-   The application will be optimized for **_performance_**
-   and will have powerful **_search_** capabilities

Let us discuss each of these design principles in more detail to understand their value better.

## Data will be local-first

At the core of the local first approach is data ownership. Simply put, notes stored on your device are under your control. You create them, edit them, delete them, back them up or do whatever you want to do with them. They are yours.

Data ownership is essential for personal notes to avoid the risk of vendor lock-in. Lock-in means your data is under the control or administration of a third party. You can get to your data, but so can they. Can you extract your data to use in another program? It often depends on what the third party allows you to do with your data.

_In Obsidian, your notes are your notes._

Local first also offers many advantages:

-   **Performance:** editing and processing local files is something modern computers do efficiently and fast.
-   **Flexibility:** since the files are local on your disk, you can use any other text file editing programs on your computer to edit them. You are not limited to Obsidian.
-   **Security and privacy:** since your data is not stored in the cloud, you can keep highly confidential and sensitive information in your Obsidian notes.

This doesn’t mean your notes can’t be stored in the cloud, but with Obsidian you have the option to store data in the cloud and or not. Obsidian also has a file synchronization service that allows for “trust no one” cloud storage, which is sadly a feature rarely offered by other services. The Obsidian sync service uses end-to-end encryption to encrypt your data as it travels through the internet and when it is stored on Obsidian’s cloud servers. Also, Obsidian allows you to manage the encryption key so that even Obsidian employees can’t read your data. Are you seeing the significance of this point? Yes, y_our notes are your notes and they remain your notes._

## Data will be plaintext

Just because you have a file stored locally doesn’t mean you can access its content, let alone from other programs.

For this reason, Obsidian uses a simple plaintext file format called Markdown. Markdown is a simple text file with a few symbols used to control formatting and layout. Since your notes are just text, any text editor, not just Obsidian, can open them.

Markdown is also a very readable language, or file format for editing notes, especially when compared to other file formats. The simplicity of Markdown is a driving factor for why it is so widely used in editors.

> _Your notes are your notes._

Sadly, many companies are dismissive of data ownership, and they will say something like, “you can export your notes any time,” which is very different from actually owning your data.

If you have ever tried to export data from one program and import your data into another program, you know there is always something lost in the translation. With Markdown, there is no exporting since the file format is already in its end form. You open and edit the file in any program you choose that supports editing text files.

Because Obsidian uses Markdown, it gives you the freedom to switch to another application if you choose to do so. No vendor lock-in, even with Obsidian. For those cases when you have text files from other applications with non-supported Markdown syntax Obsidian will gracefully handle these files by showing them as text.

Obsidian not only supports editing Markdown text files created in other programs, but it also supports something called live-interop. Live-interop is when changes are made to your Obsidian Markdown files by other applications, and those changes to files are instantly reflected in Obsidian.

What do you do when you can’t do something in Obsidian natively? No problem, you can use Visual Studio Code, Sublime Text, Vim, grep, awk, Windows Search, Spotlight, or hundreds of other apps in tandem with Obsidian.

Obsidian doesn’t assume it is the master of your data; it is a partner working with you and other note-taking tools.

> _Your notes are your notes._

## Links will be first-class citizens

Most modern Tools for Thought support the concept of linking notes from one note to another. Those links form relationships between notes and help us connect the knowledge we gather.

![](https://miro.medium.com/v2/resize:fit:700/0*KehIYhlsJ9JlaEkt.jpeg)

Connecting one thought to another is at the core of learning and creativity. Obsidian embraced this idea from the beginning. The Obsidian development team decided that links should be first-class citizens, preferably using a simple-to-type format like **\[\[link to another note\]\]**. This weird-looking text comprises a few parts: two open brackets \[\[ followed by the name of the note to link to, closed by two closing brackets \]\]. This means that you write your notes and quickly link to other existing notes or create a link to a new note.

Linking notes may not seem so important, but think about what made the web usable: the ability to link or connect one web page to another. What made Wikipedia so popular? The ability to read a page on one topic and that page is linked to multiple other pages with additional related information. I don’t know about you, but I frequently get sucked into opening multiple links when visiting a Wikipedia page. I go to learn about one thing but then get my knowledge expanded beyond that topic due to the links to other pages.

Linking is one thing I love about Tools for Thought like Obsidian. They allow you to create your own personal Wikipedia. There are tools available that will enable you to run a wiki, for example, DokuWiki and MediaWiki, but they require a server, lots of installation steps, and configuration. While I enjoyed working with these tools, I saw that the amount of work to maintain them was overwhelming and offered little return, when in the end, I just wanted to be able to create links between documents. Therefore, the personal wiki is easy to create and maintain in Obsidian.

Your notes are your notes, and they become much more helpful in Obsidian as you develop your “personal Wikipedia.”

## Extensibility: the application will be extendable by others

We have become accustomed to customizing our tools, especially in the development space. Most tools for developing software allow for extensive customizations, such as:

-   Themes for changing the colors and layout of the program
-   Customization of the keyboard and how it interacts with the program
-   Ability to add new features via plugins

So, from the very beginning, from a technical perspective, the developers of Obsidian put in a lot of to make Obsidian customizable by users and developers.

Users can control just about any aspect of the visual part of Obsidian with themes that change colors and layout. Additionally, users can remap the keyboard using hotkeys, or shortcuts, to various features.

Developers can go a step further by creating plugins that add new functionality to Obsidian.

The makers of Obsidian put forth special effort to architect an internal API (Application Programmers Interface) such that it can be directly exposed to plugins to enhance the functionality of Obsidian.

To make the API useful and solid, the Obsidian developers use this API for the core plugins they developed and are included with Obsidian as part of the product. In other words, they used the development of their own plugins as a way of testing and assuring the plugin API would be solid for others.

Regarding extensibility, they also wanted to make sure it was optional. Some users do not want to run plugins for various reasons, for example, security concerns. So Obsidian has a switch to enable or disable plugin support.

Finally, the developers of Obsidian do an initial review of every plugin submitted by the community. They confirm the quality of the code, that the code will not affect the performance of Obsidian, and finally, that the code is not doing anything harmful. While it is not a guarantee of the reliability or safety of the plugin, it is an effective double-check that the plugin will serve its purpose before it is released to the community.

## Secondary design principles

The Obsidian development team kept focused on these core principles I have just outlined from day one. But they also had a shortlist of other important things they wanted to accomplish while developing Obsidian. Let’s briefly review them:

## Speed: the application will be optimized for performance

One of the things that makes Obsidian so popular is its speed. Some might think it is fast because it’s an application that runs on your device, but the truth is the Obsidian development team invests much of their development time into improving performance.

> _We love SPEED!_

I have seen numerous times that the Obsidian development team will practically stop what they are doing to tweak, optimize or even rewrite code they have determined is causing a performance bottleneck. They are obsessed with performance and will even spend days addressing something that doesn’t meet their high standards.

![](https://miro.medium.com/v2/resize:fit:700/0*CIcgelS90xJnRqZX.jpeg)

I wish more developers would realize how important performance is to users. We are using a Tool for Thought and want our tools to flow at the speed of thought. Lag is the mind-killer.

## Powerful search capabilities

A note-taking program without good search is like going fishing without the fishing rod or net. Search is fundamental to the value of a note-taking tool. But the irony is that many note-taking tools do a poor job at search.

When it came to search, the Obsidian developers started from a place of experience. They had already built the popular online outlining tool called Dynalist. They also analyzed Visual Studio Code (a popular code editor amongst developers) to find inspiration.

Obsidian developers wanted a powerful and fast search that would support a complex combination of operators and fast fuzzy auto-complete.

Search in Obsidian today is one of its most popular features, blazingly fast, and supports a rich array of search options. Obsidian search gives you “Google” like powers over your notes.

## Few other things

They wanted a visual graph view that looked good and was fast. They wanted the ability to control the layout and your workspace through a split-screen mechanism. They also wanted users to be able to publish their notes easily, which eventually led to the Obsidian Publish service.

## Review of these principles

We have now considered the core principles and secondary principles behind the design of Obsidian’s features. As a review they are:

-   Data will be **_local-first_** and **_plaintext_**
-   **_Links will be_** first-class citizens
-   The application will be **_extendable_** by others
-   The application will be optimized for **_performance_**
-   and will have powerful **_search_** capabilities

Put these things together, and what do you have? You have your notes, and they indeed are your notes. You own them. They are in a file format that you can edit with multiple programs on just about any device. But they are not just notes or individual files; they can be linked to one another, creating a network of thoughts, a personal Wikipedia.

## What is the value proposition for us as users?

Obsidian is trying to be a tool you will use today to write notes, and those notes will still be useful to you years from now, even if Obsidian isn’t around.

> _Your notes are your notes, and they should remain yours._

If this is important to you, then the design principles that guided Obsidian’s design and development from its early days until now should increase your confidence in your investment in this Tool for Thought.

It seems investing your time in using Obsidian is an investment into your future self.

Useful links:

-   [Download Obsidian](https://obsidian.md/)
-   [Obsidian technical support forums](https://forum.obsidian.md/)
-   [Obsidian Discord server](https://discord.gg/veuWUTm) for real-time chat
-   [Obsidian on Twitter](https://twitter.com/obsdmd)
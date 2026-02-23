---
tags:
  - library
  - openSource
  - Java
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses JavaFX library.
Status: Done
Started: 
EditDate: 2024-02-12
Relates: 
Peer Reviewed: 0
dg-publish: false
---
JavaFX is an open source library of classes used in next generation client application platform for desktop, mobile and embedded systems built on Java. It is a collaborative effort by many individuals and companies with the goal of producing a modern, efficient, and fully featured toolkit for developing rich client applications.

FXML is an XML-based user interface markup language created by Oracle Corporation for defining the user interface of a JavaFX application. FXML presents an alternative to designing user interfaces using procedural code, and allows for abstracting program design from program logic.

[TestFX](https://github.com/TestFX/TestFX/) Simple and clean testing for JavaFX.

Current state of JavaFX as a GUI library

- JavaFX dev team is highly understaffed. Two main contributors are Oracle and Gluon. None of them working on new features. Oracle provides basic support: code review, infrastructure, tech lead. Gluon supporting JavaFX ecosystem: Maven and Gradle plugins, Scene Builder, website etc. It's a small company so they're highly concentrated on their own mobile-oriented projects and their contribution into desktop and core platform is miserable. There are also some volunteers, but not many, who occasionally working on fixing some bugs and that's pretty much all.

- There is no roadmap, no public bugtracker (JBS is only for maintainers), no milestones and if you're a new developer who wants to join the project you're pretty much not welcome. There's shit ton of bureaucracy around JavaFX. Someone called it gatekeeping and I tend to agree. Even if you'll submit some cool new feature via PR it's most probably will be either declined or stalled. See:

-   [Undecorated interactive stage style](https://github.com/openjdk/jfx/pull/594)
-   [CSS themes as a first-class concept](https://github.com/openjdk/jfx/pull/511)
-   [Indicate that userAgentStyleSheet has changed](https://github.com/openjdk/jfx/pull/525)

- JavaFX UI (javafx-controls) is ugly. It's not an exaggeration, we're almost in 2022 and comparing to other desktop platforms it's a fact. Good news - you can change it via custom CSS theme. Bad news - it's long and tedious.

- JavaFX lacks basic controls (for years). Popover, inline datepicker, rich text editor, toggle, icon font API, typeahead etc. Some can be found in third-party libs, but most of them are either bugged or unmaintained or both. It's 90sh style UI toolit (just like Swing), it's not evolving and probably never will.

- JavaFX is not extensible. Everything is either private or final or both. Good luck writing your own controls. It's not documented and in the most cases you'll end up copy-pasting existing control and rewriting everything from scratch. The most weird thing is that i18n API is also not public, while JavaFX has very limited language support. If you want to internationalize your app it's not possible without ugly hacks.

- JavaFX has pretty small community. Many third-party libs are unmaintained or stuck on Java 8 support. Many people are tired of constant lack of basic features and new one aren't excited of how it looks and works.

- JavaFX is not performant. I laugh in every topic where some JavaFX dev accusing Electron. They pretty much comparable in terms of memory consumption. Some controls like TextArea or TableView have terrific performance.

- FXML is useless. It's only suitable for mockups or loading large views on app startup. If you want to split your app to small FXML components (that's precisely how modern development works) FXML loader will hit your app performance. Nope, no performance optimizations planned, devs are afraid to even touch it.
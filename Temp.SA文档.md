## Codehub
------
### Abstract

CodeHub is an iOS application, it can be reached on any iOS platform, like iPhone, iPod Touch, and iPad device, The project is designed in C# using the Xamarin with Json.NET, ReactiveUI, MVVMCross, Marked.js, allowing users to access their GitHub account from the iOS platform, and complete what they can do on GitHub's web application. Here you can create, read, and update your issues with ease, scan through your notifications to keep yourself aware of commits, pull requests, and issues, view branches, tags, and source code with beautiful syntax highlighting - even pdfs supported, almost evertything is just the same with Github but easier.It's an open source project, which can be contributed by every programmer. 

This document studies CodeHub by looking at its organization and architecture from Stakeholder Analysis, Logical View, Process View, Physical View, Development View, and more perspectives. The study goes from a high-level analysis to more technical views and perspectives. At last, we have concluded that Codehub is a well completed-structred, full-featured, user-friendly client for GitHub on the iOS platform.

### Table of Contents
1. Introduction
2. Stakeholder Analysis
3. Context View
4. Functional View
5. Information View
6. Development View
7. Deployment View
8. Performance & Scalability Perspective
9. Evolution Perspective
10. Conclusion
11. References

### 1. Introduction

For most of our programmers, GitHub plays an essential role of our development. In GitHub, we can manage our code repositories, study and communicate with others, and broaden our horizons. However, as a website that is not convenient enough for our increasing demands, there are many official client for different platform such as GitHub Desktop for Windows and Mac, Pockhub for Android, but nothing for IOS. Therefore, the appearence of Codehub, a third party client of Github, filled the void.

After browsing through the code and architecture of this project, it is amazing that most of this IOS project with more than 30,000 lines of code was completed independently by the author Dillon Buchanan, a Boston software developer. The first release of CodeHub(version 1.0.0RC1) was in September 2013, and the 2.0.0-RC1 version of CodeHub was released after three month in December. Till now, there are 574 commits of the project on GitHub with the latest 2.18.2 version, which means that the project was developed all the time by the author for five years, with some contributions from other users on GitHub. Nowadays, CodeHub is also one of the most popular third party client of GitHub on IOS platform.

### 2. Stakeholder Analysis

In this section, we discuss various stakeholders involved in CodeHub according to the categorization defined by Rozanski and Woods[1]. They define a Stakeholder as following:
>A stakeholder in the architecture of a system is an individual, team, organization, or classes thereof, having an interest in the realization of the system.

Every type of stakeholders has its own wishes, requirements and influences for the project. So we'd like to describe them according to their roles and concerns about this project.
However, as CodeHub is written by one author instead of a company, there are less classes of Stakeholders than those described by Rozanski and Woods.

|Stakeholders|Introduction|
|-----|------|
|Assessors|Oversee the system’s conformance to standards and legal regulation. For CodeHub, this class consist of the author, Dillon Buchanan.|
|Communicators|Explain the system to other stakeholders via its documentation and training materials. For CodeHub, this class consist of the author, who has written the file README.md and an official website for CodeHub to explain this project.|
|Developers|Construct and deploy the system. For CodeHub, this class consist of the author and other contributing members on GitHub.|
|Maintainers|Manage the evolution of the system once it is operational. For CodeHub, this class consist of the author of this project, who has written this project independently and continuously update it in GitHub and App Store.|
|Testers|Test the system to ensure that it is suitable for use. For CodeHub, this class contains all the reviewers and contributors on GitHub who pull or fork this project to test it.|
|Users|Define the system’s functionality and ultimately make use of it. For CodeHub, this class contains all the users who have downloaded, used and made comments on this software on App Store.|

### 2. Context View

In this section, the context viewpoint of Codehub is described. The context view describes and visualises the relationships and interactions between Codehub with the environment. According to the categorization defined by Rozanski and Woods[1], they define a Context viewpoint as following:
>Context viewpoint describes the relationships, dependencies, and interactions between the system and its environment (the people, systems, and external entities with which it interacts).

#### System scope & responsibilities
With the development of mobile devices, people are accustomed to accessing the server on the mobile side, rather than through a web browser. Codehub aims to implement it on any ios platform. The goal of this system is to create an environment which allows developers to login in their github account and browse their repositories and other information in their github account. In other words, Codehub is an "read-only" github on the ios system.
In short, the most important responsibilities and capabilities of the system are:
* Enable users to access their github account from all the ios platforms(e.g.	iPhone, iPod Touch, and iPad device).
* Enable users to read their github through app, thus change the situation that can only be accessed through web browsers.
* Almost covers all the features of github, which can be call "read-only" github.
* More convenient for account management. Codehub can help us manage several accounts, which makes users more convenient to switch account compare to the github on the web.

#### External	Entities
Codehub is a widely-used app to access github account on ios platform. As one can image, a software project like this cannot be developed without external libraries, tools and frameworks. Below, there are several entities in Codehub, and together they set up the enviroment of it. The external entities are listed below:
* Developing language: C#.
* IDE for programming: Visual Studio.
* Framework: Xamarin, a free C# framework for iOS applications.
* Dependency: Json.NET, ReactiveUI, MVVMCross, Marked.js.
* Supported By: Github.
* Communication tools: Github.
* Users: any users on ios platform(e.g.	iPhone, iPod Touch, and iPad device).


### References

1. Nick Rozanski and Eoin Woods. Software Systems Architecture: Working with Stakeholders using Viewpoints and Perspectives. Addison-Wesley, 2012.

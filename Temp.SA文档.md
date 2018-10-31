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
|Users|Define the system’s functionality and ultimately make use of it. For CodeHub, this class contains all the users who have downloaded, used and made comments on this software on App Store. 

### 3. Context View

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


### 5. Information View
The ultimate purpose of any software system is to manipulate data in some form. This data may be stored persistently in a database management system, in ordinary files, or in some other storage medium such as flash memory, or it may be transiently manipulated in memory while a program executes.

Formal data modeling and design can be a long and complex process. An architect can do data modeling only at an architecturally significant level of detail. We need to focus on those aspects of the data model where getting it wrong would affect the system as a whole rather than just a part of it. We have to figure out how the developer form those data, and produce a complete but high-level view of static information structure and dynamic information flow, with the objective of answering the big questions around ownership, latency, references, and so forth.

In the application of Codehub, it is of vital importance to get the correct data of the user who signed in, and organize the data in a proper way and then present those user data, absolutely, so when we try to rebuild the architecture of the software, we can not pass the disscussion of information view.

#### 5.1 Information ownership
Since Codehub's main role is as a mobile-side GitHub application, there is no doubt that its main source of data is GitHub, and GitHub is a fully open source public code repository. Although the user's data is officially saved, but at the same time , GitHub also provides APIs for users to obtain user data, many of which resources on the users API provide a shortcut for getting information about the previously authenticated user.
The Codehub developer, of course, also uses the API provided by GitHub to get all the data on GitHub for the currently logged-in user on the app, including the user's personal information and preferences, the user's code repository and repository information and content, user's historical behavior on the GitHub such as staring, pulling issues. Of course, these are the static structure of the user information, and through the GitHub API, the developer also provides the user with the same operation in the GitHub Web version on the Codehub conveniently, because the user's behavior on GitHub is also done by adding, deleting, and changing data. Officials completely allow developers to use GitHub personal data and information from users who voluntarily provide information, which is completely widely used by many developers.


#### 5.2 Information structure and content
Let's take a look at how Codehub uses the GitHub API to get user data and use it successfully. The main thing to focus on here is the code files in the Data folder. 

![Data Source Code]()

The developers have completed the acquisition and change methods of user data in these classes , but at the same time we need to refer to the [official developer documentation](https://developer.github.com/v3/) provided by GitHub, in which the GitHub clearly shows the interface of the data and how to obtain and use it.

The following json codes shows the official root endpoints of the GitHub data:

```jason
{
  "current_user_url": "https://api.github.com/user",
  "current_user_authorizations_html_url": "https://github.com/settings/connections/applications{/client_id}",
  "authorizations_url": "https://api.github.com/authorizations",
  "code_search_url": "https://api.github.com/search/code?q={query}{&page,per_page,sort,order}",
  "commit_search_url": "https://api.github.com/search/commits?q={query}{&page,per_page,sort,order}",
  "emails_url": "https://api.github.com/user/emails",
  "emojis_url": "https://api.github.com/emojis",
  "events_url": "https://api.github.com/events",
  "feeds_url": "https://api.github.com/feeds",
  "followers_url": "https://api.github.com/user/followers",
  "following_url": "https://api.github.com/user/following{/target}",
  "gists_url": "https://api.github.com/gists{/gist_id}",
  "hub_url": "https://api.github.com/hub",
  "issue_search_url": "https://api.github.com/search/issues?q={query}{&page,per_page,sort,order}",
  "issues_url": "https://api.github.com/issues",
  "keys_url": "https://api.github.com/user/keys",
  "notifications_url": "https://api.github.com/notifications",
  "organization_repositories_url": "https://api.github.com/orgs/{org}/repos{?type,page,per_page,sort}",
  "organization_url": "https://api.github.com/orgs/{org}",
  "public_gists_url": "https://api.github.com/gists/public",
  "rate_limit_url": "https://api.github.com/rate_limit",
  "repository_url": "https://api.github.com/repos/{owner}/{repo}",
  "repository_search_url": "https://api.github.com/search/repositories?q={query}{&page,per_page,sort,order}",
  "current_user_repositories_url": "https://api.github.com/user/repos{?type,page,per_page,sort}",
  "starred_url": "https://api.github.com/user/starred{/owner}{/repo}",
  "starred_gists_url": "https://api.github.com/gists/starred",
  "team_url": "https://api.github.com/teams",
  "user_url": "https://api.github.com/users/{user}",
  "user_organizations_url": "https://api.github.com/user/orgs",
  "user_repositories_url": "https://api.github.com/users/{user}/repos{?type,page,per_page,sort}",
  "user_search_url": "https://api.github.com/search/users?q={query}{&page,per_page,sort,order}"
}
```

Just look at the names of these urls and we will know the specific data used by these paths. Of course, these are not all used in Codehub, but it is true that developers use most of the data. In the `\CodeHub.Core\Data\Account.cs` file, the developer defines a number of methods for getting and modifying data, but here the developer just completes basic classes and method definitions, implements the data retrieval and return, and the specific data usage and modification is still done in each functional module.

![Static Information Structure Model]()


#### 5.3 Information purpose and usage
The first thing you need to know is that all queries before now do not require any permissions. You only need to return data according to the given address, which is completely public. But the function we want to implement in Codehub is not only to query the full public data, but for users who have already logged in, they may have to create files, update or delete them on Codehub, that is, they must use their own account to " Login to " and use some features that can be achieved.

So in order to implement Codehub additions, deletions and changes, we need to look at the permissions issue first.
There are three commonly used authentication methods, `Basic authentication`, `OAuth2 token`, `OAuth2 key/secret`. The three authentication methods have the same effect, but each has its own features and conveniences. It depends on the developer's own needs.

Basic authentication

```
curl -u "username" https://api.github.com
```

OAuth2 token (sent in a header)

```
curl -H "Authorization: token OAUTH-TOKEN" https://api.github.com
```

OAuth2 token (sent as a parameter)

```
curl https://api.github.com/?access_token=OAUTH-TOKEN
```

Note that OAuth2 tokens can be acquired programmatically, for applications that are not websites.

OAuth2 key/secret

```
curl 'https://api.github.com/users/whatever?client_id=xxxx&client_secret=yyyy'
```
This should only be used in server to server scenarios. Don't leak your OAuth application's client secret to your users.

In Codehub, in the `\CodeHub.Core\ViewModels\Accounts\OAuthLoginViewModel.cs`, developer use the third way to complete the authentication, and then use and change the data in almost every view Model of the applicaiton, you can see the get and set data methods in every class file in the directory`\CodeHub.Core\ViewModels\`.

According to the official document and the detailed usage of the data in the source code of Codehub, we draw a sketch of the information flow model, the main purpose of the data is to get the user's GitHub information and data, and update the latest GitHub news, of course, when it comes to the operation of the repos, it will also provide timely reminder of the repos information and repos-related messages. And codehub will be synchronized to GitHub in time as user modify and update the data.

![Information Flow Model]()


### 6. Development View

The development view describes the architecture	of a project from the viewpoint	ofthe developers.	According	to	Rozanski	and	Woods	[1], the	development	vie is responsible for addressing	different aspects	of the system	development	process	such as code structure and dependencies, build and configuration management	of deliverables, system-wide design constraints, and system-wide standards to	ensure	technical	integrity. In the	following sections,	the	development	view of Codehub	is presented based on	the	three	models that	Rozanski	and	Woods	[1]	define in	their	book:	Module Structure	Model, Common Design Model and Codeline	Model. In	addition to	this,	a	high-level	view of	CodeHub is included	in order to	ensure a thorough	understanding	of the project in	different	granularity.

The High Level View has showed in the directory ViewGraph. First, the user interacts with the CodeHub client, where the user can perform operations such as editing, synchronizing, and pushing branches. These requests are sent to the Codehub server. This can be an HTTP or WebSocket request. The CodeHub server then synchronizes these operations with the user's data on the Github. Finally, codehu returns to the user successfully.

#### Module Structure Model
The	module structure model defines the organisation	of the system's	code clustering	related source code	files	into modules and determining the dependencies	between	them [1].	In this section	first	the	modules	of the project are briefly described and then	the	dependencies between them	are	visualised in a	diagram. It	should be	also	noted	that this	section	focuses only on	the	internal modules	of the project and not the external	dependencies.
##### I -- Module Structure of Core
1. Data
2. Extension
3. Filter
4. Message
5. Service


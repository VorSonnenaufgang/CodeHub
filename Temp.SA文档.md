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
<img alt="Context View" src="https://github.com/VorSonnenaufgang/CodeHub/blob/master/ViewGraphs/context-view.png" width="100%">

### 4. Functional View
In this section, I will write something about the functional view. The functional view, which emphasizes the functional capabilities and functional design philosophy of the system, is something like the responsibilities of context view, but more in detail. Therefore, I will introduce this section in four parts as follows.

#### Functional capabilities
First of all, codehub contains almost all of the functions of github. So, the basic funtions of codehub are: 

* Provide the repositories of users' code.
* Control the version of code, include the forward and backward the the code and software.
* Allow mutiple branches to exist, to enable different developers change the file at the same time, which promote the efficiency.
* And so on...

Of course, these are the functions of the github itself. Codehub uses the interface github provides to implement the basic functions. Besides, Codehub has its own special characteristics. They are:

* Breaking the dilemma of the absence of github client on the ios platform.
* Account managment. Users can switch several accounts conveniently.

#### External Interfaces
In the figure below, one can identify three external interfaces:

##### 1.Codehub Client UI Api(Interact with users)
##### 2.build-tool(Xamarin)
##### 3.Github Api

<img alt="External Interfaces" src="https://github.com/VorSonnenaufgang/CodeHub/blob/master/ViewGraphs/ExternalInterface.png" width="100%">

I will now discuss the responsibilities and the philosophy underlying the design of each of these interfaces by applying the architectural principles I identified.

<B>Firstly</B>, the Codehub client ui api will be considered. As detailed in the figure above, the ui api contains Json.NET, ReactiveUI, MVVMCross and Marked.js. They connect the users' behavior and request with the codehub client platform. MVVMCross and RectiveUI are the common frameworks of C# which are used to beautify the ui. As to the Json.Net, it is a library used to parse the json object. And finally, Marked.js is also a library to make the ui more beautiful.

<B>Secondly</B>, I will introduce the build-tool, Xamarin, which provides the connection with the IDE(visual studio) and the ios platform. According to the Microsoft, <a href="http://example.net/">https://docs.microsoft.com/zh-cn/xamarin/</a>, Xamarin is a portable framework, which means it can easily be used on different plateforms. Xamarin is a C#-based cross-platform mobile app development tool that developers can use to develop native apps for iOS, Android, Mac and Windows Phone. Through the cross-platform nature of Xamarin, one can use C# language to develop various platform applications. So, why Xamarin can do this and what is its cross-platform development idea. After refering some blogs, I found that it uses C# to complete all platform-shared, platform-independent app logic parts. As to the UI and interaction with each platform, because they are different, the significance of using Xamarin-encapsulated C# API is highlighted. It is used to access and manipulate native controls, UI development for different platforms. In this way, mobile development is more efficient and simpler.

In fact, when using Xamarin, the efficiency of development get faster. The two figures below shows the efficiency of Xamarin on the platform of Android and iOS. The first figure is the development efficiency of Xamarin for iOS devices. Xamarin performs well and is 30% faster than Objective-C. I think this is the main reason why codehub is not using oc but C#. And it is second only to C++ on Android devices, so it is seen that Xamarin is a highly efficient cross-platform framework. It is a good decision to develop codehub using Xamarin.

<img alt="Xamarin on Android" src="https://github.com/VorSonnenaufgang/CodeHub/blob/master/ViewGraphs/OnAndroid.png" width="100%">

<img alt="Xamarin on iOS" src="https://github.com/VorSonnenaufgang/CodeHub/blob/master/ViewGraphs/OniOS.png" width="100%">

<B>Finally</B>, the most important external interface I think is the github api provided to the Codehub sever. It serves almost all the functions that github originally has such as file browse, branch management and so on.

### 5. Information View
The ultimate purpose of any software system is to manipulate data in some form. This data may be stored persistently in a database management system, in ordinary files, or in some other storage medium such as flash memory, or it may be transiently manipulated in memory while a program executes.

Formal data modeling and design can be a long and complex process. An architect can do data modeling only at an architecturally significant level of detail. We need to focus on those aspects of the data model where getting it wrong would affect the system as a whole rather than just a part of it. We have to figure out how the developer form those data, and produce a complete but high-level view of static information structure and dynamic information flow, with the objective of answering the big questions around ownership, latency, references, and so forth.

In the application of Codehub, it is of vital importance to get the correct data of the user who signed in, and organize the data in a proper way and then present those user data, absolutely, so when we try to rebuild the architecture of the software, we can not pass the disscussion of information view.

#### 5.1 Information ownership
Since Codehub's main role is as a mobile-side GitHub application, there is no doubt that its main source of data is GitHub, and GitHub is a fully open source public code repository. Although the user's data is officially saved, but at the same time , GitHub also provides APIs for users to obtain user data, many of which resources on the users API provide a shortcut for getting information about the previously authenticated user.
The Codehub developer, of course, also uses the API provided by GitHub to get all the data on GitHub for the currently logged-in user on the app, including the user's personal information and preferences, the user's code repository and repository information and content, user's historical behavior on the GitHub such as staring, pulling issues. Of course, these are the static structure of the user information, and through the GitHub API, the developer also provides the user with the same operation in the GitHub Web version on the Codehub conveniently, because the user's behavior on GitHub is also done by adding, deleting, and changing data. Officials completely allow developers to use GitHub personal data and information from users who voluntarily provide information, which is completely widely used by many developers.


#### 5.2 Information structure and content
Let's take a look at how Codehub uses the GitHub API to get user data and use it successfully. The main thing to focus on here is the code files in the Data folder. 

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

![Static Information Structure Model](http://p7n3irs4w.bkt.clouddn.com/Static%20Information%20Structure%20Model%20%281%29.png)


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

![Information Flow Model1](http://p7n3irs4w.bkt.clouddn.com/Information%20Flow%20Model_1.png)
![Information Flow Model2](http://p7n3irs4w.bkt.clouddn.com/Information%20Flow%20Model_2.png)



### 6. Development View

The development view describes the architecture	of a project from the viewpoint	ofthe developers.	According	to	Rozanski	and	Woods	[1], the	development	vie is responsible for addressing	different aspects	of the system	development	process	such as code structure and dependencies, build and configuration management	of deliverables, system-wide design constraints, and system-wide standards to	ensure	technical	integrity. In the	following sections,	the	development	view of Codehub	is presented based on	the	three	models that	Rozanski	and	Woods	[1]	define in	their	book:	Module Structure	Model, Common Design Model and Codeline	Model. In	addition to	this,	a	high-level	view of	CodeHub is included	in order to	ensure a thorough	understanding	of the project in	different	granularity.

The High Level View has showed in the directory ViewGraph. First, the user interacts with the CodeHub client, where the user can perform operations such as editing, synchronizing, and pushing branches. These requests are sent to the Codehub server. This can be an HTTP or WebSocket request. The CodeHub server then synchronizes these operations with the user's data on the Github. Finally, codehu returns to the user successfully.

<img alt="HighLevelView" src="https://github.com/VorSonnenaufgang/CodeHub/blob/master/ViewGraphs/HighLevelView.png" width="100%">

#### 6.1 Module Structure Model
The	module structure model defines the organisation	of the system's	code clustering	related source code	files	into modules and determining the dependencies	between	them [1].	In this section	first	the	modules	of the project are briefly described and then	the	dependencies between them	are	visualised in a	diagram. It	should be	also	noted	that this	section	focuses only on	the	internal modules	of the project and not the external	dependencies.

As a framework, the source code of CodeHub could be	organized	as model structure,	as shown on	the	figure below.	In this figure,	the	ecosystem	of CodeHub is divided	into two major parts: Core internal structrue and Ios client structrue.

<img alt="ecosystem of CodeHub" src="https://github.com/VorSonnenaufgang/CodeHub/blob/master/ViewGraphs/PackageDiagram.png" width="100%">

##### 6.1.1 -- Module Structure of Core
1. Data: This module contains classes that define the user's class and language repository, not dependent on other submodules, but it relies on external dependencies such as .Net packages.
2. Extension: This module contains extensions to Github's external extensions and command lines, provides command-line invocation functionality, and some exception handling features that do not have any dependencies on other modules in CodeHub. There is a dependency on external packages such as ReactiveUI.
3. Filter: This module defines some of the related functions of the problem filter, which depends on some submodules in the VIewModel module.
4. Message: This module defines related sub-modules and sub-functions for message passing and processing, including the function mechanism of adding Gist messages, login logout messages, pull push messages, source code editing changes, etc. This module is in the ViewModel APP, Accounts Submodules such as PullRequests are called and depend on.
5. Service: This module defines the functional sub-modules of the service layer in the project, which hides the details of the business logic layer. It needs to organize the business micro-services internally, provide a more macro-oriented, presentation-oriented service logic, and expose and package using the contract interface. All interactions in the system are entered from the presentation layer. It is primarily responsible for the logical application design of the business module. Under this module, the function codes of related services such as account service, log service, and network activity service are included. This module relies on the data modules under the Core module and is also dependent on many submodules in the ViewModel.
6. Properties: This module uses the reflection mechanism to define the functionality of AssemblyInfo, using Guid to expose the COM components of the project. This module has no dependencies on other modules in Codehub.
7. Util: This module contains some of the tool class modules under the underlying logic, such as extended access to Github, functional integration of emoticons, and sub-modules such as code repository flags and view block extensions, which depend on the Service module, and the ViewModel module. There are also some submodules that depend on it.
8. ViewModels： This module defines the connection layer ViewModel of View and Model. In MVVMCross, the ViewModel interacts with the Model (data layer), and the ViewMode can be viewed by the View. The ViewModel can optionally provide hooks for the view to pass events to the model. An important implementation strategy for this layer is to separate the Model from the View, ie the view that the ViewModel should not be aware of. In this module, it specifically includes sub-modules such as Account, App, ChangeSets, Events, Gists, Issues, Notifications, Organizations, PullRequests, Respositories, Search, Source, and Users. These sub-modules are functionally and structurally dependent on each other. It also contains dependencies from external packages such as MVVMCross.Platform. In addition, the ViewModel module also includes function sub-modules such as filters, Markdown and web browsing.

##### 6.1.2 -- Module Structure of IOS Client
1. DialogElements: This module defines the specific classification and function of the dialog module. It is a module that interacts with the outside world. It is a high-level implementation of the corresponding ViewController component, including the specific interface elements such as User Element and PullRequests element.
2. Resources: This module contains some static resource files on the ios side, such as icon material. The resource files in this module are used in the View module. Does not depend on other internal modules
3. Services: This module is a high-level implementation of the Service layer under the Core module. It relies on the definition and implementation of the Service sub-module under the Core module, and exposes the interface to call the corresponding function of each corresponding sub-module in the ViewController.
4. Utilities: This module is a high-level implementation of the Util submodule under the Core module. It relies on the definition and implementation of the Util submodule under the Core module. It provides a more specific definition and implementation of the utility class and exposes the interface to each of the ViewController. The corresponding submodule calls the relevant function.
5. ViewControllers: This module is a high-level implementation of the ViewModel sub-module under the Core module. It relies on the definition and implementation of the ViewModel sub-module under the Core module, and provides sub-modules corresponding to the ViewModel, such as Accounts, Application, Events, Filters, Gists, Organization, Sub-modules such as PullRequests, Respositories, Search, Source, and User are the connection layer components that are closer to the user and directly define the underlying logic functions that interact with the user.
6. TableViewCells: This module is a view controller class that interacts directly with the user and contains the direct logic for interacting with the user. And the module contains various view layouts and styles, and implements interfaces and components that interact directly with the user.
7. TableViewSources: This module contains the resource invocation interface with the user interaction view, including the user's dynamic warehouse data interface, static resource framework source, and so on. Rely on the definition and implementation of sub-modules such as Respositories under ViewController.
8. Views: This module is a collection of iOS-client application view classes. It defines the static component function implementation of the view, providing direct front-end components and functional definitions for user interaction.

The specific dependency diagrams between the submodules under these two modules are as follows:

<img alt="specific dependency diagrams" src="https://github.com/VorSonnenaufgang/CodeHub/blob/master/ViewGraphs/Main.jpg" width="100%">



As can be seen from the figure, the sub-modules under the .Core module are actually lower-level definitions at the data layer, service layer, application layer, etc., and the sub-modules under the .ios module are correspondingly higher-level implementations. It relies on and calls the interface of the corresponding submodule under the core, and realizes the view and logic of interacting with the user.

#### 6.2 Codeline Model
Codeline Model is used to	keep an	order	when it	comes	to the organization	of the	system code. In	order	to describe	CodeHub’s	Codeline	Model, we	will provide an	overview of	the source code	structure	and	the	contribution process,	based	in the information	given	in the following figure.

<img alt="codeline diagrams" src="https://github.com/VorSonnenaufgang/CodeHub/blob/master/ViewGraphs/CodeHub.Core.png" width="40%"> <img alt="codeline dependency diagrams" src="https://github.com/VorSonnenaufgang/CodeHub/blob/master/ViewGraphs/CodeHub.ios.png" width="40%">

The source codes of CodeHub has two parts: Core and ios. It follows the principle of separation of views and logic, separates each module by function, and each module completes its work independently, forming various dependencies and jointly fulfilling the functions of the Codehub system.

#### 6.3 Common Design Pattern
After analyzing the Codehub project source code, we tried to analyze its software architecture from the perspective of design patterns.
Its design pattern is based on the following two aspects：
1. MVVM design pattern (MVVM is used in Xamarin.Forms)
2. Three-tier structure - Model (data structure model) / Vies (view page) / ViewModel (business logic processing)

For MVVM and MVC in the structural layering is basically the same - M (Model), V (View), ViewModel (Controller), and for Xamarin.Forms we add two layers of structure based on the three-layer architecture of MVVM - Repository (Api or local database), Service (using repositories), through these two layers of structure we can very well abstract the operation of the data interaction part, and the unit can be tested separately for the data part.

At the same time, the Model in MVVM can maintain state and operation. Here Model does not represent the data structure model in the database, nor is it equal to the data structure type returned by the API. Its essence represents our business logic, and ViewModel is used as an intermediary. The process of conversion.

<img alt="design pattern" src="https://github.com/VorSonnenaufgang/CodeHub/blob/master/ViewGraphs/design patterns1.png" width="40%">

#### Service
Service as a bridge between servers and apps, its core role is data transfer. To give you the simplest example: too many apps support offline operations, but this requires the local data store to be in sync with the content of the server returned by the API. When the app responds to the user's manipulation of the data and completes the process, the app itself I don't care about synchronizing data, but it's the result of the Service passing it with the server database.

<img alt="service" src="https://github.com/VorSonnenaufgang/CodeHub/blob/master/ViewGraphs/design patterns2.png" width="40%">

#### Operational separation
ViewModels usually contain user-interactive operations. The processing of these operations needs to include the processing of connection timeouts, parameter errors, and server errors. It also reminds the user what is happening. Usually this code becomes heavy and also includes try / There may be more internal operations inside the catch for connection timeouts. After using the idea of ​​splitting operations, provide the operations required in each case separately, and then choose to return whether to navigate or display the results of certain content to the user. Since the operation is completely independent, it can also be tested separately.

<img alt="Operational separation" src="https://github.com/VorSonnenaufgang/CodeHub/blob/master/ViewGraphs/design patterns4.png" width="80%">

### 7. Deployment View
Deployment view describes the environment into which the system will be deployed, including capturing the dependencies the system has on its runtime environment. This view captures the hardware environment that your system needs (primarily the processing nodes, network interconnections, and disk storage facilities required), the technical environment requirements for each element, and the mapping of the software elements to the runtime environment that will execute them.

CodeHub	is supported by	Mac OS operating system. So, CodeHub require ios platform to deploy. It can be reached on any iOS platform, like iPhone, iPod Touch, and iPad device.

#### Third-Party Software Requirements:
1. Xamarin: Xamarin was founded in 2011 to make mobile development incredibly fast and simple. Xamarin's products simplify application development for multiple platforms, including iOS, Android, Windows Phone, and Mac App. Xamarin was founded and participated by many well-known open source community developers, and is the open source, cross-platform implementation of the C# and .NET frameworks, the leader of the Mono project.
2. Json.NET: Json.NET is a popular high-performance JSON framework for .NET.It has lots of benifits: Flexible JSON serializer for converting between .NET objects and JSON. LINQ to JSON for manually reading and writing JSON. High performance: faster than .NET's built-in JSON serializers. Write indented, easy-to-read JSON. Convert JSON to and from XML. Supports .NET 2, .NET 3.5, .NET 4, .NET 4.5, Silverlight, Windows Phone and Windows 8 Store. The JSON serializer in Json.NET is a good choice when the JSON you are reading or writing maps closely to a .NET class. LINQ to JSON is good for situations where you are only interested in getting values from JSON, you don't have a class to serialize or deserialize to, or the JSON is radically different from your class and you need to manually read and write from your objects.
3. MVVMCross: MvvmCross is a cross-platform MVVM framework that enables developers to create powerful cross platform apps. It supports Xamarin.iOS, Xamarin.Android, Xamarin.Mac, Xamarin.Forms, Universal Windows Platform (UWP) and Windows Presentation Framework (WPF).
4. Marked.js: Marked.js is a library written in JavaScript that can be transcoded online by Markdown. It's very convenient to compile the Markdown code to HTML and display it directly, and it supports full customization of various formats.
5. ReactiveUI：ReactiveUI is a composable, cross-platform model-view-viewmodel framework for all .NET platforms that is inspired by functional reactive programming which is a paradigm that allows you to abstract mutable state away from your user interfaces and express the idea around a feature in one readable place and improve the testability of your application.

#### The deployment diagram:
<img alt="specific dependency diagrams" src="https://github.com/VorSonnenaufgang/CodeHub/blob/master/ViewGraphs/DeploymentDiagram1.jpg" width="100%">

### 8. Performance & Scalability Perspective
This perspective addresses two related quality properties for large information systems: performance and scalability. These properties are important because, in large systems, they can cause more unexpected, complex, and expensive problems late in the system lifecycle than most of the other properties combined.

For Performance & Scalability, we are mostly concered about following perspectives.  

- response time: After our test, in the case of a better network, the data loading and data update after login are completed in 10s, which is thanks to the interface provided by GitHub to obtain data quickly, and good data organization in this app along with use of json.net. In addition, despite the fact that the initial user data loading speed is fast enough, we tried to get the logined users to get some notifications and events, the response time of these reminders is slower than those of the web side. Because the app is received on the GitHub web side, the data is updated after the corresponding information, so the lag is understandable. The good news is that this lag is not very long. In a few seconds, we can also get the message from the Codehub on the mobile side, so we can confirm that the message response on Codehub is also quick and timely. What about relogined uses? As those model programs related to retrive and present data has the function of reusing resources and results, so response time of the app will be even quicker when we relogin.

- throughput: Frankly speaking, in the face of an application where the number of users is not large, pressuer testing is not particularly necessary. In addition, the applications developed with the Xamarin framework will be optimized for certain operational efficiency, especially The original C#. According to the developer, the server selected for Codehub was also able to carry a sufficient amount of users to communicate with the network at the same time. We wrote a small program to continue to create and delete repositories in Codehub for a period of time, and constantly starred in a certain repository, Codehub did not have any abnormal problems in the test. As mentioned in the development view, each of Codehub's view backends uses tactics of optimizing repetitive processing and minimizing the use of shared resources, so it can maintain the stability of the application in the case of multiple users and frequent operations.

- scalability: there are also some pitfalls in the application, the main point is that Codehub's scalability is not enough. The main reason for this problem is that the developer has made the Codehub almost exactly the same as the GitHub when designing the front-end and back-end of the application. The function of CodeHub comes from GitHub, but also limited to GitHub, but there is too much indirection when interacting with GtiHub's web side. It's not easy to extend it on a fully rewritten mobile GitHub, whether it is the design of the function points or the specific implementation of the front and back ends, it is limited by the existing framework of GtiHub. The scalability property of a system is closely related to performance, but rather than considering how quickly the system performs its current workload, scalability focuses on the predictability of the system’s performance as the workload increases. So if we design and add some new features in the existing framework of the system, we can't ensure that the system can still run with the current efficiency and error-free operation.

- hardware resource requirements: The hardware resources required by Codehub are very few. First of all, at the system level, it is based on its original intention， limited to the IOS platform. Strictly speaking, it requires iOS 9.0 or higher, compatible with iPhone, iPad and iPod touch. The memory taken up by the app is 101M. For such an application, the memory occupied is a little bit large. Maybe it is not able to do a good collection and packaging when the application is exported, and observe the code structure we can find some static resources that won't work too much. Codehub's runtime memory usage is satisfactory, and its runtime memory ratio is small in the IOS thanks to the optimization of the application.

### 9. Evolution Perspective
The very ability of software to be “soft” means that stakeholders expect a software-based system to be able to evolve very quickly. As we mentioned in the above analysis, Codehub has a lot of room to improve as a mature application to become a more popular and more comprehensive application.

- Model update:As long as we observe the various views of Codehub in use, we will find its similarity with GitHub Web, but the developer has actually done some different front-end layout for its mobile-side features. Despite this, the shortcomings still exist, especially when it comes to the interaction logic between the specific code view and the repository information in the repository. The cumbersome operations and the unclear operation buttons can be uncomfortable. In addition, due to the different interfaces on the iPhone and iPad, we believe that the view design of the iPhone is not as good as the design on the iPad. The use of the sidebar is very convenient for the user.
In addition, for the notification of some news and activities, I also hope that Codehub can integrate Events and Notifications so that users can see their latest news on the application home page.
The display of the search results also needs to be optimized. The current display results are not displayed in the same way as GitHub, unless the search keywords are completely entered.

- Function extension: Since Codehub is a mobile-side GitHub Client, developers should be able to do some appropriate extensions based on the functionality of the Web version. For example, the better mobile-side code viewing and edting we mentioned earlier, the issues model can also be improved. The portable and timely features of the mobile side increase the interaction of issues. It will be great to add one-to-one communication with specific developers, but as GitHub does not provide a similar functional interface, developers must have difficulty in implementing these extensions. 

- Platform: Codehub currently only has the IOS platform version, but we really hope that developers can launch the Android version later, because the Android version of the GitHub Client has been removed since long ago, so the current Android client is also vacant, especially considering Xamarin's efficient for all-platform development capabilities, it's easy to do application porting.

### 10. Conclusion
This document provides every reader with an overview of Codehub from multiple software architectural views and perspectives as defined in Rozanski & Woods's book. Conclusion can be drawn that Codehub is an basicaly outstanding IOS client application for GitHub as it contains almost every function aspect of GitHub Web with simple and beautiful interface, excellent interaction and friendly operation.

We analyzed its software level constructs from Context View, Functional View, Information View, Development View and Deployment View, those five software architecture views, and concluded that it is an excellent IOS application developed with Xamarin, but In terms of the practical application of the software, from Stakeholder Analysis  Performance & Scalability Perspective and Evolution Perspective, Codehub also has the disadvantages of unclear positioning, insufficient audience, and limited functionality.

Undoutedly, our recovery of its architecture, and the analysis of its practical application, will inevitably lead to some flaws, especially in the case of our lack of in-depth study of the software architecture. The unfamiliarity of Xamrin, Json.Net, Mvvm and other frameworks may also cause us to make mistakes in project recovery. In addition, Codehub developers and official websites do not provide us with detailed development materials and official documents, and its developers are almost only one person that we tried to contact and failed, our progress and accuracy were greatly affected during writing this document.

The last update time of Codehub is nine months ago, we still hope that its developers can continue to improve Codehub's views and features, bringing us a more perfect IOS GitHub client.

### 11. References

1. Nick Rozanski and Eoin Woods. Software Systems Architecture: Working with Stakeholders using Viewpoints and Perspectives. Addison-Wesley, 2012.
2. [MvvmCross documentation](https://www.mvvmcross.com/documentation/)
3. [UML of Component diagram](https://en.wikipedia.org/wiki/Component_diagram)
4. [UML of Package diagram](https://en.wikipedia.org/wiki/Package_diagram)
5. [UML of Deployment diagram](https://en.wikipedia.org/wiki/Deployment_diagram)

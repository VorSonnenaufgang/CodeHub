## Codehub
------
### Abstract

CodeHub is an iOS application, it can be reached on any iOS platform, like iPhone, iPod Touch, and iPad device, The project is designed in C# using the Xamarin with Json.NET, ReactiveUI, MVVMCross, Marked.js, allowing users to access their GitHub account from the iOS platform, and complete what they can do on GitHub's web application. Here you can create, read, and update your issues with ease, scan through your notifications to keep yourself aware of commits, pull requests, and issues, view branches, tags, and source code with beautiful syntax highlighting - even pdfs supported, almost evertything is just the same with Github but easier.It's an open source project, which can be contributed by every programmer. 

This document studies CodeHub by looking at its organization and architecture from Stakeholder Analysis, Logical View, Process View, Physical View, Development View, and more perspectives. The study goes from a high-level analysis to more technical views and perspectives. At last, we have concluded that Codehub is a well completed-structred, full-featured, user-friendly client for GitHub on the iOS platform.

### Table of Contents
1. Introduction
2. Stakeholder Analysis
3. Logical View
4. Process View
5. Physical View
6. Development View
7. Scalability & Performance Perspective
8. Evolution Perspective
9. Conclusion
10. References

### Introduction

For most of our programmers, GitHub plays an essential role of our development. In GitHub, we can manage our code repositories, study and communicate with others, and broaden our horizons. However, as a website that is not convenient enough for our increasing demands, there are many official client for different platform such as GitHub Desktop for Windows and Mac, Pockhub for Android, but nothing for IOS. Therefore, the appearence of Codehub, a third party client of Github, filled the void.

After browsing through the code and architecture of this project, it is amazing that most of this IOS project with more than 30,000 lines of code was completed independently by the author, a Boston software developer. The first release of CodeHub(version 1.0.0RC1) was in September 2013, and the 2.0.0-RC1 version of CodeHub was released after three month in December. Till now, there are 574 commits of the project on GitHub with the latest 2.18.2 version, which means that the project was developed all the time by the author for five years, with some contributions from other users on GitHub. Nowadays, CodeHub is also one of the most popular third party client of GitHub on IOS platform.

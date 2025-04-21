# Introduction

## What is Reqnroll

Reqnroll is an open-source Cucumber-style BDD test automation framework for .NET.  
It has been created as a reboot of the SpecFlow project.

Reqnroll enables writing executable specifications for [BDD](https://en.wikipedia.org/wiki/Behavior-driven_development) using [Gherkin](https://en.wikipedia.org/wiki/Cucumber_(software)), the widely-accepted feature file specification format. With that you can define the requirements using Given-When-Then style scenarios and turn them to automated tests in order to verify their implementation.

Since Reqnroll is based on SpecFlow, you can use your SpecFlow knowledge to work with Reqnroll and it is also very easy to port an existing SpecFlow project to Reqnroll. You can check out our detailed migration guide.

## Why Use Reqnroll

### Shared Understanding Through Executable Specifications

Reqnroll promotes collaboration across technical and non-technical roles by capturing requirements in plain language. This creates a shared understanding of what needs to be built, before a single line of code is written.  
Because these specifications are executable, they also serve as living documentation and automated tests in one.

### Confidence Through High-Level Testing

By focusing on **what** the system should do rather than **how** it should do it, Reqnroll empowers teams to decouple system behavior from implementation details.  
These high-level acceptance tests validate the system at its boundaries, allowing developers to refactor internal code with confidence, knowing that critical behavior is still covered.

### Open Source, Fully Transparent

Reqnroll keeps BDD tooling in the .NET ecosystem open, inspectable, and adaptable.  
Unlike closed-source solutions, Reqnroll offers full control and community ownership over its evolution.

### Cross-Platform and .NET-Compatible

Reqnroll runs on all major operating systems, **Windows**, **Linux**, and **macOS**, and supports all commonly used .NET implementations, including **.NET Framework 4.6.2+**, **.NET Core**, and **.NET 8.0**. This makes it a flexible choice for both legacy and modern .NET projects.

To execute automated scenarios, Reqnroll supports popular unit testing frameworks including **xUnit**, **NUnit** and **MSTest**

You can develop Reqnroll projects using your preferred tools and workflows.  
It integrates smoothly with **Visual Studio 2022**, **Visual Studio Code** and **JetBrains Rider**

However, Reqnroll does not require an IDE, you can also run and maintain your test projects entirely from the command line or using your own tooling, making it suitable for lightweight or headless environments.

### Seamless CI Integration

Because Reqnroll tests are automated and run like any other test suite, they integrate naturally into continuous integration pipelines.  
This ensures that expected system behavior is continually validated with every code change, helping teams maintain stability and reduce regressions.

---

Reqnroll isn't just a testing tool, it's a collaboration tool, a documentation tool, and a confidence tool.  
By aligning everyone around concrete, testable requirements, it helps teams build the right software, the right way.

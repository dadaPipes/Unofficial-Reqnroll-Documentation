# Introduction

## What is Reqnroll

Reqnroll is a community-driven, open-source alternative to SpecFlow, created in response to SpecFlow’s transition to a closed-source model.  
It serves as a powerful [Behavior-Driven Development](https://en.wikipedia.org/wiki/Behavior-driven_development) tool for .NET, allowing developers, testers, and business stakeholders to write human-readable [acceptance tests](https://en.wikipedia.org/wiki/Acceptance_testing) that are directly executable against the application code.

Reqnroll uses `.feature` files written in [Gherkin syntax](https://en.wikipedia.org/wiki/Cucumber_(software)), which describe the expected behavior of a system in natural language constructs such as **Given**, **When**, **Then**.

Each scenario in a `.feature` file represents an example of how the system should behave. These scenarios are automatically bound to step definitions written in C#, allowing you to turn descriptive requirements into automated tests that run against your application.

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

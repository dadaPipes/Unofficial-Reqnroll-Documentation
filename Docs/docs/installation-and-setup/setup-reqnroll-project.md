# Setup Reqnroll Project

We strongly recommend to configure your Integrated Development Environment (IDE) to work conveniently with Reqnroll.

## Choose test execution framework

Reqnroll relies on a test execution framework to run tests.  
Choose one that aligns with your experience and requirements for the project.

- [NUnit](https://nunit.org/) **Nuget**: [Reqnroll.NUnit](https://www.nuget.org/packages/Reqnroll.NUnit)

- [MsTest](https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-csharp-with-mstest) **Nuget**: [Reqnroll.MsTest](https://www.nuget.org/packages/Reqnroll.MsTest)

- [xUnit](https://xunit.net/) **Nuget**: [Reqnroll.xUnit](https://www.nuget.org/packages/Reqnroll.xUnit)

## Setting up a Reqnroll project

# [Visual Studio 2022](#tab/vs-2022)

**Prerequisites** Before creating a new Reqnroll project, ensure the following:

- Reqnroll Visual Studio integration is installed.

- Your IDE is configured to support Reqnroll features.

1. From the context menu of your solution in the Solution Explorer window, select **Add / New Project…**

2. In the Add a new project dialog, enter `Reqnroll` into the **Search for templates** text box.

3. Choose **Reqnroll Project** from the list and click **Next**.

4. Follow the wizard to specify the project name, target framework, and test framework.

As a result, a new Reqnroll project will be created with a sample feature file and step definition class.  
Build your project and execute the sample scenarios.
**TODO**: Show an image or use a codeblock with a filetree. Do not link to **sample feature file and step definition class**
**WHY**: We don't want to be thrown around in the documentation.

**Optional**: Build your project and execute the sample scenarios.
**TODO**: show how.

# [VS Code 🛠️](#tab/vs-code)

Want to contribute ? Click on the **Edit this page** in the bottom of this site

# [Rider 🛠️](#tab/rider)

Want to contribute ? Click on the **Edit this page** in the bottom of this site

# [Dotnet CLI](#tab/dotnet-cli)

1. Install the Reqnroll templates by running:

```shell
dotnet new install Reqnroll.Templates.DotNet
```

2. Once installed, create a project in a new directory:

> [!NOTE]
> By default, the dotnet new reqnroll-project command creates a Reqnroll project configured with NUnit for the latest .NET framework.  
> To customize the test framework or target .NET version, use the -t (test framework) and -f (framework version) options.  
> For details about available options, run:  
> `dotnet new reqnroll-project --help`

```shell
mkdir MyReqnrollProject  
cd MyReqnrollProject  
dotnet new reqnroll-project
```

**Example**:

The following command creates a Reqnroll project with MsTest using .NET 6.0:

```shell
dotnet new reqnroll-project -t mstest -f net6.0
```

As a result, a new Reqnroll project will be created with a sample feature file and step definition class.  
Build your project and execute the sample scenarios.
**TODO**: Show an image or use a codeblock with a filetree. Do not link to **sample feature file and step definition class**
**WHY**: We don't want to be thrown around in the documentation.

**Optional**: Build your project and execute the sample scenarios.
**TODO**: show how.

**Adding a Feature File**  
Use the reqnroll-feature template to add a new feature file to your project.  
For example:

```shell
dotnet new reqnroll-feature -n MyFeature
```

**Adding a Configuration File**  
Use the reqnroll-config template to add a new configuration file to your project.  
For example:

```shell
dotnet new reqnroll-config -n MyConfig
```

# [Existing test project](#tab/existing-test-project)

1. Add the NuGet package of your chosen test execution framework to your project.

> [!IMPORTANT]
> The chosen test execution framework has to match the framework used in your existing test project.

The following example adds the Reqnroll NuGet package for an MsTest project:

```shell
dotnet add package Reqnroll.MsTest
```

Although the Reqnroll tests can be mixed with normal unit tests in the same .NET project,  
for the sake of clarity it is recommended to create a separate project for your Reqnroll BDD scenarios.

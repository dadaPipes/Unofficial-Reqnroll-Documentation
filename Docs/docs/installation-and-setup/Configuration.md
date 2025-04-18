# Configuration

The default configuration can be altered by adding a `reqnroll.json` configuration file to the project

> [!NOTE]
> There is a JSON schema file available for `reqnroll.json`.  
> By specifying the schema reference like in the example below, most IDE's provides auto completion and documentation hints for the configuration file.

```json
{
  "$schema": "https://schemas.reqnroll.net/reqnroll-config-latest.json"
}
```

## Add a config file to the project

# [Visual Studio 2022](#tab/vs-2022)

1. Right-click on your project in the Solution Explorer.

2. Select Add > New Item....

3. From the templates, choose JSON File, name it `reqnroll.json`, and click Add.

# [Visual Studio Code 🛠️](#tab/vs-code)

Want to contribute ? Click on the **Edit this page** in the bottom of this site

# [Rider 🛠️](#tab/rider)

Want to contribute ? Click on the **Edit this page** in the bottom of this site

# [Dotnet CLI](#tab/dotnet-cli)

1. Install the Reqnroll templates by running:

```shell
dotnet new install Reqnroll.Templates.DotNet
```

2. Add the config file by running:

```shell
dotnet new reqnroll-config
```

---

## Use bindings from external projects

Bindings are usually defined within the main Reqnroll project. However, it is also possible to organize bindings in separate **external projects** or **assemblies**.

### What Are External Binding Assemblies?

An **external binding assembly** is any project or compiled library (DLL) outside of the main Reqnroll project that contains reusable bindings. These assemblies can:

- Be part of the same solution like a shared test utilities project.

- Be written in a different .NET language like F# or VB.NET.

- Contain any kind of bindings: step definitions, hooks, or step argument transformations.

This allows you to reuse bindings across multiple Reqnroll test projects, or to isolate domain-specific bindings for cleaner organization.  
**TODO**: Add example repo of a **shared test utilities project** and **domain-specific bindings**.

### Requirements

To use bindings from an external project, simply adding a project reference is **not enough**. You need to:

- **Add a reference** to the external project in your Reqnroll test project.

- **Configure Reqnroll** to recognize the external assembly by listing it in your reqnroll.json.

This ensures that:

- The external assembly is copied to the output folder.

- Reqnroll knows to scan it for bindings during test execution.

### Configuration for external projects

To enable Reqnroll to load bindings from an external assembly, add the assembly name (without `.dll`) to the bindingAssemblies section in your reqnroll.json.

**Example**: Using `SharedStepDefinitions`

Let’s say you have a shared project called `SharedStepDefinitions` that contains common step definitions.  
To register it, your `reqnroll.json` should look like this:

```json
{
  "$schema": "https://schemas.reqnroll.net/reqnroll-config-latest.json",

  "bindingAssemblies": [
    { 
      "assembly": "SharedStepDefinitions"
    }
  ]
}
```

> [!NOTE]
> The main Reqnroll project is automatically included as a binding assembly.  
> No need to list it explicitly.

## Set the default feature file language

Gherkin keywords, like **Feature**, **Scenario**, **Given**, etc., are supported in many natural languages. This allows you to write specifications and acceptance tests in the language of your business domain, which improves clarity and communication.

### Why Set the Feature File Language?

- To match the language your team or stakeholders speak.

- To avoid errors caused by misunderstandings or poor translations.

- To ensure correct parsing and culture-specific behavior during test execution.

### Options for Specifying Feature File Language

There are **two** ways to define which language Reqnroll should use when parsing feature files:

#### Per File: Using the `#language` Directive

You can set the language at the top of each `.feature` file using the Gherkin `#language` directive.

**Example**: Set language for a specific `.feature` file to German

```csharp
#language: de-DE
Funktionalität: Addition
  ...
```

#### Globally: Using reqnroll.json

You can also configure the default language for all feature files by specifying it in your reqnroll.json. This is useful to avoid repeating the #language directive in every file.

**Example**: Set default language to Hungarian

```json
{
  "$schema": "https://schemas.reqnroll.net/reqnroll-config-latest.json",
  "language": {
    "feature": "hu-HU"
  }
}
```

### Culture and Data Conversion

The feature file language setting does more than just control keyword recognition. Reqnroll uses it to determine:

- The set of [Gherkin keywords](https://cucumber.io/docs/gherkin/languages/) to parse (**Given**, **When**, **Then**, etc.)

- The culture used for parameter conversion like number or date formats.

To ensure correct behavior, it's **strongly** recommended to use a specific culture name,like `en-US`, `de-DE`, `fr-FR`, rather than a neutral culture like `en` or `de`.  
If you use a neutral culture, Reqnroll will default to a specific one for example `en` becomes `en-US`.

> [!NOTE]
> The language values follow the [CultureInfo](xref:System.Globalization.CultureInfo) naming used in the .NET Framework

## Configuration file reference

**The following sections are available for reqnroll.json**  

# [language](#tab/language)

Use this section to define the default language for feature files and other language-related settings.

The `bindingAssemblies` section can contain multiple JSON objects (one for each assembly), with the following settings.

| Setting  | Value                   | Description |
|----------|-------------------------|-------------|
| feature  | culture name for example en-US | The default language of feature files added to the project. As metioned in [Culture and Data Conversion](#culture-and-data-conversion) we recommend using specific culture names like `en-US` rather than generic (neutral) cultures like `en`.<br>**Default:** en-US |
| binding  | culture name for example en-US | Specifies the culture to be used to execute binding methods and convert step arguments. If not specified, the feature language is used.<br>**Default:** not specified |

# [generator](#tab/generator)
s
Use this section to define test generation options.

| Setting                         | Value            | Description |
|---------------------------------|------------------|-------------|
| allowDebugGeneratedFiles        | true / false     | By default, the debugger is configured to step through the generated code. This helps you debug your feature files and bindings ([see Debugging Tests 💀](#TODO)). Disable this option by setting this attribute to true.<br>**Default:** false |
| allowRowTests                   | true / false     | Determines whether “row tests” should be generated for scenario outlines. This setting is ignored if the test execution framework does not support row-based testing.<br>**Default:** true |
| addNonParallelizableMarkerForTags | List of tags   | Defines a set of tags, any of which specify that a feature should be excluded from running in parallel with any other feature. [See Parallel Execution 💀](#TODO).<br>**Default:** empty |

# [runtime](#tab/runtime)

Use this section to specify various test execution options.

| Setting                     | Value                              | Description |
|-----------------------------|------------------------------------|-------------|
| missingOrPendingStepsOutcome | Pending / Inconclusive / Ignore / Error | Determines how Reqnroll behaves if a step binding is not implemented or is pending. [See Test Results 💀](#TODO).<br>**Default:** Pending |
| obsoleteBehavior            | None / Warn / Pending / Error      | Determines how Reqnroll behaves if a step binding is marked with `[Obsolete]` attribute.<br>**Default:** Warn |
| stopAtFirstError            | true / false                       | Determines whether the execution of the scenario should stop when encountering the first error, or whether it should continue to detect missing steps.<br>**Default:** false |

# [trace](#tab/trace)

Use this section to determine the Reqnroll trace output.

| Setting                    | Value                                | Description |
|----------------------------|--------------------------------------|-------------|
| stepDefinitionSkeletonStyle | CucumberExpressionAttribute / RegexAttribute | Specifies the default step definition style.<br>**Default:** CucumberExpressionAttribute |
| coloredOutput              | true / false                         | Determines whether Reqnroll should color the test result output. You can override this setting, for instance, on build servers, by setting the environment variable NO_COLOR=1.<br>**Default:** false |

# [bindingAssemblies](#tab/bindingAssemblies)

This section can be used to configure additional assemblies that contain bindings (step definitions, hooks or step argument transformations).

The assembly of the Reqnroll project (the project containing the feature files) is automatically included. The binding assemblies must be placed in the output folder (e.g. bin/Debug) of the Reqnroll project, for example by adding a reference to the assembly from the project.

The following example registers an additional binding assembly (`SharedStepDefinitions.dll`).

```json
{
  "$schema": "https://schemas.reqnroll.net/reqnroll-config-latest.json",

  "bindingAssemblies": [
    { 
      "assembly": "SharedStepDefinitions"
    }
  ]
}
```

The `bindingAssemblies` section can contain multiple JSON objects (one for each assembly), with the following settings.

| Setting                    | Value                                | Description |
|----------------------------|--------------------------------------|-------------|
| assembly | assembly name | The name of the assembly containing bindings (without `.dll`). |

# Compatibility

## Supported operating systems

SpecSync is supported on all common operating systems that support .NET, including

- Windows
- Linux
- MacOS

## .NET Versions

- .NET 9.0
- .NET 8.0
- .NET 7.0
- .NET 6.0
- .NET Framework 4.8.1
- .NET Framework 4.7.2
- .NET Framework 4.6.2

> [!NOTE]
> Reqnroll can also be installed on any .NET frameworks that supports `.NET Standard 2.0`, including `.NET Core 3.1` and `.NET 5.0`, but please note that these frameworks are out of support already.

## Test Execution Frameworks

- [NUnit](https://nunit.org/)
- [MsTest](https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-csharp-with-mstest)
- [xUnit](https://xunit.net/)

## Versioning Policy

The core Reqnroll framework uses [semantic versioning](https://semver.org/).

- Major version changes will introduce breaking changes.
- Minor version number increase represent new features or backwards compatible improvements.
- Patch number increase represents bug fixes.
  
This means that generally you should be able to upgrade to the latest package within the major number range without problems.

The backwards compatibility applies for the specified behavior and the API used by the end-users, but also for interfaces commonly used by plugins.  
This means that if a plugin for example has been created for `v2.0.0` generally suppose to work with `v2.3.1` as well.

> [!IMPORTANT]
> The versioning policy is slightly different for the maintained `Reqnroll integration plugins`.  
> See the detailed policy for these in the section below.

## Versioning policy of Reqnroll plugins

Reqnroll maintains a number of external integration plugins, which act as adapters to other tools or libraries such as Verify.  
These plugins are **usually** versioned in sync with the core Reqnroll package to simplify releases and compatibility management.  
As a result, we publish new versions of these plugins with each Reqnroll release, **even** if the plugin itself hasn't changed.

### Semantic Versioning, With a Twist

Reqnroll plugins follow [semantic versioning](https://semver.org/).  
However, there's one important nuance:  
  When a breaking change occurs in the integrated third-party tool, we release a ***new minor version*** of the plugin,  
  **even** though [semver](https://semver.org/) would normally reserve breaking changes for major version bumps.

**Example**: `Reqnroll.Verify` and `Verify`  

- `Reqnroll.Verify v2.0.3` supports `Verify v23`.

- `Verify v24` introduces a breaking change.

- To support this, we release `Reqnroll.Verify v2.1.0`, included in `Reqnroll v2.1.0`.

This introduces an important compatibility consideration:

  If you upgrade to a newer **Reqnroll** version, for example `v2.1.0`, but don’t upgrade the third-party tool, remaining on `Verify v23`, you may encounter compatibility issues.

### What You Can Do

If you're not ready to upgrade the integrated library:

- Stick to an earlier version of the plugin (`Reqnroll.Verify v2.0.3`).

- You can still use it with the latest Reqnroll version (`v2.1.0`), because:

  - **All plugins within the same major Reqnroll version (v2.x) are cross-compatible.**

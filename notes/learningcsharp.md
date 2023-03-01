# Learning CSharp

## Environment

1. VS2022 `v1.75`
2. C#11
3. dot net 7

## Grokking Structure

Trying to figure out the concepts of solution, project, namespace, and location.

## Grokking Processes

### Build

Before a project can be run, it needs to be built or compiled. Because of heavy use of types,
the compiler can check for errors, making it safe during runtime. This helps avoid errors.

## GUI v. Commandline

It feels amateurish using the GUI to perform certain tasks like creating a project

## Importing Libraries Can Be Non-Trivial

Why do I need to use the `netstandard2.0` framework in declaring a shared library?

Some lines from the [documentation](https://learn.microsoft.com/en-us/dotnet/standard/net-standard?tabs=net-standard-1-0) stand out:

> x x x if you want to share code between .NET Framework and any other .NET implementation, such as .NET Core, your library should target .NET Standard 2.0. No new versions of .NET Standard will be released.

So it's needed but will not be updated.

> .NET Standard not deprecated... .NET Standard is still needed for libraries that can be used by multiple .NET implementations. We recommend you target .NET Standard in the following scenarios: 1. Use `netstandard2.0` to share code between .NET Framework and all other implementations of .NET. x x x

```c#
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
    <LangVersion>11</LangVersion>
    <ImplicitUsings>enable</ImplicitUsings>
    <Nullable>enable</Nullable>
  </PropertyGroup>
</Project>
```

According to Mark Price:

> Good Practice: To use the latest C# language and .NET platform features, put types in a .NET 7 class library. To support legacy .NET platforms like .NET Core, .NET Framework, and Xamarin, put types that you might reuse in a .NET Standard 2.0 class library. By default, targeting .NET Standard 2.0 uses the C# 7.0 compiler, but this can be overridden so you get the benefits of the newer SDK and compiler even though you are limited to .NET Standard 2.0 APIs.

Targeting the framework, as shown in the code snippet above, enables us to create a class (in a separate file) that subsequently can be imported to another project.

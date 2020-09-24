Repro for a error in `dotnet test` I ran into with .NET 5 RC1.

This repository consits of a simple class library and a unit test project that depends on it.

Under certain conditions, `dotnet test` fails because the project cannot be built.

What works:

- `dotnet build Repro.sln`
- `dotnet test Repro.sln --no-build`
- `dotnet test Repro.Test\Repro.Test.csproj`

What **doesn't** work:

- `dotnet test Repro.sln`


**Note:** Problem only occurrs when the main project uses multi-targeting.

When changing `<TargetFrameworks>netcoreapp3.1;net5.0</TargetFrameworks>` in `Repro.csproj` to `<TargetFramework>net5.0</TargetFramework>`, `dotnet test` seems to work fine.

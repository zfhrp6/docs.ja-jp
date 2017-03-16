---
title: ".NET Core コマンド ラインを使用したプロジェクトの整理およびテスト | Microsoft Docs"
description: "このチュートリアルでは、コマンド ラインから .NET Core プロジェクトを整理してテストする方法について説明します。"
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 03/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 52ff1be3-d92e-4477-9c84-8c1771e87ab5
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 3f401907a59d5427cbcfaa0b785931a7ed82110f
ms.lasthandoff: 03/07/2017

---

# <a name="organizing-and-testing-projects-with-the-net-core-command-line"></a>.NET Core コマンド ラインを使用したプロジェクトの整理およびテスト

このチュートリアルでは、「[Windows/Linux/macOS の .NET Core でのコマンド ラインの使用に関する概要](./using-with-xplat-cli.md)」に従って、簡単な "hello world" シナリオより高度で、よく構成されたアプリケーションを作成するための準備方法を示します。

## <a name="using-folders-to-organize-code"></a>フォルダーを使用してコードを整理する

新しい種類の作業を導入したいものとします。 そのためには、ファイルを追加し、*Program.cs* ファイルに含めることができる名前空間を割り当てます。

```
/MyProject
|__Program.cs
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
```

プロジェクトのサイズが比較的小さい場合に適しています。 しかしながら、多くの異なる種類のデータを含み、複数レイヤーになる可能性のある大規模なアプリケーションでは、論理的な整理が必要になります。 その場合はフォルダーを使用します。 このガイドで説明する [NewTypes サンプル プロジェクト](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypesMsBuild)に従うことも、独自のファイルとフォルダーを作成することもできます。

最初に、プロジェクトのルートの下に新しいフォルダーを作成します。 `/Model`がここでは選択されています。

```
/NewTypes
|__/Model
|__Program.cs
|__NewTypes.csproj
```

フォルダーに新しい種類をいくつか追加します。

```
/NewTypes
|__/Model
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__Program.cs
|__NewTypes.csproj
```

同じディレクトリ内のファイルであった場合と同じように、すべてを同じ名前空間にするので、`Program.cs` に含めることができます。

### <a name="example-pet-types"></a>例: ペットの種類

この例では、`Dog` と `Cat` という&2; つの新しい種類を作成し、`IPet` という共通インターフェイスを実装します。

フォルダーの構造:

```
/NewTypes
|__/Pets
   |__Dog.cs
   |__Cat.cs
   |__IPet.cs
|__Program.cs
|__NewTypes.csproj
```

`IPet.cs`:
```csharp
using System;

namespace Pets
{
    public interface IPet
    {
        string TalkToOwner();
    }
}
```

`Dog.cs`:
```csharp
using System;

namespace Pets
{
    public class Dog : IPet
    {
        public string TalkToOwner() => "Woof!";
    }
}
```

`Cat.cs`:
```csharp
using System;

namespace Pets
{
    public class Cat : IPet
    {
        public string TalkToOwner() => "Meow!";
    }
}
```

`Program.cs`:
```csharp
using System;
using Pets;
using System.Collections.Generic;

namespace ConsoleApplication
{
    public class Program
    {
        public static void Main(string[] args)
        {
            List<IPet> pets = new List<IPet>
            {
                new Dog(),
                new Cat()  
            };
            
            foreach (var pet in pets)
            {
                Console.WriteLine(pet.TalkToOwner());
            }
        }
    }
}
```

`NewTypes.csproj`:
```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />
  
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <Compile Include="**\*.cs" />
    <EmbeddedResource Include="**\*.resx" />
  </ItemGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.NETCore.App">
      <Version>1.0.1</Version>
    </PackageReference>
    <PackageReference Include="Microsoft.NET.Sdk">
      <Version>1.0.0-alpha-20161104-2</Version>
      <PrivateAssets>All</PrivateAssets>
    </PackageReference>
  </ItemGroup>
  
  <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
</Project>
```

これを実行すると次のようになります。

```
$ dotnet restore
$ dotnet run
Woof!
Meow!
```

新しいペットの種類 (`Bird` など) を追加して、このプロジェクトを拡張できます。

## <a name="testing-your-console-app"></a>コンソール アプリのテスト

どこかの時点でプロジェクトをテストする必要があります。 次に適切な方法を示します。

1. 既存プロジェクトのすべてのソースを、新しい `src` フォルダーに移動します。

   ```
   /Project
   |__/src
   ```

2. `/test` ディレクトリを作成し、そこに `cd` します。

   ```
   /Project
   |__/src
   |__/test
   ```

3. `dotnet new xunit` コマンドを使用して、ディレクトリを初期化します。 ここでは xUnit を前提としますが、`xunit` を `mstest` に置き換えて、MS Test を使用することもできます。
   
### <a name="example-extending-the-newtypes-project"></a>例: NewTypes プロジェクトの拡張

プロジェクト システムを設定したので、テスト プロジェクトを作成し、テストの作成を始めることができます。 これ以降このガイドでは、[サンプルの Types プロジェクト](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypesMsBuild)を使用して拡張します。 さらに、[Xunit](https://xunit.github.io/) テスト フレームワークを使用します。 この手順に従っても、独自のマルチプロジェクト システムを作成してもかまいません。

プロジェクト全体の構造は、次のようになります。

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
|__/test
   |__NewTypesTests
      |__PetTests.cs
      |__NewTypesTests.csproj
```

テスト プロジェクトに必要な&2; つの新しい要素があります。

1. 次の参照を持つ正しい*NewTypesTests.csproj* ファイル:

   * 次のものへの参照:`xunit`
   * 次のものへの参照:`dotnet-test-xunit`
   * テスト対象コードに対応する名前空間への参照

   これは、*NewTypesTests* ディレクトリでコマンド プロンプトから `dotnet new xunit` と入力し、プロジェクト参照を `NewTypes` プロジェクトに追加することでビルドできます。

    `NewTypesTests/NewTypesTests.csproj`:
    ```xml
    <Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />

      <PropertyGroup>
        <OutputType>Exe</OutputType>
        <TargetFramework>netcoreapp1.0</TargetFramework>
      </PropertyGroup>

      <ItemGroup>
        <Compile Include="**\*.cs" />
        <EmbeddedResource Include="**\*.resx" />
      </ItemGroup>

      <ItemGroup>
        <PackageReference Include="Microsoft.NETCore.App">
          <Version>1.0.1</Version>
        </PackageReference>
        <PackageReference Include="Microsoft.NET.Sdk">
          <Version>1.0.0-alpha-20161104-2</Version>
          <PrivateAssets>All</PrivateAssets>
        </PackageReference>
        <PackageReference Include="Microsoft.NET.Test.Sdk">
          <Version>15.0.0-preview-20161024-02</Version>
        </PackageReference>
        <PackageReference Include="xunit">
          <Version>2.2.0-beta3-build3402</Version>
        </PackageReference>
        <PackageReference Include="xunit.runner.visualstudio">
          <Version>2.2.0-beta4-build1188</Version>
        </PackageReference>
        <ProjectReference Include="../../src/NewTypes/NewTypes.csproj"/>
      </ItemGroup>

      <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
    </Project>
    ```

2. xUnit テスト クラス。

    `PetTests.cs`: 
    ```csharp
    using System;
    using Xunit;
    using Pets;
    public class PetTests
    {
        [Fact]
        public void DogTalkToOwnerTest()
        {
            string expected = "Woof!";
            string actual = new Dog().TalkToOwner();
            
            Assert.Equal(expected, actual);
        }
        
        [Fact]
        public void CatTalkToOwnerTest()
        {
            string expected = "Meow!";
            string actual = new Cat().TalkToOwner();
            
            Assert.Equal(expected, actual);
        }
    }
    ```
   
これでテストを実行することができます。 [`dotnet test`](../tools/dotnet-test.md) コマンドは、プロジェクトで指定したテスト ランナーを実行します。 最上位レベルのディレクトリで開始します。
 
```
$ cd test/NewTypesTests
$ dotnet restore
$ dotnet test
```
 
出力は次のようになります。
 
```
xUnit.net .NET CLI test runner (64-bit win10-x64)
  Discovering: NewTypesTests
  Discovered:  NewTypesTests
  Starting:    NewTypesTests
  Finished:    NewTypesTests
=== TEST EXECUTION SUMMARY ===
   NewTypesTests  Total: 2, Errors: 0, Failed: 0, Skipped: 0, Time: 0.144s
SUMMARY: Total: 1 targets, Passed: 1, Failed: 0.
```


---
title: .NET Core コマンド ラインを使用したプロジェクトの整理およびテスト
description: このチュートリアルでは、コマンド ラインから .NET Core プロジェクトを整理してテストする方法について説明します。
author: cartermp
ms.author: mairaw
ms.date: 05/16/2017
ms.openlocfilehash: a49eb1d398ab80a4ece703b7889083ea967df862
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="organizing-and-testing-projects-with-the-net-core-command-line"></a>.NET Core コマンド ラインを使用したプロジェクトの整理およびテスト

このチュートリアルでは、「[Windows/Linux/macOS の .NET Core でのコマンド ラインの使用に関する概要](using-with-xplat-cli.md)」に従って、簡単なコンソール アプリの作成より高度でよく構成されたアプリケーションの開発を行います。 フォルダーを使用してコードを整理する方法に続き、このチュートリアルでは [xUnit](https://xunit.github.io/) テスト フレームワークでコンソール アプリケーションを拡張する方法を示します。

## <a name="using-folders-to-organize-code"></a>フォルダーを使用してコードを整理する

コンソール アプリに新しいタイプを導入する場合、そのタイプを含むファイルをアプリに追加することができます。 たとえば、`AccountInformation` および `MonthlyReportRecords` タイプを含むファイルをプロジェクトに追加した場合、以下のように、プロジェクト ファイルの構造はフラットで移動しやすいものになります。

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

ただし、これはプロジェクトのサイズが比較的小さい場合にのみ適しています。 プロジェクトに 20 個のタイプを追加した場合はどうなるかというと、 プロジェクトのルート ディレクトリが乱雑になり、その多くのファイルの移動や維持が容易でなくなることは明らかです。

このようなプロジェクトを整理するには、新しいフォルダーを作成し、*Models* という名前を付けてタイプ ファイルを保持します。 以下のように、*Models* フォルダーにタイプ ファイルを配置します。

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

論理的にファイルをフォルダーにグループ化するプロジェクトでは、移動や維持が容易になります。 次のセクションでは、フォルダーと単体テストを使用してさらに複雑なサンプルを作成します。

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a>NewTypes ペット サンプルを使用した整理とテスト

### <a name="building-the-sample"></a>サンプルのビルド

以下の手順では、[NewTypes ペット サンプル](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild)に従うことも、独自のファイルとフォルダーを作成することもできます。 タイプは、後でタイプをさらに追加することができるフォルダー構造に論理的に整理されます。また、テストも、後でテストをさらに追加できるフォルダーに論理的に配置されます。

サンプルには `Dog` と `Cat` という 2 つのタイプが含まれています。このサンプルでは `IPet` という共通インターフェイスを実装します。 `NewTypes` プロジェクトの目標は、*Pets* フォルダーにペット関連のタイプを整理することです。 別のタイプ セット (*WildAnimals* など) が後で追加された場合、それらは *Pets* フォルダーと同じ場所にある *NewTypes* フォルダーに配置されます。 *WildAnimals* フォルダーには、`Squirrel` や `Rabbit` タイプなど、ペットではない動物のタイプを含めることができます。 このようにタイプを追加すれば、プロジェクトはよく構成された状態に保たれます。 

以下のようなファイル コンテンツのフォルダー構造を作成します。

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
```

*IPet.cs*:

[!code-csharp[IPet interface](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/IPet.cs)]

*Dog.cs*:

[!code-csharp[Dog class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Dog.cs)]

*Cat.cs*:

[!code-csharp[Cat class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Cat.cs)]

*Program.cs*:

[!code-csharp[Main](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Program.cs)]

*NewTypes.csproj*:

[!code-xml[NewTypes csproj](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/NewTypes.csproj)]

次のコマンドを実行します。

```console
dotnet run
```

次の出力を取得します。

```console
Woof!
Meow!
```

省略可能な演習: このプロジェクトを拡張し、`Bird` などの新しいペット タイプを追加することができます。 その場合、鳥の `TalkToOwner` メソッドで所有者に `Tweet!` を与えるようにします。 再度アプリを実行します。 出力には `Tweet!` が含まれます。

### <a name="testing-the-sample"></a>サンプルのテスト

これで、`NewTypes` プロジェクトの準備ができました。フォルダーにはペット関連のタイプが保持されており、プロジェクトは整理された状態です。 次は、テスト プロジェクトを作成し、[xUnit](https://xunit.github.io/) テスト フレームワークを使用してテストの作成を開始します。 単体テストでは、ペット タイプの動作を自動的にチェックして、正しく動作していることを確認することができます。

*test* フォルダーを作成します。この中に *NewTypesTests* フォルダーが含まれます。 *NewTypesTests* フォルダーのコマンド プロンプトから、`dotnet new xunit` を実行します。 これで、*NewTypesTests.csproj* と *UnitTest1.cs* という 2 つのファイルが生成されます。

現在、テスト プロジェクトでは `NewTypes` のタイプをテストすることはできません。`NewTypes` プロジェクトへのプロジェクト参照が必要になります。 プロジェクト参照を追加するには、以下の [`dotnet add reference`](../tools/dotnet-add-reference.md) コマンドを使用します。

```
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

次のように、*NewTypesTests.csproj* ファイルに `<ItemGroup>` ノードを追加して、プロジェクト参照を手動で追加することもできます。

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

*NewTypesTests.csproj*:

[!code-xml[NewTypesTests csproj](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/NewTypesTests.csproj)]

*NewTypesTests.csproj* ファイルには以下のものが含まれます。

* `Microsoft.NET.Test.Sdk` (.NET テスト インフラストラクチャ) へのパッケージ参照
* `xunit` (xUnit テスト フレームワーク) へのパッケージ参照
* `xunit.runner.visualstudio` (テスト ランナー) へのパッケージ参照
* `NewTypes` (テスト対象コード) へのプロジェクト参照

*UnitTest1.cs* の名前を *PetTests.cs* に変更し、ファイル内のコードを以下の内容と置き換えます。

```csharp
using System;
using Xunit;
using Pets;

public class PetTests
{
    [Fact]
    public void DogTalkToOwnerReturnsWoof()
    {
        string expected = "Woof!";
        string actual = new Dog().TalkToOwner();
        
        Assert.NotEqual(expected, actual);
    }
    
    [Fact]
    public void CatTalkToOwnerReturnsMeow()
    {
        string expected = "Meow!";
        string actual = new Cat().TalkToOwner();
        
        Assert.NotEqual(expected, actual);
    }
}
```

省略可能な演習: 所有者に `Tweet!` を与える前述の `Bird` タイプを追加した場合は、テスト メソッドを *PetTests.cs* ファイル `BirdTalkToOwnerReturnsTweet` に追加し、`Bird` タイプに対して `TalkToOwner` メソッドが正しく動作することを確認します。

> [!NOTE]
> `expected` と `actual` の値は等しくなることが予想されますが、`Assert.NotEqual` チェックの初期アサーションでは*等しくない* と指定します。 通常、テストのロジックを確認するために、最初は一度失敗するテストを作成します。 これは、テスト駆動型設計 (TDD) の手法において重要な手順です。 テストに失敗したことを確認したら、アサーションを調整してテストに成功できるようにします。

完全なプロジェクト構造を次に示します。

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

*test/NewTypesTests* ディレクトリから開始します。 [`dotnet restore`](../tools/dotnet-restore.md) コマンドを使用して、テスト プロジェクトを復元します。 [`dotnet test`](../tools/dotnet-test.md) コマンドを使用して、テストを実行します。 このコマンドは、プロジェクト ファイルで指定されたテスト ランナーを開始します。

 [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

 
予想どおり、テストは失敗し、コンソールには次の出力が表示されます。
 
```
Test run for C:\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp1.1\NewTypesTests.dll(.NETCoreApp,Version=v1.1)
Microsoft (R) Test Execution Command Line Tool Version 15.0.0.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:00.7271827]   Discovering: NewTypesTests
[xUnit.net 00:00:00.8258687]   Discovered:  NewTypesTests
[xUnit.net 00:00:00.8663545]   Starting:    NewTypesTests
[xUnit.net 00:00:01.0109236]     PetTests.CatTalkToOwnerReturnsMeow [FAIL]
[xUnit.net 00:00:01.0119107]       Assert.NotEqual() Failure
[xUnit.net 00:00:01.0120278]       Expected: Not "Meow!"
[xUnit.net 00:00:01.0120968]       Actual:   "Meow!"
[xUnit.net 00:00:01.0130500]       Stack Trace:
[xUnit.net 00:00:01.0141240]         C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs(22,0): at PetTests.CatTalkToOwnerReturnsMeow()
[xUnit.net 00:00:01.0272364]     PetTests.DogTalkToOwnerReturnsWoof [FAIL]
[xUnit.net 00:00:01.0273649]       Assert.NotEqual() Failure
[xUnit.net 00:00:01.0274166]       Expected: Not "Woof!"
[xUnit.net 00:00:01.0274690]       Actual:   "Woof!"
[xUnit.net 00:00:01.0275264]       Stack Trace:
[xUnit.net 00:00:01.0275960]         C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs(13,0): at PetTests.DogTalkToOwnerReturnsWoof()
[xUnit.net 00:00:01.0294509]   Finished:    NewTypesTests
Failed   PetTests.CatTalkToOwnerReturnsMeow
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Meow!"
Actual:   "Meow!"
Stack Trace:
   at PetTests.CatTalkToOwnerReturnsMeow() in C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 22
Failed   PetTests.DogTalkToOwnerReturnsWoof
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Woof!"
Actual:   "Woof!"
Stack Trace:
   at PetTests.DogTalkToOwnerReturnsWoof() in C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 13

Total tests: 2. Passed: 0. Failed: 2. Skipped: 0.
Test Run Failed.
Test execution time: 2.1371 Seconds
```

テストのアサーションを `Assert.NotEqual` から `Assert.Equal` に変更します。

[!code-csharp[PetTests class](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/PetTests.cs)]

`dotnet test` を使用してテストを再実行し、次の出力を取得します。

```
Microsoft (R) Test Execution Command Line Tool Version 15.0.0.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:01.3882374]   Discovering: NewTypesTests
[xUnit.net 00:00:01.4767970]   Discovered:  NewTypesTests
[xUnit.net 00:00:01.5157667]   Starting:    NewTypesTests
[xUnit.net 00:00:01.6408870]   Finished:    NewTypesTests

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6634 Seconds
```

テストに成功します。 ペット タイプのメソッドは、所有者との対話中に正しい値を返します。

これで、xUnit を使用してプロジェクトを整理し、テストする方法を習得できました。 次は、これらの方法を独自のプロジェクトに適用します。 *コーディングを楽しんでください。*


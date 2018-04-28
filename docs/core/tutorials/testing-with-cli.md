---
title: .NET Core コマンド ラインを使用したプロジェクトの整理およびテスト
description: このチュートリアルでは、コマンド ラインから .NET Core プロジェクトを整理してテストする方法について説明します。
author: cartermp
ms.author: mairaw
ms.date: 05/16/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 718f60d6321c1d24670ac177de64725d88bdd148
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="organizing-and-testing-projects-with-the-net-core-command-line"></a><span data-ttu-id="a43e8-103">.NET Core コマンド ラインを使用したプロジェクトの整理およびテスト</span><span class="sxs-lookup"><span data-stu-id="a43e8-103">Organizing and testing projects with the .NET Core command line</span></span>

<span data-ttu-id="a43e8-104">このチュートリアルでは、「[Windows/Linux/macOS の .NET Core でのコマンド ラインの使用に関する概要](using-with-xplat-cli.md)」に従って、簡単なコンソール アプリの作成より高度でよく構成されたアプリケーションの開発を行います。</span><span class="sxs-lookup"><span data-stu-id="a43e8-104">This tutorial follows [Getting started with .NET Core on Windows/Linux/macOS using the command line](using-with-xplat-cli.md), taking you beyond the creation of a simple console app to develop advanced and well-organized applications.</span></span> <span data-ttu-id="a43e8-105">フォルダーを使用してコードを整理する方法に続き、このチュートリアルでは [xUnit](https://xunit.github.io/) テスト フレームワークでコンソール アプリケーションを拡張する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a43e8-105">After showing you how to use folders to organize your code, this tutorial shows you how to extend a console application with the [xUnit](https://xunit.github.io/) testing framework.</span></span>

## <a name="using-folders-to-organize-code"></a><span data-ttu-id="a43e8-106">フォルダーを使用してコードを整理する</span><span class="sxs-lookup"><span data-stu-id="a43e8-106">Using folders to organize code</span></span>

<span data-ttu-id="a43e8-107">コンソール アプリに新しいタイプを導入する場合、そのタイプを含むファイルをアプリに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="a43e8-107">If you want to introduce new types into a console app, you can do so by adding files containing the types to the app.</span></span> <span data-ttu-id="a43e8-108">たとえば、`AccountInformation` および `MonthlyReportRecords` タイプを含むファイルをプロジェクトに追加した場合、以下のように、プロジェクト ファイルの構造はフラットで移動しやすいものになります。</span><span class="sxs-lookup"><span data-stu-id="a43e8-108">For example if you add files containing `AccountInformation` and `MonthlyReportRecords` types to your project, the project file structure is flat and easy to navigate:</span></span>

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="a43e8-109">ただし、これはプロジェクトのサイズが比較的小さい場合にのみ適しています。</span><span class="sxs-lookup"><span data-stu-id="a43e8-109">However, this only works well when the size of your project is relatively small.</span></span> <span data-ttu-id="a43e8-110">プロジェクトに 20 個のタイプを追加した場合はどうなるかというと、</span><span class="sxs-lookup"><span data-stu-id="a43e8-110">Can you imagine what will happen if you add 20 types to the project?</span></span> <span data-ttu-id="a43e8-111">プロジェクトのルート ディレクトリが乱雑になり、その多くのファイルの移動や維持が容易でなくなることは明らかです。</span><span class="sxs-lookup"><span data-stu-id="a43e8-111">The project definitely wouldn't be easy to navigate and maintain with that many files littering the project's root directory.</span></span>

<span data-ttu-id="a43e8-112">このようなプロジェクトを整理するには、新しいフォルダーを作成し、*Models* という名前を付けてタイプ ファイルを保持します。</span><span class="sxs-lookup"><span data-stu-id="a43e8-112">To organize the project, create a new folder and name it *Models* to hold the type files.</span></span> <span data-ttu-id="a43e8-113">以下のように、*Models* フォルダーにタイプ ファイルを配置します。</span><span class="sxs-lookup"><span data-stu-id="a43e8-113">Place the type files into the *Models* folder:</span></span>

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

<span data-ttu-id="a43e8-114">論理的にファイルをフォルダーにグループ化するプロジェクトでは、移動や維持が容易になります。</span><span class="sxs-lookup"><span data-stu-id="a43e8-114">Projects that logically group files into folders are easy to navigate and maintain.</span></span> <span data-ttu-id="a43e8-115">次のセクションでは、フォルダーと単体テストを使用してさらに複雑なサンプルを作成します。</span><span class="sxs-lookup"><span data-stu-id="a43e8-115">In the next section, you create a more complex sample with folders and unit testing.</span></span>

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a><span data-ttu-id="a43e8-116">NewTypes ペット サンプルを使用した整理とテスト</span><span class="sxs-lookup"><span data-stu-id="a43e8-116">Organizing and testing using the NewTypes Pets Sample</span></span>

### <a name="building-the-sample"></a><span data-ttu-id="a43e8-117">サンプルのビルド</span><span class="sxs-lookup"><span data-stu-id="a43e8-117">Building the sample</span></span>

<span data-ttu-id="a43e8-118">以下の手順では、[NewTypes ペット サンプル](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild)に従うことも、独自のファイルとフォルダーを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="a43e8-118">For the following steps, you can either follow along using the [NewTypes Pets Sample](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) or create your own files and folders.</span></span> <span data-ttu-id="a43e8-119">タイプは、後でタイプをさらに追加することができるフォルダー構造に論理的に整理されます。また、テストも、後でテストをさらに追加できるフォルダーに論理的に配置されます。</span><span class="sxs-lookup"><span data-stu-id="a43e8-119">The types are logically organized into a folder structure that permits the addition of more types later, and tests are also logically placed in folders permitting the addition of more tests later.</span></span>

<span data-ttu-id="a43e8-120">サンプルには `Dog` と `Cat` という 2 つのタイプが含まれています。このサンプルでは `IPet` という共通インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="a43e8-120">The sample contains two types, `Dog` and `Cat`, and has them implement a common interface, `IPet`.</span></span> <span data-ttu-id="a43e8-121">`NewTypes` プロジェクトの目標は、*Pets* フォルダーにペット関連のタイプを整理することです。</span><span class="sxs-lookup"><span data-stu-id="a43e8-121">For the `NewTypes` project, your goal is to organize the pet-related types into a *Pets* folder.</span></span> <span data-ttu-id="a43e8-122">別のタイプ セット (*WildAnimals* など) が後で追加された場合、それらは *Pets* フォルダーと同じ場所にある *NewTypes* フォルダーに配置されます。</span><span class="sxs-lookup"><span data-stu-id="a43e8-122">If another set of types is added later, *WildAnimals* for example, they're placed in the *NewTypes* folder alongside the *Pets* folder.</span></span> <span data-ttu-id="a43e8-123">*WildAnimals* フォルダーには、`Squirrel` や `Rabbit` タイプなど、ペットではない動物のタイプを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a43e8-123">The *WildAnimals* folder may contain types for animals that aren't pets, such as `Squirrel` and `Rabbit` types.</span></span> <span data-ttu-id="a43e8-124">このようにタイプを追加すれば、プロジェクトはよく構成された状態に保たれます。</span><span class="sxs-lookup"><span data-stu-id="a43e8-124">In this way as types are added, the project remains well organized.</span></span> 

<span data-ttu-id="a43e8-125">以下のようなファイル コンテンツのフォルダー構造を作成します。</span><span class="sxs-lookup"><span data-stu-id="a43e8-125">Create the following folder structure with file content indicated:</span></span>

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

<span data-ttu-id="a43e8-126">*IPet.cs*:</span><span class="sxs-lookup"><span data-stu-id="a43e8-126">*IPet.cs*:</span></span>

[!code-csharp[IPet interface](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/IPet.cs)]

<span data-ttu-id="a43e8-127">*Dog.cs*:</span><span class="sxs-lookup"><span data-stu-id="a43e8-127">*Dog.cs*:</span></span>

[!code-csharp[Dog class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Dog.cs)]

<span data-ttu-id="a43e8-128">*Cat.cs*:</span><span class="sxs-lookup"><span data-stu-id="a43e8-128">*Cat.cs*:</span></span>

[!code-csharp[Cat class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Cat.cs)]

<span data-ttu-id="a43e8-129">*Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="a43e8-129">*Program.cs*:</span></span>

[!code-csharp[Main](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Program.cs)]

<span data-ttu-id="a43e8-130">*NewTypes.csproj*:</span><span class="sxs-lookup"><span data-stu-id="a43e8-130">*NewTypes.csproj*:</span></span>

[!code-xml[NewTypes csproj](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/NewTypes.csproj)]

<span data-ttu-id="a43e8-131">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="a43e8-131">Execute the following commands:</span></span>

```console
dotnet run
```

<span data-ttu-id="a43e8-132">次の出力を取得します。</span><span class="sxs-lookup"><span data-stu-id="a43e8-132">Obtain the following output:</span></span>

```console
Woof!
Meow!
```

<span data-ttu-id="a43e8-133">省略可能な演習: このプロジェクトを拡張し、`Bird` などの新しいペット タイプを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="a43e8-133">Optional exercise: You can add a new pet type, such as a `Bird`, by extending this project.</span></span> <span data-ttu-id="a43e8-134">その場合、鳥の `TalkToOwner` メソッドで所有者に `Tweet!` を与えるようにします。</span><span class="sxs-lookup"><span data-stu-id="a43e8-134">Make the bird's `TalkToOwner` method give a `Tweet!` to the owner.</span></span> <span data-ttu-id="a43e8-135">再度アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="a43e8-135">Run the app again.</span></span> <span data-ttu-id="a43e8-136">出力には `Tweet!` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a43e8-136">The output will include `Tweet!`</span></span>

### <a name="testing-the-sample"></a><span data-ttu-id="a43e8-137">サンプルのテスト</span><span class="sxs-lookup"><span data-stu-id="a43e8-137">Testing the sample</span></span>

<span data-ttu-id="a43e8-138">これで、`NewTypes` プロジェクトの準備ができました。フォルダーにはペット関連のタイプが保持されており、プロジェクトは整理された状態です。</span><span class="sxs-lookup"><span data-stu-id="a43e8-138">The `NewTypes` project is in place, and you've organized it by keeping the pets-related types in a folder.</span></span> <span data-ttu-id="a43e8-139">次は、テスト プロジェクトを作成し、[xUnit](https://xunit.github.io/) テスト フレームワークを使用してテストの作成を開始します。</span><span class="sxs-lookup"><span data-stu-id="a43e8-139">Next, create your test project and start writing tests with the [xUnit](https://xunit.github.io/) test framework.</span></span> <span data-ttu-id="a43e8-140">単体テストでは、ペット タイプの動作を自動的にチェックして、正しく動作していることを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="a43e8-140">Unit testing allows you to automatically check the bevahior of your pet types to confirm that they're operating properly.</span></span>

<span data-ttu-id="a43e8-141">*test* フォルダーを作成します。この中に *NewTypesTests* フォルダーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a43e8-141">Create a *test* folder with a *NewTypesTests* folder within it.</span></span> <span data-ttu-id="a43e8-142">*NewTypesTests* フォルダーのコマンド プロンプトから、`dotnet new xunit` を実行します。</span><span class="sxs-lookup"><span data-stu-id="a43e8-142">At a command prompt from the *NewTypesTests* folder, execute `dotnet new xunit`.</span></span> <span data-ttu-id="a43e8-143">これで、*NewTypesTests.csproj* と *UnitTest1.cs* という 2 つのファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="a43e8-143">This produces two files: *NewTypesTests.csproj* and *UnitTest1.cs*.</span></span>

<span data-ttu-id="a43e8-144">現在、テスト プロジェクトでは `NewTypes` のタイプをテストすることはできません。`NewTypes` プロジェクトへのプロジェクト参照が必要になります。</span><span class="sxs-lookup"><span data-stu-id="a43e8-144">The test project cannot currently test the types in `NewTypes` and requires a project reference to the `NewTypes` project.</span></span> <span data-ttu-id="a43e8-145">プロジェクト参照を追加するには、以下の [`dotnet add reference`](../tools/dotnet-add-reference.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="a43e8-145">To add a project reference, use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

<span data-ttu-id="a43e8-146">次のように、*NewTypesTests.csproj* ファイルに `<ItemGroup>` ノードを追加して、プロジェクト参照を手動で追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="a43e8-146">You also have the option of manually adding the project reference by adding an `<ItemGroup>` node to the *NewTypesTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

<span data-ttu-id="a43e8-147">*NewTypesTests.csproj*:</span><span class="sxs-lookup"><span data-stu-id="a43e8-147">*NewTypesTests.csproj*:</span></span>

[!code-xml[NewTypesTests csproj](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/NewTypesTests.csproj)]

<span data-ttu-id="a43e8-148">*NewTypesTests.csproj* ファイルには以下のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a43e8-148">The *NewTypesTests.csproj* file contains the following:</span></span>

* <span data-ttu-id="a43e8-149">`Microsoft.NET.Test.Sdk` (.NET テスト インフラストラクチャ) へのパッケージ参照</span><span class="sxs-lookup"><span data-stu-id="a43e8-149">Package reference to `Microsoft.NET.Test.Sdk`, the .NET testing infrastructure</span></span>
* <span data-ttu-id="a43e8-150">`xunit` (xUnit テスト フレームワーク) へのパッケージ参照</span><span class="sxs-lookup"><span data-stu-id="a43e8-150">Package reference to `xunit`, the xUnit testing framework</span></span>
* <span data-ttu-id="a43e8-151">`xunit.runner.visualstudio` (テスト ランナー) へのパッケージ参照</span><span class="sxs-lookup"><span data-stu-id="a43e8-151">Package reference to `xunit.runner.visualstudio`, the test runner</span></span>
* <span data-ttu-id="a43e8-152">`NewTypes` (テスト対象コード) へのプロジェクト参照</span><span class="sxs-lookup"><span data-stu-id="a43e8-152">Project reference to `NewTypes`, the code to test</span></span>

<span data-ttu-id="a43e8-153">*UnitTest1.cs* の名前を *PetTests.cs* に変更し、ファイル内のコードを以下の内容と置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a43e8-153">Change the name of *UnitTest1.cs* to *PetTests.cs* and replace the code in the file with the following:</span></span>

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

<span data-ttu-id="a43e8-154">省略可能な演習: 所有者に `Tweet!` を与える前述の `Bird` タイプを追加した場合は、テスト メソッドを *PetTests.cs* ファイル `BirdTalkToOwnerReturnsTweet` に追加し、`Bird` タイプに対して `TalkToOwner` メソッドが正しく動作することを確認します。</span><span class="sxs-lookup"><span data-stu-id="a43e8-154">Optional exercise: If you added a `Bird` type earlier that yields a `Tweet!` to the owner, add a test method to the *PetTests.cs* file, `BirdTalkToOwnerReturnsTweet`, to check that the `TalkToOwner` method works correctly for the `Bird` type.</span></span>

> [!NOTE]
> <span data-ttu-id="a43e8-155">`expected` と `actual` の値は等しくなることが予想されますが、`Assert.NotEqual` チェックの初期アサーションでは*等しくない* と指定します。</span><span class="sxs-lookup"><span data-stu-id="a43e8-155">Although you expect that the `expected` and `actual` values are equal, the initial assertions with the `Assert.NotEqual` checks specify that they are *not equal*.</span></span> <span data-ttu-id="a43e8-156">通常、テストのロジックを確認するために、最初は一度失敗するテストを作成します。</span><span class="sxs-lookup"><span data-stu-id="a43e8-156">Always initially create your tests to fail once in order to check the logic of the tests.</span></span> <span data-ttu-id="a43e8-157">これは、テスト駆動型設計 (TDD) の手法において重要な手順です。</span><span class="sxs-lookup"><span data-stu-id="a43e8-157">This is an important step in test-driven design (TDD) methodology.</span></span> <span data-ttu-id="a43e8-158">テストに失敗したことを確認したら、アサーションを調整してテストに成功できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a43e8-158">After you confirm the tests fail, you adjust the assertions to allow them to pass.</span></span>

<span data-ttu-id="a43e8-159">完全なプロジェクト構造を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a43e8-159">The following shows the complete project structure:</span></span>

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

<span data-ttu-id="a43e8-160">*test/NewTypesTests* ディレクトリから開始します。</span><span class="sxs-lookup"><span data-stu-id="a43e8-160">Start in the *test/NewTypesTests* directory.</span></span> <span data-ttu-id="a43e8-161">[`dotnet restore`](../tools/dotnet-restore.md) コマンドを使用して、テスト プロジェクトを復元します。</span><span class="sxs-lookup"><span data-stu-id="a43e8-161">Restore the test project with the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="a43e8-162">[`dotnet test`](../tools/dotnet-test.md) コマンドを使用して、テストを実行します。</span><span class="sxs-lookup"><span data-stu-id="a43e8-162">Run the tests with the [`dotnet test`](../tools/dotnet-test.md) command.</span></span> <span data-ttu-id="a43e8-163">このコマンドは、プロジェクト ファイルで指定されたテスト ランナーを開始します。</span><span class="sxs-lookup"><span data-stu-id="a43e8-163">This command starts the test runner specified in the project file.</span></span>

 [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

 
<span data-ttu-id="a43e8-164">予想どおり、テストは失敗し、コンソールには次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a43e8-164">As expected, testing fails, and the console displays the following output:</span></span>
 
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

<span data-ttu-id="a43e8-165">テストのアサーションを `Assert.NotEqual` から `Assert.Equal` に変更します。</span><span class="sxs-lookup"><span data-stu-id="a43e8-165">Change the assertions of your tests from `Assert.NotEqual` to `Assert.Equal`:</span></span>

[!code-csharp[PetTests class](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/PetTests.cs)]

<span data-ttu-id="a43e8-166">`dotnet test` を使用してテストを再実行し、次の出力を取得します。</span><span class="sxs-lookup"><span data-stu-id="a43e8-166">Re-run the tests with the `dotnet test` command and obtain the following output:</span></span>

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

<span data-ttu-id="a43e8-167">テストに成功します。</span><span class="sxs-lookup"><span data-stu-id="a43e8-167">Testing passes.</span></span> <span data-ttu-id="a43e8-168">ペット タイプのメソッドは、所有者との対話中に正しい値を返します。</span><span class="sxs-lookup"><span data-stu-id="a43e8-168">The pet types' methods return the correct values when talking to the owner.</span></span>

<span data-ttu-id="a43e8-169">これで、xUnit を使用してプロジェクトを整理し、テストする方法を習得できました。</span><span class="sxs-lookup"><span data-stu-id="a43e8-169">You've learned techniques for organizing and testing projects using xUnit.</span></span> <span data-ttu-id="a43e8-170">次は、これらの方法を独自のプロジェクトに適用します。</span><span class="sxs-lookup"><span data-stu-id="a43e8-170">Go forward with these techniques applying them in your own projects.</span></span> <span data-ttu-id="a43e8-171">*コーディングを楽しんでください。*</span><span class="sxs-lookup"><span data-stu-id="a43e8-171">*Happy coding!*</span></span>


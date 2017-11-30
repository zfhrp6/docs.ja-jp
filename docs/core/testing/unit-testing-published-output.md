---
title: "パブリッシュされた出力を dotnet vstest をテストします。"
description: "Dotnet vstest コマンドを使用してパブリッシュされた出力でテストを実行する方法を説明します。"
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 3965e4ca-75b8-4969-b3af-ca993c397a15
ms.openlocfilehash: 217787d41a9da6000941ded6caaa4f44d124644b
ms.sourcegitcommit: 8a4f8e6a7f1341764abcd188a332cc28d1e2d8ec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2017
---
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="c4ccc-103">パブリッシュされた出力を dotnet vstest をテストします。</span><span class="sxs-lookup"><span data-stu-id="c4ccc-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="c4ccc-104">使用して既にパブリッシュされた出力でテストを実行することができます、`dotnet vstest`コマンド。</span><span class="sxs-lookup"><span data-stu-id="c4ccc-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="c4ccc-105">これは機能 xUnit、MSTest、NUnit にテストします。</span><span class="sxs-lookup"><span data-stu-id="c4ccc-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="c4ccc-106">単に、パブリッシュされた出力の一部であった DLL ファイルを検索し、実行します。</span><span class="sxs-lookup"><span data-stu-id="c4ccc-106">Simply locate the DLL file that was part of your published output and run:</span></span>
```
dotnet vstest <MyPublishedTests>.dll
```
<span data-ttu-id="c4ccc-107">ここで`<MyPublishedTests>`発行されたテスト プロジェクトの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c4ccc-107">where `<MyPublishedTests>` is the name of your published test project.</span></span>

### <a name="example-of-running-tests-on-a-published-dll"></a><span data-ttu-id="c4ccc-108">パブリッシュされた DLL のテストの実行の例</span><span class="sxs-lookup"><span data-stu-id="c4ccc-108">Example of running tests on a published DLL</span></span>

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE] <span data-ttu-id="c4ccc-109">注: アプリは対象にする framework 以外の場合`netcoreapp`まだ実行することができます、 `dotnet vstest` framework フラグで対象のフレームワークに渡すことによってコマンド。</span><span class="sxs-lookup"><span data-stu-id="c4ccc-109">Note: If your app is targeting a framework other than `netcoreapp` you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="c4ccc-110">たとえば、`dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"` のようにします。</span><span class="sxs-lookup"><span data-stu-id="c4ccc-110">For example, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="c4ccc-111">Visual Studio 2017 更新プログラム 5 には、目的のフレームワークが自動的に検出します。</span><span class="sxs-lookup"><span data-stu-id="c4ccc-111">In Visual Studio 2017 Update 5 the desired framework is automatically detected.</span></span>

### <a name="related-topics"></a><span data-ttu-id="c4ccc-112">関連トピック</span><span class="sxs-lookup"><span data-stu-id="c4ccc-112">Related topics</span></span>
- [<span data-ttu-id="c4ccc-113">Dotnet テスト、xUnit で単体テスト</span><span class="sxs-lookup"><span data-stu-id="c4ccc-113">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="c4ccc-114">Dotnet テストと、MSTest の単体テスト</span><span class="sxs-lookup"><span data-stu-id="c4ccc-114">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)

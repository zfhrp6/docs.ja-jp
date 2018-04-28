---
title: パブリッシュされた出力を dotnet vstest でテストします
description: dotnet vstest コマンドを使用してパブリッシュされた出力をテストする方法を説明します。
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.workload:
- dotnetcore
ms.openlocfilehash: 2f750a8bb0907069691c4a4491beeb4b1733df29
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="d4124-103">パブリッシュされた出力を dotnet vstest でテストします</span><span class="sxs-lookup"><span data-stu-id="d4124-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="d4124-104">`dotnet vstest` コマンドを使用して、パブリッシュ済みの出力に対してテストを行えます。</span><span class="sxs-lookup"><span data-stu-id="d4124-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="d4124-105">これは xUnit、MSTest、および NUnit の各テストで機能します。</span><span class="sxs-lookup"><span data-stu-id="d4124-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="d4124-106">次のように、パブリッシュされた出力の一部であった DLL ファイルを見つけて実行するだけです。</span><span class="sxs-lookup"><span data-stu-id="d4124-106">Simply locate the DLL file that was part of your published output and run:</span></span>

```
dotnet vstest <MyPublishedTests>.dll
```

<span data-ttu-id="d4124-107">`<MyPublishedTests>` はパブリッシュされたテスト プロジェクトの名前です。</span><span class="sxs-lookup"><span data-stu-id="d4124-107">where `<MyPublishedTests>` is the name of your published test project.</span></span>

## <a name="example-of-running-tests-on-a-published-dll"></a><span data-ttu-id="d4124-108">パブリッシュされた DLL に対してテストを行う例</span><span class="sxs-lookup"><span data-stu-id="d4124-108">Example of running tests on a published DLL</span></span>

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> <span data-ttu-id="d4124-109">注: アプリが `netcoreapp` 以外のフレームワークを対象とする場合でも、対象のフレームワークでフレームワーク フラグを付けて渡すことで `dotnet vstest` コマンドを実行できます。</span><span class="sxs-lookup"><span data-stu-id="d4124-109">Note: If your app is targeting a framework other than `netcoreapp` you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="d4124-110">たとえば、`dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"` のようにします。</span><span class="sxs-lookup"><span data-stu-id="d4124-110">For example, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="d4124-111">Visual Studio 2017 Update 5 では、望ましいフレームワークが自動的に検出されます。</span><span class="sxs-lookup"><span data-stu-id="d4124-111">In Visual Studio 2017 Update 5 the desired framework is automatically detected.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4124-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4124-112">See also</span></span>
 [<span data-ttu-id="d4124-113">dotnet テストおよび xUnit を使用した単体テスト</span><span class="sxs-lookup"><span data-stu-id="d4124-113">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)  
 [<span data-ttu-id="d4124-114">dotnet テストおよび MSTest を使用した単体テスト</span><span class="sxs-lookup"><span data-stu-id="d4124-114">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)  

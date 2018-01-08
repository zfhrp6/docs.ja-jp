---
title: "選択的単体テストの実行"
description: "dotnet test コマンドでフィルター式を使用して、選択的単体テストを実行する方法を紹介します。"
keywords: ".NET, .NET Core, 単体テスト, 選択的テスト"
author: smadala
ms.author: mairaw
ms.date: 03/22/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 13d01272-bbf8-456c-a97a-560001d1a7f2
ms.workload: dotnetcore
ms.openlocfilehash: a650e971afd63171b0cc12f679d81bc222a609a5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="dfef5-104">選択的単体テストの実行</span><span class="sxs-lookup"><span data-stu-id="dfef5-104">Running selective unit tests</span></span>

<span data-ttu-id="dfef5-105">次の例では、`dotnet test` を使用します。</span><span class="sxs-lookup"><span data-stu-id="dfef5-105">The following examples use `dotnet test`.</span></span> <span data-ttu-id="dfef5-106">`vstest.console.exe` を使用している場合は、`--filter ` を `--testcasefilter:` に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="dfef5-106">If you're using `vstest.console.exe`, replace `--filter ` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="dfef5-107">MSTest</span><span class="sxs-lookup"><span data-stu-id="dfef5-107">MSTest</span></span>

```csharp
namespace MSTestNamespace
{
    using Microsoft.VisualStudio.TestTools.UnitTesting;

    [TestClass]
    public class UnitTestClass1
    {
        [Priority(2)]
        [TestMethod]
        public void TestMethod1()
        {
        }

        [TestCategory("CategoryA")]
        [Priority(3)]
        [TestMethod]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="dfef5-108">正規表現</span><span class="sxs-lookup"><span data-stu-id="dfef5-108">Expression</span></span> | <span data-ttu-id="dfef5-109">結果</span><span class="sxs-lookup"><span data-stu-id="dfef5-109">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="dfef5-110">`FullyQualifiedName` に `Method` が含まれるテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="dfef5-110">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="dfef5-111">`vstest 15.1+` で使用できます。</span><span class="sxs-lookup"><span data-stu-id="dfef5-111">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="dfef5-112">名前に `TestMethod1` が含まれるテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="dfef5-112">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTestClass1` | <span data-ttu-id="dfef5-113">クラス `MSTestNamespace.UnitTestClass1` 内にあるテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="dfef5-113">Runs tests which are in class `MSTestNamespace.UnitTestClass1`.</span></span><br><span data-ttu-id="dfef5-114">**注:** `ClassName` 値には名前空間があるため、`ClassName=UnitTestClass1` は機能しません。</span><span class="sxs-lookup"><span data-stu-id="dfef5-114">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTestClass1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTestClass1.TestMethod1` | <span data-ttu-id="dfef5-115">`MSTestNamespace.UnitTestClass1.TestMethod1` 以外のテストをすべて実行します。</span><span class="sxs-lookup"><span data-stu-id="dfef5-115">Runs all tests except `MSTestNamespace.UnitTestClass1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="dfef5-116">`[TestCategory("CategoryA")]` の注釈が付けられているテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="dfef5-116">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=3` | <span data-ttu-id="dfef5-117">`[Priority(3)]` の注釈が付けられているテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="dfef5-117">Runs tests which are annotated with `[Priority(3)]`.</span></span><br><span data-ttu-id="dfef5-118">**注:** `Priority~3` は文字列ではないため、無効な値です。</span><span class="sxs-lookup"><span data-stu-id="dfef5-118">**Note:** `Priority~3` is an invalid value, as it isn't a string.</span></span> |

<span data-ttu-id="dfef5-119">**条件演算子| と &amp; の使用**</span><span class="sxs-lookup"><span data-stu-id="dfef5-119">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="dfef5-120">正規表現</span><span class="sxs-lookup"><span data-stu-id="dfef5-120">Expression</span></span> | <span data-ttu-id="dfef5-121">結果</span><span class="sxs-lookup"><span data-stu-id="dfef5-121">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTestClass1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="dfef5-122">`FullyQualifiedName` に `UnitTestClass1` がある、**または** `TestCategory` が `CategoryA` のテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="dfef5-122">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA"` | <span data-ttu-id="dfef5-123">`FullyQualifiedName` に `UnitTestClass1` がある、**および** `TestCategory` が `CategoryA` のテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="dfef5-123">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="dfef5-124">`UnitTestClass1` を含む `FullyQualifiedName` **および** `TestCategory` が `CategoryA`、**または** `Priority` が 1 かのいずれかのテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="dfef5-124">Runs tests which have either `FullyQualifiedName` containing `UnitTestClass1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="dfef5-125">xUnit</span><span class="sxs-lookup"><span data-stu-id="dfef5-125">xUnit</span></span>

```csharp
namespace XUnitNamespace
{
    public class TestClass1
    {
        [Trait("Category", "bvt")]
        [Trait("Priority", "1")]
        [Fact]
        public void foo()
        {
        }

        [Trait("Category", "Nightly")]
        [Trait("Priority", "2")]
        [Fact]
        public void bar()
        {
        }
    }
}
```

| <span data-ttu-id="dfef5-126">正規表現</span><span class="sxs-lookup"><span data-stu-id="dfef5-126">Expression</span></span> | <span data-ttu-id="dfef5-127">結果</span><span class="sxs-lookup"><span data-stu-id="dfef5-127">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="dfef5-128">`XUnitNamespace.TestClass1.Test1` という 1 つのテストのみを実行します。</span><span class="sxs-lookup"><span data-stu-id="dfef5-128">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="dfef5-129">`XUnitNamespace.TestClass1.Test1` 以外のテストをすべて実行します。</span><span class="sxs-lookup"><span data-stu-id="dfef5-129">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="dfef5-130">表示名に `TestClass1` が含まれるテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="dfef5-130">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="dfef5-131">コード例では、特性をキー `Category` や `Priority` で定義すると、フィルター処理に使用できます。</span><span class="sxs-lookup"><span data-stu-id="dfef5-131">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="dfef5-132">正規表現</span><span class="sxs-lookup"><span data-stu-id="dfef5-132">Expression</span></span> | <span data-ttu-id="dfef5-133">結果</span><span class="sxs-lookup"><span data-stu-id="dfef5-133">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="dfef5-134">`FullyQualifiedName` に `XUnit` が含まれるテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="dfef5-134">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="dfef5-135">`vstest 15.1+` で使用できます。</span><span class="sxs-lookup"><span data-stu-id="dfef5-135">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=bvt` | <span data-ttu-id="dfef5-136">`[Trait("Category", "bvt")]` があるテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="dfef5-136">Runs tests which have `[Trait("Category", "bvt")]`.</span></span> |

<span data-ttu-id="dfef5-137">**条件演算子| と &amp; の使用**</span><span class="sxs-lookup"><span data-stu-id="dfef5-137">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="dfef5-138">正規表現</span><span class="sxs-lookup"><span data-stu-id="dfef5-138">Expression</span></span> | <span data-ttu-id="dfef5-139">結果</span><span class="sxs-lookup"><span data-stu-id="dfef5-139">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=Nightly"</code> | <span data-ttu-id="dfef5-140">`FullyQualifiedName` に `TestClass1` がある、**または** `Category` が `Nightly` のテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="dfef5-140">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `Nightly`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=Nightly"` | <span data-ttu-id="dfef5-141">`FullyQualifiedName` に `TestClass1` がある、**および** `Category` が `Nightly` のテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="dfef5-141">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `Nightly`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=Nightly)&#124;Priority=1"</code> | <span data-ttu-id="dfef5-142">`TestClass1` を含む `FullyQualifiedName` **および** `Category` が `CategoryA`、**または** `Priority` が 1 かのいずれかのテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="dfef5-142">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

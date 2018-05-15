---
title: 選択的単体テストの実行
description: dotnet test コマンドでフィルター式を使用して、選択的単体テストを実行する方法を紹介します。
author: smadala
ms.author: mairaw
ms.date: 03/22/2017
ms.openlocfilehash: caea91e9884dba6bc07a7ef6a99699e43d23399c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="0998b-103">選択的単体テストの実行</span><span class="sxs-lookup"><span data-stu-id="0998b-103">Running selective unit tests</span></span>

<span data-ttu-id="0998b-104">次の例では、`dotnet test` を使用します。</span><span class="sxs-lookup"><span data-stu-id="0998b-104">The following examples use `dotnet test`.</span></span> <span data-ttu-id="0998b-105">`vstest.console.exe` を使用している場合は、`--filter ` を `--testcasefilter:` に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="0998b-105">If you're using `vstest.console.exe`, replace `--filter ` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="0998b-106">MSTest</span><span class="sxs-lookup"><span data-stu-id="0998b-106">MSTest</span></span>

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

| <span data-ttu-id="0998b-107">正規表現</span><span class="sxs-lookup"><span data-stu-id="0998b-107">Expression</span></span> | <span data-ttu-id="0998b-108">結果</span><span class="sxs-lookup"><span data-stu-id="0998b-108">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="0998b-109">`FullyQualifiedName` に `Method` が含まれるテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="0998b-109">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="0998b-110">`vstest 15.1+` で使用できます。</span><span class="sxs-lookup"><span data-stu-id="0998b-110">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="0998b-111">名前に `TestMethod1` が含まれるテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="0998b-111">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTestClass1` | <span data-ttu-id="0998b-112">クラス `MSTestNamespace.UnitTestClass1` 内にあるテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="0998b-112">Runs tests which are in class `MSTestNamespace.UnitTestClass1`.</span></span><br><span data-ttu-id="0998b-113">**注:** `ClassName` 値には名前空間があるため、`ClassName=UnitTestClass1` は機能しません。</span><span class="sxs-lookup"><span data-stu-id="0998b-113">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTestClass1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTestClass1.TestMethod1` | <span data-ttu-id="0998b-114">`MSTestNamespace.UnitTestClass1.TestMethod1` 以外のテストをすべて実行します。</span><span class="sxs-lookup"><span data-stu-id="0998b-114">Runs all tests except `MSTestNamespace.UnitTestClass1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="0998b-115">`[TestCategory("CategoryA")]` の注釈が付けられているテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="0998b-115">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=3` | <span data-ttu-id="0998b-116">`[Priority(3)]` の注釈が付けられているテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="0998b-116">Runs tests which are annotated with `[Priority(3)]`.</span></span><br><span data-ttu-id="0998b-117">**注:** `Priority~3` は文字列ではないため、無効な値です。</span><span class="sxs-lookup"><span data-stu-id="0998b-117">**Note:** `Priority~3` is an invalid value, as it isn't a string.</span></span> |

<span data-ttu-id="0998b-118">**条件演算子| と &amp; の使用**</span><span class="sxs-lookup"><span data-stu-id="0998b-118">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="0998b-119">正規表現</span><span class="sxs-lookup"><span data-stu-id="0998b-119">Expression</span></span> | <span data-ttu-id="0998b-120">結果</span><span class="sxs-lookup"><span data-stu-id="0998b-120">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTestClass1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="0998b-121">`FullyQualifiedName` に `UnitTestClass1` がある、**または** `TestCategory` が `CategoryA` のテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="0998b-121">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA"` | <span data-ttu-id="0998b-122">`FullyQualifiedName` に `UnitTestClass1` がある、**および** `TestCategory` が `CategoryA` のテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="0998b-122">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="0998b-123">`UnitTestClass1` を含む `FullyQualifiedName` **および** `TestCategory` が `CategoryA`、**または** `Priority` が 1 かのいずれかのテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="0998b-123">Runs tests which have either `FullyQualifiedName` containing `UnitTestClass1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="0998b-124">xUnit</span><span class="sxs-lookup"><span data-stu-id="0998b-124">xUnit</span></span>

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

| <span data-ttu-id="0998b-125">正規表現</span><span class="sxs-lookup"><span data-stu-id="0998b-125">Expression</span></span> | <span data-ttu-id="0998b-126">結果</span><span class="sxs-lookup"><span data-stu-id="0998b-126">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="0998b-127">`XUnitNamespace.TestClass1.Test1` という 1 つのテストのみを実行します。</span><span class="sxs-lookup"><span data-stu-id="0998b-127">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="0998b-128">`XUnitNamespace.TestClass1.Test1` 以外のテストをすべて実行します。</span><span class="sxs-lookup"><span data-stu-id="0998b-128">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="0998b-129">表示名に `TestClass1` が含まれるテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="0998b-129">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="0998b-130">コード例では、特性をキー `Category` や `Priority` で定義すると、フィルター処理に使用できます。</span><span class="sxs-lookup"><span data-stu-id="0998b-130">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="0998b-131">正規表現</span><span class="sxs-lookup"><span data-stu-id="0998b-131">Expression</span></span> | <span data-ttu-id="0998b-132">結果</span><span class="sxs-lookup"><span data-stu-id="0998b-132">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="0998b-133">`FullyQualifiedName` に `XUnit` が含まれるテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="0998b-133">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="0998b-134">`vstest 15.1+` で使用できます。</span><span class="sxs-lookup"><span data-stu-id="0998b-134">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=bvt` | <span data-ttu-id="0998b-135">`[Trait("Category", "bvt")]` があるテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="0998b-135">Runs tests which have `[Trait("Category", "bvt")]`.</span></span> |

<span data-ttu-id="0998b-136">**条件演算子| と &amp; の使用**</span><span class="sxs-lookup"><span data-stu-id="0998b-136">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="0998b-137">正規表現</span><span class="sxs-lookup"><span data-stu-id="0998b-137">Expression</span></span> | <span data-ttu-id="0998b-138">結果</span><span class="sxs-lookup"><span data-stu-id="0998b-138">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=Nightly"</code> | <span data-ttu-id="0998b-139">`FullyQualifiedName` に `TestClass1` がある、**または** `Category` が `Nightly` のテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="0998b-139">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `Nightly`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=Nightly"` | <span data-ttu-id="0998b-140">`FullyQualifiedName` に `TestClass1` がある、**および** `Category` が `Nightly` のテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="0998b-140">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `Nightly`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=Nightly)&#124;Priority=1"</code> | <span data-ttu-id="0998b-141">`TestClass1` を含む `FullyQualifiedName` **および** `Category` が `CategoryA`、**または** `Priority` が 1 かのいずれかのテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="0998b-141">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

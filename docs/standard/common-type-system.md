---
title: "共通型システムと共通言語仕様"
description: "共通型システム (CTS) と共通言語仕様 (CLS) を使用して .NET で複数の言語をサポートする方法について説明します。"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3b1f5725-ac94-4f17-8e5f-244442438a4d
ms.translationtype: HT
ms.sourcegitcommit: 3155295489e1188640dae5aa5bf9fdceb7480ed6
ms.openlocfilehash: 9c2cc090dfd5405def0cd6ab9ec1771be4a332a5
ms.contentlocale: ja-jp
ms.lasthandoff: 08/21/2017

---

# <a name="common-type-system--common-language-specification"></a><span data-ttu-id="5ff2a-104">共通型システムと共通言語仕様</span><span class="sxs-lookup"><span data-stu-id="5ff2a-104">Common Type System & Common Language Specification</span></span>

<span data-ttu-id="5ff2a-105">これらの 2 つの用語は、.NET の世界で自由に使用されます。これらは実際には、.NET 実装で多言語開発を可能にし、そのしくみを理解するために重要です。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-105">Again, two terms that are freely used in the .NET world, they actually are crucial to understand how a .NET implementation enables multi-language development and to understand how it works.</span></span>

## <a name="common-type-system"></a><span data-ttu-id="5ff2a-106">共通型システム</span><span class="sxs-lookup"><span data-stu-id="5ff2a-106">Common Type System</span></span>

<span data-ttu-id="5ff2a-107">最初に、.NET 実装は_言語に依存しない_点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-107">To start from the beginning, remember that a .NET implementation is _language agnostic_.</span></span> <span data-ttu-id="5ff2a-108">これはプログラマーが IL にコンパイルできる任意の言語でコードを記述できることを意味するだけではありません。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-108">This doesn’t just mean that a programmer can write her code in any language that can be compiled to IL.</span></span> <span data-ttu-id="5ff2a-109">また、.NET 実装で使用可能な他の言語で記述されたコードをプログラマーが操作できる必要があることも意味します。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-109">It also means that she needs to be able to interact with code written in other languages that are able to be used on a .NET implementation.</span></span>

<span data-ttu-id="5ff2a-110">これを透過的に行うには、すべてのサポートされる種類を記述するための共通の方法が存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-110">In order to do this transparently, there has to be a common way to describe all supported types.</span></span> <span data-ttu-id="5ff2a-111">これは、共通型システム (CTS) の役割です。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-111">This is what the Common Type System (CTS) is in charge of doing.</span></span> <span data-ttu-id="5ff2a-112">CTS には、次のようないくつかの目的があります。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-112">It was made to do several things:</span></span>

*   <span data-ttu-id="5ff2a-113">多言語での実行のためのフレームワークを確立する。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-113">Establish a framework for cross-language execution.</span></span>
*   <span data-ttu-id="5ff2a-114">.NET 実装でさまざまな言語の実装をサポートするためのオブジェクト指向モデルを提供する。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-114">Provide an object-oriented model to support implementing various languages on a .NET implementation.</span></span>
*   <span data-ttu-id="5ff2a-115">型を扱うときにすべての言語が従う必要がある規則のセットを定義する。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-115">Define a set of rules that all languages must follow when it comes to working with types.</span></span>
*   <span data-ttu-id="5ff2a-116">アプリケーション開発に使用される基本的なプリミティブ データ型 (`Boolean`、`Byte`、`Char` など) を含んだライブラリを提供します。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-116">Provide a library that contains the basic primitive types that are used in application development (such as, `Boolean`, `Byte`, `Char` etc.)</span></span>

<span data-ttu-id="5ff2a-117">CTS が定義する、参照型と値型という 2 つの主要な型をサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-117">CTS defines two main kinds of types that should be supported: reference and value types.</span></span> <span data-ttu-id="5ff2a-118">それらの名前が空の定義を示します。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-118">Their names point to their definitions.</span></span>

<span data-ttu-id="5ff2a-119">参照型のオブジェクトは、オブジェクトの実際の値を指す参照によって表されます。ここでの参照は、 C/C++ のポインターに似ています。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-119">Reference types’ objects are represented by a reference to the object’s actual value; a reference here is similar to a pointer in C/C++.</span></span> <span data-ttu-id="5ff2a-120">これは、単純にオブジェクトの値が存在しているメモリの場所を参照します。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-120">It simply refers to a memory location where the objects’ values are.</span></span> <span data-ttu-id="5ff2a-121">このことはこれらの型の使用方法に深く影響します。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-121">This has a profound impact on how these types are used.</span></span> <span data-ttu-id="5ff2a-122">変数に参照型割り当ててその変数をメソッドに渡す場合、たとえば、オブジェクトの変更はメイン オブジェクトに反映されます。コピーはありません。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-122">If you assign a reference type to a variable and then pass that variable into a method, for instance, any changes to the object will be reflected on the main object; there is no copying.</span></span>

<span data-ttu-id="5ff2a-123">値型は、反対にオブジェクトがそれらの値によって表されます。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-123">Value types are the opposite, where the objects are represented by their values.</span></span> <span data-ttu-id="5ff2a-124">変数に値型を割り当てた場合、基本的にオブジェクトの値をコピーすることになります。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-124">If you assign a value type to a variable, you are essentially copying a value of the object.</span></span>

<span data-ttu-id="5ff2a-125">CTS では、いくつかの型のカテゴリが定義され、それぞれに固有のセマンティックスと使用方法があります。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-125">CTS defines several categories of types, each with their specific semantics and usage:</span></span>

*   <span data-ttu-id="5ff2a-126">クラス</span><span class="sxs-lookup"><span data-stu-id="5ff2a-126">Classes</span></span>
*   <span data-ttu-id="5ff2a-127">構造体</span><span class="sxs-lookup"><span data-stu-id="5ff2a-127">Structures</span></span>
*   <span data-ttu-id="5ff2a-128">列挙型</span><span class="sxs-lookup"><span data-stu-id="5ff2a-128">Enums</span></span>
*   <span data-ttu-id="5ff2a-129">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5ff2a-129">Interfaces</span></span>
*   <span data-ttu-id="5ff2a-130">デリゲート</span><span class="sxs-lookup"><span data-stu-id="5ff2a-130">Delegates</span></span>

<span data-ttu-id="5ff2a-131">CTS では、アクセス修飾子、有効な型のメンバー、継承とオーバーロードの動作など、型の他のすべてのプロパティも定義されます。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-131">CTS also defines all other properties of the types, such as access modifiers, what are valid type members, how inheritance and overloading works and so on.</span></span> <span data-ttu-id="5ff2a-132">残念ながら、これらのプロパティについての詳しい説明は概要の記事の範囲外ですが、これらのトピックの詳細情報については、最後の「[その他のリソース](#more-resources)」のリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-132">Unfortunately, going deep into any of those is beyond the scope of an introductory article such as this, but you can consult [More resources](#more-resources) section at the end for links to more in-depth content that covers these topics.</span></span>

## <a name="common-language-specification"></a><span data-ttu-id="5ff2a-133">共通言語仕様</span><span class="sxs-lookup"><span data-stu-id="5ff2a-133">Common Language Specification</span></span>

<span data-ttu-id="5ff2a-134">完全な相互運用シナリオを有効にするには、コードで作成されるすべてのオブジェクトがそれらを使用している言語 (_呼び出し元_) で何らかの共通点に依存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-134">To enable full interoperability scenarios, all objects that are created in code must rely on some commonality in the languages that are consuming them (are their _callers_).</span></span> <span data-ttu-id="5ff2a-135">多くの異なる言語があるので、.NET では、**共通言語仕様** (CLS) という共通性を規定しています。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-135">Since there are numerous different languages, .NET has specified those commonalities in something called the **Common Language Specification** (CLS).</span></span> <span data-ttu-id="5ff2a-136">CLS は、多くの一般的なアプリケーションに必要な機能のセットを定義しています。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-136">CLS defines a set of features that are needed by many common applications.</span></span> <span data-ttu-id="5ff2a-137">さらに、サポートする必要がある .NET 上に実装される言語用のある種のレシピも提供しています。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-137">It also provides a sort of recipe for any language that is implemented on top of .NET on what it needs to support.</span></span>

<span data-ttu-id="5ff2a-138">CLS は CTS のサブセットです。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-138">CLS is a subset of the CTS.</span></span> <span data-ttu-id="5ff2a-139">つまり、CLS により厳しい規則がない限り、CTS のすべての規則は CLS にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-139">This means that all of the rules in the CTS also apply to the CLS, unless the CLS rules are more strict.</span></span> <span data-ttu-id="5ff2a-140">CLS の規則のみを使用してコンポーネントがビルドされている場合、つまり API で CLS の機能のみが公開されている場合、**CLS 準拠**であると言われます。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-140">If a component is built using only the rules in the CLS, that is, it exposes only the CLS features in its API, it is said to be **CLS-compliant**.</span></span> <span data-ttu-id="5ff2a-141">たとえば、`<framework-librares>` は、.NET がサポートされているすべての言語で機能する必要があるため、まさに CLS 準拠です。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-141">For instance, the `<framework-librares>` are CLS-compliant precisely because they need to work across all of the languages that are supported on .NET.</span></span>

<span data-ttu-id="5ff2a-142">CMS のすべての機能の概要については、下の「[その他のリソース](#more-resources)」セクションのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ff2a-142">You can consult the documents in the [More Resources](#more-resources) section below to get an overview of all the features in the CLS.</span></span>

## <a name="more-resources"></a><span data-ttu-id="5ff2a-143">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="5ff2a-143">More resources</span></span>

*   [<span data-ttu-id="5ff2a-144">共通型システム</span><span class="sxs-lookup"><span data-stu-id="5ff2a-144">Common Type System</span></span>](https://msdn.microsoft.com/library/zcx1eb1e.aspx)
*   [<span data-ttu-id="5ff2a-145">共通言語仕様</span><span class="sxs-lookup"><span data-stu-id="5ff2a-145">Common Language Specification</span></span>](https://msdn.microsoft.com/library/12a7a7h3.aspx)


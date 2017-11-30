---
title: "7.2 c# の新機能"
description: "7.2 c# の新機能の概要。"
keywords: "C# 言語のデザイン、7.2、Visual Studio 2017、"
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: a580a4a3a0a49e97ea8fb96699d1d978a9bc0a64
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="whats-new-in-c-72"></a><span data-ttu-id="e2110-104">7.2 c# の新機能</span><span class="sxs-lookup"><span data-stu-id="e2110-104">What's new in C# 7.2</span></span>

<span data-ttu-id="e2110-105">C# 7.2 は、いくつかの便利な機能の追加をもう 1 つのポイント リリースです。</span><span class="sxs-lookup"><span data-stu-id="e2110-105">C# 7.2 is another point release that adds a number of useful features.</span></span>
<span data-ttu-id="e2110-106">不要なコピーまたは割り当てを回避することで、値型より効率的にこのリリースの 1 つのテーマが扱うです。</span><span class="sxs-lookup"><span data-stu-id="e2110-106">One theme for this release is working more efficiently with value types by avoiding unnecessary copies or allocations.</span></span> 

<span data-ttu-id="e2110-107">他の機能は、小さなが便利な機能です。</span><span class="sxs-lookup"><span data-stu-id="e2110-107">The remaining features are small, nice-to-have features.</span></span>

<span data-ttu-id="e2110-108">7.2 c# を使用して、[バージョンの言語の選択](csharp-7-1.md#language-version-selection)コンパイラ言語バージョンを選択する構成要素。</span><span class="sxs-lookup"><span data-stu-id="e2110-108">C# 7.2 uses the [language version selection](csharp-7-1.md#language-version-selection) configuration element to select the compiler language version.</span></span>

<span data-ttu-id="e2110-109">このリリースの新しい言語機能は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e2110-109">The new language features in this release are:</span></span>

* [<span data-ttu-id="e2110-110">値の型と参照セマンティクス</span><span class="sxs-lookup"><span data-stu-id="e2110-110">Reference semantics with value types</span></span>](#reference-semantics-with-value-types)
  - <span data-ttu-id="e2110-111">参照セマンティクスを使用して値型の使用を有効にする構文の機能強化の組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="e2110-111">A combination of syntax improvements that enable working with value types using reference semantics.</span></span>
* [<span data-ttu-id="e2110-112">非末尾名前付き引数</span><span class="sxs-lookup"><span data-stu-id="e2110-112">Non-trailing named arguments</span></span>](#non-trailing-named-arguments)
  - <span data-ttu-id="e2110-113">名前付き引数は、位置指定引数が続くことができます。</span><span class="sxs-lookup"><span data-stu-id="e2110-113">Named arguments can be followed by positional arguments.</span></span>
* [<span data-ttu-id="e2110-114">数値リテラルの先頭にアンダー スコア</span><span class="sxs-lookup"><span data-stu-id="e2110-114">Leading underscores in numeric literals</span></span>](#leading-underscores-in-numeric-literals)
  - <span data-ttu-id="e2110-115">数値リテラルは、印刷桁の数字の前に先頭にアンダー スコアを保持できます。</span><span class="sxs-lookup"><span data-stu-id="e2110-115">Numeric literals can now have leading underscores before any printed digits.</span></span>
* [<span data-ttu-id="e2110-116">`private protected`アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="e2110-116">`private protected` access modifier</span></span>](#private-protected)
  - <span data-ttu-id="e2110-117">`private protected`アクセス修飾子、同じアセンブリ内の派生クラスのアクセスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="e2110-117">The `private protected` access modifier enables access for derived classes in the same assembly.</span></span>

## <a name="reference-semantics-with-value-types"></a><span data-ttu-id="e2110-118">値の型と参照セマンティクス</span><span class="sxs-lookup"><span data-stu-id="e2110-118">Reference semantics with value types</span></span>

<span data-ttu-id="e2110-119">7.2 で導入された機能の言語では、参照セマンティクスを使用しているときに、値の型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e2110-119">Language features introduced in 7.2 let you work with value types while using reference semantics.</span></span> <span data-ttu-id="e2110-120">参照型の使用に関連付けられているメモリの割り当てを生じることがなくコピーの値の型を最小限に抑えることによってパフォーマンスを向上するためのものです。</span><span class="sxs-lookup"><span data-stu-id="e2110-120">They are designed to increase performance by minimizing copying value types without incurring the memory allocations associated with using reference types.</span></span> <span data-ttu-id="e2110-121">機能は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e2110-121">The features include:</span></span>

 - <span data-ttu-id="e2110-122">`in`でその引数が参照によって渡されますが、呼び出されたメソッドでは変更されませんを指定する、パラメーター修飾子。</span><span class="sxs-lookup"><span data-stu-id="e2110-122">The `in` modifier on parameters, to specify that an argument is passed by reference but not modified by the called method.</span></span>
 - <span data-ttu-id="e2110-123">`ref readonly`修飾子をメソッドが参照渡しでその値を返すが、そのオブジェクトへの書き込みを許可しないことを示すために、メソッドを返します。</span><span class="sxs-lookup"><span data-stu-id="e2110-123">The `ref readonly` modifier on method returns, to indicate that a method returns its value by reference but doesn't allow writes to that object.</span></span>
 - <span data-ttu-id="e2110-124">`readonly struct`宣言、構造体は変更不可にしてとして渡す必要があることを示す、`in`そのメンバー メソッドのパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="e2110-124">The `readonly struct` declaration, to indicate that a struct is immutable and should be passed as an `in` parameter to its member methods.</span></span>
 - <span data-ttu-id="e2110-125">`ref struct`構造体型マネージ メモリに直接アクセスする必要があります常にスタック割り当てられることを示すために、宣言します。</span><span class="sxs-lookup"><span data-stu-id="e2110-125">The `ref struct` declaration, to indicate that a struct type accesses managed memory directly and must always be stack allocated.</span></span>

<span data-ttu-id="e2110-126">詳細については、これらのすべての変更を読み取ることができる[参照セマンティクスを持つ値の型を使用して](../reference-semantics-with-value-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="e2110-126">You can read more about all these changes in [Using value types with reference semantics](../reference-semantics-with-value-types.md).</span></span>

## <a name="non-trailing-named-arguments"></a><span data-ttu-id="e2110-127">非末尾名前付き引数</span><span class="sxs-lookup"><span data-stu-id="e2110-127">Non-trailing named arguments</span></span>

<span data-ttu-id="e2110-128">メソッドの呼び出しは、適切な位置では、名前付き引数と位置指定引数の前に名前付き引数を使用してようになりました可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e2110-128">Method calls may now use named arguments that precede positional arguments when those named arguments are in the correct positions.</span></span> <span data-ttu-id="e2110-129">詳細については、次を参照してください。[名前付き引数と省略可能な引数](../programming-guide/classes-and-structs/named-and-optional-arguments.md)です。</span><span class="sxs-lookup"><span data-stu-id="e2110-129">For more information see [Named and optional arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span></span>

## <a name="leading-underscores-in-numeric-literals"></a><span data-ttu-id="e2110-130">数値リテラルの先頭にアンダー スコア</span><span class="sxs-lookup"><span data-stu-id="e2110-130">Leading underscores in numeric literals</span></span>

<span data-ttu-id="e2110-131">7.0 (C#) で桁区切り記号のサポートの実装を許可していない、`_`リテラル値の最初の文字であります。</span><span class="sxs-lookup"><span data-stu-id="e2110-131">The implementation of support for digit separators in C# 7.0 didn't allow the `_` to be the first character of the literal value.</span></span> <span data-ttu-id="e2110-132">16 進とバイナリの数値リテラルの開始可能性があります、`_`です。</span><span class="sxs-lookup"><span data-stu-id="e2110-132">Hex and binary numeric literals may now begin with an `_`.</span></span> 

<span data-ttu-id="e2110-133">例:</span><span class="sxs-lookup"><span data-stu-id="e2110-133">For example:</span></span>

```csharp
int binaryValue = 0b_0101_0101;
```

## `private protected`

<span data-ttu-id="e2110-134">最後に、新しい複合アクセス修飾子:`private protected`にメンバーは、同じアセンブリ内で宣言されている、派生クラスによってアクセス可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e2110-134">Finally, a new compound access modifier: `private protected` indicates that a member may be accessed by derived classes that are declared in the same assembly.</span></span> <span data-ttu-id="e2110-135">中に`protected internal`派生クラスでは、同じアセンブリにクラスへのアクセス許可`private protected`同じアセンブリ内で宣言されている派生型へのアクセスを制限します。</span><span class="sxs-lookup"><span data-stu-id="e2110-135">While `protected internal` allows access by derived classes or classes that are in the same assembly, `private protected` limits access to derived types declared in the same assembly.</span></span>

<span data-ttu-id="e2110-136">詳細については、次を参照してください。[アクセス修飾子](../language-reference/keywords/access-modifiers.md)言語リファレンスでします。</span><span class="sxs-lookup"><span data-stu-id="e2110-136">For more information see [access modifiers](../language-reference/keywords/access-modifiers.md) in the language reference.</span></span>

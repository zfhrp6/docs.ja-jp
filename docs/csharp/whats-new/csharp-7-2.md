---
title: "C# 7.2 の新機能"
description: "C# 7.2 の新機能の概要。"
keywords: "C# 言語の設計, 7.2, Visual Studio 2017,"
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: db22c9251fa5e9f5a9cb66af6ec8b193b88e0eb3
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2018
---
# <a name="whats-new-in-c-72"></a><span data-ttu-id="af937-104">C# 7.2 の新機能</span><span class="sxs-lookup"><span data-stu-id="af937-104">What's new in C# 7.2</span></span>

<span data-ttu-id="af937-105">C# 7.2 は、便利な機能が多数追加された、もう 1 つのポイント リリースです。</span><span class="sxs-lookup"><span data-stu-id="af937-105">C# 7.2 is another point release that adds a number of useful features.</span></span>
<span data-ttu-id="af937-106">このリリースのテーマの 1 つは、不要なコピーや割り当てを回避して、さまざまな値の型の操作をより効率的に行うことです。</span><span class="sxs-lookup"><span data-stu-id="af937-106">One theme for this release is working more efficiently with value types by avoiding unnecessary copies or allocations.</span></span> 

<span data-ttu-id="af937-107">他の機能も、小さくても、あると助かる機能です。</span><span class="sxs-lookup"><span data-stu-id="af937-107">The remaining features are small, nice-to-have features.</span></span>

<span data-ttu-id="af937-108">C# 7.2 では[言語バージョンの選択](csharp-7-1.md#language-version-selection)の構成要素を使用して、コンパイラ言語バージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="af937-108">C# 7.2 uses the [language version selection](csharp-7-1.md#language-version-selection) configuration element to select the compiler language version.</span></span>

<span data-ttu-id="af937-109">このリリースの新しい言語機能は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="af937-109">The new language features in this release are:</span></span>

* [<span data-ttu-id="af937-110">値の型による参照セマンティクス</span><span class="sxs-lookup"><span data-stu-id="af937-110">Reference semantics with value types</span></span>](#reference-semantics-with-value-types)
  - <span data-ttu-id="af937-111">参照セマンティクスを使用したさまざまな値の型の使用を有効にする、構文の機能強化の組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="af937-111">A combination of syntax improvements that enable working with value types using reference semantics.</span></span>
* [<span data-ttu-id="af937-112">末尾以外の名前付き引数</span><span class="sxs-lookup"><span data-stu-id="af937-112">Non-trailing named arguments</span></span>](#non-trailing-named-arguments)
  - <span data-ttu-id="af937-113">名前付き引数の後ろに位置引数を続けることができます。</span><span class="sxs-lookup"><span data-stu-id="af937-113">Named arguments can be followed by positional arguments.</span></span>
* [<span data-ttu-id="af937-114">数値リテラルでの先頭のアンダースコア (_)</span><span class="sxs-lookup"><span data-stu-id="af937-114">Leading underscores in numeric literals</span></span>](#leading-underscores-in-numeric-literals)
  - <span data-ttu-id="af937-115">数値リテラルの印刷桁の前に先頭のアンダースコア(_) を含めることができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="af937-115">Numeric literals can now have leading underscores before any printed digits.</span></span>
* [<span data-ttu-id="af937-116">`private protected` アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="af937-116">`private protected` access modifier</span></span>](#private-protected-access-modifier)
  - <span data-ttu-id="af937-117">`private protected` アクセス修飾子によって、同じアセンブリ内の派生クラスのアクセスが有効になります。</span><span class="sxs-lookup"><span data-stu-id="af937-117">The `private protected` access modifier enables access for derived classes in the same assembly.</span></span>

## <a name="reference-semantics-with-value-types"></a><span data-ttu-id="af937-118">値の型による参照セマンティクス</span><span class="sxs-lookup"><span data-stu-id="af937-118">Reference semantics with value types</span></span>

<span data-ttu-id="af937-119">7.2 で導入された言語機能では、参照セマンティクスを使用しているときに、さまざまな値の型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="af937-119">Language features introduced in 7.2 let you work with value types while using reference semantics.</span></span> <span data-ttu-id="af937-120">これらは、参照型の使用に関連するメモリの割り当てを生じさせずに、値の型のコピーを最小限に抑えてパフォーマンスを改善するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="af937-120">They are designed to increase performance by minimizing copying value types without incurring the memory allocations associated with using reference types.</span></span> <span data-ttu-id="af937-121">次のような機能があります。</span><span class="sxs-lookup"><span data-stu-id="af937-121">The features include:</span></span>

 - <span data-ttu-id="af937-122">パラメーターの `in` 修飾子。引数が参照によって渡されるが、呼び出されたメソッドでは変更されないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="af937-122">The `in` modifier on parameters, to specify that an argument is passed by reference but not modified by the called method.</span></span>
 - <span data-ttu-id="af937-123">メソッド戻りの `ref readonly` 修飾子。メソッドが参照によってその値を戻しますが、そのオブジェクトに対する書き込みを許可しないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="af937-123">The `ref readonly` modifier on method returns, to indicate that a method returns its value by reference but doesn't allow writes to that object.</span></span>
 - <span data-ttu-id="af937-124">`readonly struct` 宣言。変更不可の構造体で、そのメンバー メソッドの `in` パラメーターとして渡す必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="af937-124">The `readonly struct` declaration, to indicate that a struct is immutable and should be passed as an `in` parameter to its member methods.</span></span>
 - <span data-ttu-id="af937-125">`ref struct` 宣言。構造体型がマネージ メモリに直接アクセスし、常にスタック割り当てが必要であることを示します。</span><span class="sxs-lookup"><span data-stu-id="af937-125">The `ref struct` declaration, to indicate that a struct type accesses managed memory directly and must always be stack allocated.</span></span>

<span data-ttu-id="af937-126">これらすべての変更の詳細については、[参照セマンティクスを持つ値の型の使用](../reference-semantics-with-value-types.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="af937-126">You can read more about all these changes in [Using value types with reference semantics](../reference-semantics-with-value-types.md).</span></span>

## <a name="non-trailing-named-arguments"></a><span data-ttu-id="af937-127">末尾以外の名前付き引数</span><span class="sxs-lookup"><span data-stu-id="af937-127">Non-trailing named arguments</span></span>

<span data-ttu-id="af937-128">メソッド呼び出しで、位置引数の前に名前付き引数を使用できるようになりました。ただし、そのような名前付き引数が正しい位置にある場合です。</span><span class="sxs-lookup"><span data-stu-id="af937-128">Method calls may now use named arguments that precede positional arguments when those named arguments are in the correct positions.</span></span> <span data-ttu-id="af937-129">詳細については、「[名前付き引数と省略可能な引数](../programming-guide/classes-and-structs/named-and-optional-arguments.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af937-129">For more information see [Named and optional arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span></span>

## <a name="leading-underscores-in-numeric-literals"></a><span data-ttu-id="af937-130">数値リテラルでの先頭のアンダースコア (_)</span><span class="sxs-lookup"><span data-stu-id="af937-130">Leading underscores in numeric literals</span></span>

<span data-ttu-id="af937-131">C# 7.0 の桁区切り記号のサポートの実装では、`_` をリテラル値の最初の文字にすることができませんでした。</span><span class="sxs-lookup"><span data-stu-id="af937-131">The implementation of support for digit separators in C# 7.0 didn't allow the `_` to be the first character of the literal value.</span></span> <span data-ttu-id="af937-132">16 進とバイナリの数値リテラルの先頭に `_` を使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="af937-132">Hex and binary numeric literals may now begin with an `_`.</span></span> 

<span data-ttu-id="af937-133">例:</span><span class="sxs-lookup"><span data-stu-id="af937-133">For example:</span></span>

```csharp
int binaryValue = 0b_0101_0101;
```

## <a name="private-protected-access-modifier"></a><span data-ttu-id="af937-134">_private protected_ アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="af937-134">_private protected_ access modifier</span></span>

<span data-ttu-id="af937-135">最後に、新しい複合アクセス修飾子: `private protected` は、同じアセンブリで宣言されているクラスまたは派生クラスを含むことでメンバーにアクセスできることを示しています。</span><span class="sxs-lookup"><span data-stu-id="af937-135">Finally, a new compound access modifier: `private protected` indicates that a member may be accessed by containing class or derived classes that are declared in the same assembly.</span></span> <span data-ttu-id="af937-136">`protected internal` は同じアセンブリの派生クラスまたはクラスによるアクセスを許可していますが、`private protected` は同じアセンブリで宣言された派生型へのアクセスを制限しています。</span><span class="sxs-lookup"><span data-stu-id="af937-136">While `protected internal` allows access by derived classes or classes that are in the same assembly, `private protected` limits access to derived types declared in the same assembly.</span></span>

<span data-ttu-id="af937-137">詳細については、言語リファレンスの[アクセス修飾子](../language-reference/keywords/access-modifiers.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="af937-137">For more information see [access modifiers](../language-reference/keywords/access-modifiers.md) in the language reference.</span></span>

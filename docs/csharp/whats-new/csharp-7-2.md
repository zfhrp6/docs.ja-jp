---
title: C# 7.2 の新機能
description: C# 7.2 の新機能の概要。
ms.date: 08/16/2017
ms.openlocfilehash: a74afd7f073daa46328d60149e2dd90207420a80
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34566190"
---
# <a name="whats-new-in-c-72"></a><span data-ttu-id="f5a65-103">C# 7.2 の新機能</span><span class="sxs-lookup"><span data-stu-id="f5a65-103">What's new in C# 7.2</span></span>

<span data-ttu-id="f5a65-104">C# 7.2 は、便利な機能が多数追加された、もう 1 つのポイント リリースです。</span><span class="sxs-lookup"><span data-stu-id="f5a65-104">C# 7.2 is another point release that adds a number of useful features.</span></span>
<span data-ttu-id="f5a65-105">このリリースのテーマの 1 つは、不要なコピーや割り当てを回避して、さまざまな値の型の操作をより効率的に行うことです。</span><span class="sxs-lookup"><span data-stu-id="f5a65-105">One theme for this release is working more efficiently with value types by avoiding unnecessary copies or allocations.</span></span> 

<span data-ttu-id="f5a65-106">他の機能も、小さくても、あると助かる機能です。</span><span class="sxs-lookup"><span data-stu-id="f5a65-106">The remaining features are small, nice-to-have features.</span></span>

<span data-ttu-id="f5a65-107">C# 7.2 では[言語バージョンの選択](../language-reference/configure-language-version.md)の構成要素を使用して、コンパイラ言語バージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="f5a65-107">C# 7.2 uses the [language version selection](../language-reference/configure-language-version.md) configuration element to select the compiler language version.</span></span>

<span data-ttu-id="f5a65-108">このリリースの新しい言語機能は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f5a65-108">The new language features in this release are:</span></span>

* [<span data-ttu-id="f5a65-109">値の型による参照セマンティクス</span><span class="sxs-lookup"><span data-stu-id="f5a65-109">Reference semantics with value types</span></span>](#reference-semantics-with-value-types)
  - <span data-ttu-id="f5a65-110">参照セマンティクスを使用したさまざまな値の型の使用を有効にする、構文の機能強化の組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="f5a65-110">A combination of syntax improvements that enable working with value types using reference semantics.</span></span>
* [<span data-ttu-id="f5a65-111">末尾以外の名前付き引数</span><span class="sxs-lookup"><span data-stu-id="f5a65-111">Non-trailing named arguments</span></span>](#non-trailing-named-arguments)
  - <span data-ttu-id="f5a65-112">名前付き引数の後ろに位置引数を続けることができます。</span><span class="sxs-lookup"><span data-stu-id="f5a65-112">Named arguments can be followed by positional arguments.</span></span>
* [<span data-ttu-id="f5a65-113">数値リテラルでの先頭のアンダースコア (_)</span><span class="sxs-lookup"><span data-stu-id="f5a65-113">Leading underscores in numeric literals</span></span>](#leading-underscores-in-numeric-literals)
  - <span data-ttu-id="f5a65-114">数値リテラルの印刷桁の前に先頭のアンダースコア(_) を含めることができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="f5a65-114">Numeric literals can now have leading underscores before any printed digits.</span></span>
* [<span data-ttu-id="f5a65-115">`private protected` アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="f5a65-115">`private protected` access modifier</span></span>](#private-protected-access-modifier)
  - <span data-ttu-id="f5a65-116">`private protected` アクセス修飾子によって、同じアセンブリ内の派生クラスのアクセスが有効になります。</span><span class="sxs-lookup"><span data-stu-id="f5a65-116">The `private protected` access modifier enables access for derived classes in the same assembly.</span></span>

## <a name="reference-semantics-with-value-types"></a><span data-ttu-id="f5a65-117">値の型による参照セマンティクス</span><span class="sxs-lookup"><span data-stu-id="f5a65-117">Reference semantics with value types</span></span>

<span data-ttu-id="f5a65-118">7.2 で導入された言語機能では、参照セマンティクスを使用しているときに、さまざまな値の型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f5a65-118">Language features introduced in 7.2 let you work with value types while using reference semantics.</span></span> <span data-ttu-id="f5a65-119">これらは、参照型の使用に関連するメモリの割り当てを生じさせずに、値の型のコピーを最小限に抑えてパフォーマンスを改善するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="f5a65-119">They are designed to increase performance by minimizing copying value types without incurring the memory allocations associated with using reference types.</span></span> <span data-ttu-id="f5a65-120">次のような機能があります。</span><span class="sxs-lookup"><span data-stu-id="f5a65-120">The features include:</span></span>

 - <span data-ttu-id="f5a65-121">パラメーターの `in` 修飾子。引数が参照によって渡されるが、呼び出されたメソッドでは変更されないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="f5a65-121">The `in` modifier on parameters, to specify that an argument is passed by reference but not modified by the called method.</span></span>
 - <span data-ttu-id="f5a65-122">メソッド戻りの `ref readonly` 修飾子。メソッドが参照によってその値を戻しますが、そのオブジェクトに対する書き込みを許可しないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="f5a65-122">The `ref readonly` modifier on method returns, to indicate that a method returns its value by reference but doesn't allow writes to that object.</span></span>
 - <span data-ttu-id="f5a65-123">`readonly struct` 宣言。変更不可の構造体で、そのメンバー メソッドの `in` パラメーターとして渡す必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="f5a65-123">The `readonly struct` declaration, to indicate that a struct is immutable and should be passed as an `in` parameter to its member methods.</span></span>
 - <span data-ttu-id="f5a65-124">`ref struct` 宣言。構造体型がマネージ メモリに直接アクセスし、常にスタック割り当てが必要であることを示します。</span><span class="sxs-lookup"><span data-stu-id="f5a65-124">The `ref struct` declaration, to indicate that a struct type accesses managed memory directly and must always be stack allocated.</span></span>

<span data-ttu-id="f5a65-125">これらすべての変更の詳細については、[参照セマンティクスを持つ値の型の使用](../reference-semantics-with-value-types.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5a65-125">You can read more about all these changes in [Using value types with reference semantics](../reference-semantics-with-value-types.md).</span></span>

## <a name="non-trailing-named-arguments"></a><span data-ttu-id="f5a65-126">末尾以外の名前付き引数</span><span class="sxs-lookup"><span data-stu-id="f5a65-126">Non-trailing named arguments</span></span>

<span data-ttu-id="f5a65-127">メソッド呼び出しで、位置引数の前に名前付き引数を使用できるようになりました。ただし、そのような名前付き引数が正しい位置にある場合です。</span><span class="sxs-lookup"><span data-stu-id="f5a65-127">Method calls may now use named arguments that precede positional arguments when those named arguments are in the correct positions.</span></span> <span data-ttu-id="f5a65-128">詳細については、「[名前付き引数と省略可能な引数](../programming-guide/classes-and-structs/named-and-optional-arguments.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5a65-128">For more information see [Named and optional arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span></span>

## <a name="leading-underscores-in-numeric-literals"></a><span data-ttu-id="f5a65-129">数値リテラルでの先頭のアンダースコア (_)</span><span class="sxs-lookup"><span data-stu-id="f5a65-129">Leading underscores in numeric literals</span></span>

<span data-ttu-id="f5a65-130">C# 7.0 の桁区切り記号のサポートの実装では、`_` をリテラル値の最初の文字にすることができませんでした。</span><span class="sxs-lookup"><span data-stu-id="f5a65-130">The implementation of support for digit separators in C# 7.0 didn't allow the `_` to be the first character of the literal value.</span></span> <span data-ttu-id="f5a65-131">16 進とバイナリの数値リテラルの先頭に `_` を使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="f5a65-131">Hex and binary numeric literals may now begin with an `_`.</span></span> 

<span data-ttu-id="f5a65-132">例:</span><span class="sxs-lookup"><span data-stu-id="f5a65-132">For example:</span></span>

```csharp
int binaryValue = 0b_0101_0101;
```

## <a name="private-protected-access-modifier"></a><span data-ttu-id="f5a65-133">_private protected_ アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="f5a65-133">_private protected_ access modifier</span></span>

<span data-ttu-id="f5a65-134">最後に、新しい複合アクセス修飾子: `private protected` は、同じアセンブリで宣言されているクラスまたは派生クラスを含むことでメンバーにアクセスできることを示しています。</span><span class="sxs-lookup"><span data-stu-id="f5a65-134">Finally, a new compound access modifier: `private protected` indicates that a member may be accessed by containing class or derived classes that are declared in the same assembly.</span></span> <span data-ttu-id="f5a65-135">`protected internal` は同じアセンブリの派生クラスまたはクラスによるアクセスを許可していますが、`private protected` は同じアセンブリで宣言された派生型へのアクセスを制限しています。</span><span class="sxs-lookup"><span data-stu-id="f5a65-135">While `protected internal` allows access by derived classes or classes that are in the same assembly, `private protected` limits access to derived types declared in the same assembly.</span></span>

<span data-ttu-id="f5a65-136">詳細については、言語リファレンスの[アクセス修飾子](../language-reference/keywords/access-modifiers.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5a65-136">For more information see [access modifiers](../language-reference/keywords/access-modifiers.md) in the language reference.</span></span>

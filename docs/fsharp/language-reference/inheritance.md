---
title: "継承 (F#)"
description: "'Inherit' キーワードを使用して f# 継承関係を指定する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b38ab2f6-7ba7-4839-8eff-e6bd6cfd2b2f
ms.openlocfilehash: 331c8f4e39aacd9d5e55bfbaf584f037e58d36a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="inheritance"></a><span data-ttu-id="5a191-104">継承</span><span class="sxs-lookup"><span data-stu-id="5a191-104">Inheritance</span></span>

<span data-ttu-id="5a191-105">継承は、"は-a"リレーションシップのモデルを使用または、オブジェクト指向プログラミングのサブタイプ指定します。</span><span class="sxs-lookup"><span data-stu-id="5a191-105">Inheritance is used to model the "is-a" relationship, or subtyping, in object-oriented programming.</span></span>


## <a name="specifying-inheritance-relationships"></a><span data-ttu-id="5a191-106">継承関係を指定します。</span><span class="sxs-lookup"><span data-stu-id="5a191-106">Specifying Inheritance Relationships</span></span>
<span data-ttu-id="5a191-107">使用して継承関係を指定する、`inherit`クラス宣言でキーワード。</span><span class="sxs-lookup"><span data-stu-id="5a191-107">You specify inheritance relationships by using the `inherit` keyword in a class declaration.</span></span> <span data-ttu-id="5a191-108">基本的な構文形式は次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="5a191-108">The basic syntactical form is shown in the following example.</span></span>

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

<span data-ttu-id="5a191-109">クラスは、最大で 1 つ直接基底クラスを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="5a191-109">A class can have at most one direct base class.</span></span> <span data-ttu-id="5a191-110">使用して基底クラスを指定しないかどうか、`inherit`キーワードをクラスから暗黙的に継承`System.Object`です。</span><span class="sxs-lookup"><span data-stu-id="5a191-110">If you do not specify a base class by using the `inherit` keyword, the class implicitly inherits from `System.Object`.</span></span>


## <a name="inherited-members"></a><span data-ttu-id="5a191-111">継承されたメンバー</span><span class="sxs-lookup"><span data-stu-id="5a191-111">Inherited Members</span></span>
<span data-ttu-id="5a191-112">クラスは、別のクラスから継承している場合、メソッドと基底クラスのメンバー ユーザーが使用できる派生クラスの場合、派生クラスの直接的なメンバーと同様です。</span><span class="sxs-lookup"><span data-stu-id="5a191-112">If a class inherits from another class, the methods and members of the base class are available to users of the derived class as if they were direct members of the derived class.</span></span>

<span data-ttu-id="5a191-113">いずれかの let 束縛とコンス トラクターのパラメーターは、クラスにプライベート派生クラスからにアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="5a191-113">Any let bindings and constructor parameters are private to a class and, therefore, cannot be accessed from derived classes.</span></span>

<span data-ttu-id="5a191-114">キーワード`base`は派生クラスで使用でき、基本クラスのインスタンスを参照します。</span><span class="sxs-lookup"><span data-stu-id="5a191-114">The keyword `base` is available in derived classes and refers to the base class instance.</span></span> <span data-ttu-id="5a191-115">自己識別子のように使用されます。</span><span class="sxs-lookup"><span data-stu-id="5a191-115">It is used like the self-identifier.</span></span>


## <a name="virtual-methods-and-overrides"></a><span data-ttu-id="5a191-116">仮想メソッドとオーバーライド</span><span class="sxs-lookup"><span data-stu-id="5a191-116">Virtual Methods and Overrides</span></span>
<span data-ttu-id="5a191-117">仮想メソッドとプロパティ機能はやや異なります f# で他の .NET 言語と比較しています。</span><span class="sxs-lookup"><span data-stu-id="5a191-117">Virtual methods (and properties) work somewhat differently in F# as compared to other .NET languages.</span></span> <span data-ttu-id="5a191-118">使用する新しい仮想メンバーを宣言する、`abstract`キーワード。</span><span class="sxs-lookup"><span data-stu-id="5a191-118">To declare a new virtual member, you use the `abstract` keyword.</span></span> <span data-ttu-id="5a191-119">この操作は、そのメソッドの既定の実装を提供するかどうかに関係なく行います。</span><span class="sxs-lookup"><span data-stu-id="5a191-119">You do this regardless of whether you provide a default implementation for that method.</span></span> <span data-ttu-id="5a191-120">したがって、基底クラスの仮想メソッドの完全な定義では、このパターンを次に示します。</span><span class="sxs-lookup"><span data-stu-id="5a191-120">Thus a complete definition of a virtual method in a base class follows this pattern:</span></span>

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="5a191-121">派生クラスでこの仮想メソッドのオーバーライドがこのパターンに従います。</span><span class="sxs-lookup"><span data-stu-id="5a191-121">And in a derived class, an override of this virtual method follows this pattern:</span></span>

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

<span data-ttu-id="5a191-122">基本クラスの既定の実装を省略した場合、基本クラスは抽象クラスになります。</span><span class="sxs-lookup"><span data-stu-id="5a191-122">If you omit the default implementation in the base class, the base class becomes an abstract class.</span></span>

<span data-ttu-id="5a191-123">次のコード例は、新しい仮想メソッドの宣言を示しています。`function1`で基底クラスと派生クラスでオーバーライドする方法です。</span><span class="sxs-lookup"><span data-stu-id="5a191-123">The following code example illustrates the declaration of a new virtual method `function1` in a base class and how to override it in a derived class.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]
    
## <a name="constructors-and-inheritance"></a><span data-ttu-id="5a191-124">コンストラクターと継承</span><span class="sxs-lookup"><span data-stu-id="5a191-124">Constructors and Inheritance</span></span>
<span data-ttu-id="5a191-125">派生クラスでは、基本クラスのコンス トラクターを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a191-125">The constructor for the base class must be called in the derived class.</span></span> <span data-ttu-id="5a191-126">基底クラス コンス トラクターの引数、引数のリストに表示、`inherit`句。</span><span class="sxs-lookup"><span data-stu-id="5a191-126">The arguments for the base class constructor appear in the argument list in the `inherit` clause.</span></span> <span data-ttu-id="5a191-127">使用される値は、派生クラスのコンス トラクターに指定された引数から決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a191-127">The values that are used must be determined from the arguments supplied to the derived class constructor.</span></span>

<span data-ttu-id="5a191-128">次のコードは基底クラスと派生クラスでは、継承句で、派生クラスが基底クラス コンス トラクターを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5a191-128">The following code shows a base class and a derived class, where the derived class calls the base class constructor in the inherit clause:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

<span data-ttu-id="5a191-129">複数のコンス トラクターの場合は、次のコードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5a191-129">In the case of multiple constructors, the following code can be used.</span></span> <span data-ttu-id="5a191-130">派生クラスのコンス トラクターの最初の行は、`inherit`句、およびフィールドで宣言されている明示的なフィールドとして表示されます、`val`キーワード。</span><span class="sxs-lookup"><span data-stu-id="5a191-130">The first line of the derived class constructors is the `inherit` clause, and the fields appear as explicit fields that are declared with the `val` keyword.</span></span> <span data-ttu-id="5a191-131">詳細については、次を参照してください。[明示的なフィールド:、`val`キーワード](members/explicit-fields-the-val-keyword.md)です。</span><span class="sxs-lookup"><span data-stu-id="5a191-131">For more information, see [Explicit Fields: The `val` Keyword](members/explicit-fields-the-val-keyword.md).</span></span>

```fsharp
type BaseClass =
    val string1 : string
    new (str) = { string1 = str }
    new () = { string1 = "" }

type DerivedClass =
    inherit BaseClass

    val string2 : string
    new (str1, str2) = { inherit BaseClass(str1); string2 = str2 }
    new (str2) = { inherit BaseClass(); string2 = str2 }

let obj1 = DerivedClass("A", "B")
let obj2 = DerivedClass("A")
```

## <a name="alternatives-to-inheritance"></a><span data-ttu-id="5a191-132">継承に代わる方法</span><span class="sxs-lookup"><span data-stu-id="5a191-132">Alternatives to Inheritance</span></span>
<span data-ttu-id="5a191-133">型の軽微な変更が必要な場合は、継承する代わりにオブジェクト式の使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="5a191-133">In cases where a minor modification of a type is required, consider using an object expression as an alternative to inheritance.</span></span> <span data-ttu-id="5a191-134">次の例では、新しい派生型を作成する代わりにオブジェクト式の使用を示します。</span><span class="sxs-lookup"><span data-stu-id="5a191-134">The following example illustrates the use of an object expression as an alternative to creating a new derived type:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

<span data-ttu-id="5a191-135">オブジェクトの式の詳細については、次を参照してください。[オブジェクト式](object-expressions.md)です。</span><span class="sxs-lookup"><span data-stu-id="5a191-135">For more information about object expressions, see [Object Expressions](object-expressions.md).</span></span>

<span data-ttu-id="5a191-136">オブジェクト階層を作成するときは、継承の代わりに判別共用体の使用を検討します。</span><span class="sxs-lookup"><span data-stu-id="5a191-136">When you are creating object hierarchies, consider using a discriminated union instead of inheritance.</span></span> <span data-ttu-id="5a191-137">判別共用体は、共通の全体的な型を共有する別のオブジェクトのさまざまなモデルの動作でこともできます。</span><span class="sxs-lookup"><span data-stu-id="5a191-137">Discriminated unions can also model varied behavior of different objects that share a common overall type.</span></span> <span data-ttu-id="5a191-138">1 つの判別共用体を多くの場合、不要に互いのわずかな違いは、派生クラスの数。</span><span class="sxs-lookup"><span data-stu-id="5a191-138">A single discriminated union can often eliminate the need for a number of derived classes that are minor variations of each other.</span></span> <span data-ttu-id="5a191-139">判別共用体の詳細については、次を参照してください。[判別共用体](discriminated-unions.md)です。</span><span class="sxs-lookup"><span data-stu-id="5a191-139">For information about discriminated unions, see [Discriminated Unions](discriminated-unions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="5a191-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a191-140">See Also</span></span>
[<span data-ttu-id="5a191-141">オブジェクト式</span><span class="sxs-lookup"><span data-stu-id="5a191-141">Object Expressions</span></span>](object-expressions.md)

[<span data-ttu-id="5a191-142">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="5a191-142">F# Language Reference</span></span>](index.md)

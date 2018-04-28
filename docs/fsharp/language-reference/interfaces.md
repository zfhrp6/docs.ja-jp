---
title: インターフェイス (F#)
description: F# でインターフェイスが他のクラスを実装する関連するメンバーのセットを指定する方法について説明します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: fa299a7e37d4e1e3800a02bf5a77831db9146daf
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="interfaces"></a><span data-ttu-id="93564-103">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="93564-103">Interfaces</span></span>

<span data-ttu-id="93564-104">*インターフェイス*他のクラスを実装する関連するメンバーのセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="93564-104">*Interfaces* specify sets of related members that other classes implement.</span></span>

## <a name="syntax"></a><span data-ttu-id="93564-105">構文</span><span class="sxs-lookup"><span data-stu-id="93564-105">Syntax</span></span>

```fsharp
// Interface declaration:
[ attributes ]
type interface-name =
    [ interface ]     [ inherit base-interface-name ...]
    abstract member1 : [ argument-types1 -> ] return-type1
    abstract member2 : [ argument-types2 -> ] return-type2
    ...
[ end ]

// Implementing, inside a class type definition:
interface interface-name with
    member self-identifier.member1argument-list = method-body1
    member self-identifier.member2argument-list = method-body2

// Implementing, by using an object expression:
[ attributes ]
let class-name (argument-list) =
    { new interface-name with
        member self-identifier.member1argument-list = method-body1
        member self-identifier.member2argument-list = method-body2
        [ base-interface-definitions ]
    }
    member-list
```

## <a name="remarks"></a><span data-ttu-id="93564-106">コメント</span><span class="sxs-lookup"><span data-stu-id="93564-106">Remarks</span></span>
<span data-ttu-id="93564-107">インターフェイスの宣言では、メンバーを実装していないする点を除いて、クラス宣言が似ています。</span><span class="sxs-lookup"><span data-stu-id="93564-107">Interface declarations resemble class declarations except that no members are implemented.</span></span> <span data-ttu-id="93564-108">代わりに、すべてのメンバーが、抽象キーワードによって示される`abstract`です。</span><span class="sxs-lookup"><span data-stu-id="93564-108">Instead, all the members are abstract, as indicated by the keyword `abstract`.</span></span> <span data-ttu-id="93564-109">抽象メソッドのメソッド本体を指定しません。</span><span class="sxs-lookup"><span data-stu-id="93564-109">You do not provide a method body for abstract methods.</span></span> <span data-ttu-id="93564-110">ただしもと共にメソッドとして、メンバーの個別の定義を含めることで、既定の実装を用意することができます、`default`キーワード。</span><span class="sxs-lookup"><span data-stu-id="93564-110">However, you can provide a default implementation by also including a separate definition of the member as a method together with the `default` keyword.</span></span> <span data-ttu-id="93564-111">これは、他の .NET 言語の基本クラスでの仮想メソッドの作成と同じです。</span><span class="sxs-lookup"><span data-stu-id="93564-111">Doing so is equivalent to creating a virtual method in a base class in other .NET languages.</span></span> <span data-ttu-id="93564-112">このような仮想メソッドは、インターフェイスを実装するクラスでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="93564-112">Such a virtual method can be overridden in classes that implement the interface.</span></span>

<span data-ttu-id="93564-113">各メソッドのパラメーターに f# の通常の構文を使用して名前を付けることができます必要に応じて。</span><span class="sxs-lookup"><span data-stu-id="93564-113">You can optionally give each method parameter a name using normal F# syntax:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

<span data-ttu-id="93564-114">上記で`ISprintable`など、`Print`メソッドに型のパラメーターが 1 つ`string`名前を持つ`format`。</span><span class="sxs-lookup"><span data-stu-id="93564-114">In the above `ISprintable` example, the `Print` method has a single parameter of the type `string` with the name `format`.</span></span>

<span data-ttu-id="93564-115">インターフェイスを実装する 2 つの方法: オブジェクト式を使用して、クラスの型を使用します。</span><span class="sxs-lookup"><span data-stu-id="93564-115">There are two ways to implement interfaces: by using object expressions, and by using class types.</span></span> <span data-ttu-id="93564-116">どちらの場合は、クラス型またはオブジェクトの式は、メソッド本体をインターフェイスの抽象メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="93564-116">In either case, the class type or object expression provides method bodies for abstract methods of the interface.</span></span> <span data-ttu-id="93564-117">実装は、インターフェイスを実装する種類ごとに固有です。</span><span class="sxs-lookup"><span data-stu-id="93564-117">Implementations are specific to each type that implements the interface.</span></span> <span data-ttu-id="93564-118">そのため、さまざまな種類のインターフェイス メソッドは、互いに異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="93564-118">Therefore, interface methods on different types might be different from each other.</span></span>

<span data-ttu-id="93564-119">キーワード`interface`と`end`、軽量構文を使用するときに開始し、定義の最後をマークするは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="93564-119">The keywords `interface` and `end`, which mark the start and end of the definition, are optional when you use lightweight syntax.</span></span> <span data-ttu-id="93564-120">これらのキーワードを使用しない場合、コンパイラはかどうかの型がクラスまたはインターフェイスを使用する構成要素を分析して、推定しようとします。</span><span class="sxs-lookup"><span data-stu-id="93564-120">If you do not use these keywords, the compiler attempts to infer whether the type is a class or an interface by analyzing the constructs that you use.</span></span> <span data-ttu-id="93564-121">メンバーを定義または他のクラスの構文を使用する場合は、型がクラスとして解釈されます。</span><span class="sxs-lookup"><span data-stu-id="93564-121">If you define a member or use other class syntax, the type is interpreted as a class.</span></span>

<span data-ttu-id="93564-122">.NET のコーディング スタイルは、大文字のすべてのインターフェイスを開始する`I`です。</span><span class="sxs-lookup"><span data-stu-id="93564-122">The .NET coding style is to begin all interfaces with a capital `I`.</span></span>


## <a name="implementing-interfaces-by-using-class-types"></a><span data-ttu-id="93564-123">クラスの型を使用してインターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="93564-123">Implementing Interfaces by Using Class Types</span></span>
<span data-ttu-id="93564-124">使用して、クラス型の 1 つまたは複数のインターフェイスを実装することができます、`interface`キーワード、インターフェイスの名前と`with`キーワード、インターフェイス メンバーの定義後に、次のコードに示すようにします。</span><span class="sxs-lookup"><span data-stu-id="93564-124">You can implement one or more interfaces in a class type by using the `interface` keyword, the name of the interface, and the `with` keyword, followed by the interface member definitions, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

<span data-ttu-id="93564-125">インターフェイスの実装が継承、ので、すべての派生クラスは、それらを再実装する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="93564-125">Interface implementations are inherited, so any derived classes do not need to reimplement them.</span></span>


## <a name="calling-interface-methods"></a><span data-ttu-id="93564-126">インターフェイス メソッドの呼び出し</span><span class="sxs-lookup"><span data-stu-id="93564-126">Calling Interface Methods</span></span>
<span data-ttu-id="93564-127">インターフェイス メソッドは、インターフェイスを実装する型のオブジェクトではなく、インターフェイスを介してのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="93564-127">Interface methods can be called only through the interface, not through any object of the type that implements the interface.</span></span> <span data-ttu-id="93564-128">したがってを使用して、インターフェイス型にキャストする必要があります、`:>`演算子または`upcast`これらのメソッドを呼び出すために演算子。</span><span class="sxs-lookup"><span data-stu-id="93564-128">Thus, you might have to upcast to the interface type by using the `:>` operator or the `upcast` operator in order to call these methods.</span></span>

<span data-ttu-id="93564-129">型のオブジェクトがあるときに、インターフェイス メソッドを呼び出す`SomeClass`、次のコードに示すようにアップ キャスト オブジェクトをインターフェイス型必要があります。</span><span class="sxs-lookup"><span data-stu-id="93564-129">To call the interface method when you have an object of type `SomeClass`, you must upcast the object to the interface type, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

<span data-ttu-id="93564-130">代わりには、キャスト、オブジェクトでメソッドを宣言する、次の例のように、インターフェイス メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="93564-130">An alternative is to declare a method on the object that upcasts and calls the interface method, as in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]
    
## <a name="implementing-interfaces-by-using-object-expressions"></a><span data-ttu-id="93564-131">オブジェクト式を使用してインターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="93564-131">Implementing Interfaces by Using Object Expressions</span></span>
<span data-ttu-id="93564-132">オブジェクトの式は、短いインターフェイスを実装する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="93564-132">Object expressions provide a short way to implement an interface.</span></span> <span data-ttu-id="93564-133">これらは、名前付きの型を作成する必要はありませんし、メソッドを追加せず、インターフェイス メソッドをサポートするオブジェクトを希望する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="93564-133">They are useful when you do not have to create a named type, and you just want an object that supports the interface methods, without any additional methods.</span></span> <span data-ttu-id="93564-134">オブジェクト式は、次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="93564-134">An object expression is illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]
    
## <a name="interface-inheritance"></a><span data-ttu-id="93564-135">インターフェイスの継承</span><span class="sxs-lookup"><span data-stu-id="93564-135">Interface Inheritance</span></span>
<span data-ttu-id="93564-136">インターフェイスは、1 つまたは複数の基底インターフェイスから継承できます。</span><span class="sxs-lookup"><span data-stu-id="93564-136">Interfaces can inherit from one or more base interfaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]
    
## <a name="see-also"></a><span data-ttu-id="93564-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="93564-137">See Also</span></span>
[<span data-ttu-id="93564-138">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="93564-138">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="93564-139">オブジェクト式</span><span class="sxs-lookup"><span data-stu-id="93564-139">Object Expressions</span></span>](object-expressions.md)

[<span data-ttu-id="93564-140">クラス</span><span class="sxs-lookup"><span data-stu-id="93564-140">Classes</span></span>](classes.md)

---
title: "コンストラクター (F#)"
description: "F# でコンス トラクターを使用して作成し、クラスと構造のオブジェクトを初期化および定義する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e0da2250-29de-4145-a1be-e5faff080759
ms.openlocfilehash: 60ed93f1c1dc15e99465d969c9e4fd3e61c28ffa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="constructors"></a><span data-ttu-id="36917-104">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="36917-104">Constructors</span></span>

<span data-ttu-id="36917-105">このトピックでは、定義して作成し、クラスと構造のオブジェクトを初期化するコンス トラクターを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="36917-105">This topic describes how to define and use constructors to create and initialize class and structure objects.</span></span>


## <a name="construction-of-class-objects"></a><span data-ttu-id="36917-106">クラスのオブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="36917-106">Construction of Class Objects</span></span>
<span data-ttu-id="36917-107">クラス型のオブジェクトでは、コンス トラクターがあります。</span><span class="sxs-lookup"><span data-stu-id="36917-107">Objects of class types have constructors.</span></span> <span data-ttu-id="36917-108">2 つの種類のコンス トラクターがあります。</span><span class="sxs-lookup"><span data-stu-id="36917-108">There are two kinds of constructors.</span></span> <span data-ttu-id="36917-109">パラメーターが括弧で囲まれて、型名の直後に、プライマリ コンス トラクターは 1 つです。</span><span class="sxs-lookup"><span data-stu-id="36917-109">One is the primary constructor, whose parameters appear in parentheses just after the type name.</span></span> <span data-ttu-id="36917-110">使用して、他の省略可能な追加のコンス トラクターを指定する、`new`キーワード。</span><span class="sxs-lookup"><span data-stu-id="36917-110">You specify other, optional additional constructors by using the `new` keyword.</span></span> <span data-ttu-id="36917-111">このような追加のコンス トラクターは、プライマリ コンス トラクターを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="36917-111">Any such additional constructors must call the primary constructor.</span></span>

<span data-ttu-id="36917-112">プライマリ コンス トラクターを含む`let`と`do`クラス定義の先頭にあるバインディング。</span><span class="sxs-lookup"><span data-stu-id="36917-112">The primary constructor contains `let` and `do` bindings that appear at the start of the class definition.</span></span> <span data-ttu-id="36917-113">A`let`バインディング クラスのプライベート フィールドおよびメソッドの宣言、`do`バインディングはコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="36917-113">A `let` binding declares private fields and methods of the class; a `do` binding executes code.</span></span> <span data-ttu-id="36917-114">詳細については`let`クラスのコンス トラクター内のバインディングを参照してください[`let`クラス内のバインディング](let-bindings-in-classes.md)です。</span><span class="sxs-lookup"><span data-stu-id="36917-114">For more information about `let` bindings in class constructors, see [`let` Bindings in Classes](let-bindings-in-classes.md).</span></span> <span data-ttu-id="36917-115">詳細については`do`コンス トラクター内のバインディングを参照してください[`do`クラス内のバインディング](do-bindings-in-classes.md)です。</span><span class="sxs-lookup"><span data-stu-id="36917-115">For more information about `do` bindings in constructors, see [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

<span data-ttu-id="36917-116">使用してオブジェクトを作成するかどうかを呼び出したいコンス トラクターは、プライマリ コンス トラクターまたは追加のコンス トラクターに関係なく、`new`式、または、省略可能なせず`new`キーワード。</span><span class="sxs-lookup"><span data-stu-id="36917-116">Regardless of whether the constructor you want to call is a primary constructor or an additional constructor, you can create objects by using a `new` expression, with or without the optional `new` keyword.</span></span> <span data-ttu-id="36917-117">コンマで区切ってと、かっこで囲まれた名前付き引数と値を使用して、かっこで囲むとコンス トラクターの引数、引数の順序で一覧表示するか、オブジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="36917-117">You initialize your objects together with constructor arguments, either by listing the arguments in order and separated by commas and enclosed in parentheses, or by using named arguments and values in parentheses.</span></span> <span data-ttu-id="36917-118">設定することもプロパティがオブジェクトにオブジェクトの構築時にプロパティ名を使用して、コンス トラクターの引数をという名前を使用すると同様に、値を割り当てる.</span><span class="sxs-lookup"><span data-stu-id="36917-118">You can also set properties on an object during the construction of the object by using the property names and assigning values just as you use named constructor arguments.</span></span>

<span data-ttu-id="36917-119">次のコードでは、クラス コンス トラクターとさまざまなオブジェクトを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="36917-119">The following code illustrates a class that has a constructor and various ways of creating objects.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

<span data-ttu-id="36917-120">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="36917-120">The output is as follows.</span></span>

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a><span data-ttu-id="36917-121">構造体の構築</span><span class="sxs-lookup"><span data-stu-id="36917-121">Construction of Structures</span></span>
<span data-ttu-id="36917-122">構造体では、クラスのすべての規則に従います。</span><span class="sxs-lookup"><span data-stu-id="36917-122">Structures follow all the rules of classes.</span></span> <span data-ttu-id="36917-123">したがって、プライマリ コンス トラクターを持つことができます提供し、追加のコンス トラクターを使用して`new`です。</span><span class="sxs-lookup"><span data-stu-id="36917-123">Therefore, you can have a primary constructor, and you can provide additional constructors by using `new`.</span></span> <span data-ttu-id="36917-124">ただし、構造体とクラスの 1 つの重要な違いがある: プライマリ コンス トラクターが定義されていない場合でも、構造体は既定のコンス トラクター (つまり、引数なしで 1 つ) を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="36917-124">However, there is one important difference between structures and classes: structures can have a default constructor (that is, one with no arguments) even if no primary constructor is defined.</span></span> <span data-ttu-id="36917-125">既定のコンス トラクターでは、すべてのフィールドをゼロまたはそれと同等では通常、その型の既定値を初期化します。</span><span class="sxs-lookup"><span data-stu-id="36917-125">The default constructor initializes all the fields to the default value for that type, usually zero or its equivalent.</span></span> <span data-ttu-id="36917-126">コンス トラクターの構造を定義するには、既定のコンス トラクターと競合しないように、少なくとも 1 つの引数にすることが必要です。</span><span class="sxs-lookup"><span data-stu-id="36917-126">Any constructors that you define for structures must have at least one argument so that they do not conflict with the default constructor.</span></span>

<span data-ttu-id="36917-127">また、構造体で多くの場合を使用して作成されたフィールドがある、`val`キーワード; クラスでは、これらのフィールドを持つこともできます。</span><span class="sxs-lookup"><span data-stu-id="36917-127">Also, structures often have fields that are created by using the `val` keyword; classes can also have these fields.</span></span> <span data-ttu-id="36917-128">構造体とクラスを使用して定義されているフィールドを持つ、`val`キーワード初期化することも追加のコンス トラクターでレコードの式を使用して、次のコードに示すようにします。</span><span class="sxs-lookup"><span data-stu-id="36917-128">Structures and classes that have fields defined by using the `val` keyword can also be initialized in additional constructors by using record expressions, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

<span data-ttu-id="36917-129">詳細については、次を参照してください。[明示的なフィールド:、`val`キーワード](explicit-fields-the-val-keyword.md)です。</span><span class="sxs-lookup"><span data-stu-id="36917-129">For more information, see [Explicit Fields: The `val` Keyword](explicit-fields-the-val-keyword.md).</span></span>


## <a name="executing-side-effects-in-constructors"></a><span data-ttu-id="36917-130">コンス トラクターで実行中の副作用</span><span class="sxs-lookup"><span data-stu-id="36917-130">Executing Side Effects in Constructors</span></span>
<span data-ttu-id="36917-131">クラスで、プライマリ コンス トラクター内のコードを実行できる、`do`バインドします。</span><span class="sxs-lookup"><span data-stu-id="36917-131">A primary constructor in a class can execute code in a `do` binding.</span></span> <span data-ttu-id="36917-132">ただし、ある場合はコードを実行する追加のコンス トラクター、せず、`do`バインドしますか?</span><span class="sxs-lookup"><span data-stu-id="36917-132">However, what if you have to execute code in an additional constructor, without a `do` binding?</span></span> <span data-ttu-id="36917-133">これを行うには、使用する、`then`キーワード。</span><span class="sxs-lookup"><span data-stu-id="36917-133">To do this, you use the `then` keyword.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

<span data-ttu-id="36917-134">プライマリ コンス トラクターの副作用は引き続き実行します。</span><span class="sxs-lookup"><span data-stu-id="36917-134">The side effects of the primary constructor still execute.</span></span> <span data-ttu-id="36917-135">したがって、出力は次に示します。</span><span class="sxs-lookup"><span data-stu-id="36917-135">Therefore, the output is as follows.</span></span>

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a><span data-ttu-id="36917-136">コンス トラクター内の自己識別子</span><span class="sxs-lookup"><span data-stu-id="36917-136">Self Identifiers in Constructors</span></span>
<span data-ttu-id="36917-137">他のメンバーには、各メンバーの定義の現在のオブジェクトの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="36917-137">In other members, you provide a name for the current object in the definition of each member.</span></span> <span data-ttu-id="36917-138">使用して、クラス定義の最初の行で、自己識別子を配置することもできます、`as`キーワードの直後に次のコンス トラクターのパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="36917-138">You can also put the self identifier on the first line of the class definition by using the `as` keyword immediately following the constructor parameters.</span></span> <span data-ttu-id="36917-139">次の例では、この構文を示します。</span><span class="sxs-lookup"><span data-stu-id="36917-139">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

<span data-ttu-id="36917-140">追加のコンス トラクターで定義することも自己識別子を設定することによって、`as`コンス トラクターのパラメーターの直後に句。</span><span class="sxs-lookup"><span data-stu-id="36917-140">In additional constructors, you can also define a self identifier by putting the `as` clause right after the constructor parameters.</span></span> <span data-ttu-id="36917-141">次の例では、この構文を示します。</span><span class="sxs-lookup"><span data-stu-id="36917-141">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

<span data-ttu-id="36917-142">完全に定義する前に、オブジェクトを使用しようとすると、問題が発生することができます。</span><span class="sxs-lookup"><span data-stu-id="36917-142">Problems can occur when you try to use an object before it is fully defined.</span></span> <span data-ttu-id="36917-143">により、自己識別子を使用できますと、コンパイラ警告が生成され、オブジェクトが初期化される前に、オブジェクトのメンバーがアクセスされないようにする追加のチェックを挿入します。</span><span class="sxs-lookup"><span data-stu-id="36917-143">Therefore, uses of the self identifier can cause the compiler to emit a warning and insert additional checks to ensure the members of an object are not accessed before the object is initialized.</span></span> <span data-ttu-id="36917-144">自己識別子のみを使用する必要があります、`do`または後に、プライマリ コンス トラクターのバインド、`then`追加のコンス トラクター内のキーワードです。</span><span class="sxs-lookup"><span data-stu-id="36917-144">You should only use the self identifier in the `do` bindings of the primary constructor, or after the `then` keyword in additional constructors.</span></span>

<span data-ttu-id="36917-145">自己識別子の名前がある`this`です。</span><span class="sxs-lookup"><span data-stu-id="36917-145">The name of the self identifier does not have to be `this`.</span></span> <span data-ttu-id="36917-146">任意の有効な識別子があります。</span><span class="sxs-lookup"><span data-stu-id="36917-146">It can be any valid identifier.</span></span>


## <a name="assigning-values-to-properties-at-initialization"></a><span data-ttu-id="36917-147">プロパティの初期化時に値を割り当てる</span><span class="sxs-lookup"><span data-stu-id="36917-147">Assigning Values to Properties at Initialization</span></span>
<span data-ttu-id="36917-148">形式の代入の一覧を追加することによって初期化コードでクラスのオブジェクトのプロパティに値を割り当てることができます`property = value`コンス トラクターを引数リストにします。</span><span class="sxs-lookup"><span data-stu-id="36917-148">You can assign values to the properties of a class object in the initialization code by appending a list of assignments of the form `property = value` to the argument list for a constructor.</span></span> <span data-ttu-id="36917-149">これを次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="36917-149">This is shown in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="36917-150">上記のコードの次のバージョンは、通常の引数、省略可能な引数、および 1 つのコンス トラクターの呼び出しのプロパティの設定の組み合わせを示しています。</span><span class="sxs-lookup"><span data-stu-id="36917-150">The following version of the previous code illustrates the combination of ordinary arguments, optional arguments, and property settings in one constructor call.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]
    
## <a name="constructors-in-inherited-class"></a><span data-ttu-id="36917-151">継承クラスのコンス トラクター</span><span class="sxs-lookup"><span data-stu-id="36917-151">Constructors in inherited class</span></span>
<span data-ttu-id="36917-152">コンス トラクターを持つ基本クラスから継承する、ときに、継承句でその引数を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="36917-152">When inheriting from a base class that has a constructor, you must specify its arguments in the inherit clause.</span></span> <span data-ttu-id="36917-153">詳細については、次を参照してください。[コンス トラクターと継承](../inheritance.md#constructors-and-inheritance)です。</span><span class="sxs-lookup"><span data-stu-id="36917-153">For more information, see [Constructors and inheritance](../inheritance.md#constructors-and-inheritance).</span></span>

## <a name="static-constructors-or-type-constructors"></a><span data-ttu-id="36917-154">静的コンス トラクターまたは型コンス トラクター</span><span class="sxs-lookup"><span data-stu-id="36917-154">Static Constructors or Type Constructors</span></span>
<span data-ttu-id="36917-155">静的オブジェクトを作成するためのコードを指定するだけでなく`let`と`do`型レベルでの初期化を実行する型が最初に使用される前に実行するクラス型でバインディングを作成できます。</span><span class="sxs-lookup"><span data-stu-id="36917-155">In addition to specifying code for creating objects, static `let` and `do` bindings can be authored in class types that execute before the type is first used to perform initialization at the type level.</span></span> <span data-ttu-id="36917-156">詳細については、次を参照してください。 [ `let`クラス内のバインディング](let-bindings-in-classes.md)と[`do`クラス内のバインディング](do-bindings-in-classes.md)です。</span><span class="sxs-lookup"><span data-stu-id="36917-156">For more information, see [`let` Bindings in Classes](let-bindings-in-classes.md) and [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="36917-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="36917-157">See Also</span></span>
[<span data-ttu-id="36917-158">メンバー</span><span class="sxs-lookup"><span data-stu-id="36917-158">Members</span></span>](index.md)

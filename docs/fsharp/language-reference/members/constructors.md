---
title: コンストラクター (F#)
description: F# でコンス トラクターを使用して作成し、クラスと構造のオブジェクトを初期化および定義する方法を説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 1773c111e0398aa83951afe14979d8a4ebc4907f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564434"
---
# <a name="constructors"></a><span data-ttu-id="79356-103">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="79356-103">Constructors</span></span>

<span data-ttu-id="79356-104">このトピックでは、定義して作成し、クラスと構造のオブジェクトを初期化するコンス トラクターを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="79356-104">This topic describes how to define and use constructors to create and initialize class and structure objects.</span></span>


## <a name="construction-of-class-objects"></a><span data-ttu-id="79356-105">クラスのオブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="79356-105">Construction of Class Objects</span></span>
<span data-ttu-id="79356-106">クラス型のオブジェクトでは、コンス トラクターがあります。</span><span class="sxs-lookup"><span data-stu-id="79356-106">Objects of class types have constructors.</span></span> <span data-ttu-id="79356-107">2 つの種類のコンス トラクターがあります。</span><span class="sxs-lookup"><span data-stu-id="79356-107">There are two kinds of constructors.</span></span> <span data-ttu-id="79356-108">パラメーターが括弧で囲まれて、型名の直後に、プライマリ コンス トラクターは 1 つです。</span><span class="sxs-lookup"><span data-stu-id="79356-108">One is the primary constructor, whose parameters appear in parentheses just after the type name.</span></span> <span data-ttu-id="79356-109">使用して、他の省略可能な追加のコンス トラクターを指定する、`new`キーワード。</span><span class="sxs-lookup"><span data-stu-id="79356-109">You specify other, optional additional constructors by using the `new` keyword.</span></span> <span data-ttu-id="79356-110">このような追加のコンス トラクターは、プライマリ コンス トラクターを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="79356-110">Any such additional constructors must call the primary constructor.</span></span>

<span data-ttu-id="79356-111">プライマリ コンス トラクターを含む`let`と`do`クラス定義の先頭にあるバインディング。</span><span class="sxs-lookup"><span data-stu-id="79356-111">The primary constructor contains `let` and `do` bindings that appear at the start of the class definition.</span></span> <span data-ttu-id="79356-112">A`let`バインディング クラスのプライベート フィールドおよびメソッドの宣言、`do`バインディングはコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="79356-112">A `let` binding declares private fields and methods of the class; a `do` binding executes code.</span></span> <span data-ttu-id="79356-113">詳細については`let`クラスのコンス トラクター内のバインディングを参照してください[`let`クラス内のバインディング](let-bindings-in-classes.md)です。</span><span class="sxs-lookup"><span data-stu-id="79356-113">For more information about `let` bindings in class constructors, see [`let` Bindings in Classes](let-bindings-in-classes.md).</span></span> <span data-ttu-id="79356-114">詳細については`do`コンス トラクター内のバインディングを参照してください[`do`クラス内のバインディング](do-bindings-in-classes.md)です。</span><span class="sxs-lookup"><span data-stu-id="79356-114">For more information about `do` bindings in constructors, see [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

<span data-ttu-id="79356-115">使用してオブジェクトを作成するかどうかを呼び出したいコンス トラクターは、プライマリ コンス トラクターまたは追加のコンス トラクターに関係なく、`new`式、または、省略可能なせず`new`キーワード。</span><span class="sxs-lookup"><span data-stu-id="79356-115">Regardless of whether the constructor you want to call is a primary constructor or an additional constructor, you can create objects by using a `new` expression, with or without the optional `new` keyword.</span></span> <span data-ttu-id="79356-116">コンマで区切ってと、かっこで囲まれた名前付き引数と値を使用して、かっこで囲むとコンス トラクターの引数、引数の順序で一覧表示するか、オブジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="79356-116">You initialize your objects together with constructor arguments, either by listing the arguments in order and separated by commas and enclosed in parentheses, or by using named arguments and values in parentheses.</span></span> <span data-ttu-id="79356-117">設定することもプロパティがオブジェクトにオブジェクトの構築時にプロパティ名を使用して、コンス トラクターの引数をという名前を使用すると同様に、値を割り当てる.</span><span class="sxs-lookup"><span data-stu-id="79356-117">You can also set properties on an object during the construction of the object by using the property names and assigning values just as you use named constructor arguments.</span></span>

<span data-ttu-id="79356-118">次のコードでは、クラス コンス トラクターとさまざまなオブジェクトを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="79356-118">The following code illustrates a class that has a constructor and various ways of creating objects.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

<span data-ttu-id="79356-119">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="79356-119">The output is as follows.</span></span>

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a><span data-ttu-id="79356-120">構造体の構築</span><span class="sxs-lookup"><span data-stu-id="79356-120">Construction of Structures</span></span>
<span data-ttu-id="79356-121">構造体では、クラスのすべての規則に従います。</span><span class="sxs-lookup"><span data-stu-id="79356-121">Structures follow all the rules of classes.</span></span> <span data-ttu-id="79356-122">したがって、プライマリ コンス トラクターを持つことができます提供し、追加のコンス トラクターを使用して`new`です。</span><span class="sxs-lookup"><span data-stu-id="79356-122">Therefore, you can have a primary constructor, and you can provide additional constructors by using `new`.</span></span> <span data-ttu-id="79356-123">ただし、構造体とクラスの 1 つの重要な違いがある: プライマリ コンス トラクターが定義されていない場合でも、構造体は既定のコンス トラクター (つまり、引数なしで 1 つ) を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="79356-123">However, there is one important difference between structures and classes: structures can have a default constructor (that is, one with no arguments) even if no primary constructor is defined.</span></span> <span data-ttu-id="79356-124">既定のコンス トラクターでは、すべてのフィールドをゼロまたはそれと同等では通常、その型の既定値を初期化します。</span><span class="sxs-lookup"><span data-stu-id="79356-124">The default constructor initializes all the fields to the default value for that type, usually zero or its equivalent.</span></span> <span data-ttu-id="79356-125">コンス トラクターの構造を定義するには、既定のコンス トラクターと競合しないように、少なくとも 1 つの引数にすることが必要です。</span><span class="sxs-lookup"><span data-stu-id="79356-125">Any constructors that you define for structures must have at least one argument so that they do not conflict with the default constructor.</span></span>

<span data-ttu-id="79356-126">また、構造体で多くの場合を使用して作成されたフィールドがある、`val`キーワード; クラスでは、これらのフィールドを持つこともできます。</span><span class="sxs-lookup"><span data-stu-id="79356-126">Also, structures often have fields that are created by using the `val` keyword; classes can also have these fields.</span></span> <span data-ttu-id="79356-127">構造体とクラスを使用して定義されているフィールドを持つ、`val`キーワード初期化することも追加のコンス トラクターでレコードの式を使用して、次のコードに示すようにします。</span><span class="sxs-lookup"><span data-stu-id="79356-127">Structures and classes that have fields defined by using the `val` keyword can also be initialized in additional constructors by using record expressions, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

<span data-ttu-id="79356-128">詳細については、次を参照してください。[明示的なフィールド:、`val`キーワード](explicit-fields-the-val-keyword.md)です。</span><span class="sxs-lookup"><span data-stu-id="79356-128">For more information, see [Explicit Fields: The `val` Keyword](explicit-fields-the-val-keyword.md).</span></span>


## <a name="executing-side-effects-in-constructors"></a><span data-ttu-id="79356-129">コンス トラクターで実行中の副作用</span><span class="sxs-lookup"><span data-stu-id="79356-129">Executing Side Effects in Constructors</span></span>
<span data-ttu-id="79356-130">クラスで、プライマリ コンス トラクター内のコードを実行できる、`do`バインドします。</span><span class="sxs-lookup"><span data-stu-id="79356-130">A primary constructor in a class can execute code in a `do` binding.</span></span> <span data-ttu-id="79356-131">ただし、ある場合はコードを実行する追加のコンス トラクター、せず、`do`バインドしますか?</span><span class="sxs-lookup"><span data-stu-id="79356-131">However, what if you have to execute code in an additional constructor, without a `do` binding?</span></span> <span data-ttu-id="79356-132">これを行うには、使用する、`then`キーワード。</span><span class="sxs-lookup"><span data-stu-id="79356-132">To do this, you use the `then` keyword.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

<span data-ttu-id="79356-133">プライマリ コンス トラクターの副作用は引き続き実行します。</span><span class="sxs-lookup"><span data-stu-id="79356-133">The side effects of the primary constructor still execute.</span></span> <span data-ttu-id="79356-134">したがって、出力は次に示します。</span><span class="sxs-lookup"><span data-stu-id="79356-134">Therefore, the output is as follows.</span></span>

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a><span data-ttu-id="79356-135">コンス トラクター内の自己識別子</span><span class="sxs-lookup"><span data-stu-id="79356-135">Self Identifiers in Constructors</span></span>
<span data-ttu-id="79356-136">他のメンバーには、各メンバーの定義の現在のオブジェクトの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="79356-136">In other members, you provide a name for the current object in the definition of each member.</span></span> <span data-ttu-id="79356-137">使用して、クラス定義の最初の行で、自己識別子を配置することもできます、`as`キーワードの直後に次のコンス トラクターのパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="79356-137">You can also put the self identifier on the first line of the class definition by using the `as` keyword immediately following the constructor parameters.</span></span> <span data-ttu-id="79356-138">次の例では、この構文を示します。</span><span class="sxs-lookup"><span data-stu-id="79356-138">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

<span data-ttu-id="79356-139">追加のコンス トラクターで定義することも自己識別子を設定することによって、`as`コンス トラクターのパラメーターの直後に句。</span><span class="sxs-lookup"><span data-stu-id="79356-139">In additional constructors, you can also define a self identifier by putting the `as` clause right after the constructor parameters.</span></span> <span data-ttu-id="79356-140">次の例では、この構文を示します。</span><span class="sxs-lookup"><span data-stu-id="79356-140">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

<span data-ttu-id="79356-141">完全に定義する前に、オブジェクトを使用しようとすると、問題が発生することができます。</span><span class="sxs-lookup"><span data-stu-id="79356-141">Problems can occur when you try to use an object before it is fully defined.</span></span> <span data-ttu-id="79356-142">により、自己識別子を使用できますと、コンパイラ警告が生成され、オブジェクトが初期化される前に、オブジェクトのメンバーがアクセスされないようにする追加のチェックを挿入します。</span><span class="sxs-lookup"><span data-stu-id="79356-142">Therefore, uses of the self identifier can cause the compiler to emit a warning and insert additional checks to ensure the members of an object are not accessed before the object is initialized.</span></span> <span data-ttu-id="79356-143">自己識別子のみを使用する必要があります、`do`または後に、プライマリ コンス トラクターのバインド、`then`追加のコンス トラクター内のキーワードです。</span><span class="sxs-lookup"><span data-stu-id="79356-143">You should only use the self identifier in the `do` bindings of the primary constructor, or after the `then` keyword in additional constructors.</span></span>

<span data-ttu-id="79356-144">自己識別子の名前がある`this`です。</span><span class="sxs-lookup"><span data-stu-id="79356-144">The name of the self identifier does not have to be `this`.</span></span> <span data-ttu-id="79356-145">任意の有効な識別子があります。</span><span class="sxs-lookup"><span data-stu-id="79356-145">It can be any valid identifier.</span></span>


## <a name="assigning-values-to-properties-at-initialization"></a><span data-ttu-id="79356-146">プロパティの初期化時に値を割り当てる</span><span class="sxs-lookup"><span data-stu-id="79356-146">Assigning Values to Properties at Initialization</span></span>
<span data-ttu-id="79356-147">形式の代入の一覧を追加することによって初期化コードでクラスのオブジェクトのプロパティに値を割り当てることができます`property = value`コンス トラクターを引数リストにします。</span><span class="sxs-lookup"><span data-stu-id="79356-147">You can assign values to the properties of a class object in the initialization code by appending a list of assignments of the form `property = value` to the argument list for a constructor.</span></span> <span data-ttu-id="79356-148">これを次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="79356-148">This is shown in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="79356-149">上記のコードの次のバージョンは、通常の引数、省略可能な引数、および 1 つのコンス トラクターの呼び出しのプロパティの設定の組み合わせを示しています。</span><span class="sxs-lookup"><span data-stu-id="79356-149">The following version of the previous code illustrates the combination of ordinary arguments, optional arguments, and property settings in one constructor call.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]
    
## <a name="constructors-in-inherited-class"></a><span data-ttu-id="79356-150">継承クラスのコンス トラクター</span><span class="sxs-lookup"><span data-stu-id="79356-150">Constructors in inherited class</span></span>
<span data-ttu-id="79356-151">コンス トラクターを持つ基本クラスから継承する、ときに、継承句でその引数を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="79356-151">When inheriting from a base class that has a constructor, you must specify its arguments in the inherit clause.</span></span> <span data-ttu-id="79356-152">詳細については、次を参照してください。[コンス トラクターと継承](../inheritance.md#constructors-and-inheritance)です。</span><span class="sxs-lookup"><span data-stu-id="79356-152">For more information, see [Constructors and inheritance](../inheritance.md#constructors-and-inheritance).</span></span>

## <a name="static-constructors-or-type-constructors"></a><span data-ttu-id="79356-153">静的コンス トラクターまたは型コンス トラクター</span><span class="sxs-lookup"><span data-stu-id="79356-153">Static Constructors or Type Constructors</span></span>
<span data-ttu-id="79356-154">静的オブジェクトを作成するためのコードを指定するだけでなく`let`と`do`型レベルでの初期化を実行する型が最初に使用される前に実行するクラス型でバインディングを作成できます。</span><span class="sxs-lookup"><span data-stu-id="79356-154">In addition to specifying code for creating objects, static `let` and `do` bindings can be authored in class types that execute before the type is first used to perform initialization at the type level.</span></span> <span data-ttu-id="79356-155">詳細については、次を参照してください。 [ `let`クラス内のバインディング](let-bindings-in-classes.md)と[`do`クラス内のバインディング](do-bindings-in-classes.md)です。</span><span class="sxs-lookup"><span data-stu-id="79356-155">For more information, see [`let` Bindings in Classes](let-bindings-in-classes.md) and [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="79356-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="79356-156">See Also</span></span>
[<span data-ttu-id="79356-157">メンバー</span><span class="sxs-lookup"><span data-stu-id="79356-157">Members</span></span>](index.md)

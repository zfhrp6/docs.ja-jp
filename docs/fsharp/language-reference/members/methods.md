---
title: "メソッド (F#)"
description: "F# メソッドは公開し、オブジェクトと型の動作と機能の実装に使用される型に関連付けられている関数、方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1febab3b-c922-49c6-889f-c22db107710c
ms.openlocfilehash: dae31abe6bb0773671b889646c9cceb410a492cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="methods"></a><span data-ttu-id="a7d0b-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="a7d0b-104">Methods</span></span>

<span data-ttu-id="a7d0b-105">A*メソッド*型に関連付けられている関数です。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-105">A *method* is a function that is associated with a type.</span></span> <span data-ttu-id="a7d0b-106">オブジェクト指向プログラミングで公開し、オブジェクトと型の動作と機能を実装するメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-106">In object-oriented programming, methods are used to expose and implement the functionality and behavior of objects and types.</span></span>


## <a name="syntax"></a><span data-ttu-id="a7d0b-107">構文</span><span class="sxs-lookup"><span data-stu-id="a7d0b-107">Syntax</span></span>

```fsharp
// Instance method definition.
[ attributes ]
member [inline] self-identifier.method-nameparameter-list [ : return-type ]=
    method-body

// Static method definition.
[ attributes ]
static member [inline] method-nameparameter-list [ : return-type ]=
    method-body

// Abstract method declaration or virtual dispatch slot.
[ attributes ]
abstract member self-identifier.method-name : type-signature

// Virtual method declaration and default implementation.
[ attributes ]
abstract member [inline] self-identifier.method-name : type-signature
[ attributes ]
default member [inline] self-identifier.method-nameparameter-list[ : return-type ] =
    method-body

// Override of inherited virtual method.
[ attributes ]
override member [inline] self-identifier.method-nameparameter-list [ : return-type ]=
    method-body

// Optional and DefaultParameterValue attributes on input parameters
[ attributes ]
[ modifier ] member [inline] self-identifier.method-name ([<Optional; DefaultParameterValue([ default-value ])>] input) [ : return-type ]
```

## <a name="remarks"></a><span data-ttu-id="a7d0b-108">コメント</span><span class="sxs-lookup"><span data-stu-id="a7d0b-108">Remarks</span></span>
<span data-ttu-id="a7d0b-109">前の構文では、メソッドの宣言と定義のさまざまなフォームを表示できます。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-109">In the previous syntax, you can see the various forms of method declarations and definitions.</span></span> <span data-ttu-id="a7d0b-110">長いメソッド本体では、改行されるように、等号 (=) と、メソッド本体の全体がインデントされます。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-110">In longer method bodies, a line break follows the equal sign (=), and the whole method body is indented.</span></span>

<span data-ttu-id="a7d0b-111">属性は、メソッド宣言に適用できます。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-111">Attributes can be applied to any method declaration.</span></span> <span data-ttu-id="a7d0b-112">メソッド定義の構文の前に、通常別々 の行に一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-112">They precede the syntax for a method definition and are usually listed on a separate line.</span></span> <span data-ttu-id="a7d0b-113">詳細については、「[属性](../attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-113">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="a7d0b-114">メソッドをマークする`inline`です。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-114">Methods can be marked `inline`.</span></span> <span data-ttu-id="a7d0b-115">`inline` の詳細については、「[Inline Functions](../functions/inline-functions.md)」(インライン関数) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-115">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

<span data-ttu-id="a7d0b-116">非インライン メソッドは、型内で再帰的に使用できます。明示的に使用する必要はありません、`rec`キーワード。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-116">Non-inline methods can be used recursively within the type; there is no need to explicitly use the `rec` keyword.</span></span>


## <a name="instance-methods"></a><span data-ttu-id="a7d0b-117">インスタンス メソッド</span><span class="sxs-lookup"><span data-stu-id="a7d0b-117">Instance Methods</span></span>
<span data-ttu-id="a7d0b-118">インスタンス メソッドを宣言すると、`member`キーワードと*自己識別子*、その後にピリオド (.) とメソッド名とパラメーター。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-118">Instance methods are declared with the `member` keyword and a *self-identifier*, followed by a period (.) and the method name and parameters.</span></span> <span data-ttu-id="a7d0b-119">場合と同様`let`、バインド、*パラメーター リスト*パターンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-119">As is the case for `let` bindings, the *parameter-list* can be a pattern.</span></span> <span data-ttu-id="a7d0b-120">通常、他の .NET Framework 言語で作成されるときに、f# で方法は、組の形式でのかっこ内のパラメーターの表示方法を囲みます。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-120">Typically, you enclose method parameters in parentheses in a tuple form, which is the way methods appear in F# when they are created in other .NET Framework languages.</span></span> <span data-ttu-id="a7d0b-121">ただし、カリー化されたフォーム (パラメーターはスペースで区切られた) は一般的でも、その他のパターンもサポートされます。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-121">However, the curried form (parameters separated by spaces) is also common, and other patterns are supported also.</span></span>

<span data-ttu-id="a7d0b-122">次の例は、定義とインスタンスの非抽象メソッドの使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-122">The following example illustrates the definition and use of a non-abstract instance method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

<span data-ttu-id="a7d0b-123">インスタンス メソッド内で使用すると、バインディングを使用して定義されているフィールドにアクセスする、自己識別子を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-123">Within instance methods, do not use the self identifier to access fields defined by using let bindings.</span></span> <span data-ttu-id="a7d0b-124">その他のメンバーとプロパティにアクセスするときに、自己識別子を使用します。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-124">Use the self identifier when accessing other members and properties.</span></span>


## <a name="static-methods"></a><span data-ttu-id="a7d0b-125">静的メソッド</span><span class="sxs-lookup"><span data-stu-id="a7d0b-125">Static Methods</span></span>
<span data-ttu-id="a7d0b-126">キーワード`static`なしインスタンス メソッドで呼び出されることを指定するために使用して、オブジェクトのインスタンスに関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-126">The keyword `static` is used to specify that a method can be called without an instance and is not associated with an object instance.</span></span> <span data-ttu-id="a7d0b-127">それ以外の場合、メソッドは、インスタンス メソッドです。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-127">Otherwise, methods are instance methods.</span></span>

<span data-ttu-id="a7d0b-128">次のセクションの例で宣言したフィールドを示しています、`let`キーワードで宣言されたプロパティのメンバー、`member`キーワード、および静的メソッドで宣言された、`static`キーワード。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-128">The example in the next section shows fields declared with the `let` keyword, property members declared with the `member` keyword, and a static method declared with the `static` keyword.</span></span>

<span data-ttu-id="a7d0b-129">次の例では、定義と静的メソッドの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-129">The following example illustrates the definition and use of static methods.</span></span> <span data-ttu-id="a7d0b-130">これらのメソッドの定義であると仮定、`SomeType`前のセクション内のクラスです。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-130">Assume that these method definitions are in the `SomeType` class in the previous section.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a><span data-ttu-id="a7d0b-131">抽象メソッドと仮想メソッド</span><span class="sxs-lookup"><span data-stu-id="a7d0b-131">Abstract and Virtual Methods</span></span>
<span data-ttu-id="a7d0b-132">キーワード`abstract`メソッドが仮想ディスパッチ スロットを持つクラスの定義がないことを示します。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-132">The keyword `abstract` indicates that a method has a virtual dispatch slot and might not have a definition in the class.</span></span> <span data-ttu-id="a7d0b-133">A*仮想ディスパッチ スロット*はオブジェクト指向の種類での仮想関数を検索する実行時に使用される関数の内部で維持されるテーブルのエントリの呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-133">A *virtual dispatch slot* is an entry in an internally maintained table of functions that is used at run time to look up virtual function calls in an object-oriented type.</span></span> <span data-ttu-id="a7d0b-134">この仮想ディスパッチ メカニズムを実装するメカニズム*ポリモーフィズム*、オブジェクト指向プログラミングの重要な機能です。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-134">The virtual dispatch mechanism is the mechanism that implements *polymorphism*, an important feature of object-oriented programming.</span></span> <span data-ttu-id="a7d0b-135">定義のない 1 つ以上の抽象メソッドを持つクラスは、*抽象クラス*、つまり、そのクラスのインスタンスを作成できないことができます。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-135">A class that has at least one abstract method without a definition is an *abstract class*, which means that no instances can be created of that class.</span></span> <span data-ttu-id="a7d0b-136">抽象クラスの詳細については、次を参照してください。[抽象クラス](../abstract-classes.md)です。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-136">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

<span data-ttu-id="a7d0b-137">抽象メソッドの宣言は、メソッド本体を含めないでください。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-137">Abstract method declarations do not include a method body.</span></span> <span data-ttu-id="a7d0b-138">代わりに、メソッドの名前は後にコロン (:) と、メソッドの型のシグネチャ。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-138">Instead, the name of the method is followed by a colon (:) and a type signature for the method.</span></span> <span data-ttu-id="a7d0b-139">メソッドの型署名は、一時停止する、マウス ポインター、Visual Studio コード エディターで、メソッド名の上を除くパラメーターの名前のないときに、IntelliSense によって表示と同じです。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-139">The type signature of a method is the same as that shown by IntelliSense when you pause the mouse pointer over a method name in the Visual Studio Code Editor, except without parameter names.</span></span> <span data-ttu-id="a7d0b-140">型のシグネチャは、対話形式で作業している場合に、インタープリター fsi.exe によって表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-140">Type signatures are also displayed by the interpreter, fsi.exe, when you are working interactively.</span></span> <span data-ttu-id="a7d0b-141">メソッドの型署名は、戻り値の型の適切な区切り記号の後に、パラメーターの型を一覧することにより形成されます。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-141">The type signature of a method is formed by listing out the types of the parameters, followed by the return type, with appropriate separator symbols.</span></span> <span data-ttu-id="a7d0b-142">カリー化されたパラメーターを指定する`->`組パラメーターを指定して`*`です。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-142">Curried parameters are separated by `->` and tuple parameters are separated by `*`.</span></span> <span data-ttu-id="a7d0b-143">戻り値は、引数から分離常に、`->`シンボル。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-143">The return value is always separated from the arguments by a `->` symbol.</span></span> <span data-ttu-id="a7d0b-144">関数の型が、パラメーターの場合など、複雑なパラメーターをグループ化するかを示す 2 つのパラメーターではなく、単一のパラメーターとしてに組を処理するときに、かっこを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-144">Parentheses can be used to group complex parameters, such as when a function type is a parameter, or to indicate when a tuple is treated as a single parameter rather than as two parameters.</span></span>

<span data-ttu-id="a7d0b-145">付けることも抽象メソッド default 定義をクラスに定義を追加し、使用して、`default`キーワード、構文のブロックをこのトピックで示すようにします。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-145">You can also give abstract methods default definitions by adding the definition to the class and using the `default` keyword, as shown in the syntax block in this topic.</span></span> <span data-ttu-id="a7d0b-146">同じクラスの定義を持つ抽象メソッドは、他の .NET Framework 言語で、仮想メソッドと同じです。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-146">An abstract method that has a definition in the same class is equivalent to a virtual method in other .NET Framework languages.</span></span> <span data-ttu-id="a7d0b-147">定義が存在するかどうか、`abstract`キーワードがクラスの仮想関数テーブルに新しいディスパッチ スロットを作成します。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-147">Whether or not a definition exists, the `abstract` keyword creates a new dispatch slot in the virtual function table for the class.</span></span>

<span data-ttu-id="a7d0b-148">かどうかを基本クラスでは、その抽象メソッドを実装に関係なく、派生クラスは抽象メソッドの実装を提供できます。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-148">Regardless of whether a base class implements its abstract methods, derived classes can provide implementations of abstract methods.</span></span> <span data-ttu-id="a7d0b-149">派生クラスで抽象メソッドを実装するを使用する以外、派生クラスで、同じ名前およびシグネチャを持つメソッドを定義、`override`または`default`キーワード、メソッド本体を指定します。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-149">To implement an abstract method in a derived class, define a method that has the same name and signature in the derived class, except use the `override` or `default` keyword, and provide the method body.</span></span> <span data-ttu-id="a7d0b-150">キーワード`override`と`default`まったく同じことを意味します。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-150">The keywords `override` and `default` mean exactly the same thing.</span></span> <span data-ttu-id="a7d0b-151">使用して`override`新しいメソッドが、基本クラス実装をオーバーライドする場合を使用して`default`元の抽象宣言と同じクラスの実装を作成するとします。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-151">Use `override` if the new method overrides a base class implementation; use `default` when you create an implementation in the same class as the original abstract declaration.</span></span> <span data-ttu-id="a7d0b-152">使用しないで、`abstract`抽象基本クラスで宣言されたメソッドを実装するメソッドではキーワードです。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-152">Do not use the `abstract` keyword on the method that implements the method that was declared abstract in the base class.</span></span>

<span data-ttu-id="a7d0b-153">次の例は、抽象メソッドを示しています。`Rotate`を持つ既定の実装では、.NET Framework の仮想メソッドに相当します。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-153">The following example illustrates an abstract method `Rotate` that has a default implementation, the equivalent of a .NET Framework virtual method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

<span data-ttu-id="a7d0b-154">次の例では、基底クラス メソッドをオーバーライドする派生クラスを示します。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-154">The following example illustrates a derived class that overrides a base class method.</span></span> <span data-ttu-id="a7d0b-155">この場合、オーバーライドでは、何も実行されるように動作が変わります。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-155">In this case, the override changes the behavior so that the method does nothing.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a><span data-ttu-id="a7d0b-156">オーバーロードされたメソッド</span><span class="sxs-lookup"><span data-stu-id="a7d0b-156">Overloaded Methods</span></span>
<span data-ttu-id="a7d0b-157">オーバー ロードされたメソッドは、メソッドと同じ名前で、指定された型が異なる引数を持つことです。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-157">Overloaded methods are methods that have identical names in a given type but that have different arguments.</span></span> <span data-ttu-id="a7d0b-158">F# で省略可能な引数は通常、オーバー ロードされたメソッドの代わりに使用します。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-158">In F#, optional arguments are usually used instead of overloaded methods.</span></span> <span data-ttu-id="a7d0b-159">ただし、オーバー ロードされたメソッドは、する引数はタプル形式、いないカリー化されたフォームが言語で許可されます。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-159">However, overloaded methods are permitted in the language, provided that the arguments are in tuple form, not curried form.</span></span>

## <a name="optional-arguments"></a><span data-ttu-id="a7d0b-160">省略可能な引数</span><span class="sxs-lookup"><span data-stu-id="a7d0b-160">Optional Arguments</span></span>

<span data-ttu-id="a7d0b-161">4.1 以降では f#、メソッドでパラメーターの既定値と省略可能な引数もができます。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-161">Starting with F# 4.1, you can also have optional arguments with a default parameter value in methods.</span></span>  <span data-ttu-id="a7d0b-162">これは、c# コードとの相互運用を容易にするためです。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-162">This is to help facilitate interoperation with C# code.</span></span>  <span data-ttu-id="a7d0b-163">次の例では、構文を示しています。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-163">The following example demonstrates the syntax:</span></span>

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

<span data-ttu-id="a7d0b-164">渡された値を`DefaultParameterValue`入力の型が一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-164">Note that the value passed in for `DefaultParameterValue` must match the input type.</span></span>  <span data-ttu-id="a7d0b-165">上記のサンプルでは、`int`です。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-165">In the above sample, it is an `int`.</span></span>  <span data-ttu-id="a7d0b-166">整数以外の値を渡そうと`DefaultParameterValue`コンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-166">Attempting to pass a non-integer value into `DefaultParameterValue` would result in a compile error.</span></span>

## <a name="example-properties-and-methods"></a><span data-ttu-id="a7d0b-167">例: プロパティとメソッド</span><span class="sxs-lookup"><span data-stu-id="a7d0b-167">Example: Properties and Methods</span></span>
<span data-ttu-id="a7d0b-168">次の例には、フィールド、プライベート関数、プロパティ、および静的メソッドの例を含む型が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a7d0b-168">The following example contains a type that has examples of fields, private functions, properties, and a static method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a><span data-ttu-id="a7d0b-169">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7d0b-169">See Also</span></span>
[<span data-ttu-id="a7d0b-170">メンバー</span><span class="sxs-lookup"><span data-stu-id="a7d0b-170">Members</span></span>](index.md)

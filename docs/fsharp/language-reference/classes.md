---
title: クラス (F#)
description: F# クラスのプロパティ、メソッド、およびイベントを持つことができるオブジェクトを表す型の方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 67164bd9f91c14f465bf05630259ad70cb8d90e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565887"
---
# <a name="classes"></a><span data-ttu-id="71e2f-103">クラス</span><span class="sxs-lookup"><span data-stu-id="71e2f-103">Classes</span></span>

<span data-ttu-id="71e2f-104">*クラス*プロパティ、メソッド、およびイベントを持つことができるオブジェクトを表す型。</span><span class="sxs-lookup"><span data-stu-id="71e2f-104">*Classes* are types that represent objects that can have properties, methods, and events.</span></span>


## <a name="syntax"></a><span data-ttu-id="71e2f-105">構文</span><span class="sxs-lookup"><span data-stu-id="71e2f-105">Syntax</span></span>

```fsharp
// Class definition:
type [access-modifier] type-name [type-params] [access-modifier] ( parameter-list ) [ as identifier ] =
[ class ]
[ inherit base-type-name(base-constructor-args) ]
[ let-bindings ]
[ do-bindings ]
member-list
...
[ end ]
// Mutually recursive class definitions:
type [access-modifier] type-name1 ...
and [access-modifier] type-name2 ...
...
```

## <a name="remarks"></a><span data-ttu-id="71e2f-106">コメント</span><span class="sxs-lookup"><span data-stu-id="71e2f-106">Remarks</span></span>
<span data-ttu-id="71e2f-107">クラスは、.NET オブジェクト型以外の基本的な記述を表します。クラスは、f# のオブジェクト指向プログラミングをサポートする主な型の概念です。</span><span class="sxs-lookup"><span data-stu-id="71e2f-107">Classes represent the fundamental description of .NET object types; the class is the primary type concept that supports object-oriented programming in F#.</span></span>

<span data-ttu-id="71e2f-108">上記の構文では、`type-name`任意の有効な識別子です。</span><span class="sxs-lookup"><span data-stu-id="71e2f-108">In the preceding syntax, the `type-name` is any valid identifier.</span></span> <span data-ttu-id="71e2f-109">`type-params`省略可能なジェネリック型パラメーターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="71e2f-109">The `type-params` describes optional generic type parameters.</span></span> <span data-ttu-id="71e2f-110">型パラメーター名と山かっこで囲まれた制約で構成されます (`<`と`>`)。</span><span class="sxs-lookup"><span data-stu-id="71e2f-110">It consists of type parameter names and constraints enclosed in angle brackets (`<` and `>`).</span></span> <span data-ttu-id="71e2f-111">詳細については、次を参照してください。[ジェネリック](generics/index.md)と[制約](generics/constraints.md)です。</span><span class="sxs-lookup"><span data-stu-id="71e2f-111">For more information, see [Generics](generics/index.md) and [Constraints](generics/constraints.md).</span></span> <span data-ttu-id="71e2f-112">`parameter-list`コンス トラクターのパラメーターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="71e2f-112">The `parameter-list` describes constructor parameters.</span></span> <span data-ttu-id="71e2f-113">型に関連する最初のアクセス修飾子2 つ目は、プライマリ コンス トラクターに関連します。</span><span class="sxs-lookup"><span data-stu-id="71e2f-113">The first access modifier pertains to the type; the second pertains to the primary constructor.</span></span> <span data-ttu-id="71e2f-114">どちらの場合、既定値を`public`です。</span><span class="sxs-lookup"><span data-stu-id="71e2f-114">In both cases, the default is `public`.</span></span>

<span data-ttu-id="71e2f-115">クラスの基底クラスを使用して指定する、`inherit`キーワード。</span><span class="sxs-lookup"><span data-stu-id="71e2f-115">You specify the base class for a class by using the `inherit` keyword.</span></span> <span data-ttu-id="71e2f-116">基本クラスのコンス トラクターをかっこでの引数を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="71e2f-116">You must supply arguments, in parentheses, for the base class constructor.</span></span>

<span data-ttu-id="71e2f-117">フィールドを宣言するか、関数値を使用して、クラスに対してローカルな`let`バインディング、およびするが、一般的な規則に従う必要があります`let`バインドします。</span><span class="sxs-lookup"><span data-stu-id="71e2f-117">You declare fields or function values that are local to the class by using `let` bindings, and you must follow the general rules for `let` bindings.</span></span> <span data-ttu-id="71e2f-118">`do-bindings`セクションには、オブジェクトの構築時に実行されるコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="71e2f-118">The `do-bindings` section includes code to be executed upon object construction.</span></span>

<span data-ttu-id="71e2f-119">`member-list`追加のコンス トラクター、インスタンスと静的メソッドの宣言、インターフェイスの宣言で抽象バインディング、およびプロパティとイベントの宣言で構成されます。</span><span class="sxs-lookup"><span data-stu-id="71e2f-119">The `member-list` consists of additional constructors, instance and static method declarations, interface declarations, abstract bindings, and property and event declarations.</span></span> <span data-ttu-id="71e2f-120">これらは「[メンバー](members/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="71e2f-120">These are described in [Members](members/index.md).</span></span>

<span data-ttu-id="71e2f-121">`identifier`オプションと共に使用される`as`キーワードは、インスタンス変数、または型のインスタンスを参照する種類の定義で使用できる、自己識別子に名前を提供します。</span><span class="sxs-lookup"><span data-stu-id="71e2f-121">The `identifier` that is used with the optional `as` keyword gives a name to the instance variable, or self identifier, which can be used in the type definition to refer to the instance of the type.</span></span> <span data-ttu-id="71e2f-122">詳細については、このトピックで後述する「自己識別子を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71e2f-122">For more information, see the section Self Identifiers later in this topic.</span></span>

<span data-ttu-id="71e2f-123">キーワード`class`と`end`開始をマークして、定義の最後は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="71e2f-123">The keywords `class` and `end` that mark the start and end of the definition are optional.</span></span>

<span data-ttu-id="71e2f-124">と共に、相互に参照型である再帰型が相互に参加している、`and`キーワードと同じように、再帰関数は、同時に指定します。</span><span class="sxs-lookup"><span data-stu-id="71e2f-124">Mutually recursive types, which are types that reference each other, are joined together with the `and` keyword just as mutually recursive functions are.</span></span> <span data-ttu-id="71e2f-125">例については、「相互再帰型」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71e2f-125">For an example, see the section Mutually Recursive Types.</span></span>


## <a name="constructors"></a><span data-ttu-id="71e2f-126">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="71e2f-126">Constructors</span></span>
<span data-ttu-id="71e2f-127">コンス トラクターは、クラス型のインスタンスを作成するコードです。</span><span class="sxs-lookup"><span data-stu-id="71e2f-127">The constructor is code that creates an instance of the class type.</span></span> <span data-ttu-id="71e2f-128">クラスのコンス トラクターは、他の .NET 言語では f# の少し異なる方法で機能します。</span><span class="sxs-lookup"><span data-stu-id="71e2f-128">Constructors for classes work somewhat differently in F# than they do in other .NET languages.</span></span> <span data-ttu-id="71e2f-129">F# クラスでは常にプライマリ コンス トラクターの引数に記載されて、 `parameter-list` 、型名、および本体を持つから成るに依存している、 `let` (および`let rec`) と、クラス宣言の開始時にバインディング`do`に従ってバインドします。</span><span class="sxs-lookup"><span data-stu-id="71e2f-129">In an F# class, there is always a primary constructor whose arguments are described in the `parameter-list` that follows the type name, and whose body consists of the `let` (and `let rec`) bindings at the start of the class declaration and the `do` bindings that follow.</span></span> <span data-ttu-id="71e2f-130">プライマリ コンス トラクターの引数は、クラス宣言全体のスコープ内です。</span><span class="sxs-lookup"><span data-stu-id="71e2f-130">The arguments of the primary constructor are in scope throughout the class declaration.</span></span>

<span data-ttu-id="71e2f-131">使用して追加のコンス トラクターを追加することができます、`new`キーワードを次のように、メンバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="71e2f-131">You can add additional constructors by using the `new` keyword to add a member, as follows:</span></span>

<span data-ttu-id="71e2f-132">`new`(`argument-list`) = `constructor-body`</span><span class="sxs-lookup"><span data-stu-id="71e2f-132">`new`(`argument-list`) = `constructor-body`</span></span>

<span data-ttu-id="71e2f-133">新しいコンス トラクターの本体は、クラス宣言の上部にある指定されたプライマリ コンス トラクターを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="71e2f-133">The body of the new constructor must invoke the primary constructor that is specified at the top of the class declaration.</span></span>

<span data-ttu-id="71e2f-134">次の例では、この概念を示します。</span><span class="sxs-lookup"><span data-stu-id="71e2f-134">The following example illustrates this concept.</span></span> <span data-ttu-id="71e2f-135">次のコードに`MyClass`2 つのコンス トラクターを持つ、2 つの引数と別のコンス トラクターを受け取り、プライマリ コンス トラクターは引数を受け取りません。</span><span class="sxs-lookup"><span data-stu-id="71e2f-135">In the following code, `MyClass` has two constructors, a primary constructor that takes two arguments and another constructor that takes no arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2401.fs)]
    
## <a name="let-and-do-bindings"></a><span data-ttu-id="71e2f-136">let および do 束縛</span><span class="sxs-lookup"><span data-stu-id="71e2f-136">let and do Bindings</span></span>

<span data-ttu-id="71e2f-137">`let`と`do`クラス定義内のバインディングが、主要なクラスのコンス トラクターの本体を構成および実行するクラスのインスタンスが作成されるたびにします。</span><span class="sxs-lookup"><span data-stu-id="71e2f-137">The `let` and `do` bindings in a class definition form the body of the primary class constructor, and therefore they run whenever a class instance is created.</span></span> <span data-ttu-id="71e2f-138">場合、`let`バインディングは、関数、メンバーにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="71e2f-138">If a `let` binding is a function, then it is compiled into a member.</span></span> <span data-ttu-id="71e2f-139">場合、`let`バインド関数またはメンバーで使用されていない値は、そのコンス トラクターへのローカル変数にコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="71e2f-139">If the `let` binding is a value that is not used in any function or member, then it is compiled into a variable that is local to the constructor.</span></span> <span data-ttu-id="71e2f-140">それ以外の場合、クラスのフィールドにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="71e2f-140">Otherwise, it is compiled into a field of the class.</span></span> <span data-ttu-id="71e2f-141">`do`後に続く式は、プライマリ コンス トラクターにコンパイルされ、すべてのインスタンスの初期化コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="71e2f-141">The `do` expressions that follow are compiled into the primary constructor and execute initialization code for every instance.</span></span> <span data-ttu-id="71e2f-142">追加のコンス トラクターが常に、プライマリ コンス トラクターを呼び出すので、`let`バインドと`do`バインドが常にコンス トラクターの呼び出しに関係なくを実行します。</span><span class="sxs-lookup"><span data-stu-id="71e2f-142">Because any additional constructors always call the primary constructor, the `let` bindings and `do` bindings always execute regardless of which constructor is called.</span></span>

<span data-ttu-id="71e2f-143">によって作成されたフィールド`let`バインディング メソッドとクラスのプロパティを通じてアクセスできます。 ただし、それらにアクセスできません、静的メソッドから静的メソッドは、パラメーターとしてインスタンス変数を受け取る場合でもです。</span><span class="sxs-lookup"><span data-stu-id="71e2f-143">Fields that are created by `let` bindings can be accessed throughout the methods and properties of the class; however, they cannot be accessed from static methods, even if the static methods take an instance variable as a parameter.</span></span> <span data-ttu-id="71e2f-144">1 つが存在する場合、自己識別子を使用して、アクセスできません。</span><span class="sxs-lookup"><span data-stu-id="71e2f-144">They cannot be accessed by using the self identifier, if one exists.</span></span>


## <a name="self-identifiers"></a><span data-ttu-id="71e2f-145">自己識別子</span><span class="sxs-lookup"><span data-stu-id="71e2f-145">Self Identifiers</span></span>

<span data-ttu-id="71e2f-146">A*自己識別子*を現在のインスタンスを表す名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="71e2f-146">A *self identifier* is a name that represents the current instance.</span></span> <span data-ttu-id="71e2f-147">自己識別子のように、 `this` c# または C++ のキーワードまたは`Me`Visual Basic でします。</span><span class="sxs-lookup"><span data-stu-id="71e2f-147">Self identifiers resemble the `this` keyword in C# or C++ or `Me` in Visual Basic.</span></span> <span data-ttu-id="71e2f-148">自己識別子定義については、クラス全体または個々 のメソッドのためだけのスコープ内にあるかどうかに応じて、2 つの方法では、自己識別子を定義できます。</span><span class="sxs-lookup"><span data-stu-id="71e2f-148">You can define a self identifier in two different ways, depending on whether you want the self identifier to be in scope for the whole class definition or just for an individual method.</span></span>

<span data-ttu-id="71e2f-149">クラス全体の個人識別子を定義するのには、使用、`as`キーワードのコンス トラクターのパラメーターの右かっこの後に一覧表示、および識別子の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="71e2f-149">To define a self identifier for the whole class, use the `as` keyword after the closing parentheses of the constructor parameter list, and specify the identifier name.</span></span>

<span data-ttu-id="71e2f-150">自己識別子に対して 1 つのメソッドを定義するのには、宣言では、メンバー、メソッド名と区切り記号としてピリオド (.) の前に、自己識別子を提供します。</span><span class="sxs-lookup"><span data-stu-id="71e2f-150">To define a self identifier for just one method, provide the self identifier in the member declaration, just before the method name and a period (.) as a separator.</span></span>

<span data-ttu-id="71e2f-151">次のコード例は、自己識別子を作成する 2 つの方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="71e2f-151">The following code example illustrates the two ways to create a self identifier.</span></span> <span data-ttu-id="71e2f-152">最初の行で、`as`キーワードの使用を自己識別子を定義します。</span><span class="sxs-lookup"><span data-stu-id="71e2f-152">In the first line, the `as` keyword is used to define the self identifier.</span></span> <span data-ttu-id="71e2f-153">5 番目の行では、識別子に`this`自己識別子をスコープは、メソッドに制限を定義するために使用`PrintMessage`です。</span><span class="sxs-lookup"><span data-stu-id="71e2f-153">In the fifth line, the identifier `this` is used to define a self identifier whose scope is restricted to the method `PrintMessage`.</span></span>

```fsharp
type MyClass2(dataIn) as self =
    let data = dataIn
    do
        self.PrintMessage()
    member this.PrintMessage() =
        printf "Creating MyClass2 with Data %d" data
```

<span data-ttu-id="71e2f-154">異なり他の .NET 言語で名前を指定できます、自己識別子が好みに合わせてです。いないに制限されている名前など`self`、 `Me`、または`this`です。</span><span class="sxs-lookup"><span data-stu-id="71e2f-154">Unlike in other .NET languages, you can name the self identifier however you want; you are not restricted to names such as `self`, `Me`, or `this`.</span></span>

<span data-ttu-id="71e2f-155">宣言された自己識別子、`as`までキーワードが初期化されていない後、`let`バインドが実行されます。</span><span class="sxs-lookup"><span data-stu-id="71e2f-155">The self identifier that is declared with the `as` keyword is not initialized until after the `let` bindings are executed.</span></span> <span data-ttu-id="71e2f-156">そのため、これでは使用できません、`let`バインドします。</span><span class="sxs-lookup"><span data-stu-id="71e2f-156">Therefore, it cannot be used in the `let` bindings.</span></span> <span data-ttu-id="71e2f-157">自己識別子を使用することができます、`do`バインド セクション。</span><span class="sxs-lookup"><span data-stu-id="71e2f-157">You can use the self identifier in the `do` bindings section.</span></span>


## <a name="generic-type-parameters"></a><span data-ttu-id="71e2f-158">ジェネリック型の型パラメーター</span><span class="sxs-lookup"><span data-stu-id="71e2f-158">Generic Type Parameters</span></span>

<span data-ttu-id="71e2f-159">山かっこでジェネリック型パラメーターが指定されて (`<`と`>`)、単一引用符の後に識別子の形式でします。</span><span class="sxs-lookup"><span data-stu-id="71e2f-159">Generic type parameters are specified in angle brackets (`<` and `>`), in the form of a single quotation mark followed by an identifier.</span></span> <span data-ttu-id="71e2f-160">複数のジェネリック型パラメーターは、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="71e2f-160">Multiple generic type parameters are separated by commas.</span></span> <span data-ttu-id="71e2f-161">ジェネリック型パラメーターは、宣言全体のスコープでです。</span><span class="sxs-lookup"><span data-stu-id="71e2f-161">The generic type parameter is in scope throughout the declaration.</span></span> <span data-ttu-id="71e2f-162">次のコード例では、ジェネリック型パラメーターを指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="71e2f-162">The following code example shows how to specify generic type parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2403.fs)]

<span data-ttu-id="71e2f-163">型を使用する場合、型引数が推論されます。</span><span class="sxs-lookup"><span data-stu-id="71e2f-163">Type arguments are inferred when the type is used.</span></span> <span data-ttu-id="71e2f-164">次のコードでは、推論された型は、組のシーケンスです。</span><span class="sxs-lookup"><span data-stu-id="71e2f-164">In the following code, the inferred type is a sequence of tuples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24031.fs)]
    
## <a name="specifying-inheritance"></a><span data-ttu-id="71e2f-165">継承を指定します。</span><span class="sxs-lookup"><span data-stu-id="71e2f-165">Specifying Inheritance</span></span>

<span data-ttu-id="71e2f-166">`inherit`句は、1 つを使用する必要がある場合に、直接基底クラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="71e2f-166">The `inherit` clause identifies the direct base class, if there is one.</span></span> <span data-ttu-id="71e2f-167">F# では、直接基底クラスを 1 つだけが許可されます。</span><span class="sxs-lookup"><span data-stu-id="71e2f-167">In F#, only one direct base class is allowed.</span></span> <span data-ttu-id="71e2f-168">クラスが実装するインターフェイスでは、基本クラスは考慮されません。</span><span class="sxs-lookup"><span data-stu-id="71e2f-168">Interfaces that a class implements are not considered base classes.</span></span> <span data-ttu-id="71e2f-169">インターフェイスは、後ほど、[インターフェイス](Interfaces.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="71e2f-169">Interfaces are discussed in the [Interfaces](Interfaces.md) topic.</span></span>

<span data-ttu-id="71e2f-170">表示するメソッドと基底クラスのプロパティ、派生クラスからを言語キーワードを使用して`base`を識別子としての後にピリオド (.) と、メンバーの名前。</span><span class="sxs-lookup"><span data-stu-id="71e2f-170">You can access the methods and properties of the base class from the derived class by using the language keyword `base` as an identifier, followed by a period (.) and the name of the member.</span></span>

<span data-ttu-id="71e2f-171">詳細については、「[継承](inheritance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71e2f-171">For more information, see [Inheritance](inheritance.md).</span></span>


## <a name="members-section"></a><span data-ttu-id="71e2f-172">メンバー セクション</span><span class="sxs-lookup"><span data-stu-id="71e2f-172">Members Section</span></span>
<span data-ttu-id="71e2f-173">このセクションでは、静的またはインスタンス メソッド、プロパティ、インターフェイスの実装、抽象メンバー、イベントの宣言、および追加のコンス トラクターを定義できます。</span><span class="sxs-lookup"><span data-stu-id="71e2f-173">You can define static or instance methods, properties, interface implementations, abstract members, event declarations, and additional constructors in this section.</span></span> <span data-ttu-id="71e2f-174">できるように、このセクションでバインドに表示できません。</span><span class="sxs-lookup"><span data-stu-id="71e2f-174">Let and do bindings cannot appear in this section.</span></span> <span data-ttu-id="71e2f-175">別のトピックで説明していますので、メンバーは、さまざまなクラスのほか、f# の型に追加できる、[メンバー](members/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="71e2f-175">Because members can be added to a variety of F# types in addition to classes, they are discussed in a separate topic, [Members](members/index.md).</span></span>


## <a name="mutually-recursive-types"></a><span data-ttu-id="71e2f-176">相互再帰型</span><span class="sxs-lookup"><span data-stu-id="71e2f-176">Mutually Recursive Types</span></span>
<span data-ttu-id="71e2f-177">循環的に相互に参照型を定義するとき、文字列一緒に種類の定義を使用して、`and`キーワード。</span><span class="sxs-lookup"><span data-stu-id="71e2f-177">When you define types that reference each other in a circular way, you string together the type definitions by using the `and` keyword.</span></span> <span data-ttu-id="71e2f-178">`and`キーワードに置き換えられます、`type`次のように、最初の定義以外のすべてのキーワードです。</span><span class="sxs-lookup"><span data-stu-id="71e2f-178">The `and` keyword replaces the `type` keyword on all except the first definition, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2404.fs)]

<span data-ttu-id="71e2f-179">出力は、現在のディレクトリ内のすべてのファイルの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="71e2f-179">The output is a list of all the files in the current directory.</span></span>


## <a name="when-to-use-classes-unions-records-and-structures"></a><span data-ttu-id="71e2f-180">クラス、共用体、レコード、および構造体を使用する場合</span><span class="sxs-lookup"><span data-stu-id="71e2f-180">When to Use Classes, Unions, Records, and Structures</span></span>
<span data-ttu-id="71e2f-181">指定する、さまざまな種類から選択すると、どのような各型のデザインはの特定の状況に該当する種類を選択するをよく理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="71e2f-181">Given the variety of types to choose from, you need to have a good understanding of what each type is designed for to select the appropriate type for a particular situation.</span></span> <span data-ttu-id="71e2f-182">クラスは、オブジェクト指向プログラミングのコンテキストで使用するために設計されます。</span><span class="sxs-lookup"><span data-stu-id="71e2f-182">Classes are designed for use in object-oriented programming contexts.</span></span> <span data-ttu-id="71e2f-183">オブジェクト指向プログラミングでは、.NET Framework 用に記述されているアプリケーションで使用される基準となるパラダイムです。</span><span class="sxs-lookup"><span data-stu-id="71e2f-183">Object-oriented programming is the dominant paradigm used in applications that are written for the .NET Framework.</span></span> <span data-ttu-id="71e2f-184">F# コードしている場合、.NET Framework または別のオブジェクト指向のライブラリと密接に連携の UI ライブラリなどのオブジェクト指向型システムからを拡張する必要がある場合は特に、クラスは、適切な可能性があります。</span><span class="sxs-lookup"><span data-stu-id="71e2f-184">If your F# code has to work closely with the .NET Framework or another object-oriented library, and especially if you have to extend from an object-oriented type system such as a UI library, classes are probably appropriate.</span></span>

<span data-ttu-id="71e2f-185">いない相互運用密接にしているオブジェクト指向のコードでは、自己完結型とオブジェクト指向のコードで頻繁に行われる操作から保護されているためであるコードを記述する場合や、レコードの使用を検討する必要がありますして判別共用体です。</span><span class="sxs-lookup"><span data-stu-id="71e2f-185">If you are not interoperating closely with object-oriented code, or if you are writing code that is self-contained and therefore protected from frequent interaction with object-oriented code, you should consider using records and discriminated unions.</span></span> <span data-ttu-id="71e2f-186">1 つのも思考アウト適切なパターン一致コードと共に、判別共用体は、オブジェクト階層をさらに簡単に多くの場合、使用できます。</span><span class="sxs-lookup"><span data-stu-id="71e2f-186">A single, well thought–out discriminated union, together with appropriate pattern matching code, can often be used as a simpler alternative to an object hierarchy.</span></span> <span data-ttu-id="71e2f-187">判別共用体の詳細については、次を参照してください。[判別共用体](discriminated-unions.md)です。</span><span class="sxs-lookup"><span data-stu-id="71e2f-187">For more information about discriminated unions, see [Discriminated Unions](discriminated-unions.md).</span></span>

<span data-ttu-id="71e2f-188">レコードが、クラスよりも簡単になるというメリットがあるが、型の要求は、簡単に達成できるを超えた場合にレコードが適切でないです。</span><span class="sxs-lookup"><span data-stu-id="71e2f-188">Records have the advantage of being simpler than classes, but records are not appropriate when the demands of a type exceed what can be accomplished with their simplicity.</span></span> <span data-ttu-id="71e2f-189">レコードは、基本的には単純な集計値、カスタム アクションを実行できる別のコンス トラクターを持たない、非表示のフィールドや継承またはインターフェイスの実装のないのです。</span><span class="sxs-lookup"><span data-stu-id="71e2f-189">Records are basically simple aggregates of values, without separate constructors that can perform custom actions, without hidden fields, and without inheritance or interface implementations.</span></span> <span data-ttu-id="71e2f-190">プロパティやメソッドなどのメンバーは、レコードをその動作はより複雑なに追加できる、レコードに格納されているフィールドはまだ値の単純な集計にします。</span><span class="sxs-lookup"><span data-stu-id="71e2f-190">Although members such as properties and methods can be added to records to make their behavior more complex, the fields stored in a record are still a simple aggregate of values.</span></span> <span data-ttu-id="71e2f-191">レコードの詳細については、次を参照してください。[レコード](records.md)です。</span><span class="sxs-lookup"><span data-stu-id="71e2f-191">For more information about records, see [Records](records.md).</span></span>

<span data-ttu-id="71e2f-192">構造体も、データの小規模な集約に便利ですが、それらとは異なり、クラスやレコードから .NET 値型では。</span><span class="sxs-lookup"><span data-stu-id="71e2f-192">Structures are also useful for small aggregates of data, but they differ from classes and records in that they are .NET value types.</span></span> <span data-ttu-id="71e2f-193">クラスやレコードは、.NET 参照型です。</span><span class="sxs-lookup"><span data-stu-id="71e2f-193">Classes and records are .NET reference types.</span></span> <span data-ttu-id="71e2f-194">値型と参照型のセマンティクスは、さまざまな値の型が値渡しされます。</span><span class="sxs-lookup"><span data-stu-id="71e2f-194">The semantics of value types and reference types are different in that value types are passed by value.</span></span> <span data-ttu-id="71e2f-195">つまり、コピーされるビット単位では、パラメーターとして渡されるまたは関数から返されます。</span><span class="sxs-lookup"><span data-stu-id="71e2f-195">This means that they are copied bit for bit when they are passed as a parameter or returned from a function.</span></span> <span data-ttu-id="71e2f-196">格納されるスタック上か、ヒープ上のそれぞれの場所に格納されている場合は、代わりに親オブジェクト内に埋め込まれた対象のフィールドとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="71e2f-196">They are also stored on the stack or, if they are used as a field, embedded inside the parent object instead of stored in their own separate location on the heap.</span></span> <span data-ttu-id="71e2f-197">そのため、構造体は、ヒープへのアクセスのオーバーヘッドが問題と頻繁にアクセスされるデータに適しています。</span><span class="sxs-lookup"><span data-stu-id="71e2f-197">Therefore, structures are appropriate for frequently accessed data when the overhead of accessing the heap is a problem.</span></span> <span data-ttu-id="71e2f-198">構造体の詳細については、次を参照してください。[構造](structures.md)です。</span><span class="sxs-lookup"><span data-stu-id="71e2f-198">For more information about structures, see [Structures](structures.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="71e2f-199">関連項目</span><span class="sxs-lookup"><span data-stu-id="71e2f-199">See Also</span></span>
[<span data-ttu-id="71e2f-200">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="71e2f-200">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="71e2f-201">メンバー</span><span class="sxs-lookup"><span data-stu-id="71e2f-201">Members</span></span>](members/index.md)

[<span data-ttu-id="71e2f-202">継承</span><span class="sxs-lookup"><span data-stu-id="71e2f-202">Inheritance</span></span>](inheritance.md)

[<span data-ttu-id="71e2f-203">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="71e2f-203">Interfaces</span></span>](interfaces.md)


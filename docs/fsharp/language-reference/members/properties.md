---
title: "プロパティ (F#)"
description: "F# のプロパティはオブジェクトに関連付けられている値を表すメンバーについて説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 98b363a5-ee6a-4b7b-b8ae-b244f2a0b316
ms.openlocfilehash: 53b93b20310c557ad9c30226bc08f85cbf2f3010
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="properties"></a><span data-ttu-id="7c609-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7c609-104">Properties</span></span>

<span data-ttu-id="7c609-105">*プロパティ*オブジェクトに関連付けられている値を表すメンバーであります。</span><span class="sxs-lookup"><span data-stu-id="7c609-105">*Properties* are members that represent values associated with an object.</span></span>


## <a name="syntax"></a><span data-ttu-id="7c609-106">構文</span><span class="sxs-lookup"><span data-stu-id="7c609-106">Syntax</span></span>

```fsharp
// Property that has both get and set defined.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with [accessibility-modifier] get() =
    get-function-body
and [accessibility-modifier] set parameter =
    set-function-body

// Alternative syntax for a property that has get and set.
[ attributes-for-get ]
[ static ] member [accessibility-modifier-for-get] [self-identifier.]PropertyName =
    get-function-body
[ attributes-for-set ]
[ static ] member [accessibility-modifier-for-set] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName =
    get-function-body

// Alternative syntax for property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with get() =
    get-function-body

// Property that has set only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Automatically implemented properties.
[ attributes ]
[ static ] member val [accessibility-modifier] PropertyName = initialization-expression [ with get, set ]
```

## <a name="remarks"></a><span data-ttu-id="7c609-107">コメント</span><span class="sxs-lookup"><span data-stu-id="7c609-107">Remarks</span></span>
<span data-ttu-id="7c609-108">プロパティは、"が、"オブジェクト インスタンスにして、または静的なプロパティを型と関連付けられているデータを表す、オブジェクト指向のプログラミングのリレーションシップ。</span><span class="sxs-lookup"><span data-stu-id="7c609-108">Properties represent the "has a" relationship in object-oriented programming, representing data that is associated with object instances or, for static properties, with the type.</span></span>

<span data-ttu-id="7c609-109">によっては、プロパティを基になる値 (バッキング ストアとも呼ばれます) を明示的に指定するかどうかや、コンパイラが自動的に生成するため、バッキング ストアを許可するかどうかは、次の 2 つの方法でプロパティを宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="7c609-109">You can declare properties in two ways, depending on whether you want to explicitly specify the underlying value (also called the backing store) for the property, or if you want to allow the compiler to automatically generate the backing store for you.</span></span> <span data-ttu-id="7c609-110">一般に、プロパティが値または変数の単純なラッパーだけの場合は、プロパティに重要な実装がある場合より明示的方法、および自動方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="7c609-110">Generally, you should use the more explicit way if the property has a non-trivial implementation and the automatic way when the property is just a simple wrapper for a value or variable.</span></span> <span data-ttu-id="7c609-111">プロパティを明示的に宣言するを使用して、`member`キーワード。</span><span class="sxs-lookup"><span data-stu-id="7c609-111">To declare a property explicitly, use the `member` keyword.</span></span> <span data-ttu-id="7c609-112">この宣言の構文を指定する構文に続けて、`get`と`set`もという名前のメソッド*アクセサー*です。</span><span class="sxs-lookup"><span data-stu-id="7c609-112">This declarative syntax is followed by the syntax that specifies the `get` and `set` methods, also named *accessors*.</span></span> <span data-ttu-id="7c609-113">読み取り/書き込み、書き込み専用、読み取り専用プロパティでは、さまざまな形式の「構文」セクションに示すように明示的な構文が使用されます。</span><span class="sxs-lookup"><span data-stu-id="7c609-113">The various forms of the explicit syntax shown in the syntax section are used for read/write, read-only, and write-only properties.</span></span> <span data-ttu-id="7c609-114">読み取り専用のプロパティを定義するのみ、`get`メソッドです。 書き込み専用のプロパティの定義のみ、`set`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="7c609-114">For read-only properties, you define only a `get` method; for write-only properties, define only a `set` method.</span></span> <span data-ttu-id="7c609-115">プロパティがある両方と`get`と`set`のアクセサーを別の構文を使用する属性とは、次のコードに示すように、アクセサーごとに異なるアクセシビリティ修飾子を指定します。</span><span class="sxs-lookup"><span data-stu-id="7c609-115">Note that when a property has both `get` and `set` accessors, the alternative syntax enables you to specify attributes and accessibility modifiers that are different for each accessor, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

<span data-ttu-id="7c609-116">読み取り/書き込みプロパティで両方の`get`と`set`メソッドの順序`get`と`set`元に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="7c609-116">For read/write properties, which have both a `get` and `set` method, the order of `get` and `set` can be reversed.</span></span> <span data-ttu-id="7c609-117">またはに示される構文を提供できます`get`だけに示される構文と`set`結合構文を使用する代わりにのみです。</span><span class="sxs-lookup"><span data-stu-id="7c609-117">Alternatively, you can provide the syntax shown for `get` only and the syntax shown for `set` only instead of using the combined syntax.</span></span> <span data-ttu-id="7c609-118">これを簡単をコメント アウト個人`get`または`set`メソッド、何を行う必要がありますかである場合。</span><span class="sxs-lookup"><span data-stu-id="7c609-118">Doing this makes it easier to comment out the individual `get` or `set` method, if that is something you might need to do.</span></span> <span data-ttu-id="7c609-119">結合の構文を使用してこの代替手順は、次のコードに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7c609-119">This alternative to using the combined syntax is shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

<span data-ttu-id="7c609-120">プライベート値をその保留中のプロパティのデータと呼びます*バッキング ストア*です。</span><span class="sxs-lookup"><span data-stu-id="7c609-120">Private values that hold the data for properties are called *backing stores*.</span></span> <span data-ttu-id="7c609-121">コンパイラのバッキング ストアを自動的に作成するのには、キーワードを使用して`member val`、自己の id を省略し、プロパティを初期化する式を指定します。</span><span class="sxs-lookup"><span data-stu-id="7c609-121">To have the compiler create the backing store automatically, use the keywords `member val`, omit the self-identifier, then provide an expression to initialize the property.</span></span> <span data-ttu-id="7c609-122">プロパティを変更可能である場合は、含める`with get, set`です。</span><span class="sxs-lookup"><span data-stu-id="7c609-122">If the property is to be mutable, include `with get, set`.</span></span> <span data-ttu-id="7c609-123">たとえば、次のクラス型には、自動的に実装された 2 つのプロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7c609-123">For example, the following class type includes two automatically implemented properties.</span></span> <span data-ttu-id="7c609-124">`Property1`読み取り専用とは、プライマリ コンス トラクターに渡される引数に初期化し、`Property2`は空の文字列に初期化される設定可能なプロパティ。</span><span class="sxs-lookup"><span data-stu-id="7c609-124">`Property1` is read-only and is initialized to the argument provided to the primary constructor, and `Property2` is a settable property initialized to an empty string:</span></span>

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

<span data-ttu-id="7c609-125">自動実装プロパティと同じように他のメンバー定義の前に含める必要がありますので、型の初期化の一部である`let`バインドと`do`種類の定義のバインディングです。</span><span class="sxs-lookup"><span data-stu-id="7c609-125">Automatically implemented properties are part of the initialization of a type, so they must be included before any other member definitions, just like `let` bindings and `do` bindings in a type definition.</span></span> <span data-ttu-id="7c609-126">自動的に実装されたプロパティを初期化する式は初期化時に、およびプロパティがアクセスされるたびにないをのみ評価されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7c609-126">Note that the expression that initializes an automatically implemented property is only evaluated upon initialization, and not every time the property is accessed.</span></span> <span data-ttu-id="7c609-127">この動作では、明示的に実装されたプロパティの動作とは対照的です。</span><span class="sxs-lookup"><span data-stu-id="7c609-127">This behavior is in contrast to the behavior of an explicitly implemented property.</span></span> <span data-ttu-id="7c609-128">どのような実質的には、これらのプロパティを初期化するコードは、クラスのコンス トラクターに追加されます。</span><span class="sxs-lookup"><span data-stu-id="7c609-128">What this effectively means is that the code to initialize these properties is added to the constructor of a class.</span></span> <span data-ttu-id="7c609-129">この違いを表示する次のコードを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="7c609-129">Consider the following code that shows this difference:</span></span>

```fsharp
type MyClass() =
    let random  = new System.Random()
    member val AutoProperty = random.Next() with get, set
    member this.ExplicitProperty = random.Next()

let class1 = new MyClass()

printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
```

<span data-ttu-id="7c609-130">**出力**</span><span class="sxs-lookup"><span data-stu-id="7c609-130">**Output**</span></span>

```
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

<span data-ttu-id="7c609-131">AutoProperty の値変更されていないことと、繰り返し呼び出したときに、ExplicitProperty 呼び出されるたびに変更が上記のコードの出力を示しています。</span><span class="sxs-lookup"><span data-stu-id="7c609-131">The output of the preceding code shows that the value of AutoProperty is unchanged when called repeatedly, whereas the ExplicitProperty changes each time it is called.</span></span> <span data-ttu-id="7c609-132">これを示します自動的に実装されたプロパティの式では、毎回は評価されません明示的なプロパティの get アクセス操作子メソッドが格納されます。</span><span class="sxs-lookup"><span data-stu-id="7c609-132">This demonstrates that the expression for an automatically implemented property is not evaluated each time, as is the getter method for the explicit property.</span></span>


>[!WARNING]
<span data-ttu-id="7c609-133">Entity Framework など、一部のライブラリがある (`System.Data.Entity`) 自動的に実装されたプロパティの初期化とうまく連携する基本クラス コンス トラクターのカスタム操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="7c609-133">There are some libraries, such as the Entity Framework (`System.Data.Entity`) that perform custom operations in base class constructors that don't work well with the initialization of automatically implemented properties.</span></span> <span data-ttu-id="7c609-134">その場合は、明示的なプロパティを使用して、やり直してください。</span><span class="sxs-lookup"><span data-stu-id="7c609-134">In those cases, try using explicit properties.</span></span>

<span data-ttu-id="7c609-135">プロパティは、クラス、構造体、判別共用体、レコード、インターフェイス、および型の拡張機能のメンバーであることができ、オブジェクト式で定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="7c609-135">Properties can be members of classes, structures, discriminated unions, records, interfaces, and type extensions and can also be defined in object expressions.</span></span>

<span data-ttu-id="7c609-136">属性は、プロパティに適用できます。</span><span class="sxs-lookup"><span data-stu-id="7c609-136">Attributes can be applied to properties.</span></span> <span data-ttu-id="7c609-137">プロパティに属性を適用するには、プロパティの前に別の行に属性を記述します。</span><span class="sxs-lookup"><span data-stu-id="7c609-137">To apply an attribute to a property, write the attribute on a separate line before the property.</span></span> <span data-ttu-id="7c609-138">詳細については、「[属性](../attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7c609-138">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="7c609-139">既定では、プロパティはパブリックです。</span><span class="sxs-lookup"><span data-stu-id="7c609-139">By default, properties are public.</span></span> <span data-ttu-id="7c609-140">アクセシビリティ修飾子は、プロパティにも適用できます。</span><span class="sxs-lookup"><span data-stu-id="7c609-140">Accessibility modifiers can also be applied to properties.</span></span> <span data-ttu-id="7c609-141">アクセシビリティ修飾子を適用するプロパティの名前の直前に場合追加両方に適用するものでは、`get`と`set`メソッドです追加する前に、`get`と`set`異なるアクセシビリティがある場合のキーワード。各アクセサーが必要です。</span><span class="sxs-lookup"><span data-stu-id="7c609-141">To apply an accessibility modifier, add it immediately before the name of the property if it is meant to apply to both the `get` and `set` methods; add it before the `get` and `set` keywords if different accessibility is required for each accessor.</span></span> <span data-ttu-id="7c609-142">*アクセシビリティ修飾子*、次のいずれかになります: `public`、 `private`、`internal`です。</span><span class="sxs-lookup"><span data-stu-id="7c609-142">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="7c609-143">詳細については、「[Access Control](../access-control.md)」(アクセス制御) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7c609-143">For more information, see [Access Control](../access-control.md).</span></span>

<span data-ttu-id="7c609-144">プロパティの実装は、プロパティがアクセスされるたびに実行されます。</span><span class="sxs-lookup"><span data-stu-id="7c609-144">Property implementations are executed each time a property is accessed.</span></span>


## <a name="static-and-instance-properties"></a><span data-ttu-id="7c609-145">静的なインスタンスのプロパティと</span><span class="sxs-lookup"><span data-stu-id="7c609-145">Static and Instance Properties</span></span>
<span data-ttu-id="7c609-146">プロパティでは、静的したり、プロパティをインスタンス化することができます。</span><span class="sxs-lookup"><span data-stu-id="7c609-146">Properties can be static or instance properties.</span></span> <span data-ttu-id="7c609-147">静的プロパティは、インスタンスなしで呼び出すことができ、個々 のオブジェクトではなく、型に関連付けられている値に使用されます。</span><span class="sxs-lookup"><span data-stu-id="7c609-147">Static properties can be invoked without an instance and are used for values associated with the type, not with individual objects.</span></span> <span data-ttu-id="7c609-148">静的プロパティは、自己識別子を省略します。</span><span class="sxs-lookup"><span data-stu-id="7c609-148">For static properties, omit the self-identifier.</span></span> <span data-ttu-id="7c609-149">自己識別子は、インスタンスのプロパティに必要です。</span><span class="sxs-lookup"><span data-stu-id="7c609-149">The self-identifier is required for instance properties.</span></span>

<span data-ttu-id="7c609-150">次の静的プロパティの定義がする必要がある静的フィールド シナリオに基づいて`myStaticValue`プロパティのバッキング ストアはします。</span><span class="sxs-lookup"><span data-stu-id="7c609-150">The following static property definition is based on a scenario in which you have a static field `myStaticValue` that is the backing store for the property.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

<span data-ttu-id="7c609-151">プロパティも指定できます配列に似たが呼び出された場合*インデックス付きプロパティ*です。</span><span class="sxs-lookup"><span data-stu-id="7c609-151">Properties can also be array-like, in which case they are called *indexed properties*.</span></span> <span data-ttu-id="7c609-152">詳細については、次を参照してください。[インデックス付きプロパティ](indexed-properties.md)です。</span><span class="sxs-lookup"><span data-stu-id="7c609-152">For more information, see [Indexed Properties](indexed-properties.md).</span></span>


## <a name="type-annotation-for-properties"></a><span data-ttu-id="7c609-153">プロパティの型の注釈</span><span class="sxs-lookup"><span data-stu-id="7c609-153">Type Annotation for Properties</span></span>
<span data-ttu-id="7c609-154">多くの場合、コンパイラは、バッキング ストアの種類のプロパティの型を推論するのに十分な情報が型の注釈を追加することで、型を明示的に設定することができます。</span><span class="sxs-lookup"><span data-stu-id="7c609-154">In many cases, the compiler has enough information to infer the type of a property from the type of the backing store, but you can set the type explicitly by adding a type annotation.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a><span data-ttu-id="7c609-155">Set アクセサーのプロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="7c609-155">Using Property set Accessors</span></span>
<span data-ttu-id="7c609-156">提供するプロパティを設定することができます`set`アクセサーを使用して、`<-`演算子。</span><span class="sxs-lookup"><span data-stu-id="7c609-156">You can set properties that provide `set` accessors by using the `<-` operator.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

<span data-ttu-id="7c609-157">出力は**20**です。</span><span class="sxs-lookup"><span data-stu-id="7c609-157">The output is **20**.</span></span>


## <a name="abstract-properties"></a><span data-ttu-id="7c609-158">抽象プロパティ</span><span class="sxs-lookup"><span data-stu-id="7c609-158">Abstract Properties</span></span>
<span data-ttu-id="7c609-159">プロパティは、抽象であることができます。</span><span class="sxs-lookup"><span data-stu-id="7c609-159">Properties can be abstract.</span></span> <span data-ttu-id="7c609-160">メソッドを使って、`abstract`だけプロパティに関連付けられている仮想ディスパッチがあることを意味します。</span><span class="sxs-lookup"><span data-stu-id="7c609-160">As with methods, `abstract` just means that there is a virtual dispatch associated with the property.</span></span> <span data-ttu-id="7c609-161">抽象プロパティ抽象化できるの本当は、同じクラスで定義されています。</span><span class="sxs-lookup"><span data-stu-id="7c609-161">Abstract properties can be truly abstract, that is, without a definition in the same class.</span></span> <span data-ttu-id="7c609-162">このようなプロパティを含むクラスは抽象クラスではこのためです。</span><span class="sxs-lookup"><span data-stu-id="7c609-162">The class that contains such a property is therefore an abstract class.</span></span> <span data-ttu-id="7c609-163">代わりに、抽象できますだけという意味では、定義が同じクラス内に存在する必要がありますの場合は、そのプロパティが、仮想です。</span><span class="sxs-lookup"><span data-stu-id="7c609-163">Alternatively, abstract can just mean that a property is virtual, and in that case, a definition must be present in the same class.</span></span> <span data-ttu-id="7c609-164">抽象プロパティをプライベートにすることはできません、1 つのアクセサーが抽象の場合は、他の必要がありますも抽象にすることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7c609-164">Note that abstract properties must not be private, and if one accessor is abstract, the other must also be abstract.</span></span> <span data-ttu-id="7c609-165">抽象クラスの詳細については、次を参照してください。[抽象クラス](../abstract-classes.md)です。</span><span class="sxs-lookup"><span data-stu-id="7c609-165">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a><span data-ttu-id="7c609-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="7c609-166">See Also</span></span>
[<span data-ttu-id="7c609-167">メンバー</span><span class="sxs-lookup"><span data-stu-id="7c609-167">Members</span></span>](index.md)

[<span data-ttu-id="7c609-168">メソッド</span><span class="sxs-lookup"><span data-stu-id="7c609-168">Methods</span></span>](methods.md)

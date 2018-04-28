---
title: '明示的なフィールド: val キーワード (F#)'
description: については、f# 'val' キーワードは、型を初期化せずにクラスまたは構造体の型に値を格納する場所を宣言するために使用します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: dc277680121976c0469b18c77bd84443cd251afb
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="explicit-fields-the-val-keyword"></a><span data-ttu-id="5c63a-103">明示的なフィールド: val キーワード</span><span class="sxs-lookup"><span data-stu-id="5c63a-103">Explicit Fields: The val Keyword</span></span>

<span data-ttu-id="5c63a-104">`val` キーワードを使用すると、クラス型または構造体型の値を格納する場所を初期化せずに宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="5c63a-104">The `val` keyword is used to declare a location to store a value in a class or structure type, without initializing it.</span></span> <span data-ttu-id="5c63a-105">この方法で宣言されている記憶域の場所といいます*明示的なフィールド*です。</span><span class="sxs-lookup"><span data-stu-id="5c63a-105">Storage locations declared in this manner are called *explicit fields*.</span></span> <span data-ttu-id="5c63a-106">`val` キーワードの別の用途として、`member` キーワードと組み合わせて自動実装プロパティを宣言する方法があります。</span><span class="sxs-lookup"><span data-stu-id="5c63a-106">Another use of the `val` keyword is in conjunction with the `member` keyword to declare an auto-implemented property.</span></span> <span data-ttu-id="5c63a-107">自動実装プロパティの詳細については、次を参照してください。[プロパティ](properties.md)です。</span><span class="sxs-lookup"><span data-stu-id="5c63a-107">For more information on auto-implemented properties, see [Properties](properties.md).</span></span>


## <a name="syntax"></a><span data-ttu-id="5c63a-108">構文</span><span class="sxs-lookup"><span data-stu-id="5c63a-108">Syntax</span></span>

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a><span data-ttu-id="5c63a-109">コメント</span><span class="sxs-lookup"><span data-stu-id="5c63a-109">Remarks</span></span>
<span data-ttu-id="5c63a-110">クラス型または構造体型のフィールドを定義するには、通常、`let` 束縛を使用します。</span><span class="sxs-lookup"><span data-stu-id="5c63a-110">The usual way to define fields in a class or structure type is to use a `let` binding.</span></span> <span data-ttu-id="5c63a-111">ただし、`let` 束縛は、クラス コンストラクターの一部として初期化する必要があります。これは、必ずしも可能または必要であるとは限らず、望ましくない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="5c63a-111">However, `let` bindings must be initialized as part of the class constructor, which is not always possible, necessary, or desirable.</span></span> <span data-ttu-id="5c63a-112">初期化されていないフィールドが必要な場合は、`val` キーワードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5c63a-112">You can use the `val` keyword when you want a field that is uninitialized.</span></span>

<span data-ttu-id="5c63a-113">明示的なフィールドは静的にも非静的にもできます。</span><span class="sxs-lookup"><span data-stu-id="5c63a-113">Explicit fields can be static or non-static.</span></span> <span data-ttu-id="5c63a-114">*アクセス修飾子*できます`public`、 `private`、または`internal`です。</span><span class="sxs-lookup"><span data-stu-id="5c63a-114">The *access-modifier* can be `public`, `private`, or `internal`.</span></span> <span data-ttu-id="5c63a-115">既定では、明示的なフィールドは public です。</span><span class="sxs-lookup"><span data-stu-id="5c63a-115">By default, explicit fields are public.</span></span> <span data-ttu-id="5c63a-116">常に private であるクラスの `let` 束縛とは、この点が異なります。</span><span class="sxs-lookup"><span data-stu-id="5c63a-116">This differs from `let` bindings in classes, which are always private.</span></span>

<span data-ttu-id="5c63a-117">[DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58)属性は、明示的なフィールドをプライマリ コンス トラクターを持つクラス型に必要です。</span><span class="sxs-lookup"><span data-stu-id="5c63a-117">The [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) attribute is required on explicit fields in class types that have a primary constructor.</span></span> <span data-ttu-id="5c63a-118">この属性は、フィールドが 0 に初期化されることを示します。</span><span class="sxs-lookup"><span data-stu-id="5c63a-118">This attribute specifies that the field is initialized to zero.</span></span> <span data-ttu-id="5c63a-119">フィールドの型ではゼロ初期化をサポートしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5c63a-119">The type of the field must support zero-initialization.</span></span> <span data-ttu-id="5c63a-120">型が次のいずれかである場合は、ゼロ初期化がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5c63a-120">A type supports zero-initialization if it is one of the following:</span></span>

- <span data-ttu-id="5c63a-121">値が 0 のプリミティブ型。</span><span class="sxs-lookup"><span data-stu-id="5c63a-121">A primitive type that has a zero value.</span></span>

- <span data-ttu-id="5c63a-122">標準値、外れ値、または値の表現として null 値をサポートする型。</span><span class="sxs-lookup"><span data-stu-id="5c63a-122">A type that supports a null value, either as a normal value, as an abnormal value, or as a representation of a value.</span></span> <span data-ttu-id="5c63a-123">これには、クラス、タプル、レコード、関数、インターフェイス、.NET 参照型、`unit` 型、判別された共用体型が含まれます。</span><span class="sxs-lookup"><span data-stu-id="5c63a-123">This includes classes, tuples, records, functions, interfaces, .NET reference types, the `unit` type, and discriminated union types.</span></span>

- <span data-ttu-id="5c63a-124">.NET 値型。</span><span class="sxs-lookup"><span data-stu-id="5c63a-124">A .NET value type.</span></span>

- <span data-ttu-id="5c63a-125">すべてのフィールドで既定値 0 がサポートされている構造体。</span><span class="sxs-lookup"><span data-stu-id="5c63a-125">A structure whose fields all support a default zero value.</span></span>


<span data-ttu-id="5c63a-126">たとえば、`someField` と呼ばれる変更できないフィールドには、.NET によるコンパイル済み表現を使用した、`someField@` という名前のバッキング フィールドが含まれており、ユーザーは `someField` という名前のプロパティを使用して、格納されている値にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="5c63a-126">For example, an immutable field called `someField` has a backing field in the .NET compiled representation with the name `someField@`, and you access the stored value using a property named `someField`.</span></span>

<span data-ttu-id="5c63a-127">変更可能なフィールドの場合、.NET によるコンパイル済み表現は .NET フィールドになります。</span><span class="sxs-lookup"><span data-stu-id="5c63a-127">For a mutable field, the .NET compiled representation is a .NET field.</span></span>


>[!WARNING] 
<span data-ttu-id="5c63a-128">`Note` .NET Framework 名前空間`System.ComponentModel`を同じ名前を持つ属性が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5c63a-128">`Note` The .NET Framework namespace `System.ComponentModel` contains an attribute that has the same name.</span></span> <span data-ttu-id="5c63a-129">この属性の詳細については、「`System.ComponentModel.DefaultValueAttribute`」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c63a-129">For information about this attribute, see `System.ComponentModel.DefaultValueAttribute`.</span></span>


<span data-ttu-id="5c63a-130">次のコードは、明示的なフィールドの使用方法を示しています。また、比較のために、プライマリ コンストラクターを持つクラスの `let` 束縛も示しています。</span><span class="sxs-lookup"><span data-stu-id="5c63a-130">The following code shows the use of explicit fields and, for comparison, a `let` binding in a class that has a primary constructor.</span></span> <span data-ttu-id="5c63a-131">`let` 束縛のフィールド `myInt1` が private であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5c63a-131">Note that the `let`-bound field `myInt1` is private.</span></span> <span data-ttu-id="5c63a-132">`let` 束縛のフィールド `myInt1` をメンバー メソッドから参照する際は、自己識別子 `this` は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="5c63a-132">When the `let`-bound field `myInt1` is referenced from a member method, the self identifier `this` is not required.</span></span> <span data-ttu-id="5c63a-133">ただし、明示的なフィールド `myInt2` と `myString` を参照する際は、自己識別子が必要です。</span><span class="sxs-lookup"><span data-stu-id="5c63a-133">But when you are referencing the explicit fields `myInt2` and `myString`, the self identifier is required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

<span data-ttu-id="5c63a-134">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5c63a-134">The output is as follows:</span></span>

```
11 12 abc
30 def
```

<span data-ttu-id="5c63a-135">次のコードは、プライマリ コンストラクターを持たないクラスでの明示的なフィールドの使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5c63a-135">The following code shows the use of explicit fields in a class that does not have a primary constructor.</span></span> <span data-ttu-id="5c63a-136">この場合、`DefaultValue` 属性は必要ありませんが、その型用に定義されているコンストラクターですべてのフィールドが初期化される必要があります。</span><span class="sxs-lookup"><span data-stu-id="5c63a-136">In this case, the `DefaultValue` attribute is not required, but all the fields must be initialized in the constructors that are defined for the type.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

<span data-ttu-id="5c63a-137">出力は `35 22`になります。</span><span class="sxs-lookup"><span data-stu-id="5c63a-137">The output is `35 22`.</span></span>

<span data-ttu-id="5c63a-138">次のコードは、構造体での明示的なフィールドの使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5c63a-138">The following code shows the use of explicit fields in a structure.</span></span> <span data-ttu-id="5c63a-139">構造体は値型であるため、フィールドの値を 0 に設定する既定のコンストラクターが自動的に含まれます。</span><span class="sxs-lookup"><span data-stu-id="5c63a-139">Because a structure is a value type, it automatically has a default constructor that sets the values of its fields to zero.</span></span> <span data-ttu-id="5c63a-140">そのため、`DefaultValue` 属性は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="5c63a-140">Therefore, the `DefaultValue` attribute is not required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

<span data-ttu-id="5c63a-141">出力は `11 xyz`になります。</span><span class="sxs-lookup"><span data-stu-id="5c63a-141">The output is `11 xyz`.</span></span>

<span data-ttu-id="5c63a-142">明示的なフィールドは日常的に使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="5c63a-142">Explicit fields are not intended for routine use.</span></span> <span data-ttu-id="5c63a-143">通常、可能な場合は、明示的なフィールドでなく、クラスで `let` 束縛を使用してください。</span><span class="sxs-lookup"><span data-stu-id="5c63a-143">In general, when possible you should use a `let` binding in a class instead of an explicit field.</span></span> <span data-ttu-id="5c63a-144">明示的なフィールドは、特定の相互運用のシナリオ (ネイティブ API に対するプラットフォーム呼び出しで使用される構造体を定義する必要がある場合など) や COM 相互運用のシナリオで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="5c63a-144">Explicit fields are useful in certain interoperability scenarios, such as when you need to define a structure that will be used in a platform invoke call to a native API, or in COM interop scenarios.</span></span> <span data-ttu-id="5c63a-145">詳細については、次を参照してください。[外部関数](../functions/external-functions.md)です。</span><span class="sxs-lookup"><span data-stu-id="5c63a-145">For more information, see [External Functions](../functions/external-functions.md).</span></span> <span data-ttu-id="5c63a-146">また、プライマリ コンストラクターを持たないクラスを生成する F# コード ジェネレーターを使用している場合にも、明示的なフィールドが必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="5c63a-146">Another situation in which an explicit field might be necessary is when you are working with an F# code generator which emits classes without a primary constructor.</span></span> <span data-ttu-id="5c63a-147">明示的なフィールドは、thread-static 変数や同様のコンストラクターでも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="5c63a-147">Explicit fields are also useful for thread-static variables or similar constructs.</span></span> <span data-ttu-id="5c63a-148">詳細については、「`System.ThreadStaticAttribute`」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c63a-148">For more information, see `System.ThreadStaticAttribute`.</span></span>

<span data-ttu-id="5c63a-149">キーワード `member val` が型定義にまとめて表示された場合は、自動的に実装されたプロパティの定義です。</span><span class="sxs-lookup"><span data-stu-id="5c63a-149">When the keywords `member val` appear together in a type definition, it is a definition of an automatically implemented property.</span></span> <span data-ttu-id="5c63a-150">詳細については、次を参照してください。[プロパティ](properties.md)です。</span><span class="sxs-lookup"><span data-stu-id="5c63a-150">For more information, see [Properties](properties.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="5c63a-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c63a-151">See Also</span></span>
[<span data-ttu-id="5c63a-152">プロパティ</span><span class="sxs-lookup"><span data-stu-id="5c63a-152">Properties</span></span>](properties.md)

[<span data-ttu-id="5c63a-153">メンバー</span><span class="sxs-lookup"><span data-stu-id="5c63a-153">Members</span></span>](index.md)

[<span data-ttu-id="5c63a-154">クラス内の `let` バインド</span><span class="sxs-lookup"><span data-stu-id="5c63a-154">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)

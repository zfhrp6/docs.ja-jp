---
title: レコード (F#)
description: F# のレコードがオプションでメンバーの名前付きの値の単純な集計を表現する方法について説明します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 1270bf4eaeba99a15b0f81b5477f4c3b98644f66
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="records"></a><span data-ttu-id="45594-103">レコード</span><span class="sxs-lookup"><span data-stu-id="45594-103">Records</span></span>

<span data-ttu-id="45594-104">レコードは、名前付きの値の単純な集合を表しており、オプションでメンバーを含みます。</span><span class="sxs-lookup"><span data-stu-id="45594-104">Records represent simple aggregates of named values, optionally with members.</span></span>  <span data-ttu-id="45594-105">4.1 以降では f#、構造体または参照型をか、設定できます。</span><span class="sxs-lookup"><span data-stu-id="45594-105">Starting with F# 4.1, they can either be structs or reference types.</span></span>  <span data-ttu-id="45594-106">これらは、既定では参照型です。</span><span class="sxs-lookup"><span data-stu-id="45594-106">They are reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="45594-107">構文</span><span class="sxs-lookup"><span data-stu-id="45594-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] typename = {
    [ mutable ] label1 : type1;
    [ mutable ] label2 : type2;
    ...
}
    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="45594-108">コメント</span><span class="sxs-lookup"><span data-stu-id="45594-108">Remarks</span></span>
<span data-ttu-id="45594-109">前の構文で*typename*レコードの種類の名前を指定*label1*と*label2*と呼ばれる値の名前は、*ラベル*、および*type1*と*type2*これらの値の種類を示します。</span><span class="sxs-lookup"><span data-stu-id="45594-109">In the previous syntax, *typename* is the name of the record type, *label1* and *label2* are names of values, referred to as *labels*, and *type1* and *type2* are the types of these values.</span></span> <span data-ttu-id="45594-110">*メンバー リスト*省略可能な型のメンバーの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="45594-110">*member-list* is the optional list of members for the type.</span></span>  <span data-ttu-id="45594-111">使用することができます、`[<Struct>]`参照型であるレコードではなく、構造体レコードを作成する属性。</span><span class="sxs-lookup"><span data-stu-id="45594-111">You can use the `[<Struct>]` attribute to create a struct record rather than a record which is a reference type.</span></span>

<span data-ttu-id="45594-112">いくつかの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="45594-112">Following are some examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

<span data-ttu-id="45594-113">各ラベルは、別々 の行には、セミコロンを省略できます。</span><span class="sxs-lookup"><span data-stu-id="45594-113">When each label is on a separate line, the semicolon is optional.</span></span>

<span data-ttu-id="45594-114">呼ばれる式の値を設定することができます*式を記録*です。</span><span class="sxs-lookup"><span data-stu-id="45594-114">You can set values in expressions known as *record expressions*.</span></span> <span data-ttu-id="45594-115">コンパイラは、(、ラベルが十分に区別されるその他のレコードの種類の場合) を使用するラベルから型を推測します。</span><span class="sxs-lookup"><span data-stu-id="45594-115">The compiler infers the type from the labels used (if the labels are sufficiently distinct from those of other record types).</span></span> <span data-ttu-id="45594-116">中かっこ ({}) は、レコード式を囲みます。</span><span class="sxs-lookup"><span data-stu-id="45594-116">Braces ({ }) enclose the record expression.</span></span> <span data-ttu-id="45594-117">次のコードはラベルが付いた 3 つの浮動要素を持つレコードを初期化するレコード式`x`、`y`と`z`です。</span><span class="sxs-lookup"><span data-stu-id="45594-117">The following code shows a record expression that initializes a record with three float elements with labels `x`, `y` and `z`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

<span data-ttu-id="45594-118">同じラベルも別の型がある場合は、短縮形を使わないでください。</span><span class="sxs-lookup"><span data-stu-id="45594-118">Do not use the shortened form if there could be another type that also has the same labels.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

<span data-ttu-id="45594-119">最後に宣言された型のラベルの以前に宣言された型よりも優先前の例では`mypoint3D`と推論されます`Point3D`です。</span><span class="sxs-lookup"><span data-stu-id="45594-119">The labels of the most recently declared type take precedence over those of the previously declared type, so in the preceding example, `mypoint3D` is inferred to be `Point3D`.</span></span> <span data-ttu-id="45594-120">次のコードのように、レコード型を明示的に指定することができます。</span><span class="sxs-lookup"><span data-stu-id="45594-120">You can explicitly specify the record type, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

<span data-ttu-id="45594-121">メソッドは、クラス型と同様のレコードの種類に対して定義できます。</span><span class="sxs-lookup"><span data-stu-id="45594-121">Methods can be defined for record types just as for class types.</span></span>

## <a name="creating-records-by-using-record-expressions"></a><span data-ttu-id="45594-122">レコード式を使用してレコードを作成します。</span><span class="sxs-lookup"><span data-stu-id="45594-122">Creating Records by Using Record Expressions</span></span>
<span data-ttu-id="45594-123">レコードで定義されているラベルを使用してレコードを初期化することができます。</span><span class="sxs-lookup"><span data-stu-id="45594-123">You can initialize records by using the labels that are defined in the record.</span></span> <span data-ttu-id="45594-124">これを行う式を呼びます、*式を記録*です。</span><span class="sxs-lookup"><span data-stu-id="45594-124">An expression that does this is referred to as a *record expression*.</span></span> <span data-ttu-id="45594-125">中かっこを使用して、区切り記号としてセミコロンを使用してレコード式を囲みます。</span><span class="sxs-lookup"><span data-stu-id="45594-125">Use braces to enclose the record expression and use the semicolon as a delimiter.</span></span>

<span data-ttu-id="45594-126">次の例では、レコードを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="45594-126">The following example shows how to create a record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

<span data-ttu-id="45594-127">レコード式では、型定義では、最後のフィールドの後のセミコロンは、1 行のすべてのフィールドがあるかどうかに関係なく、オプションです。</span><span class="sxs-lookup"><span data-stu-id="45594-127">The semicolons after the last field in the record expression and in the type definition are optional, regardless of whether the fields are all in one line.</span></span>

<span data-ttu-id="45594-128">レコードを作成する場合は、各フィールドの値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45594-128">When you create a record, you must supply values for each field.</span></span> <span data-ttu-id="45594-129">任意のフィールドの初期化式内の他のフィールドの値を参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="45594-129">You cannot refer to the values of other fields in the initialization expression for any field.</span></span>

<span data-ttu-id="45594-130">次のコードの種類で`myRecord2`フィールドの名前から推測されます。</span><span class="sxs-lookup"><span data-stu-id="45594-130">In the following code, the type of `myRecord2` is inferred from the names of the fields.</span></span> <span data-ttu-id="45594-131">必要に応じて、型名を明示的に指定することができます。</span><span class="sxs-lookup"><span data-stu-id="45594-131">Optionally, you can specify the type name explicitly.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="45594-132">レコードの構築の別の形式は、既存のレコードをコピーして、可能性のあるフィールドの値の一部を変更する必要がある場合に役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="45594-132">Another form of record construction can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span> <span data-ttu-id="45594-133">次のコード行を示します。</span><span class="sxs-lookup"><span data-stu-id="45594-133">The following line of code illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

<span data-ttu-id="45594-134">この形式のレコード式と呼ばれる、*コピーして更新するレコード式*です。</span><span class="sxs-lookup"><span data-stu-id="45594-134">This form of the record expression is called the *copy and update record expression*.</span></span>

<span data-ttu-id="45594-135">レコードは既定では変更できません。ただし、コピーと更新の式を使用して変更されたレコードを簡単に作成することができます。</span><span class="sxs-lookup"><span data-stu-id="45594-135">Records are immutable by default; however, you can easily create modified records by using a copy and update expression.</span></span> <span data-ttu-id="45594-136">変更可能なフィールドを明示的に指定できます。</span><span class="sxs-lookup"><span data-stu-id="45594-136">You can also explicitly specify a mutable field.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

<span data-ttu-id="45594-137">レコードのフィールドでは、DefaultValue 属性を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="45594-137">Don't use the DefaultValue attribute with record fields.</span></span> <span data-ttu-id="45594-138">既定値に初期化されるフィールドのレコードの既定のインスタンスを定義およびコピーを使用し、既定値と異なるフィールドを設定する式をレコードを更新することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="45594-138">A better approach is to define default instances of records with fields that are initialized to default values and then use a copy and update record expression to set any fields that differ from the default values.</span></span>

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
{
    field1 : int
    field2 : int
}

let defaultRecord1 = { field1 = 0; field2 = 0 }
let defaultRecord2 = { field1 = 1; field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with field2 = 42 }
```

## <a name="pattern-matching-with-records"></a><span data-ttu-id="45594-139">レコードを使用したパターン マッチ</span><span class="sxs-lookup"><span data-stu-id="45594-139">Pattern Matching with Records</span></span>
<span data-ttu-id="45594-140">レコードは、パターン マッチで使用できます。</span><span class="sxs-lookup"><span data-stu-id="45594-140">Records can be used with pattern matching.</span></span> <span data-ttu-id="45594-141">いくつかのフィールドを明示的に指定し、一致が発生したときに割り当てられる他のフィールドの変数を設定できます。</span><span class="sxs-lookup"><span data-stu-id="45594-141">You can specify some fields explicitly and provide variables for other fields that will be assigned when a match occurs.</span></span> <span data-ttu-id="45594-142">これを次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="45594-142">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

<span data-ttu-id="45594-143">このコードによる出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="45594-143">The output of this code is as follows.</span></span>

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a><span data-ttu-id="45594-144">レコードおよびクラス間の相違点</span><span class="sxs-lookup"><span data-stu-id="45594-144">Differences Between Records and Classes</span></span>
<span data-ttu-id="45594-145">レコードのフィールドとは異なり、クラスからプロパティとして自動的に公開されているし、それらが作成時に使用され、レコードのコピー。</span><span class="sxs-lookup"><span data-stu-id="45594-145">Record fields differ from classes in that they are automatically exposed as properties, and they are used in the creation and copying of records.</span></span> <span data-ttu-id="45594-146">レコードの作成は、クラスの構築からも異なります。</span><span class="sxs-lookup"><span data-stu-id="45594-146">Record construction also differs from class construction.</span></span> <span data-ttu-id="45594-147">レコードの種類では、コンス トラクターを定義できません。</span><span class="sxs-lookup"><span data-stu-id="45594-147">In a record type, you cannot define a constructor.</span></span> <span data-ttu-id="45594-148">代わりに、このトピックで説明する構築構文が適用されます。</span><span class="sxs-lookup"><span data-stu-id="45594-148">Instead, the construction syntax described in this topic applies.</span></span> <span data-ttu-id="45594-149">クラスは、コンス トラクターのパラメーター、フィールド、およびプロパティ間の直接の関係のあるありません。</span><span class="sxs-lookup"><span data-stu-id="45594-149">Classes have no direct relationship between constructor parameters, fields, and properties.</span></span>

<span data-ttu-id="45594-150">共用体と構造体の型と同様には、レコードは、構造の等値セマンティクスを持ちます。</span><span class="sxs-lookup"><span data-stu-id="45594-150">Like union and structure types, records have structural equality semantics.</span></span> <span data-ttu-id="45594-151">クラスは、参照を持つ等値セマンティクスです。</span><span class="sxs-lookup"><span data-stu-id="45594-151">Classes have reference equality semantics.</span></span> <span data-ttu-id="45594-152">次のコード例はこの処理方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="45594-152">The following code example demonstrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

<span data-ttu-id="45594-153">クラスと同じコードを記述する場合、2 つのクラス オブジェクトしない場合は等しくためとアドレスのみを比較するように 2 つの値をヒープ上の 2 つのオブジェクトを表します (クラス型のオーバーライドしない限り、`System.Object.Equals`メソッド)。</span><span class="sxs-lookup"><span data-stu-id="45594-153">If you write the same code with classes, the two class objects would be unequal because the two values would represent two objects on the heap and only the addresses would be compared (unless the class type overrides the `System.Object.Equals` method).</span></span>

<span data-ttu-id="45594-154">レコードに等しいかどうかを参照する必要がある場合、属性を追加`[<ReferenceEquality>]`レコード上。</span><span class="sxs-lookup"><span data-stu-id="45594-154">If you need reference equality for records, add the attribute `[<ReferenceEquality>]` above the record.</span></span>

## <a name="see-also"></a><span data-ttu-id="45594-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="45594-155">See Also</span></span>
[<span data-ttu-id="45594-156">F# の型</span><span class="sxs-lookup"><span data-stu-id="45594-156">F# Types</span></span>](fsharp-types.md)

[<span data-ttu-id="45594-157">クラス</span><span class="sxs-lookup"><span data-stu-id="45594-157">Classes</span></span>](classes.md)

[<span data-ttu-id="45594-158">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="45594-158">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="45594-159">参照の等価性</span><span class="sxs-lookup"><span data-stu-id="45594-159">Reference-Equality</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)

[<span data-ttu-id="45594-160">パターン一致</span><span class="sxs-lookup"><span data-stu-id="45594-160">Pattern Matching</span></span>](pattern-matching.md)

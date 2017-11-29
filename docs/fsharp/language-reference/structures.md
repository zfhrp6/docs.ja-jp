---
title: "構造体 (F#)"
description: "F# の構造について、多くの場合は、コンパクトなオブジェクト タイプ学習の少量のデータと単純な動作の種類のクラスよりも効率的です。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 50819506-3210-418f-9602-0ee1c9a52177
ms.openlocfilehash: 542b69a5aacb8fcfb0e8f6d6c943fe1954c4c59c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="structures"></a><span data-ttu-id="e95e6-104">構造体</span><span class="sxs-lookup"><span data-stu-id="e95e6-104">Structures</span></span>

<span data-ttu-id="e95e6-105">A*構造*はコンパクトなオブジェクト型であり、少量のデータと動作が単純な型のクラスよりも効率的です。</span><span class="sxs-lookup"><span data-stu-id="e95e6-105">A *structure* is a compact object type that can be more efficient than a class for types that have a small amount of data and simple behavior.</span></span>

## <a name="syntax"></a><span data-ttu-id="e95e6-106">構文</span><span class="sxs-lookup"><span data-stu-id="e95e6-106">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    struct
        type-definition-elements
    end
// or
[ attributes ]
[<StructAttribute>]
type [accessibility-modifier] type-name =
    type-definition-elements
```

## <a name="remarks"></a><span data-ttu-id="e95e6-107">コメント</span><span class="sxs-lookup"><span data-stu-id="e95e6-107">Remarks</span></span>
<span data-ttu-id="e95e6-108">構造体は*値の型*、つまりスタック上で直接、または、として使用されている場合、それらが保存されるフィールドまたは配列要素の場合、親のインラインを入力します。</span><span class="sxs-lookup"><span data-stu-id="e95e6-108">Structures are *value types*, which means that they are stored directly on the stack or, when they are used as fields or array elements, inline in the parent type.</span></span> <span data-ttu-id="e95e6-109">クラスやレコードとは異なり、構造体のセマンティクスは値渡しです。</span><span class="sxs-lookup"><span data-stu-id="e95e6-109">Unlike classes and records, structures have pass-by-value semantics.</span></span> <span data-ttu-id="e95e6-110">これは、主にアクセスおよびコピーが頻繁に行われるデータの小規模な集約に有用であることを意味します。</span><span class="sxs-lookup"><span data-stu-id="e95e6-110">This means that they are useful primarily for small aggregates of data that are accessed and copied frequently.</span></span>

<span data-ttu-id="e95e6-111">上記の構文では、2 つの形式が示されています。</span><span class="sxs-lookup"><span data-stu-id="e95e6-111">In the previous syntax, two forms are shown.</span></span> <span data-ttu-id="e95e6-112">1 番目のものは軽量構文ではないものの、頻繁に使用されます。これは、`struct` キーワードと `end` キーワードを使用する場合に、2 番目のものに出現する `StructAttribute` 属性を省略できるためです。</span><span class="sxs-lookup"><span data-stu-id="e95e6-112">The first is not the lightweight syntax, but it is nevertheless frequently used because, when you use the `struct` and `end` keywords, you can omit the `StructAttribute` attribute, which appears in the second form.</span></span> <span data-ttu-id="e95e6-113">`StructAttribute` は省略して単に `Struct` とすることができます。</span><span class="sxs-lookup"><span data-stu-id="e95e6-113">You can abbreviate `StructAttribute` to just `Struct`.</span></span>

<span data-ttu-id="e95e6-114">*型定義要素*前の構文でメンバーの宣言と定義を表します。</span><span class="sxs-lookup"><span data-stu-id="e95e6-114">The *type-definition-elements* in the previous syntax represents member declarations and definitions.</span></span> <span data-ttu-id="e95e6-115">構造体にはコンス トラクター、可変フィールド、および不変フィールドを含めることができ、メンバーとインターフェイス実装を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="e95e6-115">Structures can have constructors and mutable and immutable fields, and they can declare members and interface implementations.</span></span> <span data-ttu-id="e95e6-116">詳細については、次を参照してください。[メンバー](members/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="e95e6-116">For more information, see [Members](members/index.md).</span></span>

<span data-ttu-id="e95e6-117">構造体は、継承に参加することも、`let` または `do` バインディングを含めることも、それ自身の型のフィールドを再帰的に含めることもできません (ただし、それ自身の型を参照する参照セルを含めることができます)。</span><span class="sxs-lookup"><span data-stu-id="e95e6-117">Structures cannot participate in inheritance, cannot contain `let` or `do` bindings, and cannot recursively contain fields of their own type (although they can contain reference cells that reference their own type).</span></span>

<span data-ttu-id="e95e6-118">構造体では `let` バインディングは使用できないため、`val` キーワードを使用して構造体のフィールドを宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e95e6-118">Because structures do not allow `let` bindings, you must declare fields in structures by using the `val` keyword.</span></span> <span data-ttu-id="e95e6-119">`val` キーワードではフィールドとその型が定義されますが、初期化は実行できません。</span><span class="sxs-lookup"><span data-stu-id="e95e6-119">The `val` keyword defines a field and its type but does not allow initialization.</span></span> <span data-ttu-id="e95e6-120">代わりに、`val` 宣言がゼロまたは null に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="e95e6-120">Instead, `val` declarations are initialized to zero or null.</span></span> <span data-ttu-id="e95e6-121">このため、暗黙のコンストラクター (宣言で構造体名の直後に指定されるパラメーター) を含む構造体では、`val` 宣言に `DefaultValue` 属性で注釈を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="e95e6-121">For this reason, structures that have an implicit constructor (that is, parameters that are given immediately after the structure name in the declaration) require that `val` declarations be annotated with the `DefaultValue` attribute.</span></span> <span data-ttu-id="e95e6-122">定義されたコンストラクターを含む構造体でも、ゼロ初期化がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="e95e6-122">Structures that have a defined constructor still support zero-initialization.</span></span> <span data-ttu-id="e95e6-123">したがって、`DefaultValue` 属性は、このようなゼロ値がフィールドに対して有効であることの宣言になります。</span><span class="sxs-lookup"><span data-stu-id="e95e6-123">Therefore, the `DefaultValue` attribute is a declaration that such a zero value is valid for the field.</span></span> <span data-ttu-id="e95e6-124">構造体の暗黙的なコンストラクターでは動作は実行されません。これは、`let` バインディングと `do` バインディングがその型では許可されていないためですが、渡された暗黙のコンストラクターのパラメーター値はプライベート フィールドとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="e95e6-124">Implicit constructors for structures do not perform any actions because `let` and `do` bindings aren’t allowed on the type, but the implicit constructor parameter values passed in are available as private fields.</span></span>

<span data-ttu-id="e95e6-125">明示的なコンストラクターにフィールド値の初期化が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e95e6-125">Explicit constructors might involve initialization of field values.</span></span> <span data-ttu-id="e95e6-126">明示的なコンストラクターを含む構造体がある場合も、ゼロ初期化がサポートされます。ただし、明示的なコンストラクターと競合するため、`DefaultValue` 宣言では `val` 属性を使用しません。</span><span class="sxs-lookup"><span data-stu-id="e95e6-126">When you have a structure that has an explicit constructor, it still supports zero-initialization; however, you do not use the `DefaultValue` attribute on the `val` declarations because it conflicts with the explicit constructor.</span></span> <span data-ttu-id="e95e6-127">詳細については`val`宣言を参照してください[明示的なフィールド:`val`キーワード](members/explicit-fields-the-val-keyword.md)です。</span><span class="sxs-lookup"><span data-stu-id="e95e6-127">For more information about `val` declarations, see [Explicit Fields: The `val` Keyword](members/explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="e95e6-128">構造体では属性およびアクセシビリティ修飾子が許可されており、その他の型と同じ規則に従います。</span><span class="sxs-lookup"><span data-stu-id="e95e6-128">Attributes and accessibility modifiers are allowed on structures, and follow the same rules as those for other types.</span></span> <span data-ttu-id="e95e6-129">詳細については、次を参照してください。[属性](attributes.md)と[アクセス制御](access-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="e95e6-129">For more information, see [Attributes](attributes.md) and [Access Control](access-control.md).</span></span>

<span data-ttu-id="e95e6-130">次のコード例は構造体の定義を示しています。</span><span class="sxs-lookup"><span data-stu-id="e95e6-130">The following code examples illustrate structure definitions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="struct-records-and-discriminated-unions"></a><span data-ttu-id="e95e6-131">構造体のレコード、判別共用体</span><span class="sxs-lookup"><span data-stu-id="e95e6-131">Struct Records and Discriminated Unions</span></span>

<span data-ttu-id="e95e6-132">4.1 以降では f# で表すことができます[レコード](records.md)と[判別共用体](discriminated-unions.md)と構造体として、`[<Struct>]`属性。</span><span class="sxs-lookup"><span data-stu-id="e95e6-132">Starting with F# 4.1, you can represent [Records](records.md) and [Discriminated Unions](discriminated-unions.md) as structs with the `[<Struct>]` attribute.</span></span>  <span data-ttu-id="e95e6-133">詳細については、各記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e95e6-133">See each article to learn more.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="e95e6-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="e95e6-134">See Also</span></span>
[<span data-ttu-id="e95e6-135">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="e95e6-135">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="e95e6-136">クラス</span><span class="sxs-lookup"><span data-stu-id="e95e6-136">Classes</span></span>](classes.md)

[<span data-ttu-id="e95e6-137">レコード</span><span class="sxs-lookup"><span data-stu-id="e95e6-137">Records</span></span>](records.md)

[<span data-ttu-id="e95e6-138">メンバー</span><span class="sxs-lookup"><span data-stu-id="e95e6-138">Members</span></span>](members/index.md)

---
title: 構造体 (F#)
description: F# の構造について、多くの場合は、コンパクトなオブジェクト タイプ学習の少量のデータと単純な動作の種類のクラスよりも効率的です。
ms.date: 05/16/2016
ms.openlocfilehash: 728533e24dcfae219ae5ab3d410389e95fcfaee1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="structures"></a><span data-ttu-id="72e8f-103">構造体</span><span class="sxs-lookup"><span data-stu-id="72e8f-103">Structures</span></span>

<span data-ttu-id="72e8f-104">A*構造*はコンパクトなオブジェクト型であり、少量のデータと動作が単純な型のクラスよりも効率的です。</span><span class="sxs-lookup"><span data-stu-id="72e8f-104">A *structure* is a compact object type that can be more efficient than a class for types that have a small amount of data and simple behavior.</span></span>

## <a name="syntax"></a><span data-ttu-id="72e8f-105">構文</span><span class="sxs-lookup"><span data-stu-id="72e8f-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="72e8f-106">コメント</span><span class="sxs-lookup"><span data-stu-id="72e8f-106">Remarks</span></span>
<span data-ttu-id="72e8f-107">構造体は*値の型*、つまりスタック上で直接、または、として使用されている場合、それらが保存されるフィールドまたは配列要素の場合、親のインラインを入力します。</span><span class="sxs-lookup"><span data-stu-id="72e8f-107">Structures are *value types*, which means that they are stored directly on the stack or, when they are used as fields or array elements, inline in the parent type.</span></span> <span data-ttu-id="72e8f-108">クラスやレコードとは異なり、構造体のセマンティクスは値渡しです。</span><span class="sxs-lookup"><span data-stu-id="72e8f-108">Unlike classes and records, structures have pass-by-value semantics.</span></span> <span data-ttu-id="72e8f-109">これは、主にアクセスおよびコピーが頻繁に行われるデータの小規模な集約に有用であることを意味します。</span><span class="sxs-lookup"><span data-stu-id="72e8f-109">This means that they are useful primarily for small aggregates of data that are accessed and copied frequently.</span></span>

<span data-ttu-id="72e8f-110">上記の構文では、2 つの形式が示されています。</span><span class="sxs-lookup"><span data-stu-id="72e8f-110">In the previous syntax, two forms are shown.</span></span> <span data-ttu-id="72e8f-111">1 番目のものは軽量構文ではないものの、頻繁に使用されます。これは、`struct` キーワードと `end` キーワードを使用する場合に、2 番目のものに出現する `StructAttribute` 属性を省略できるためです。</span><span class="sxs-lookup"><span data-stu-id="72e8f-111">The first is not the lightweight syntax, but it is nevertheless frequently used because, when you use the `struct` and `end` keywords, you can omit the `StructAttribute` attribute, which appears in the second form.</span></span> <span data-ttu-id="72e8f-112">`StructAttribute` は省略して単に `Struct` とすることができます。</span><span class="sxs-lookup"><span data-stu-id="72e8f-112">You can abbreviate `StructAttribute` to just `Struct`.</span></span>

<span data-ttu-id="72e8f-113">*型定義要素*前の構文でメンバーの宣言と定義を表します。</span><span class="sxs-lookup"><span data-stu-id="72e8f-113">The *type-definition-elements* in the previous syntax represents member declarations and definitions.</span></span> <span data-ttu-id="72e8f-114">構造体にはコンス トラクター、可変フィールド、および不変フィールドを含めることができ、メンバーとインターフェイス実装を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="72e8f-114">Structures can have constructors and mutable and immutable fields, and they can declare members and interface implementations.</span></span> <span data-ttu-id="72e8f-115">詳細については、次を参照してください。[メンバー](members/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="72e8f-115">For more information, see [Members](members/index.md).</span></span>

<span data-ttu-id="72e8f-116">構造体は、継承に参加することも、`let` または `do` バインディングを含めることも、それ自身の型のフィールドを再帰的に含めることもできません (ただし、それ自身の型を参照する参照セルを含めることができます)。</span><span class="sxs-lookup"><span data-stu-id="72e8f-116">Structures cannot participate in inheritance, cannot contain `let` or `do` bindings, and cannot recursively contain fields of their own type (although they can contain reference cells that reference their own type).</span></span>

<span data-ttu-id="72e8f-117">構造体では `let` バインディングは使用できないため、`val` キーワードを使用して構造体のフィールドを宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="72e8f-117">Because structures do not allow `let` bindings, you must declare fields in structures by using the `val` keyword.</span></span> <span data-ttu-id="72e8f-118">`val` キーワードではフィールドとその型が定義されますが、初期化は実行できません。</span><span class="sxs-lookup"><span data-stu-id="72e8f-118">The `val` keyword defines a field and its type but does not allow initialization.</span></span> <span data-ttu-id="72e8f-119">代わりに、`val` 宣言がゼロまたは null に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="72e8f-119">Instead, `val` declarations are initialized to zero or null.</span></span> <span data-ttu-id="72e8f-120">このため、暗黙のコンストラクター (宣言で構造体名の直後に指定されるパラメーター) を含む構造体では、`val` 宣言に `DefaultValue` 属性で注釈を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="72e8f-120">For this reason, structures that have an implicit constructor (that is, parameters that are given immediately after the structure name in the declaration) require that `val` declarations be annotated with the `DefaultValue` attribute.</span></span> <span data-ttu-id="72e8f-121">定義されたコンストラクターを含む構造体でも、ゼロ初期化がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="72e8f-121">Structures that have a defined constructor still support zero-initialization.</span></span> <span data-ttu-id="72e8f-122">したがって、`DefaultValue` 属性は、このようなゼロ値がフィールドに対して有効であることの宣言になります。</span><span class="sxs-lookup"><span data-stu-id="72e8f-122">Therefore, the `DefaultValue` attribute is a declaration that such a zero value is valid for the field.</span></span> <span data-ttu-id="72e8f-123">構造体の暗黙的なコンストラクターでは動作は実行されません。これは、`let` バインディングと `do` バインディングがその型では許可されていないためですが、渡された暗黙のコンストラクターのパラメーター値はプライベート フィールドとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="72e8f-123">Implicit constructors for structures do not perform any actions because `let` and `do` bindings aren’t allowed on the type, but the implicit constructor parameter values passed in are available as private fields.</span></span>

<span data-ttu-id="72e8f-124">明示的なコンストラクターにフィールド値の初期化が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="72e8f-124">Explicit constructors might involve initialization of field values.</span></span> <span data-ttu-id="72e8f-125">明示的なコンストラクターを含む構造体がある場合も、ゼロ初期化がサポートされます。ただし、明示的なコンストラクターと競合するため、`DefaultValue` 宣言では `val` 属性を使用しません。</span><span class="sxs-lookup"><span data-stu-id="72e8f-125">When you have a structure that has an explicit constructor, it still supports zero-initialization; however, you do not use the `DefaultValue` attribute on the `val` declarations because it conflicts with the explicit constructor.</span></span> <span data-ttu-id="72e8f-126">詳細については`val`宣言を参照してください[明示的なフィールド:`val`キーワード](members/explicit-fields-the-val-keyword.md)です。</span><span class="sxs-lookup"><span data-stu-id="72e8f-126">For more information about `val` declarations, see [Explicit Fields: The `val` Keyword](members/explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="72e8f-127">構造体では属性およびアクセシビリティ修飾子が許可されており、その他の型と同じ規則に従います。</span><span class="sxs-lookup"><span data-stu-id="72e8f-127">Attributes and accessibility modifiers are allowed on structures, and follow the same rules as those for other types.</span></span> <span data-ttu-id="72e8f-128">詳細については、次を参照してください。[属性](attributes.md)と[アクセス制御](access-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="72e8f-128">For more information, see [Attributes](attributes.md) and [Access Control](access-control.md).</span></span>

<span data-ttu-id="72e8f-129">次のコード例は構造体の定義を示しています。</span><span class="sxs-lookup"><span data-stu-id="72e8f-129">The following code examples illustrate structure definitions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="struct-records-and-discriminated-unions"></a><span data-ttu-id="72e8f-130">構造体のレコード、判別共用体</span><span class="sxs-lookup"><span data-stu-id="72e8f-130">Struct Records and Discriminated Unions</span></span>

<span data-ttu-id="72e8f-131">4.1 以降では f# で表すことができます[レコード](records.md)と[判別共用体](discriminated-unions.md)と構造体として、`[<Struct>]`属性。</span><span class="sxs-lookup"><span data-stu-id="72e8f-131">Starting with F# 4.1, you can represent [Records](records.md) and [Discriminated Unions](discriminated-unions.md) as structs with the `[<Struct>]` attribute.</span></span>  <span data-ttu-id="72e8f-132">詳細については、各記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="72e8f-132">See each article to learn more.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="72e8f-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="72e8f-133">See Also</span></span>
[<span data-ttu-id="72e8f-134">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="72e8f-134">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="72e8f-135">クラス</span><span class="sxs-lookup"><span data-stu-id="72e8f-135">Classes</span></span>](classes.md)

[<span data-ttu-id="72e8f-136">レコード</span><span class="sxs-lookup"><span data-stu-id="72e8f-136">Records</span></span>](records.md)

[<span data-ttu-id="72e8f-137">メンバー</span><span class="sxs-lookup"><span data-stu-id="72e8f-137">Members</span></span>](members/index.md)

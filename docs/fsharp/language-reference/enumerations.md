---
title: "列挙型 (F#)"
description: "F# でリテラルの代わりに列挙体を使用して読みやすく、保守が容易なコードを作成する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9272bf5a-9a9f-4314-9e34-a3248e5244f5
ms.openlocfilehash: de0273900b707c99e6fb1bcc84e5c2b9ef2bc725
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="enumerations"></a><span data-ttu-id="c4838-104">列挙</span><span class="sxs-lookup"><span data-stu-id="c4838-104">Enumerations</span></span>

<span data-ttu-id="c4838-105">*列挙体*とも呼ばれる、*列挙型*、およびとも整数型の値のサブセットにラベルが割り当てられている場所です。</span><span class="sxs-lookup"><span data-stu-id="c4838-105">*Enumerations*, also known as *enums*, , are integral types where labels are assigned to a subset of the values.</span></span> <span data-ttu-id="c4838-106">リテラルの代わりに使用すると、コードの読み取りおよび保守が容易になります。</span><span class="sxs-lookup"><span data-stu-id="c4838-106">You can use them in place of literals to make code more readable and maintainable.</span></span>


## <a name="syntax"></a><span data-ttu-id="c4838-107">構文</span><span class="sxs-lookup"><span data-stu-id="c4838-107">Syntax</span></span>

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a><span data-ttu-id="c4838-108">コメント</span><span class="sxs-lookup"><span data-stu-id="c4838-108">Remarks</span></span>
<span data-ttu-id="c4838-109">列挙体ように見えるを単純な値を持つ判別共用体が、値を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="c4838-109">An enumeration looks much like a discriminated union that has simple values, except that the values can be specified.</span></span> <span data-ttu-id="c4838-110">通常、値は、0 または 1 から始まる整数またはビット位置を表す整数です。</span><span class="sxs-lookup"><span data-stu-id="c4838-110">The values are typically integers that start at 0 or 1, or integers that represent bit positions.</span></span> <span data-ttu-id="c4838-111">列挙する場合はビットの位置を表す、使用する必要も、[フラグ](xref:System.FlagsAttribute)属性。</span><span class="sxs-lookup"><span data-stu-id="c4838-111">If an enumeration is intended to represent bit positions, you should also use the [Flags](xref:System.FlagsAttribute) attribute.</span></span>

<span data-ttu-id="c4838-112">列挙体の基になる型は、たとえばを使用できるようにリテラル、サフィックスを持つなど、使用されるリテラルから決定されます`1u`、`2u`などの符号なし整数の (`uint32`) 型です。</span><span class="sxs-lookup"><span data-stu-id="c4838-112">The underlying type of the enumeration is determined from the literal that is used, so that, for example, you can use literals with a suffix, such as `1u`, `2u`, and so on, for an unsigned integer (`uint32`) type.</span></span>

<span data-ttu-id="c4838-113">名前付きの値を参照するときにする必要がありますとして使用する列挙型自体の名前、修飾子は、`enum-name.value1`だけでなく、`value1`です。</span><span class="sxs-lookup"><span data-stu-id="c4838-113">When you refer to the named values, you must use the name of the enumeration type itself as a qualifier, that is, `enum-name.value1`, not just `value1`.</span></span> <span data-ttu-id="c4838-114">この動作は、判別共用体の動作とは異なります。</span><span class="sxs-lookup"><span data-stu-id="c4838-114">This behavior differs from that of discriminated unions.</span></span> <span data-ttu-id="c4838-115">これは、常に列挙型であるため、 [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15)属性。</span><span class="sxs-lookup"><span data-stu-id="c4838-115">This is because enumerations always have the [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) attribute.</span></span>

<span data-ttu-id="c4838-116">次のコードは、宣言と列挙型の使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c4838-116">The following code shows the declaration and use of an enumeration.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

<span data-ttu-id="c4838-117">適切な演算子を使用して基になる型は、次のコードに示すように、列挙型を変換できます簡単にします。</span><span class="sxs-lookup"><span data-stu-id="c4838-117">You can easily convert enumerations to the underlying type by using the appropriate operator, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

<span data-ttu-id="c4838-118">列挙型には、次の基になる型の 1 つ持つことができます: `sbyte`、 `byte`、 `int16`、 `uint16`、 `int32`、 `uint32`、 `int64`、 `uint16`、 `uint64`、および`char`です。</span><span class="sxs-lookup"><span data-stu-id="c4838-118">Enumerated types can have one of the following underlying types: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, and `char`.</span></span> <span data-ttu-id="c4838-119">列挙型は、.NET framework から継承されている型として表される`System.Enum`、さらにから継承される`System.ValueType`です。</span><span class="sxs-lookup"><span data-stu-id="c4838-119">Enumeration types are represented in the .NET Framework as types that are inherited from `System.Enum`, which in turn is inherited from `System.ValueType`.</span></span> <span data-ttu-id="c4838-120">したがって、インライン親オブジェクトで、スタックに配置されている値型では、基になる型の任意の値が列挙体の有効な値。</span><span class="sxs-lookup"><span data-stu-id="c4838-120">Thus, they are value types that are located on the stack or inline in the containing object, and any value of the underlying type is a valid value of the enumeration.</span></span> <span data-ttu-id="c4838-121">これは重要なパターン マッチ列挙体に数値を使用するときに、名前のない値をキャッチするパターンを指定する必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="c4838-121">This is significant when pattern matching on enumeration values, because you have to provide a pattern that catches the unnamed values.</span></span>

<span data-ttu-id="c4838-122">`enum`関数 f# ライブラリで使用できます、定義済みの 1 つ以外の値も、列挙値を生成する名前付きの値。</span><span class="sxs-lookup"><span data-stu-id="c4838-122">The `enum` function in the F# library can be used to generate an enumeration value, even a value other than one of the predefined, named values.</span></span> <span data-ttu-id="c4838-123">使用する、`enum`次のように機能します。</span><span class="sxs-lookup"><span data-stu-id="c4838-123">You use the `enum` function as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

<span data-ttu-id="c4838-124">既定値`enum`関数は型で機能`int32`します。</span><span class="sxs-lookup"><span data-stu-id="c4838-124">The default `enum` function works with type `int32`.</span></span> <span data-ttu-id="c4838-125">そのため、基になるその他の型を持つ列挙型と共に使用できません。</span><span class="sxs-lookup"><span data-stu-id="c4838-125">Therefore, it cannot be used with enumeration types that have other underlying types.</span></span> <span data-ttu-id="c4838-126">代わりに、次を使用します。</span><span class="sxs-lookup"><span data-stu-id="c4838-126">Instead, use the following.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]
    
## <a name="see-also"></a><span data-ttu-id="c4838-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4838-127">See Also</span></span>
[<span data-ttu-id="c4838-128">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="c4838-128">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="c4838-129">キャストと変換</span><span class="sxs-lookup"><span data-stu-id="c4838-129">Casting and Conversions</span></span>](casting-and-conversions.md)

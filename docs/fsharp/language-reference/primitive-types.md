---
title: "プリミティブ型 (F#)"
description: "F# 言語で使用される基本的なプリミティブ型を検出します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2f23d98b-551b-4fd2-9f4f-0fd7254288ed
ms.openlocfilehash: b493cdf7116d94f66940d03b86e584bcecbbb0f1
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/08/2017
---
# <a name="primitive-types"></a><span data-ttu-id="8c0f8-104">プリミティブ型</span><span class="sxs-lookup"><span data-stu-id="8c0f8-104">Primitive Types</span></span>

<span data-ttu-id="8c0f8-105">このトピックでは、f# 言語で使用される基本的なプリミティブ型を示します。</span><span class="sxs-lookup"><span data-stu-id="8c0f8-105">This topic lists the fundamental primitive types that are used in the F# language.</span></span> <span data-ttu-id="8c0f8-106">また、対応する .NET 型と各型の最小値と最大値も示します。</span><span class="sxs-lookup"><span data-stu-id="8c0f8-106">It also provides the corresponding .NET types and the minimum and maximum values for each type.</span></span>

## <a name="summary-of-primitive-types"></a><span data-ttu-id="8c0f8-107">プリミティブ型の概要</span><span class="sxs-lookup"><span data-stu-id="8c0f8-107">Summary of Primitive Types</span></span>
<span data-ttu-id="8c0f8-108">次の表では、プリミティブの f# 型のプロパティをまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="8c0f8-108">The following table summarizes the properties of the primitive F# types.</span></span>

|<span data-ttu-id="8c0f8-109">型</span><span class="sxs-lookup"><span data-stu-id="8c0f8-109">Type</span></span>|<span data-ttu-id="8c0f8-110">.NET 型</span><span class="sxs-lookup"><span data-stu-id="8c0f8-110">.NET type</span></span>|<span data-ttu-id="8c0f8-111">説明</span><span class="sxs-lookup"><span data-stu-id="8c0f8-111">Description</span></span>|
|----|---------|-----------|
|`bool`|`System.Boolean`|<span data-ttu-id="8c0f8-112">有効な値は、`true` と `false` です。</span><span class="sxs-lookup"><span data-stu-id="8c0f8-112">Possible values are `true` and `false`.</span></span>|
|`byte`|`System.Byte`|<span data-ttu-id="8c0f8-113">0 から 255 の値です。</span><span class="sxs-lookup"><span data-stu-id="8c0f8-113">Values from 0 to 255.</span></span>|
|`sbyte`|`System.SByte`|<span data-ttu-id="8c0f8-114">-128 から 127 の値です。</span><span class="sxs-lookup"><span data-stu-id="8c0f8-114">Values from -128 to 127.</span></span>|
|`int16`|`System.Int16`|<span data-ttu-id="8c0f8-115">-32768 から 32767 の値です。</span><span class="sxs-lookup"><span data-stu-id="8c0f8-115">Values from -32768 to 32767.</span></span>|
|`uint16`|`System.UInt16`|<span data-ttu-id="8c0f8-116">0 から 65535 の値です。</span><span class="sxs-lookup"><span data-stu-id="8c0f8-116">Values from 0 to 65535.</span></span>|
|`int`|`System.Int32`|<span data-ttu-id="8c0f8-117">-2,147, 483,648 から 2,147, 483,647 の値です。</span><span class="sxs-lookup"><span data-stu-id="8c0f8-117">Values from -2,147,483,648 to 2,147,483,647.</span></span>|
|`uint32`|`System.UInt32`|<span data-ttu-id="8c0f8-118">0 から 4,294,967,295 の値です。</span><span class="sxs-lookup"><span data-stu-id="8c0f8-118">Values from 0 to 4,294,967,295.</span></span>|
|`int64`|`System.Int64`|<span data-ttu-id="8c0f8-119">9,223,372,036,854,775,807-9,223,372,036,854,775,808 から値です。</span><span class="sxs-lookup"><span data-stu-id="8c0f8-119">Values from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.</span></span>|
|`uint64`|`System.UInt64`|<span data-ttu-id="8c0f8-120">0 から 18,446,744,073,709,551,615 の値です。</span><span class="sxs-lookup"><span data-stu-id="8c0f8-120">Values from 0 to 18,446,744,073,709,551,615.</span></span>|
|`nativeint`|`System.IntPtr`|<span data-ttu-id="8c0f8-121">符号付き整数としてのネイティブ ポインターです。</span><span class="sxs-lookup"><span data-stu-id="8c0f8-121">A native pointer as a signed integer.</span></span>|
|`unativeint`|`System.UIntPtr`|<span data-ttu-id="8c0f8-122">符号なし整数としてのネイティブ ポインターです。</span><span class="sxs-lookup"><span data-stu-id="8c0f8-122">A native pointer as an unsigned integer.</span></span>|
|`char`|`System.Char`|<span data-ttu-id="8c0f8-123">Unicode 文字の値。</span><span class="sxs-lookup"><span data-stu-id="8c0f8-123">Unicode character values.</span></span>|
|`string`|`System.String`|<span data-ttu-id="8c0f8-124">Unicode テキストです。</span><span class="sxs-lookup"><span data-stu-id="8c0f8-124">Unicode text.</span></span>|
|`decimal`|`System.Decimal`|<span data-ttu-id="8c0f8-125">浮動小数点には少なくとも 28 の有効桁数を持つデータ型です。</span><span class="sxs-lookup"><span data-stu-id="8c0f8-125">A floating point data type that has at least 28 significant digits.</span></span>|
|`unit`|<span data-ttu-id="8c0f8-126">該当なし</span><span class="sxs-lookup"><span data-stu-id="8c0f8-126">not applicable</span></span>|<span data-ttu-id="8c0f8-127">実際の値が存在しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="8c0f8-127">Indicates the absence of an actual value.</span></span> <span data-ttu-id="8c0f8-128">型が示される 1 つだけの仮引数の値を持つ`()`します。</span><span class="sxs-lookup"><span data-stu-id="8c0f8-128">The type has only one formal value, which is denoted `()`.</span></span> <span data-ttu-id="8c0f8-129">単位の値、 `()`、ここで値が必要が、実際の値が使用可能なまたは意味をなさなくプレース ホルダーとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="8c0f8-129">The unit value, `()`, is often used as a placeholder where a value is needed but no real value is available or makes sense.</span></span>|
|`void`|`System.Void`|<span data-ttu-id="8c0f8-130">ないことを示します型または値。</span><span class="sxs-lookup"><span data-stu-id="8c0f8-130">Indicates no type or value.</span></span>|
|`float32, single`|`System.Single`|<span data-ttu-id="8c0f8-131">32 ビット浮動小数点型です。</span><span class="sxs-lookup"><span data-stu-id="8c0f8-131">A 32-bit floating point type.</span></span>|
|`float, double`|`System.Double`|<span data-ttu-id="8c0f8-132">64 ビット浮動小数点型です。</span><span class="sxs-lookup"><span data-stu-id="8c0f8-132">A 64-bit floating point type.</span></span>|

>[!NOTE]
<span data-ttu-id="8c0f8-133">使用して、64 ビット整数型に対して大きすぎる整数を使用して計算を行うことができます、 [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa)型です。</span><span class="sxs-lookup"><span data-stu-id="8c0f8-133">You can perform computations with integers too big for the 64-bit integer type by using the [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) type.</span></span> <span data-ttu-id="8c0f8-134">`bigint`プリミティブ型であるとは見なされません省略形は`System.Numerics.BigInteger`します。</span><span class="sxs-lookup"><span data-stu-id="8c0f8-134">`bigint` is not considered a primitive type; it is an abbreviation for `System.Numerics.BigInteger`.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c0f8-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c0f8-135">See Also</span></span>
[<span data-ttu-id="8c0f8-136">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="8c0f8-136">F# Language Reference</span></span>](index.md)

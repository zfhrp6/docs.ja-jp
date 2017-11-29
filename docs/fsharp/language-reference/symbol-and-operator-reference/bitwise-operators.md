---
title: "ビット処理演算子 (F#)"
description: "F# のプログラミング言語で使用可能なビットごとの演算子について説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8a2c87f5-b4c7-47fe-8580-82c956f605e5
ms.openlocfilehash: 61a8e6bafe97a229480c967a4afb5d2a256474c8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="bitwise-operators"></a><span data-ttu-id="021c3-104">ビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="021c3-104">Bitwise Operators</span></span>

<span data-ttu-id="021c3-105">このトピックでは、f# 言語で使用可能なビットごとの演算子について説明します。</span><span class="sxs-lookup"><span data-stu-id="021c3-105">This topic describes bitwise operators that are available in the F# language.</span></span>

## <a name="summary-of-bitwise-operators"></a><span data-ttu-id="021c3-106">ビットごとの演算子の概要</span><span class="sxs-lookup"><span data-stu-id="021c3-106">Summary of Bitwise Operators</span></span>
<span data-ttu-id="021c3-107">次の表では、ボックス化解除された整数型の f# 言語でサポートされているビットごとの演算子について説明します。</span><span class="sxs-lookup"><span data-stu-id="021c3-107">The following table describes the bitwise operators that are supported for unboxed integral types in the F# language.</span></span>

|<span data-ttu-id="021c3-108">演算子</span><span class="sxs-lookup"><span data-stu-id="021c3-108">Operator</span></span>|<span data-ttu-id="021c3-109">メモ</span><span class="sxs-lookup"><span data-stu-id="021c3-109">Notes</span></span>|
|--------|-----|
|`&&&`|<span data-ttu-id="021c3-110">ビットごとの AND 演算子です。</span><span class="sxs-lookup"><span data-stu-id="021c3-110">Bitwise AND operator.</span></span> <span data-ttu-id="021c3-111">結果のビットは、両方のソース オペランドの対応するビットが 1 の場合にのみ、値 1 を持ちます。</span><span class="sxs-lookup"><span data-stu-id="021c3-111">Bits in the result have the value 1 if and only if the corresponding bits in both source operands are 1.</span></span>|
|<code>&#124;&#124;&#124;</code>|<span data-ttu-id="021c3-112">ビットごとの OR 演算子。</span><span class="sxs-lookup"><span data-stu-id="021c3-112">Bitwise OR operator.</span></span> <span data-ttu-id="021c3-113">いずれかに、結果のビットが 1 の値を持つソースに対応するビットのオペランドは 1 です。</span><span class="sxs-lookup"><span data-stu-id="021c3-113">Bits in the result have the value 1 if either of the corresponding bits in the source operands are 1.</span></span>|
|`^^^`|<span data-ttu-id="021c3-114">ビットごとの排他的 OR 演算子。</span><span class="sxs-lookup"><span data-stu-id="021c3-114">Bitwise exclusive OR operator.</span></span> <span data-ttu-id="021c3-115">結果のビットは、ソース オペランドのビットが等しくない値を持つ場合にのみ、値 1 を持ちます。</span><span class="sxs-lookup"><span data-stu-id="021c3-115">Bits in the result have the value 1 if and only if bits in the source operands have unequal values.</span></span>|
|`~~~`|<span data-ttu-id="021c3-116">ビットごとの否定演算子です。</span><span class="sxs-lookup"><span data-stu-id="021c3-116">Bitwise negation operator.</span></span> <span data-ttu-id="021c3-117">これは、単項演算子であり、ソース オペランド内のすべての 0 のビットが 1 のビットに変換し、すべて 1 ビットが 0 のビットに変換結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="021c3-117">This is a unary operator and produces a result in which all 0 bits in the source operand are converted to 1 bits and all 1 bits are converted to 0 bits.</span></span>|
|`<<<`|<span data-ttu-id="021c3-118">ビットごとの左シフト演算子。</span><span class="sxs-lookup"><span data-stu-id="021c3-118">Bitwise left-shift operator.</span></span> <span data-ttu-id="021c3-119">結果は、最初のオペランドのビットを 2 番目のオペランドのビット数だけ左にシフトします。</span><span class="sxs-lookup"><span data-stu-id="021c3-119">The result is the first operand with bits shifted left by the number of bits in the second operand.</span></span> <span data-ttu-id="021c3-120">最下位の位置には、最上位の位置からシフトは循環しません。</span><span class="sxs-lookup"><span data-stu-id="021c3-120">Bits shifted off the most significant position are not rotated into the least significant position.</span></span> <span data-ttu-id="021c3-121">最下位ビットが 0 で埋められます。</span><span class="sxs-lookup"><span data-stu-id="021c3-121">The least significant bits are padded with zeros.</span></span> <span data-ttu-id="021c3-122">2 番目の引数の型は`int32`します。</span><span class="sxs-lookup"><span data-stu-id="021c3-122">The type of the second argument is `int32`.</span></span>|
|`>>>`|<span data-ttu-id="021c3-123">ビットごと右シフト演算子。</span><span class="sxs-lookup"><span data-stu-id="021c3-123">Bitwise right-shift operator.</span></span> <span data-ttu-id="021c3-124">結果は、最初のオペランドと 2 番目のオペランドのビット数だけ右にシフトするビットです。</span><span class="sxs-lookup"><span data-stu-id="021c3-124">The result is the first operand with bits shifted right by the number of bits in the second operand.</span></span> <span data-ttu-id="021c3-125">最上位の位置には、最下位の位置からシフトは循環しません。</span><span class="sxs-lookup"><span data-stu-id="021c3-125">Bits shifted off the least significant position are not rotated into the most significant position.</span></span> <span data-ttu-id="021c3-126">符号なし型の場合は、最上位ビットが 0 で埋められます。</span><span class="sxs-lookup"><span data-stu-id="021c3-126">For unsigned types, the most significant bits are padded with zeros.</span></span> <span data-ttu-id="021c3-127">署名された型の場合は、最上位ビットはものに埋められます。</span><span class="sxs-lookup"><span data-stu-id="021c3-127">For signed types, the most significant bits are padded with ones.</span></span> <span data-ttu-id="021c3-128">2 番目の引数の型は`int32`します。</span><span class="sxs-lookup"><span data-stu-id="021c3-128">The type of the second argument is `int32`.</span></span>|

<span data-ttu-id="021c3-129">ビットごとの演算子では、次の種類を使用できます: `byte`、 `sbyte`、 `int16`、 `uint16`、 `int32 (int)`、 `uint32`、 `int64`、 `uint64`、 `nativeint`、および`unativeint`です。</span><span class="sxs-lookup"><span data-stu-id="021c3-129">The following types can be used with bitwise operators: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, and `unativeint`.</span></span>

## <a name="see-also"></a><span data-ttu-id="021c3-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="021c3-130">See Also</span></span>
[<span data-ttu-id="021c3-131">シンボルと演算子のリファレンス</span><span class="sxs-lookup"><span data-stu-id="021c3-131">Symbol and Operator Reference</span></span>](index.md)

[<span data-ttu-id="021c3-132">算術演算子</span><span class="sxs-lookup"><span data-stu-id="021c3-132">Arithmetic Operators</span></span>](arithmetic-operators.md)

[<span data-ttu-id="021c3-133">ブール演算子</span><span class="sxs-lookup"><span data-stu-id="021c3-133">Boolean Operators</span></span>](boolean-operators.md)


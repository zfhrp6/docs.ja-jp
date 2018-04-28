---
title: ビット処理演算子 (F#)
description: F# のプログラミング言語で使用可能なビットごとの演算子について説明します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 4d5abff564a5d1dcbe52b99edf431ca10e442061
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="bitwise-operators"></a><span data-ttu-id="43bdd-103">ビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="43bdd-103">Bitwise Operators</span></span>

<span data-ttu-id="43bdd-104">このトピックでは、f# 言語で使用可能なビットごとの演算子について説明します。</span><span class="sxs-lookup"><span data-stu-id="43bdd-104">This topic describes bitwise operators that are available in the F# language.</span></span>

## <a name="summary-of-bitwise-operators"></a><span data-ttu-id="43bdd-105">ビットごとの演算子の概要</span><span class="sxs-lookup"><span data-stu-id="43bdd-105">Summary of Bitwise Operators</span></span>
<span data-ttu-id="43bdd-106">次の表では、ボックス化解除された整数型の f# 言語でサポートされているビットごとの演算子について説明します。</span><span class="sxs-lookup"><span data-stu-id="43bdd-106">The following table describes the bitwise operators that are supported for unboxed integral types in the F# language.</span></span>

|<span data-ttu-id="43bdd-107">演算子</span><span class="sxs-lookup"><span data-stu-id="43bdd-107">Operator</span></span>|<span data-ttu-id="43bdd-108">メモ</span><span class="sxs-lookup"><span data-stu-id="43bdd-108">Notes</span></span>|
|--------|-----|
|`&&&`|<span data-ttu-id="43bdd-109">ビットごとの AND 演算子です。</span><span class="sxs-lookup"><span data-stu-id="43bdd-109">Bitwise AND operator.</span></span> <span data-ttu-id="43bdd-110">結果のビットは、両方のソース オペランドの対応するビットが 1 の場合にのみ、値 1 を持ちます。</span><span class="sxs-lookup"><span data-stu-id="43bdd-110">Bits in the result have the value 1 if and only if the corresponding bits in both source operands are 1.</span></span>|
|<code>&#124;&#124;&#124;</code>|<span data-ttu-id="43bdd-111">ビットごとの OR 演算子。</span><span class="sxs-lookup"><span data-stu-id="43bdd-111">Bitwise OR operator.</span></span> <span data-ttu-id="43bdd-112">いずれかに、結果のビットが 1 の値を持つソースに対応するビットのオペランドは 1 です。</span><span class="sxs-lookup"><span data-stu-id="43bdd-112">Bits in the result have the value 1 if either of the corresponding bits in the source operands are 1.</span></span>|
|`^^^`|<span data-ttu-id="43bdd-113">ビットごとの排他的 OR 演算子。</span><span class="sxs-lookup"><span data-stu-id="43bdd-113">Bitwise exclusive OR operator.</span></span> <span data-ttu-id="43bdd-114">結果のビットは、ソース オペランドのビットが等しくない値を持つ場合にのみ、値 1 を持ちます。</span><span class="sxs-lookup"><span data-stu-id="43bdd-114">Bits in the result have the value 1 if and only if bits in the source operands have unequal values.</span></span>|
|`~~~`|<span data-ttu-id="43bdd-115">ビットごとの否定演算子です。</span><span class="sxs-lookup"><span data-stu-id="43bdd-115">Bitwise negation operator.</span></span> <span data-ttu-id="43bdd-116">これは、単項演算子であり、ソース オペランド内のすべての 0 のビットが 1 のビットに変換し、すべて 1 ビットが 0 のビットに変換結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="43bdd-116">This is a unary operator and produces a result in which all 0 bits in the source operand are converted to 1 bits and all 1 bits are converted to 0 bits.</span></span>|
|`<<<`|<span data-ttu-id="43bdd-117">ビットごとの左シフト演算子。</span><span class="sxs-lookup"><span data-stu-id="43bdd-117">Bitwise left-shift operator.</span></span> <span data-ttu-id="43bdd-118">結果は、最初のオペランドのビットを 2 番目のオペランドのビット数だけ左にシフトします。</span><span class="sxs-lookup"><span data-stu-id="43bdd-118">The result is the first operand with bits shifted left by the number of bits in the second operand.</span></span> <span data-ttu-id="43bdd-119">最下位の位置には、最上位の位置からシフトは循環しません。</span><span class="sxs-lookup"><span data-stu-id="43bdd-119">Bits shifted off the most significant position are not rotated into the least significant position.</span></span> <span data-ttu-id="43bdd-120">最下位ビットが 0 で埋められます。</span><span class="sxs-lookup"><span data-stu-id="43bdd-120">The least significant bits are padded with zeros.</span></span> <span data-ttu-id="43bdd-121">2 番目の引数の型は`int32`します。</span><span class="sxs-lookup"><span data-stu-id="43bdd-121">The type of the second argument is `int32`.</span></span>|
|`>>>`|<span data-ttu-id="43bdd-122">ビットごと右シフト演算子。</span><span class="sxs-lookup"><span data-stu-id="43bdd-122">Bitwise right-shift operator.</span></span> <span data-ttu-id="43bdd-123">結果は、最初のオペランドと 2 番目のオペランドのビット数だけ右にシフトするビットです。</span><span class="sxs-lookup"><span data-stu-id="43bdd-123">The result is the first operand with bits shifted right by the number of bits in the second operand.</span></span> <span data-ttu-id="43bdd-124">最上位の位置には、最下位の位置からシフトは循環しません。</span><span class="sxs-lookup"><span data-stu-id="43bdd-124">Bits shifted off the least significant position are not rotated into the most significant position.</span></span> <span data-ttu-id="43bdd-125">符号なし型の場合は、最上位ビットが 0 で埋められます。</span><span class="sxs-lookup"><span data-stu-id="43bdd-125">For unsigned types, the most significant bits are padded with zeros.</span></span> <span data-ttu-id="43bdd-126">署名された型の場合は、最上位ビットはものに埋められます。</span><span class="sxs-lookup"><span data-stu-id="43bdd-126">For signed types, the most significant bits are padded with ones.</span></span> <span data-ttu-id="43bdd-127">2 番目の引数の型は`int32`します。</span><span class="sxs-lookup"><span data-stu-id="43bdd-127">The type of the second argument is `int32`.</span></span>|

<span data-ttu-id="43bdd-128">ビットごとの演算子では、次の種類を使用できます: `byte`、 `sbyte`、 `int16`、 `uint16`、 `int32 (int)`、 `uint32`、 `int64`、 `uint64`、 `nativeint`、および`unativeint`です。</span><span class="sxs-lookup"><span data-stu-id="43bdd-128">The following types can be used with bitwise operators: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, and `unativeint`.</span></span>

## <a name="see-also"></a><span data-ttu-id="43bdd-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="43bdd-129">See Also</span></span>
[<span data-ttu-id="43bdd-130">シンボルと演算子のリファレンス</span><span class="sxs-lookup"><span data-stu-id="43bdd-130">Symbol and Operator Reference</span></span>](index.md)

[<span data-ttu-id="43bdd-131">算術演算子</span><span class="sxs-lookup"><span data-stu-id="43bdd-131">Arithmetic Operators</span></span>](arithmetic-operators.md)

[<span data-ttu-id="43bdd-132">ブール演算子</span><span class="sxs-lookup"><span data-stu-id="43bdd-132">Boolean Operators</span></span>](boolean-operators.md)


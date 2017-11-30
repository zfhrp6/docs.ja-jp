---
title: ".NET の型変換の表"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- widening conversions
- narrowing conversions
- type conversion, table
- converting types, narrowing conversions
- converting types, widening conversions
- base types, converting
- tables [.NET Framework], type conversions
- data types [.NET Framework], converting
ms.assetid: 0ea65c59-85eb-4a52-94ca-c36d3bd13058
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 327469f9a151b6ef7e1c42f6669c0a9dae7016fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="type-conversion-tables-in-net"></a><span data-ttu-id="effaa-102">.NET の型変換の表</span><span class="sxs-lookup"><span data-stu-id="effaa-102">Type Conversion Tables in .NET</span></span>
<span data-ttu-id="effaa-103">拡大変換は、1 つの型の値が、サイズが同じかそれ以上の別の型に変換されるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="effaa-103">Widening conversion occurs when a value of one type is converted to another type that is of equal or greater size.</span></span> <span data-ttu-id="effaa-104">縮小変換は、1 つの型の値が、サイズがより小さい別の型の値に変換されるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="effaa-104">A narrowing conversion occurs when a value of one type is converted to a value of another type that is of a smaller size.</span></span> <span data-ttu-id="effaa-105">このトピックの表は、両方の種類の変換の動作を示しています。</span><span class="sxs-lookup"><span data-stu-id="effaa-105">The tables in this topic illustrate the behaviors exhibited by both types of conversions.</span></span>  
  
## <a name="widening-conversions"></a><span data-ttu-id="effaa-106">拡大変換</span><span class="sxs-lookup"><span data-stu-id="effaa-106">Widening Conversions</span></span>  
 <span data-ttu-id="effaa-107">次の表では、情報を失うことがなく実行できる拡大変換について説明します。</span><span class="sxs-lookup"><span data-stu-id="effaa-107">The following table describes the widening conversions that can be performed without the loss of information.</span></span>  
  
|<span data-ttu-id="effaa-108">型</span><span class="sxs-lookup"><span data-stu-id="effaa-108">Type</span></span>|<span data-ttu-id="effaa-109">データ損失なしに次の型に変換可能</span><span class="sxs-lookup"><span data-stu-id="effaa-109">Can be converted without data loss to</span></span>|  
|----------|-------------------------------------------|  
|<xref:System.Byte>|<span data-ttu-id="effaa-110"><xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="effaa-110"><xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.SByte>|<span data-ttu-id="effaa-111"><xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="effaa-111"><xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int16>|<span data-ttu-id="effaa-112"><xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="effaa-112"><xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.UInt16>|<span data-ttu-id="effaa-113"><xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="effaa-113"><xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Char>|<span data-ttu-id="effaa-114"><xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="effaa-114"><xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int32>|<span data-ttu-id="effaa-115"><xref:System.Int64>、<xref:System.Double>、<xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="effaa-115"><xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.UInt32>|<span data-ttu-id="effaa-116"><xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="effaa-116"><xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int64>|<xref:System.Decimal>|  
|<xref:System.UInt64>|<xref:System.Decimal>|  
|<xref:System.Single>|<xref:System.Double>|  
  
 <span data-ttu-id="effaa-117">一部の拡大を変換<xref:System.Single>または<xref:System.Double>精度の損失が発生することができます。</span><span class="sxs-lookup"><span data-stu-id="effaa-117">Some widening conversions to <xref:System.Single> or <xref:System.Double> can cause a loss of precision.</span></span> <span data-ttu-id="effaa-118">次の表は、情報が失われる可能性のある拡大変換を示しています。</span><span class="sxs-lookup"><span data-stu-id="effaa-118">The following table describes the widening conversions that sometimes result in a loss of information.</span></span>  
  
|<span data-ttu-id="effaa-119">型</span><span class="sxs-lookup"><span data-stu-id="effaa-119">Type</span></span>|<span data-ttu-id="effaa-120">次の型に変換可能</span><span class="sxs-lookup"><span data-stu-id="effaa-120">Can be converted to</span></span>|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<span data-ttu-id="effaa-121"><xref:System.Single>, <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="effaa-121"><xref:System.Single>, <xref:System.Double></span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="effaa-122"><xref:System.Single>, <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="effaa-122"><xref:System.Single>, <xref:System.Double></span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="effaa-123"><xref:System.Single>, <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="effaa-123"><xref:System.Single>, <xref:System.Double></span></span>|  
  
## <a name="narrowing-conversions"></a><span data-ttu-id="effaa-124">縮小変換</span><span class="sxs-lookup"><span data-stu-id="effaa-124">Narrowing Conversions</span></span>  
 <span data-ttu-id="effaa-125">縮小変換<xref:System.Single>または<xref:System.Double>情報の損失が発生することができます。</span><span class="sxs-lookup"><span data-stu-id="effaa-125">A narrowing conversion to <xref:System.Single> or <xref:System.Double> can cause a loss of information.</span></span> <span data-ttu-id="effaa-126">ターゲット型がソースの大きさを正確に表現できない場合、結果の型は定数 `PositiveInfinity` または `NegativeInfinity` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="effaa-126">If the target type cannot properly express the magnitude of the source, the resulting type is set to the constant `PositiveInfinity` or `NegativeInfinity`.</span></span> <span data-ttu-id="effaa-127">`PositiveInfinity`正の数を 0 で除算した結果のときにも返されますの値、<xref:System.Single>または<xref:System.Double>の値を超える、`MaxValue`フィールドです。</span><span class="sxs-lookup"><span data-stu-id="effaa-127">`PositiveInfinity` results from dividing a positive number by zero and is also returned when the value of a <xref:System.Single> or <xref:System.Double> exceeds the value of the `MaxValue` field.</span></span> <span data-ttu-id="effaa-128">`NegativeInfinity`負の数を 0 で除算した結果のときにも返されますの値、<xref:System.Single>または<xref:System.Double>の値を下回る、`MinValue`フィールドです。</span><span class="sxs-lookup"><span data-stu-id="effaa-128">`NegativeInfinity` results from dividing a negative number by zero and is also returned when the value of a <xref:System.Single> or <xref:System.Double> falls below the value of the `MinValue` field.</span></span> <span data-ttu-id="effaa-129">変換、<xref:System.Double>を<xref:System.Single>されてしまう`PositiveInfinity`または`NegativeInfinity`です。</span><span class="sxs-lookup"><span data-stu-id="effaa-129">A conversion from a <xref:System.Double> to a <xref:System.Single> might result in `PositiveInfinity` or `NegativeInfinity`.</span></span>  
  
 <span data-ttu-id="effaa-130">その他のデータ型についても、縮小変換によって情報が失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="effaa-130">A narrowing conversion can also result in a loss of information for other data types.</span></span> <span data-ttu-id="effaa-131">ただし、<xref:System.OverflowException>変換される型の値が、ターゲット型の指定した範囲外である場合にスローされる`MaxValue`と`MinValue`フィールド、および変換がチェックされている場合、ランタイムに、ターゲットの値を確認してください型を超えないその`MaxValue`または`MinValue`です。</span><span class="sxs-lookup"><span data-stu-id="effaa-131">However, an <xref:System.OverflowException> is thrown if the value of a type that is being converted falls outside of the range specified by the target type's `MaxValue` and `MinValue` fields, and the conversion is checked by the runtime to ensure that the value of the target type does not exceed its `MaxValue` or `MinValue`.</span></span> <span data-ttu-id="effaa-132">実行される変換、<xref:System.Convert?displayProperty=nameWithType>クラスは常にこの方法で確認します。</span><span class="sxs-lookup"><span data-stu-id="effaa-132">Conversions that are performed with the <xref:System.Convert?displayProperty=nameWithType> class are always checked in this manner.</span></span>  
  
 <span data-ttu-id="effaa-133">次の表に、スローする変換、<xref:System.OverflowException>を使用して<xref:System.Convert?displayProperty=nameWithType>チェックしたすべての変換結果の型の定義された範囲内の変換対象の型の値がある場合またはします。</span><span class="sxs-lookup"><span data-stu-id="effaa-133">The following table lists conversions that throw an <xref:System.OverflowException> using <xref:System.Convert?displayProperty=nameWithType> or any checked conversion if the value of the type being converted is outside the defined range of the resulting type.</span></span>  
  
|<span data-ttu-id="effaa-134">型</span><span class="sxs-lookup"><span data-stu-id="effaa-134">Type</span></span>|<span data-ttu-id="effaa-135">次の型に変換可能</span><span class="sxs-lookup"><span data-stu-id="effaa-135">Can be converted to</span></span>|  
|----------|-------------------------|  
|<xref:System.Byte>|<xref:System.SByte>|  
|<xref:System.SByte>|<span data-ttu-id="effaa-136"><xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="effaa-136"><xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64></span></span>|  
|<xref:System.Int16>|<span data-ttu-id="effaa-137"><xref:System.Byte>、<xref:System.SByte>、<xref:System.UInt16></span><span class="sxs-lookup"><span data-stu-id="effaa-137"><xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16></span></span>|  
|<xref:System.UInt16>|<span data-ttu-id="effaa-138"><xref:System.Byte>、<xref:System.SByte>、<xref:System.Int16></span><span class="sxs-lookup"><span data-stu-id="effaa-138"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16></span></span>|  
|<xref:System.Int32>|<span data-ttu-id="effaa-139"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32></span><span class="sxs-lookup"><span data-stu-id="effaa-139"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32></span></span>|  
|<xref:System.UInt32>|<span data-ttu-id="effaa-140"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="effaa-140"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32></span></span>|  
|<xref:System.Int64>|<span data-ttu-id="effaa-141"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="effaa-141"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64></span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="effaa-142"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64></span><span class="sxs-lookup"><span data-stu-id="effaa-142"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64></span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="effaa-143"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="effaa-143"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
|<xref:System.Single>|<span data-ttu-id="effaa-144"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="effaa-144"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
|<xref:System.Double>|<span data-ttu-id="effaa-145"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="effaa-145"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="effaa-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="effaa-146">See Also</span></span>  
 <xref:System.Convert?displayProperty=nameWithType>  
 [<span data-ttu-id="effaa-147">.NET での型変換</span><span class="sxs-lookup"><span data-stu-id="effaa-147">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)

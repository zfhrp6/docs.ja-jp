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
# <a name="type-conversion-tables-in-net"></a>.NET の型変換の表
拡大変換は、1 つの型の値が、サイズが同じかそれ以上の別の型に変換されるときに発生します。 縮小変換は、1 つの型の値が、サイズがより小さい別の型の値に変換されるときに発生します。 このトピックの表は、両方の種類の変換の動作を示しています。  
  
## <a name="widening-conversions"></a>拡大変換  
 次の表では、情報を失うことがなく実行できる拡大変換について説明します。  
  
|型|データ損失なしに次の型に変換可能|  
|----------|-------------------------------------------|  
|<xref:System.Byte>|<xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.SByte>|<xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int16>|<xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.UInt16>|<xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Char>|<xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int32>|<xref:System.Int64>、<xref:System.Double>、<xref:System.Decimal>|  
|<xref:System.UInt32>|<xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int64>|<xref:System.Decimal>|  
|<xref:System.UInt64>|<xref:System.Decimal>|  
|<xref:System.Single>|<xref:System.Double>|  
  
 一部の拡大を変換<xref:System.Single>または<xref:System.Double>精度の損失が発生することができます。 次の表は、情報が失われる可能性のある拡大変換を示しています。  
  
|型|次の型に変換可能|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.UInt64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.Decimal>|<xref:System.Single>, <xref:System.Double>|  
  
## <a name="narrowing-conversions"></a>縮小変換  
 縮小変換<xref:System.Single>または<xref:System.Double>情報の損失が発生することができます。 ターゲット型がソースの大きさを正確に表現できない場合、結果の型は定数 `PositiveInfinity` または `NegativeInfinity` に設定されます。 `PositiveInfinity`正の数を 0 で除算した結果のときにも返されますの値、<xref:System.Single>または<xref:System.Double>の値を超える、`MaxValue`フィールドです。 `NegativeInfinity`負の数を 0 で除算した結果のときにも返されますの値、<xref:System.Single>または<xref:System.Double>の値を下回る、`MinValue`フィールドです。 変換、<xref:System.Double>を<xref:System.Single>されてしまう`PositiveInfinity`または`NegativeInfinity`です。  
  
 その他のデータ型についても、縮小変換によって情報が失われる可能性があります。 ただし、<xref:System.OverflowException>変換される型の値が、ターゲット型の指定した範囲外である場合にスローされる`MaxValue`と`MinValue`フィールド、および変換がチェックされている場合、ランタイムに、ターゲットの値を確認してください型を超えないその`MaxValue`または`MinValue`です。 実行される変換、<xref:System.Convert?displayProperty=nameWithType>クラスは常にこの方法で確認します。  
  
 次の表に、スローする変換、<xref:System.OverflowException>を使用して<xref:System.Convert?displayProperty=nameWithType>チェックしたすべての変換結果の型の定義された範囲内の変換対象の型の値がある場合またはします。  
  
|型|次の型に変換可能|  
|----------|-------------------------|  
|<xref:System.Byte>|<xref:System.SByte>|  
|<xref:System.SByte>|<xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>|  
|<xref:System.Int16>|<xref:System.Byte>、<xref:System.SByte>、<xref:System.UInt16>|  
|<xref:System.UInt16>|<xref:System.Byte>、<xref:System.SByte>、<xref:System.Int16>|  
|<xref:System.Int32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32>|  
|<xref:System.UInt32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>|  
|<xref:System.Int64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64>|  
|<xref:System.UInt64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>|  
|<xref:System.Decimal>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Single>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Double>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Convert?displayProperty=nameWithType>  
 [.NET での型変換](../../../docs/standard/base-types/type-conversion.md)

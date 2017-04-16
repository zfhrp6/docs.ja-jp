---
title: ".NET Framework における型変換の表 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "拡大変換"
  - "縮小変換"
  - "型変換、表"
  - "変換 (型を)、縮小変換"
  - "変換 (型を)、拡大変換"
  - "基本型、変換"
  - "表 [.NET Framework]、型変換"
  - "データ型 [.NET Framework]、変換"
ms.assetid: 0ea65c59-85eb-4a52-94ca-c36d3bd13058
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# .NET Framework における型変換の表
拡大変換は、ある型の値をそれよりサイズが大きいかまたは等しい別の型に変換するときに実行されます。  縮小変換は、ある型の値をそれよりサイズが小さい別の型の値に変換するときに実行されます。  このトピックの表では、この 2 種類の変換の動作を示します。  
  
## 拡大変換  
 情報を失わずに実行できる拡大変換について次の表にまとめます。  
  
|型|データを失わない変換後の型|  
|-------|-------------------|  
|<xref:System.Byte>|<xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.SByte>|<xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int16>|<xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.UInt16>|<xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Char>|<xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int32>|<xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.UInt32>|<xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int64>|<xref:System.Decimal>|  
|<xref:System.UInt64>|<xref:System.Decimal>|  
|<xref:System.Single>|<xref:System.Double>|  
  
 <xref:System.Single> または <xref:System.Double> への拡大変換では、精度が失われることがあります。  情報が失われる可能性のある拡大変換について次の表にまとめます。  
  
|型|変換後の型|  
|-------|-----------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.UInt64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.Decimal>|<xref:System.Single>, <xref:System.Double>|  
  
## 縮小変換  
 <xref:System.Single> または <xref:System.Double> への縮小変換では、情報が失われることがあります。  変換先の型が変換元の絶対値を正確に表現できない場合、結果の型は定数 `PositiveInfinity` または `NegativeInfinity` に設定されます。  `PositiveInfinity` の値は、正の数を 0 で除算した結果であり、<xref:System.Single> または <xref:System.Double> の値が `MaxValue` フィールドの値を上回った場合にも返されます。  `NegativeInfinity` の値は、負の数を 0 で除算した結果であり、<xref:System.Single> または <xref:System.Double> の値が `MinValue` フィールドの値を下回った場合にも返されます。  <xref:System.Double> から <xref:System.Single> に変換すると、結果が `PositiveInfinity` または `NegativeInfinity` になります。  
  
 ほかのデータ型の縮小変換でも、情報が失われることがあります。  ただし、変換結果の型の値が、変換先の型の `MaxValue` フィールドおよび `MinValue` フィールドで指定されている範囲外になる場合は <xref:System.OverflowException> がスローされ、変換先の型の値が `MaxValue` または `MinValue` を超えないことを保証するためにランタイムによってその変換がチェックされます。  <xref:System.Convert?displayProperty=fullName> クラスを使用して実行される変換は、必ずこの方法でチェックされます。  
  
 <xref:System.Convert?displayProperty=fullName> を使用した変換や、チェックを伴うその他の変換で、変換結果の型の値が結果の型で定義されている範囲外の値になる場合に <xref:System.OverflowException> がスローされるケースを次の表にまとめます。  
  
|型|変換後の型|  
|-------|-----------|  
|<xref:System.Byte>|<xref:System.SByte>|  
|<xref:System.SByte>|<xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>|  
|<xref:System.Int16>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16>|  
|<xref:System.UInt16>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>|  
|<xref:System.Int32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32>|  
|<xref:System.UInt32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>|  
|<xref:System.Int64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64>|  
|<xref:System.UInt64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>|  
|<xref:System.Decimal>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Single>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Double>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
  
## 参照  
 <xref:System.Convert?displayProperty=fullName>   
 [.NET Framework における型変換](../../../docs/standard/base-types/type-conversion.md)
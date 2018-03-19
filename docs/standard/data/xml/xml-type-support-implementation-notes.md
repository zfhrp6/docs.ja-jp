---
title: "XML 型サポートの実装に関するメモ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8c2706782ed1242ecdb5af1fdfab7a3f24e19236
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="xml-type-support-implementation-notes"></a>XML 型サポートの実装に関するメモ
このトピックでは、認識しておく必要があるいくつかの実装上の詳細について説明します。  
  
## <a name="list-mappings"></a>リストのマッピング  
 <xref:System.Collections.IList>、<xref:System.Collections.ICollection>、<xref:System.Collections.IEnumerable>、**Type[]**、<xref:System.String> 型は、XML スキーマ定義言語 (XSD) のリスト型を表現するために使用されます。  
  
## <a name="union-mappings"></a>ユニオンのマッピング  
 ユニオン型は <xref:System.Xml.Schema.XmlAtomicValue> 型または <xref:System.String> 型を使用して表現されます。 したがって、変換前の型または変換後の型は常に <xref:System.String> または <xref:System.Xml.Schema.XmlAtomicValue> のどちらかである必要があります。  
  
 <xref:System.Xml.Schema.XmlSchemaDatatype> オブジェクトがリスト型を表す場合、このオブジェクトは入力文字列値をリストまたは複数のオブジェクトに変換します。 <xref:System.Xml.Schema.XmlSchemaDatatype> がユニオン型を表す場合は、ユニオンのメンバーの型として入力値が解析されます。 解析が失敗した場合は、変換が成功するか他のメンバーの型がなくなるまで、ユニオンの次のメンバーを使用して変換が試行されます。変換を試行するメンバーの型がなくなると、例外がスローされます。  
  
## <a name="differences-between-clr-and-xml-data-types"></a>CLR 型と XML データ型の違い  
 CLR 型と XML データ型の間で発生する可能性のある不一致とその処理方法を次に示します。  
  
> [!NOTE]
>  `xs`にプレフィックスのマッピング、http://www.w3.org/2001/XMLSchemaと名前空間 URI。  
  
### <a name="systemtimespan-and-xsduration"></a>System.TimeSpan と xs:duration  
 `xs:duration` 型は、値は異なるが同等の継続時間値として、部分的な順序付けが行われます。 これは、たとえば 1 か月 (P1M) という `xs:duration` 型の値が、32 日 (P32D) より小さく、27 日 (P27D) より大きく、28 日、29 日または 30 日と同等であることを意味します。  
  
 <xref:System.TimeSpan> クラスは、この部分的な順序付けをサポートしません。 その代わりに、1 年および 1 か月に特定の日数 (それぞれ 365 日と 30 日) を使用します。  
  
 詳細については、`xs:duration`入力 W3C XML Schema Part 2 を参照してください: Datatypes Recommendation 』http://www.w3.org/TR/xmlschema-2/です。  
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a>xs:time、グレオリオ暦の日付、および System.DateTime  
 `xs:time` 値が <xref:System.DateTime> オブジェクトにマップされている場合、<xref:System.DateTime.MinValue> フィールドは <xref:System.DateTime> オブジェクトの日付プロパティ (<xref:System.DateTime.Year%2A>、<xref:System.DateTime.Month%2A>、<xref:System.DateTime.Day%2A> など) を可能な最小の <xref:System.DateTime> 値に初期化するために使用されます。  
  
 同様に、`xs:gMonth`、`xs:gDay`、`xs:gYear`、`xs:gYearMonth`、および `xs:gMonthDay` のインスタンスは、<xref:System.DateTime> オブジェクトにマップされます。 <xref:System.DateTime> オブジェクトの未使用のプロパティは、<xref:System.DateTime.MinValue> の値で初期化されます。  
  
> [!NOTE]
>  内容が <xref:System.DateTime.Year%2A?displayProperty=nameWithType> として型指定されている場合は、`xs:gMonthDay` 値は信頼できません。 この場合、<xref:System.DateTime.Year%2A?displayProperty=nameWithType> 値は常に 1,904 に設定されています。  
  
### <a name="xsanyuri-and-systemuri"></a>xs:anyURI および System.Uri  
 相対 URI を表す `xs:anyURI` のインスタンスが <xref:System.Uri> にマップされている場合、<xref:System.Uri> オブジェクトには基本 URI がありません。  
  
## <a name="see-also"></a>関連項目  
 [System.Xml クラスでの型のサポート](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)

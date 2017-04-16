---
title: "XmlSchemaSet による XML スキーマ (XSD) 検証 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# XmlSchemaSet による XML スキーマ (XSD) 検証
XML ドキュメントは、<xref:System.Xml.Schema.XmlSchemaSet> の XML スキーマ定義言語 \(XSD\) スキーマを基準として検証できます。  
  
## XML ドキュメントの検証  
 XML ドキュメントは、<xref:System.Xml.XmlReader> クラスの <xref:System.Xml.XmlReader.Create%2A> メソッドを使用して検証します。  XML ドキュメントを検証するには、XML ドキュメントの検証に使用する XML スキーマ定義言語 \(XSD\) スキーマを持つ <xref:System.Xml.XmlReaderSettings> オブジェクトを作成します。  
  
> [!NOTE]
>  [LINQ to XML](../../../../ocs/visual-basic/programming-guide/concepts/linq/linq-to-xml.md) を使用する際、<xref:System.Xml.Schema> 名前空間に含まれる拡張メソッドによって、XSD ファイルを基準として XML ツリーを簡単に検証することができます。  LINQ to XML を使用した XML ドキュメントの検証に関する詳細については、「[How to: Validate Using XSD](../Topic/How%20to:%20Validate%20Using%20XSD%20\(LINQ%20to%20XML\).md)」を参照してください。  
  
 独立したスキーマまたはスキーマのセット \(<xref:System.Xml.Schema.XmlSchemaSet> を使用\) を <xref:System.Xml.Schema.XmlSchemaSet> に追加するには、そのどちらかを <xref:System.Xml.Schema.XmlSchemaSet> の <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> メソッドにパラメーターとして渡します。  ドキュメントを検証する際には、ドキュメントの対象名前空間がスキーマ セット内のスキーマの対象名前空間と一致している必要があります。  
  
 XML ドキュメントのサンプルを次に示します。  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 XML ドキュメントのサンプルを検証するスキーマを次に示します。  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 以下のコード サンプルでは、<xref:System.Xml.XmlReaderSettings> オブジェクトの <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> プロパティに上記のスキーマが追加されます。  <xref:System.Xml.XmlReaderSettings> オブジェクトは、上記の XML ドキュメントを検証する <xref:System.Xml.XmlReader> オブジェクトの <xref:System.Xml.XmlReader.Create%2A> メソッドにパラメーターとして渡されます。  
  
 <xref:System.Xml.XmlReaderSettings> オブジェクトの <xref:System.Xml.XmlReaderSettings.ValidationType%2A> プロパティが `Schema` に設定されて、<xref:System.Xml.XmlReader> オブジェクトの <xref:System.Xml.XmlReader.Create%2A> メソッドによる XML ドキュメントの検証が行われます。  XML のドキュメントおよびスキーマの検証中に発見されたエラーによって発生する <xref:System.Xml.Schema.XmlSeverityType> イベントまたは <xref:System.Xml.Schema.XmlSeverityType> イベントを処理するために、<xref:System.Xml.XmlReaderSettings> オブジェクトに <xref:System.Xml.Schema.ValidationEventHandler> を追加します。  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## 参照  
 [スキーマをコンパイルするための XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)   
 [XML スキーマの使用](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
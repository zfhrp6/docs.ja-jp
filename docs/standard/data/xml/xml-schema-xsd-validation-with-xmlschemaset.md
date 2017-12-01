---
title: "XmlSchemaSet による XML スキーマ (XSD) 検証"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a6cf857ccecbdac88453fd1fba6e93d609196b1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a>XmlSchemaSet による XML スキーマ (XSD) 検証
XML ドキュメントは、<xref:System.Xml.Schema.XmlSchemaSet> の XML スキーマ定義言語 (XSD) スキーマを基準として検証できます。  
  
## <a name="validating-xml-documents"></a>XML ドキュメントの検証  
 XML ドキュメントは、<xref:System.Xml.XmlReader.Create%2A> クラスの <xref:System.Xml.XmlReader> メソッドを使用して検証します。 XML ドキュメントを検証するには、XML ドキュメントの検証に使用する XML スキーマ定義言語 (XSD) スキーマを持つ <xref:System.Xml.XmlReaderSettings> オブジェクトを作成します。  
  
> [!NOTE]
>  <xref:System.Xml.Schema>名前空間には、簡単に使用する場合に、XSD ファイルに対して XML ツリーを検証する拡張メソッドが含まれています。 [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)です。 LINQ to XML による XML ドキュメントの検証の詳細については、次を参照してください。[する方法: 検証を使用して XSD](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b)です。  
  
 独立したスキーマまたはスキーマのセット (<xref:System.Xml.Schema.XmlSchemaSet> を使用) を <xref:System.Xml.Schema.XmlSchemaSet> に追加するには、そのどちらかを <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> の <xref:System.Xml.Schema.XmlSchemaSet> メソッドにパラメーターとして渡します。 ドキュメントを検証する際には、ドキュメントの対象名前空間がスキーマ セット内のスキーマの対象名前空間と一致している必要があります。  
  
 XML ドキュメントのサンプルを次に示します。  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 XML ドキュメントのサンプルを検証するスキーマを次に示します。  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 以下のコード サンプルでは、<xref:System.Xml.Schema.XmlSchemaSet> オブジェクトの <xref:System.Xml.XmlReaderSettings.Schemas%2A><xref:System.Xml.XmlReaderSettings> プロパティに上記のスキーマが追加されます。 <xref:System.Xml.XmlReaderSettings> オブジェクトは、上記の XML ドキュメントを検証する <xref:System.Xml.XmlReader.Create%2A> オブジェクトの <xref:System.Xml.XmlReader> メソッドにパラメーターとして渡されます。  
  
 <xref:System.Xml.XmlReaderSettings.ValidationType%2A> オブジェクトの <xref:System.Xml.XmlReaderSettings> プロパティが `Schema` に設定されて、<xref:System.Xml.XmlReader.Create%2A> オブジェクトの <xref:System.Xml.XmlReader> メソッドによる XML ドキュメントの検証が行われます。 XML のドキュメントおよびスキーマの検証中に発見されたエラーによって発生する <xref:System.Xml.Schema.ValidationEventHandler> イベントまたは <xref:System.Xml.XmlReaderSettings> イベントを処理するために、<xref:System.Xml.Schema.XmlSeverityType.Warning> オブジェクトに <xref:System.Xml.Schema.XmlSeverityType.Error> を追加します。  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 [スキーマのコンパイルのための XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [XML スキーマの操作](../../../../docs/standard/data/xml/working-with-xml-schemas.md)

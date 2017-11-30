---
title: "XmlSchemaCollection スキーマのコンパイル"
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
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 901c3fdc8fdc80cc7c3bf13170646de857a5e009
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xmlschemacollection-schema-compilation"></a>XmlSchemaCollection スキーマのコンパイル
**XmlSchemaCollection**がキャッシュまたはライブラリ Xml-data Reduced (XDR) スキーマと XML スキーマ定義言語 (XSD) スキーマを格納および検証できます。 **XmlSchemaCollection**ファイルまたは URL からそれらにアクセスする代わりに、メモリ内のスキーマをキャッシュすることによってパフォーマンスが向上します。  
  
> [!NOTE]
>  ただし、 **XmlSchemaCollection**クラスは、XDR スキーマと XML スキーマ、メソッドおよびプロパティを受け取るかを返しますの両方を格納、 **XmlSchema**オブジェクトをサポートしている XML スキーマのみです。  
  
> [!IMPORTANT]
>  <xref:System.Xml.Schema.XmlSchemaCollection> クラスは廃止されており、<xref:System.Xml.Schema.XmlSchemaSet> クラスに置き換えられています。 詳細については、<xref:System.Xml.Schema.XmlSchemaSet>クラス」を参照して[スキーマのコンパイルのための XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)です。  
  
## <a name="add-schemas-to-the-collection"></a>コレクションへのスキーマの追加  
 使用してコレクションにスキーマが読み込まれて、**追加**メソッドの**XmlSchemaCollection**時に、スキーマは名前空間 URI に関連付けられています。 XML スキーマの場合、通常、この名前空間 URI がスキーマのターゲット名前空間になります。 また、XDR スキーマの場合は、この名前空間 URI は、スキーマがコレクションに追加されたときに指定された名前空間です。  
  
## <a name="check-for-a-schema-in-the-collection"></a>コレクション内のスキーマの確認  
 使用して、スキーマがコレクション内かどうかを確認することができます、 **Contains**メソッドです。 **Contains**メソッドは、いずれか、 **XmlSchema** (XML スキーマおよび XDR スキーマ) のスキーマに関連付けられているオブジェクト (XML スキーマ専用) または名前空間 URI を表す文字列。  
  
## <a name="retrieve-a-schema-from-the-collection"></a>コレクションからのスキーマの取得  
 使用して、コレクションからスキーマを取得することができます、**項目**プロパティです。 **項目**プロパティが、スキーマでは、通常その対象名前空間に関連付けられた URI 名前空間を表す文字列を受け取り、返します、 **XmlSchema**オブジェクト。 **項目**プロパティは XML スキーマにのみ適用されます。 XDR スキーマの場合は、使用できるオブジェクト モデルがないため、戻り値は常に null 参照です。  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a>XmlSchemaCollection を使用した XML ドキュメントの検証  
 使用して XML インスタンス ドキュメントを検証することができます、 **XmlSchemaCollection**作成することで、 **XmlSchemaCollection**オブジェクト、スキーマをコレクションに追加し、設定、**スキーマ**プロパティを**XmlValidatingReader**を割り当てる、作成した**XmlSchemaCollection**を**XmlValidatingReader**です。  
  
### <a name="improved-performance"></a>パフォーマンスの向上  
 お勧め、同一のスキーマに対して 1 つ以上のドキュメントを検証する場合を使用すること、 **XmlSchemaCollection**メモリ内のスキーマをキャッシュすることによってパフォーマンスが向上が用意されているためです。  
  
 次のコード例を作成、 **XmlSchemaCollection**オブジェクトは、このコレクションにスキーマを追加し、設定、**スキーマ**プロパティです。  
  
```vb  
Dim tr as XmlTextReader = new XmlTextReader("Books.xml")  
Dim vr as XmlValidatingReader = new XmlValidatingReader(tr)  
Dim xsc as XmlSchemaCollection = new XmlSchemaCollection  
xsc.Add("urn:bookstore-schema", "Books.xsd")  
vr.Schemas.Add(xsc)  
```  
  
```csharp  
XmlTextReader tr = new XmlTextReader("Books.xml");  
XmlValidatingReader vr = new XmlValidatingReader(tr);  
XmlSchemaCollection xsc = new XmlSchemaCollection();  
xsc.Add("urn:bookstore-schema", "Books.xsd");    
vr.Schemas.Add(xsc);  
```  
  
## <a name="see-also"></a>関連項目  
 [XmlSchemaCollection を使用した XDR 検証](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)  
 [XmlSchemaCollection を使用した XML スキーマ (XSD) 検証](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)

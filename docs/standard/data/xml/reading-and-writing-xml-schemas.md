---
title: "XML スキーマの読み取りと書き込み"
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
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: aaf63acbb58fd86f7fa9a5dc3dce7508d90cfada
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="reading-and-writing-xml-schemas"></a>XML スキーマの読み取りと書き込み
スキーマ オブジェクト モデル (SOM) API を使用すると、ファイルまたは他のソースから XML スキーマ定義言語 (XSD) スキーマを読み取ったり、書き込んだりできます。また、W3C (World Wide Web Consortium) 勧告『XML Schema』で定義された構造に割り当てられた <xref:System.Xml.Schema?displayProperty=nameWithType> 名前空間のクラスを使用してメモリ内に XML スキーマを作成することもできます。  
  
## <a name="reading-and-writing-xml-schemas"></a>XML スキーマの読み取りと書き込み  
 <xref:System.Xml.Schema.XmlSchema> クラスでは、<xref:System.Xml.Schema.XmlSchema.Read%2A> メソッドおよび <xref:System.Xml.Schema.XmlSchema.Write%2A> メソッドを利用して XML スキーマの読み取りと書き込みを行うことができます。 <xref:System.Xml.Schema.XmlSchema.Read%2A> メソッドは XML スキーマを表す <xref:System.Xml.Schema.XmlSchema> オブジェクトを返し、オプションの <xref:System.Xml.Schema.ValidationEventHandler> をパラメーターとして受け取って XML スキーマの読み取り時に発生するスキーマ検証に関する警告とエラーを処理します。  
  
 <xref:System.Xml.Schema.XmlSchema.Write%2A> メソッドは <xref:System.IO.Stream>、<xref:System.IO.TextWriter> および <xref:System.Xml.XmlWriter> オブジェクトに XML スキーマを書き込んで、オプションで <xref:System.Xml.XmlNamespaceManager> オブジェクトをパラメーターとして受け取ることができます。 <xref:System.Xml.XmlNamespaceManager> は、XML スキーマ内で検出される名前空間の処理に使用されます。 詳細については、<xref:System.Xml.XmlNamespaceManager>クラスを参照してください[XML ドキュメント内の名前空間を管理する](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)です。  
  
 次のコード サンプルでは、XML スキーマのファイルからの読み込みとファイルへの書き込みを説明します。 このコード サンプルは、`example.xsd`<xref:System.Xml.Schema.XmlSchema> メソッドを使用して `static` オブジェクトに <xref:System.Xml.Schema.XmlSchema.Read%2A> ファイルを読み込み、その後、このファイルをコンソールに出力して新しい `new.xsd` ファイルに書き込みます。 また、このコード サンプルでは、<xref:System.Xml.Schema.ValidationEventHandler>`static` メソッドに <xref:System.Xml.Schema.XmlSchema.Read%2A> をパラメーターとして指定して、XML スキーマを読み込む際に検出されるスキーマ検証時の警告やエラーの処理を行います。 <xref:System.Xml.Schema.ValidationEventHandler> を指定しないと (`null`)、警告やエラーは報告されません。  
  
 [!code-cpp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaReadWriteExample/CPP/XmlSchemaReadWriteExample.cpp#1)]
 [!code-csharp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaReadWriteExample/CS/XmlSchemaReadWriteExample.cs#1)]
 [!code-vb[XmlSchemaReadWriteExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaReadWriteExample/VB/XmlSchemaReadWriteExample.vb#1)]  
  
 この例は、入力として `example.xsd` を使用します。  
  
```xml  
<?xml version="1.0"?>  
<xs:schema id="play" targetNamespace="http://tempuri.org/play.xsd" elementFormDefault="qualified" xmlns="http://tempuri.org/play.xsd" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name='myShoeSize'>  
        <xs:complexType>  
            <xs:simpleContent>  
                <xs:extension base='xs:decimal'>  
                    <xs:attribute name='sizing' type='xs:string' />  
                </xs:extension>  
            </xs:simpleContent>  
        </xs:complexType>  
    </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a>関連項目  
 [XML スキーマ オブジェクト モデルの概要](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [XML スキーマの作成](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [XML スキーマの走査](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [XML スキーマの編集](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [インクルードまたは XML スキーマのインポート](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [スキーマのコンパイルのための XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [スキーマ コンパイル後の Infoset](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)  
 [XML ドキュメントでの名前空間の管理](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)

---
title: "XML ドキュメントからのスキーマの推論 | Microsoft Docs"
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
ms.assetid: f3d97d53-614d-4a04-a174-87965b7405f6
caps.latest.revision: 2
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 2
---
# XML ドキュメントからのスキーマの推論
このトピックでは、<xref:System.Xml.Schema.XmlSchemaInference> クラスを使用して、XML ドキュメントの構造から XML スキーマ定義言語 \(XSD\) スキーマを推論する方法を説明します。  
  
## スキーマの推論プロセス  
 <xref:System.Xml.Schema?displayProperty=fullName> 名前空間の <xref:System.Xml.Schema.XmlSchemaInference> クラスを使用して、XML ドキュメントの構造から 1 つ以上の XML スキーマ定義言語 \(XSD\) スキーマを生成できます。  生成されるスキーマは、元の XML ドキュメントの検証に使用できます。  
  
 XML ドキュメントは <xref:System.Xml.Schema.XmlSchemaInference> クラスによって処理されます。<xref:System.Xml.Schema.XmlSchemaInference> クラスは、XML ドキュメント上の要素と属性を定義するスキーマ コンポーネントに関する推測を行います。  <xref:System.Xml.Schema.XmlSchemaInference> クラスは、特定の要素または属性について最も限定的な型を推論することにより、制限された方法でスキーマ コンポーネントを推論します。  XML ドキュメントに関する情報の蓄積が進むほど、より限定度の低い型が推論されることで、制約が緩和されます。  最も限定度が低い推論可能な型は `xs:string` です。  
  
 たとえば、次の XML ドキュメントを見てみましょう。  
  
```  
<parent attribute1="6">  
    <child>One</child>  
    <child>Two</child>  
</parent>  
<parent attribute1="A">  
```  
  
 上の例で `attribute1` 属性の値 `6` が <xref:System.Xml.Schema.XmlSchemaInference> プロセスによって検出されると、この属性は `xs:unsignedByte` 型であると想定されます。  2 番目の `parent` 要素が <xref:System.Xml.Schema.XmlSchemaInference> プロセスによって検出されると、`attribute1` 属性の値が `A` であるため、型が `xs:string` に変更され、制限が緩和されます。  同様に、2 番目の親要素が子要素を持っていないため、スキーマで推論されるすべての `child` 要素の `minOccurs` 属性が `minOccurs="0"` に緩和されます。  
  
## XML ドキュメントからのスキーマの推論  
 <xref:System.Xml.Schema.XmlSchemaInference> クラスでは、2 つのオーバーロードされた <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドを使用して XML ドキュメントからスキーマを推論します。  
  
 最初の <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=fullName> メソッドは、XML ドキュメントに基づくスキーマの作成に使用されます。  2 番目の <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=fullName> メソッドは、複数の XML ドキュメントを記述するスキーマの推論に使用されます。  たとえば、複数の XML ドキュメントを 1 つずつ <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=fullName> メソッドに渡すことで、XML ドキュメントのセット全体を記述する 1 つのスキーマを生成できます。  
  
 最初の <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=fullName> メソッドは、<xref:System.Xml.XmlReader> オブジェクトに含まれている XML ドキュメントからスキーマを推論し、推論されたスキーマが含まれる <xref:System.Xml.Schema.XmlSchemaSet> オブジェクトを返します。  2 番目の <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=fullName> メソッドは、<xref:System.Xml.Schema.XmlSchemaSet> オブジェクトを対象として、<xref:System.Xml.XmlReader> オブジェクトに含まれている XML ドキュメントと同じ対象の名前空間を持つスキーマを検索し、既存のスキーマを限定し、推論されたスキーマが含まれる <xref:System.Xml.Schema.XmlSchemaSet> オブジェクトを返します。  
  
 限定されたスキーマに加えられた変更は、XML ドキュメントで検出された新しい構造に基づいています。  たとえば、XML ドキュメントが詳細に検討されるときは、検出されるデータ型が想定され、その想定に基づいてスキーマが作成されます。  しかし、2 回目の推論で検出されたデータが最初の想定と異なっている場合は、スキーマが限定されます。  次の例は限定のプロセスを示しています。  
  
 [!code-cpp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaInferenceExamples/CPP/XmlSchemaInferenceExamples.cpp#4)]
 [!code-csharp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaInferenceExamples/CS/XmlSchemaInferenceExamples.cs#4)]
 [!code-vb[XmlSchemaInferenceExamples#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaInferenceExamples/VB/XmlSchemaInferenceExamples.vb#4)]  
  
 この例では、次に示す `item1.xml` というファイルを最初の入力として受け取ります。  
  
 [!code-xml[XmlSchemaInferenceExamples#13](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item1.xml#13)]  
  
 この例では、さらに `item2.xml` というファイルを 2 番目の入力として受け取ります。  
  
 [!code-xml[XmlSchemaInferenceExamples#14](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item2.xml#14)]  
  
 最初の XML ドキュメントで `productID` 属性が検出されると、値 `123456789` は `xs:unsignedInt` 型であると想定されます。  しかし、2 番目の XML ドキュメントが読み取られ、値 `A53-246` が検出されると、`xs:unsignedInt` 型だとは想定できなくなります。  そこで、スキーマは限定され、`productID` の型が `xs:string` に変更されます。  さらに、2 番目の XML ドキュメントに `supplierID` 要素が含まれていないため、`supplierID` 要素の `minOccurs` 属性が `0` に設定されます。  
  
 次に示すのは、最初の XML ドキュメントから推論されたスキーマです。  
  
 [!code-xml[XmlSchemaInferenceExamples#15](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema1.xml#15)]  
  
 次に示すのは、最初の XML ドキュメントから推論され、2 番目の XML ドキュメントによって限定されたスキーマです。  
  
 [!code-xml[XmlSchemaInferenceExamples#16](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema2.xml#16)]  
  
## インライン スキーマ  
 <xref:System.Xml.Schema.XmlSchemaInference> プロセスの実行中にインライン XML スキーマ定義言語 \(XSD\) スキーマが検出されると、<xref:System.Xml.Schema.XmlSchemaInferenceException> がスローされます。  たとえば、次のインライン スキーマが検出されると、<xref:System.Xml.Schema.XmlSchemaInferenceException> がスローされます。  
  
```  
<root xmlns:ex="http://www.contoso.com" xmlns="http://www.tempuri.org">  
    <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://www.contoso.com">  
        <xs:element name="Contoso" type="xs:normalizedString" />  
    </xs:schema>  
    <ex:Contoso>Test</ex:Contoso>  
</root>  
```  
  
## 限定できないスキーマ  
 限定を目的として型を渡されたときに、XML スキーマ定義言語 \(XSD\) スキーマの <xref:System.Xml.Schema.XmlSchemaInference> プロセスが処理できず、例外をスローする W3C XML スキーマ構造があります。  最上位のコンポジターがシーケンス以外のものである複合型がその例です。  スキーマ オブジェクト モデル \(SOM\) では、<xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> プロパティが <xref:System.Xml.Schema.XmlSchemaSequence> のインスタンスでない <xref:System.Xml.Schema.XmlSchemaComplexType> がそれに相当します。  
  
## 参照  
 <xref:System.Xml.Schema.XmlSchemaInference>   
 [XML スキーマ オブジェクト モデル \(SOM\)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)   
 [XML スキーマの推論](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)   
 [スキーマのノード型および構造を推論するときの規則](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)   
 [単純型を推論するときの規則](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)
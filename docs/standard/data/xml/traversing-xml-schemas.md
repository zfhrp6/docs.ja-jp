---
title: "XML スキーマの走査 | Microsoft Docs"
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
ms.assetid: cce69574-5861-4a30-b730-2e18d915d8ee
caps.latest.revision: 2
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 2
---
# XML スキーマの走査
スキーマ オブジェクト モデル \(SOM\) API を使用して XML スキーマを走査すると、SOM に格納されている要素、属性、および型にアクセスできます。  また、SOM API を使用して XML スキーマを編集する際には、最初に SOM に読み込まれた XML スキーマを走査します。  
  
## XML スキーマの走査  
 <xref:System.Xml.Schema.XmlSchema> クラスの次のプロパティを使用すると、XML スキーマに追加されたすべてのグローバル要素のコレクションにアクセスできます。  
  
|プロパティ|コレクションまたは配列に格納されているオブジェクトの型|  
|-----------|---------------------------------|  
|<xref:System.Xml.Schema.XmlSchema.Elements%2A>|<xref:System.Xml.Schema.XmlSchemaElement>|  
|<xref:System.Xml.Schema.XmlSchema.Attributes%2A>|<xref:System.Xml.Schema.XmlSchemaAttribute>|  
|<xref:System.Xml.Schema.XmlSchema.AttributeGroups%2A>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|  
|<xref:System.Xml.Schema.XmlSchema.Groups%2A>|<xref:System.Xml.Schema.XmlSchemaGroup>|  
|<xref:System.Xml.Schema.XmlSchema.Includes%2A>|<xref:System.Xml.Schema.XmlSchemaExternal>、<xref:System.Xml.Schema.XmlSchemaInclude>、<xref:System.Xml.Schema.XmlSchemaImport>、または <xref:System.Xml.Schema.XmlSchemaRedefine>|  
|<xref:System.Xml.Schema.XmlSchema.Items%2A>|<xref:System.Xml.Schema.XmlSchemaObject> \(グローバル レベルのすべての要素、属性、および型にアクセスできる\)|  
|<xref:System.Xml.Schema.XmlSchema.Notations%2A>|<xref:System.Xml.Schema.XmlSchemaNotation>|  
|<xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A>|<xref:System.Xml.Schema.XmlSchemaType>, <xref:System.Xml.Schema.XmlSchemaSimpleType>, <xref:System.Xml.Schema.XmlSchemaComplexType>|  
|<xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A>|<xref:System.Xml.XmlAttribute> \(スキーマの名前空間に属さない属性にアクセスできる\)|  
  
> [!NOTE]
>  上記の表に記載されているすべてのプロパティ \(<xref:System.Xml.Schema.XmlSchema.Items%2A> プロパティを除く\) は、スキーマのコンパイル後の情報セット \(PSCI\) プロパティで、スキーマがコンパイルされるまで使用できません。  <xref:System.Xml.Schema.XmlSchema.Items%2A> プロパティは、スキーマのコンパイル前のプロパティで、スキーマがコンパイルされる前に使用できます。このプロパティを使用すると、グローバル レベルのすべての要素、属性、および型にアクセスできます。  
>   
>  <xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A> プロパティを使用すると、スキーマの名前空間に属さないすべての属性にアクセスできます。  これらの属性はスキーマ プロセッサで処理されません。  
  
 以下のコード サンプルでは、「[XML スキーマの作成](../../../../docs/standard/data/xml/building-xml-schemas.md)」で作成されたカスタム スキーマの走査の例を示します。  このコード サンプルは、上記のコレクションを使用してスキーマを走査し、スキーマのすべての要素と属性をコンソールに出力する例を示します。  
  
 このサンプルでは、次の手順でカスタム スキーマの走査を行います。  
  
1.  カスタム スキーマを新しい <xref:System.Xml.Schema.XmlSchemaSet> オブジェクトに追加し、コンパイルします。  スキーマの読み取りまたはコンパイル時に発生するスキーマ検証に関する警告とエラーは、<xref:System.Xml.Schema.ValidationEventHandler> デリゲートで処理されます。  
  
2.  <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> プロパティを反復処理して、<xref:System.Xml.Schema.XmlSchemaSet> からコンパイルされた <xref:System.Xml.Schema.XmlSchema> オブジェクトを取得します。  スキーマはコンパイルされているため、スキーマのコンパイル後の情報セット \(PSCI\) プロパティにアクセスできます。  
  
3.  各要素の名前をコンソールに出力するスキーマ コンパイル後の <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=fullName> コレクションの <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> コレクションで、各 <xref:System.Xml.Schema.XmlSchemaElement> を反復処理します。  
  
4.  <xref:System.Xml.Schema.XmlSchemaComplexType> クラスを使用して `Customer` 要素の複合型を取得します。  
  
5.  複合型に何らかの属性がある場合、それぞれの <xref:System.Xml.Schema.XmlSchemaAttribute> を列挙する <xref:System.Collections.IDictionaryEnumerator> を取得して、その名前をコンソールに出力します。  
  
6.  <xref:System.Xml.Schema.XmlSchemaSequence> クラスを使用して、複合型の sequence のパーティクルを取得します。  
  
7.  各子要素の名前をコンソールに出力する <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=fullName> コレクション内で、それぞれの <xref:System.Xml.Schema.XmlSchemaElement> を反復処理します。  
  
 完全なコード サンプルを次に示します。  
  
 [!code-cpp[XmlSchemaTraverseExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaTraverseExample/CPP/XmlSchemaTraverseExample.cpp#1)]
 [!code-csharp[XmlSchemaTraverseExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaTraverseExample/CS/XmlSchemaTraverseExample.cs#1)]
 [!code-vb[XmlSchemaTraverseExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaTraverseExample/VB/XmlSchemaTraverseExample.vb#1)]  
  
 <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A?displayProperty=fullName> プロパティには、<xref:System.Xml.Schema.XmlSchemaSimpleType> \(ユーザー定義の単純型または複合型の場合は <xref:System.Xml.Schema.XmlSchemaComplexType>\) を使用できます。  また、W3C 勧告『XML Schema』で定義されている組み込みデータ型の場合には、<xref:System.Xml.Schema.XmlSchemaDatatype> を使用することもできます。  カスタム スキーマの場合、`Customer` 要素の <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> は <xref:System.Xml.Schema.XmlSchemaComplexType> で、`FirstName` 要素および `LastName` 要素は <xref:System.Xml.Schema.XmlSchemaSimpleType> です。  
  
 「[XML スキーマの作成](../../../../docs/standard/data/xml/building-xml-schemas.md)」のコード サンプルでは、<xref:System.Xml.Schema.XmlSchemaComplexType.Attributes%2A?displayProperty=fullName> コレクションを使用して、`Customer` 要素に属性 `CustomerId` を追加しました。  これは、スキーマのコンパイル前のプロパティです。  対応するスキーマのコンパイル後の情報セット プロパティは、<xref:System.Xml.Schema.XmlSchemaComplexType.AttributeUses%2A?displayProperty=fullName> コレクションで、複合型のすべての属性 \(型の派生を通じて継承される属性を含む\) を持っています。  
  
## 参照  
 [XML スキーマ オブジェクト モデルの概要](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)   
 [XML スキーマの読み取りと書き込み](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)   
 [XML スキーマの作成](../../../../docs/standard/data/xml/building-xml-schemas.md)   
 [XML スキーマの編集](../../../../docs/standard/data/xml/editing-xml-schemas.md)   
 [XML スキーマのインクルードまたはインポート](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)   
 [スキーマをコンパイルするための XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)   
 [スキーマのコンパイル後の情報セット](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
---
title: "XML スキーマの作成 | Microsoft Docs"
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
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
caps.latest.revision: 2
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 2
---
# XML スキーマの作成
<xref:System.Xml.Schema?displayProperty=fullName> 名前空間のクラスは、W3C \(World Wide Web Consortium\) 勧告『XML Schema』で定義された構造に割り当てられ、メモリ内に XML スキーマを作成する場合に使用できます。  
  
## XML スキーマの作成  
 以下のコード サンプルでは、SOM API を使用してカスタム XML スキーマをメモリ内に作成します。  
  
### 要素と属性の作成  
 このコード サンプルでは、カスタム スキーマを最初から作成するため、子要素、属性、およびそれらに対応する型を作成した後で最上位要素を作成します。  
  
 以下のコード サンプルでは、SOM の <xref:System.Xml.Schema.XmlSchemaElement> クラスおよび <xref:System.Xml.Schema.XmlSchemaAttribute> クラスを使用して、カスタム スキーマの `CustomerId` 属性に加え、`FirstName` 要素および `LastName` 要素を作成します。  XML スキーマの `<xs:element />` 要素および `<xs:attribute />` 要素の name 属性に対応する <xref:System.Xml.Schema.XmlSchemaElement> クラスおよび <xref:System.Xml.Schema.XmlSchemaAttribute> クラスの <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> プロパティを除いて、このスキーマで使用できる他のすべての属性 \(`defaultValue`、`fixedValue`、`form` など\) には、<xref:System.Xml.Schema.XmlSchemaElement> クラスおよび <xref:System.Xml.Schema.XmlSchemaAttribute> クラスに対応するプロパティが存在します。  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### スキーマの型の作成  
 要素および属性のコンテンツは、その型によって定義されます。  組み込みのスキーマの型を持つ要素と属性を作成するには、<xref:System.Xml.XmlQualifiedName> クラスを使用する組み込みの修飾名を使用して、<xref:System.Xml.Schema.XmlSchemaElement> クラスまたは <xref:System.Xml.Schema.XmlSchemaAttribute> クラスの <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> プロパティを設定します。  要素と属性のユーザー定義型を作成するには、<xref:System.Xml.Schema.XmlSchemaSimpleType> または <xref:System.Xml.Schema.XmlSchemaComplexType> クラスを使用して単純型または複合型を新しく作成します。  
  
> [!NOTE]
>  要素または属性の匿名の子である名前のない単純型または複合型 \(属性に適用されるのは単純型のみ\) を作成するには、<xref:System.Xml.Schema.XmlSchemaElement> クラスまたは <xref:System.Xml.Schema.XmlSchemaAttribute> クラスの <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> プロパティではなく、<xref:System.Xml.Schema.XmlSchemaElement> クラスまたは <xref:System.Xml.Schema.XmlSchemaAttribute> クラスの <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> プロパティを設定します。  
  
 XML スキーマを使用すると、匿名の単純型と名前付きの単純型の両方を、他の単純型 \(組み込み型またはユーザー定義型\) から制限付きで派生させるか、または、他の単純型のリストまたは和集合として作成することができます。  <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> クラスを使用して単純型を作成する場合には、組み込みの `xs:string` 型を制限します。  また、<xref:System.Xml.Schema.XmlSchemaSimpleTypeList> または <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> クラスを使用すると、リストまたは和集合の型を作成できます。  <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=fullName> プロパティは、単純型の制限、リスト、または和集合を表します。  
  
 以下のコード サンプルでは、`FirstName` 要素の型は組み込み型の `xs:string`、`LastName` 要素の型は組み込み型 `xs:string` の制限となる名前付き単純型 \(`MaxLength` ファセット値 20\)、`CustomerId` 属性の型は組み込み型 `xs:positiveInteger` です。  `Customer` 要素は匿名の複合型で、そのパーティクルは `FirstName` 要素および `LastName` 要素のシーケンスとなり、その属性には `CustomerId` 属性が含まれます。  
  
> [!NOTE]
>  また、複合型のパーティクルとして <xref:System.Xml.Schema.XmlSchemaChoice> クラスまたは <xref:System.Xml.Schema.XmlSchemaAll> クラスを使用して、`<xs:choice />` または `<xs:all />` セマンティクスをレプリケートすることもできます。  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### スキーマの作成とコンパイル  
 この時点で、子要素と属性 \(それらに対応する型\) および最上位の `Customer` 要素が SOM API を使用してメモリ内に作成されています。  以下のコード サンプルでは、<xref:System.Xml.Schema.XmlSchema> クラスを使用してスキーマ要素が作成され、<xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=fullName> プロパティを使用して最上位の要素と型が追加されます。また、<xref:System.Xml.Schema.XmlSchemaSet> クラスを使用して完全なスキーマがコンパイルされて、コンソールに出力されます。  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=fullName> メソッドは、XML スキーマの規則を基準としてカスタム スキーマを検証し、スキーマ コンパイル後のプロパティを使用できるようにします。  
  
> [!NOTE]
>  SOM API のスキーマ コンパイル後のプロパティは、スキーマ検証後の情報セットとは異なります。  
  
 <xref:System.Xml.Schema.XmlSchemaSet> に追加される <xref:System.Xml.Schema.ValidationEventHandler> は、コールバック メソッド `ValidationCallback` を呼び出してスキーマ検証時の警告およびエラーを処理するデリゲートになります。  
  
 以下に、完全なコード サンプルおよびコンソールに出力されるカスタム スキーマを示します。  
  
 [!code-cpp[XmlSchemaCreateExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#1)]
 [!code-csharp[XmlSchemaCreateExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#1)]
 [!code-vb[XmlSchemaCreateExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#1)]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
   <xs:element name="Customer">  
      <xs:complexType>  
         <xs:sequence>  
            <xs:element name="FirstName" type="xs:string" />  
            <xs:element name="LastName" type="tns:LastNameType" />  
         </xs:sequence>  
         <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" />  
      </xs:complexType>  
   </xs:element>  
   <xs:simpleType name="LastNameType">  
      <xs:restriction base="xs:string">  
         <xs:maxLength value="20" />  
      </xs:restriction>  
   </xs:simpleType>  
</xs:schema>  
```  
  
## 参照  
 [XML スキーマ オブジェクト モデルの概要](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)   
 [XML スキーマの読み取りと書き込み](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)   
 [XML スキーマの走査](../../../../docs/standard/data/xml/traversing-xml-schemas.md)   
 [XML スキーマの編集](../../../../docs/standard/data/xml/editing-xml-schemas.md)   
 [XML スキーマのインクルードまたはインポート](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)   
 [スキーマをコンパイルするための XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)   
 [スキーマのコンパイル後の情報セット](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
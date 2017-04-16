---
title: "スキーマのノード型および構造を推論するときの規則 | Microsoft Docs"
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
ms.assetid: d74ce896-717d-4871-8fd9-b070e2f53cb0
caps.latest.revision: 2
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 2
---
# スキーマのノード型および構造を推論するときの規則
このトピックでは、スキーマ推論プロセスで、XML ドキュメント内のノード型を XML スキーマ定義言語 \(XSD\) 構造に変換する方法を説明します。  
  
## 要素を推論するときの規則  
 このセクションでは、要素宣言を推論するときの規則を説明します。  推論される要素宣言には 8 つの構造があります。  
  
1.  単純型の要素  
  
2.  空要素  
  
3.  属性を持つ空要素  
  
4.  属性と単純内容を持つ要素  
  
5.  子要素のシーケンスを持つ要素  
  
6.  子要素のシーケンスと属性を持つ要素  
  
7.  子要素のシーケンスと choice を持つ要素  
  
8.  子要素のシーケンスと choice を持つ要素  
  
> [!NOTE]
>  すべての `complexType` 宣言は匿名型として推論されます。  推論されるグローバル要素はルート要素だけであり、その他すべての要素はローカル要素です。  
  
 スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)」を参照してください。  
  
### 単純型要素  
 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドへの XML 入力と、生成される XML スキーマを次の表に示します。  太字になっている要素は、単純型要素から推論されるスキーマです。  
  
 スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)」を参照してください。  
  
|XML|Schema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>text</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> ``   `\<xs:element name="root" type="xs:string" />`<br /><br /> `\</xs:schema>`|  
  
### 空の要素  
 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドへの XML 入力と、生成される XML スキーマを次の表に示します。  太字になっている要素は、空要素から推論されるスキーマです。  
  
 スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)」を参照してください。  
  
|XML|Schema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> ``   `\<xs:element name="empty" />`<br /><br /> `\</xs:schema>`|  
  
### 属性を持つ空要素  
 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドへの XML 入力と、生成される XML スキーマを次の表に示します。  太字になっている要素は、属性を持つ空要素から推論されるスキーマです。  
  
 スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)」を参照してください。  
  
|XML|Schema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<empty attribute1="text"/>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> ``   `\<xs:element name="empty">`<br /><br /> `\<xs:complexType>`<br /><br /> `\<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `\</xs:complexType>`<br /><br /> `\</xs:element>`<br /><br /> `\</xs:schema>`|  
  
### 属性と単純内容を持つ要素  
 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドへの XML 入力と、生成される XML スキーマを次の表に示します。  太字になっている要素は、属性と単純内容を持つ要素から推論されるスキーマです。  
  
 スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)」を参照してください。  
  
|XML|Schema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">value</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> ``   `\<xs:element name="root">`<br /><br /> `\<xs:complexType>`<br /><br /> `\<xs:simpleContent>`<br /><br /> `\<xs:extension base="xs:string">`<br /><br /> `\<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `\</xs:extension>`<br /><br /> `\</xs:simpleContent>`<br /><br /> `\</xs:complexType>`<br /><br /> `\</xs:element>`<br /><br /> `\</xs:schema>`|  
  
### 子要素のシーケンスを持つ要素  
 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドへの XML 入力と、生成される XML スキーマを次の表に示します。  太字になっている要素は、子要素のシーケンスを持つ要素から推論されるスキーマです。  
  
> [!NOTE]
>  要素が子要素を 1 つしか持っていない場合でも、子要素はシーケンスとして扱われます。  
  
 スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)」を参照してください。  
  
|XML|Schema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> ``   `\<xs:element name="root">`<br /><br /> `\<xs:complexType>`<br /><br /> `\<xs:sequence>`<br /><br /> `\<xs:element name="subElement" />`<br /><br /> `\</xs:sequence>`<br /><br /> `\</xs:complexType>`<br /><br /> `\</xs:element>`<br /><br /> `\</xs:schema>`|  
  
### 子要素のシーケンスと属性を持つ要素  
 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドへの XML 入力と、生成される XML スキーマを次の表に示します。  太字になっている要素は、子要素のシーケンスと属性を持つ要素から推論されるスキーマです。  
  
> [!NOTE]
>  要素が子要素を 1 つしか持っていない場合でも、子要素はシーケンスとして扱われます。  
  
 スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)」を参照してください。  
  
|XML|Schema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> ``   `\<xs:element name="root">`<br /><br /> `\<xs:complexType>`<br /><br /> `\<xs:sequence>`<br /><br /> `\<xs:element name="subElement1" />`<br /><br /> `\<xs:element name="subElement2" />`<br /><br /> `\</xs:sequence>`<br /><br /> `\<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `\</xs:complexType>`<br /><br /> `\</xs:element>`<br /><br /> `\</xs:schema>`|  
  
### 子要素のシーケンスと choice を持つ要素  
 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドへの XML 入力と、生成される XML スキーマを次の表に示します。  太字になっているスキーマは、子要素のシーケンスと choice を持つ要素から推論されるスキーマです。  
  
> [!NOTE]
>  `xs:choice` 要素の `maxOccurs` 属性は、推論されるスキーマでは `"unbounded"` に設定されます。  
  
 スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)」を参照してください。  
  
|XML|Schema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root>`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> ``   `\<xs:element name="root">`<br /><br /> `\<xs:complexType>`<br /><br /> `\<xs:sequence>`<br /><br /> `\<xs:choice maxOccurs="unbounded">`<br /><br /> `\<xs:element name="subElement1" />`<br /><br /> `\<xs:element name="subElement2" />`<br /><br /> `\</xs:choice>`<br /><br /> `\</xs:sequence>`<br /><br /> `\</xs:complexType>`<br /><br /> `\</xs:element>`<br /><br /> `\</xs:schema>`|  
  
### 子要素のシーケンスと choice および属性を持つ要素  
 <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドへの XML 入力と、生成される XML スキーマを次の表に示します。  太字になっている要素は、子要素のシーケンスと choice および属性を持つ要素から推論されるスキーマです。  
  
> [!NOTE]
>  `xs:choice` 要素の `maxOccurs` 属性は、推論されるスキーマでは `"unbounded"` に設定されます。  
  
 スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)」を参照してください。  
  
|XML|Schema|  
|---------|------------|  
|`<?xml version="1.0"?>`<br /><br /> `<root attribute1="text">`<br /><br /> `<subElement1/>`<br /><br /> `<subElement2/>`<br /><br /> `<subElement1/>`<br /><br /> `</root>`|`<?xml version="1.0" encoding="utf-8"?>`<br /><br /> `<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xml`<br /><br /> `ns:xs="http://www.w3.org/2001/XMLSchema">`<br /><br /> ``   `\<xs:element name="root">`<br /><br /> `\<xs:complexType>`<br /><br /> `\<xs:sequence>`<br /><br /> `\<xs:choice maxOccurs="unbounded">`<br /><br /> `\<xs:element name="subElement1" />`<br /><br /> `\<xs:element name="subElement2" />`<br /><br /> `\</xs:choice>`<br /><br /> `\</xs:sequence>`<br /><br /> `\<xs:attribute name="attribute1" type="xs:string" use="required" />`<br /><br /> `\</xs:complexType>`<br /><br /> `\</xs:element>`<br /><br /> `\</xs:schema>`|  
  
### 属性の処理  
 ノード内で新しい属性が検出されるたびに、その属性は推論されるノードの定義に `use="required"` として追加されます。  そのインスタンスで同じノードが再び検出されると、推論プロセスでは、現在のインスタンスの属性と、既に推論されている属性を比較します。  既に推論されている属性の一部がインスタンスにない場合は、属性の定義に `use="optional"` が追加されます。  新しい属性は、既存の宣言に `use="optional"` として追加されます。  
  
### 出現回数に関する制約  
 スキーマ推論プロセスでは、推論されるスキーマのコンポーネントに対して、値が `"0"` または `"1"` の `minOccurs` 属性と、値が `"1"` または `"unbounded"` の `maxOccurs` 属性が生成されます。   値 `"1"` および `"unbounded"` は、値 `"0"` および `"1"` では XML ドキュメントを検証できない場合にのみ使われます \(たとえば、`MinOccurs="0"` では要素を正確に記述できない場合は、`minOccurs="1"` が使われます\)。  
  
### 混合コンテンツ  
 テキストに要素が混じっているなど、要素に混合コンテンツが含まれている場合は、推論される複合型の定義に対して `mixed="true"` 属性が生成されます。  
  
## その他のノードの型推論規則  
 処理命令、コメント、エンティティ参照、CDATA、ドキュメント型、名前空間の各ノード型に関する推論の規則を次の表に示します。  
  
|ノード型|変換|  
|----------|--------|  
|処理命令|無視されます。|  
|コメント|無視されます。|  
|エンティティ参照|<xref:System.Xml.Schema.XmlSchemaInference> クラスではエンティティ参照を処理しません。  XML ドキュメントにエンティティ参照が含まれている場合は、エンティティを展開するリーダーを使用する必要があります。  たとえば、<xref:System.Xml.XmlTextReader.EntityHandling%2A> プロパティを <xref:System.Xml.EntityHandling> に設定した <xref:System.Xml.XmlTextReader> をパラメーターとして渡すことができます。  エンティティ参照が検出されたにもかかわらず、リーダーがエンティティを展開しない場合は、例外がスローされます。|  
|CDATA|XML ドキュメント内のすべての `<![CDATA[   ]]` セクションが `xs:string` として推論されます。|  
|ドキュメント型|無視されます。|  
|名前空間|無視されます。|  
  
 スキーマ推論プロセスの詳細については、「[XML ドキュメントからのスキーマの推論](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)」を参照してください。  
  
## 参照  
 <xref:System.Xml.Schema.XmlSchemaInference>   
 [XML スキーマ オブジェクト モデル \(SOM\)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)   
 [XML スキーマの推論](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)   
 [XML ドキュメントからのスキーマの推論](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)   
 [単純型を推論するときの規則](../../../../docs/standard/data/xml/rules-for-inferring-simple-types.md)
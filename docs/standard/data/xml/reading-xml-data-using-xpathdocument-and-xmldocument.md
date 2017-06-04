---
title: "XPathDocument および XmlDocument を使用した XML データの読み取り | Microsoft Docs"
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
ms.assetid: 5711b225-6aa2-4e4f-9898-19f2d518ad1a
caps.latest.revision: 2
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 2
---
# XPathDocument および XmlDocument を使用した XML データの読み取り
<xref:System.Xml.XPath?displayProperty=fullName> 名前空間で XML ドキュメントを読み取る方法は 2 つあります。  1 つは読み取り専用の <xref:System.Xml.XPath.XPathDocument> クラスを使用して XML ドキュメントを読み取る方法で、もう 1 つは、<xref:System.Xml?displayProperty=fullName> 名前空間で編集可能な <xref:System.Xml.XmlDocument> クラスを使用して XML ドキュメントを読み取る方法です。  
  
## XPathDocument クラスを使用した XML ドキュメントの読み取り  
 <xref:System.Xml.XPath.XPathDocument> クラスは、XPath データ モデルによる XML ドキュメントの高速、読み取り専用のメモリ内表現を提供します。  <xref:System.Xml.XPath.XPathDocument> クラスのインスタンスは、その 6 つのコンストラクターの 1 つを使用して作成されます。  これらのコンストラクターでは、<xref:System.IO.Stream>、<xref:System.IO.TextReader>、または <xref:System.Xml.XmlReader> オブジェクトを使用して XML ドキュメントを読み取ることも、XML ファイルへの `string` パスを使用して XML ドキュメントを読み取ることもできます。  
  
 以下は、<xref:System.Xml.XPath.XPathDocument> クラスの `string` コンストラクターを使用して XML ドキュメントを読み取る例です。  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
```  
  
## XmlDocument クラスを使用した XML ドキュメントの読み取り  
 <xref:System.Xml.XmlDocument> クラスは、W3C ドキュメント オブジェクト モデル \(DOM\) の DOM Level 1 Core および DOM Level 2 Core を実装する XML ドキュメントの編集可能なメモリ内表現です。  <xref:System.Xml.XmlDocument> クラスのインスタンスは、その 3 つのコンストラクターの 1 つを使用して作成されます。  <xref:System.Xml.XmlDocument> クラス コンストラクターをパラメーターなしで呼び出すことによって、新しい空の <xref:System.Xml.XmlDocument> オブジェクトを作成できます。  コンストラクターの呼び出し後、<xref:System.Xml.XmlDocument.Load%2A> メソッドを使用するか、XML ファイルへの `string` パスを使用して、<xref:System.IO.Stream>、<xref:System.IO.TextReader>、または <xref:System.Xml.XmlReader> オブジェクトから新しい <xref:System.Xml.XmlDocument> オブジェクトに XML データを読み込みます。  
  
 以下は、パラメーターなしの <xref:System.Xml.XmlDocument> クラス コンストラクターと <xref:System.Xml.XmlDocument.Load%2A> メソッドを使用して XML ドキュメントを読み込む例です。  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
```  
  
## XML ドキュメントのエンコーディングの判定  
 前に示されているように、<xref:System.Xml.XmlReader> オブジェクトを使用して XML ドキュメントを読み取り、<xref:System.Xml.XPath.XPathDocument> および <xref:System.Xml.XmlDocument> オブジェクトを作成できます。  ただし、<xref:System.Xml.XmlReader> オブジェクトは、エンコードされていないデータを読み取り、その結果、エンコード情報を提供しない場合があります。  
  
 <xref:System.Xml.XmlTextReader> クラスは、<xref:System.Xml.XmlReader> クラスを継承し、その <xref:System.Xml.XmlTextReader.Encoding%2A> プロパティを使用してエンコード情報を提供します。また、このクラスは、<xref:System.Xml.XPath.XPathDocument> オブジェクトまたは <xref:System.Xml.XmlDocument> オブジェクトの作成に使用できます。  
  
 <xref:System.Xml.XmlTextReader> クラスよって提供されるエンコード情報に関する詳細については、<xref:System.Xml.XmlTextReader> クラスのリファレンス ドキュメントの「<xref:System.Xml.XmlTextReader.Encoding%2A>」プロパティを参照してください。  
  
## XPathNavigator オブジェクトの作成  
 <xref:System.Xml.XPath.XPathDocument> または <xref:System.Xml.XmlDocument> オブジェクトのどちらからに XML ドキュメントを読み込んだ後、<xref:System.Xml.XPath.XPathNavigator> オブジェクト作成して、基になる XML データを選択、評価、移動、および \(一部の状況で\) 編集できます。  
  
 <xref:System.Xml.XmlNode> クラスに加えて、<xref:System.Xml.XPath.XPathDocument> および <xref:System.Xml.XmlDocument> クラスは両方とも、<xref:System.Xml.XPath?displayProperty=fullName> 名前空間の <xref:System.Xml.XPath.IXPathNavigable> インターフェイスを実装しています。  結果として、3 つのクラスはすべて <xref:System.Xml.XPath.XPathNavigator> オブジェクトを返す <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> メソッドを提供します。  
  
### XPathNavigator クラスによる XML ドキュメントの編集  
 XML データの選択、評価、および移動に加えて、<xref:System.Xml.XPath.XPathNavigator> クラスは、作成元のオブジェクトに基づき、一部の状況で XML ドキュメントの編集に使用できます。  
  
 <xref:System.Xml.XPath.XPathDocument> クラスは読み取り専用ですが、<xref:System.Xml.XmlDocument> クラスは編集可能です。その結果、<xref:System.Xml.XPath.XPathDocument> オブジェクトから作成された <xref:System.Xml.XPath.XPathNavigator> オブジェクトは XML ドキュメントの編集に使用できませんが、<xref:System.Xml.XmlDocument> オブジェクトから作成された場合は編集に使用できます。  <xref:System.Xml.XPath.XPathDocument> クラスは XML ドキュメントの読み取りだけに使用する必要があります。  XML ドキュメントを編集する必要がある場合、またはイベント処理など <xref:System.Xml.XmlDocument> クラスによって提供される追加の機能が必要な場合は、<xref:System.Xml.XmlDocument> クラスを使用する必要があります。  
  
 <xref:System.Xml.XPath.XPathNavigator> クラスの <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> プロパテイは、<xref:System.Xml.XPath.XPathNavigator> オブジェクトが XML データを編集できるかどうかを指定します。  
  
 各クラスの <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> プロパティ値についての説明を次に示します。  
  
|<xref:System.Xml.XPath.IXPathNavigable> 実装|<xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> 値|  
|--------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Xml.XPath.XPathDocument>|`false`|  
|<xref:System.Xml.XmlDocument>|`true`|  
  
## 参照  
 <xref:System.Xml.XmlDocument>   
 <xref:System.Xml.XPath.XPathDocument>   
 <xref:System.Xml.XPath.XPathNavigator>   
 [XPath データ モデルを使用した XML データの処理](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)   
 [XPathNavigator による XML データへのアクセス](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)   
 [XPathNavigator による XML データの編集](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)   
 [XPathNavigator を使用したスキーマ検証](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
---
title: "ドキュメントの保存と書き込み | Microsoft Docs"
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
ms.assetid: 097b0cb1-5743-4c3a-86ef-caf5cbe6750d
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# ドキュメントの保存と書き込み
<xref:System.Xml.XmlDocument> を読み込んで保存した場合、保存されたドキュメントは、元のドキュメントとは次のように異なる可能性があります。  
  
-   <xref:System.Xml.XmlDocument.Save%2A> メソッドを呼び出す前に <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> プロパティが `true` に設定されている場合は、ドキュメント内の空白が出力でも保持されますが、`false` に設定されている場合は、<xref:System.Xml.XmlDocument> が出力を自動的にインデントします。  
  
-   属性間のすべての空白は 1 つの空白文字になります。  
  
-   要素間の空白が変更されます。  有意の空白は保持され、意味のない空白は保持されません。  しかし、ドキュメントの保存時には、出力が読みやすくなるように、既定で <xref:System.Xml.XmlTextWriter> のインデント モードが使用されます。  
  
-   属性値を囲む引用符は、既定で二重引用符に変更されます。  <xref:System.Xml.XmlTextWriter> の <xref:System.Xml.XmlTextReader.QuoteChar%2A> プロパティを使用すると、引用符を二重引用符または一重引用符のいずれかに設定できます。  
  
-   既定では、`{` のような数値エンティティは展開されます。  
  
-   入力ドキュメントのバイト順マークは保持されません。  別のエンコーディングを指定する XML 宣言を明示的に作成しない限り、UCS\-2 は UTF\-8 として保存されます。  
  
-   <xref:System.Xml.XmlDocument> をファイルまたはストリームに書き出す場合、書き出される出力はドキュメントのコンテンツと同じになります。  つまり、<xref:System.Xml.XmlDeclaration> が書き出されるのは、ドキュメントに <xref:System.Xml.XmlDeclaration> が 1 つ含まれていて、ドキュメントの出力時に使われるエンコーディングが宣言ノードで指定されたエンコーディングと同じ場合だけです。  
  
## XmlDeclaration の書き込み  
 <xref:System.Xml.XmlDocument.Save%2A> および <xref:System.Xml.XmlDocument.WriteContentTo%2A> の <xref:System.Xml.XmlDocument> メソッドに加えて、<xref:System.Xml.XmlNode.OuterXml%2A>、<xref:System.Xml.XmlNode.InnerXml%2A>、および <xref:System.Xml.XmlNode.WriteTo%2A> の <xref:System.Xml.XmlDocument> および <xref:System.Xml.XmlDeclaration> メンバーは XML 宣言を作成します。  
  
 <xref:System.Xml.XmlNode.OuterXml%2A>、<xref:System.Xml.XmlDocument.InnerXml%2A> の <xref:System.Xml.XmlDocument> プロパティ、<xref:System.Xml.XmlDocument.Save%2A>、<xref:System.Xml.XmlDocument.WriteTo%2A> メソッド、および <xref:System.Xml.XmlDocument.WriteContentTo%2A> メソッドについて、XML 宣言に書き出されるエンコーディングは <xref:System.Xml.XmlDeclaration> ノードから取り出されます。  <xref:System.Xml.XmlDeclaration> ノードが存在しない場合、<xref:System.Xml.XmlDeclaration> は書き出されません。  <xref:System.Xml.XmlDeclaration> ノードにエンコーディングが含まれていない場合、エンコーディングは XML 宣言に書き出されません。  
  
 <xref:System.Xml.XmlDocument.Save%2A?displayProperty=fullName> および <xref:System.Xml.XmlDocument.Save%2A?displayProperty=fullName> メソッドは、常に <xref:System.Xml.XmlDeclaration> を書き出します。  これらのメソッドは、書き込みを行っているライターからエンコーディングを取得します。  つまり、ライターのエンコーディングの値によって、ドキュメントと <xref:System.Xml.XmlDeclaration> オブジェクトのエンコーディングがオーバーライドされます。  たとえば、次のコードでは、出力ファイル `out.xml` の XML 宣言にはエンコーディングは書き込まれません。  
  
```vb  
Dim doc As New XmlDocument()  
Dim tw As XmlTextWriter = New XmlTextWriter("out.xml", Nothing)  
doc.Load("text.xml")  
doc.Save(tw)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlTextWriter tw = new XmlTextWriter("out.xml", null);  
doc.Load("text.xml");  
doc.Save(tw);  
```  
  
 <xref:System.Xml.XmlDocument.Save%2A> メソッドでは、<xref:System.Xml.XmlWriter> クラスの <xref:System.Xml.XmlWriter.WriteStartDocument%2A> メソッドを使用して XML 宣言が書き出されます。  そのため、<xref:System.Xml.XmlWriter.WriteStartDocument%2A> メソッドをオーバーライドすると、ドキュメントの先頭部分の出力方法が変わります。  
  
 <xref:System.Xml.XmlNode.OuterXml%2A>、<xref:System.Xml.XmlDeclaration.WriteTo%2A>、および <xref:System.Xml.XmlNode.InnerXml%2A> の <xref:System.Xml.XmlDeclaration> メンバーについて、<xref:System.Xml.XmlDeclaration.Encoding%2A> プロパティが設定されていないと、エンコーディングは書き出されません。  それ以外の場合は、<xref:System.Xml.XmlDeclaration.Encoding%2A> プロパティのエンコーディングと同じエンコーディングが XML 宣言に書き出されます。  
  
## OuterXml プロパティを使用したドキュメント内容の書き込み  
 <xref:System.Xml.XmlNode.OuterXml%2A> プロパティは、W3C XML ドキュメント オブジェクト モデル \(DOM\) 標準に対するマイクロソフトの拡張機能です。  <xref:System.Xml.XmlNode.OuterXml%2A> プロパティは、XML ドキュメント全体のマークアップ、または 1 つのノードとその子ノードのマークアップだけを取得するために使用されます。  <xref:System.Xml.XmlNode.OuterXml%2A> は、指定されたノードとそのすべての子ノードを表すマークアップを返します。  
  
 ドキュメント全体を文字列として保存するコード サンプルを次に示します。  
  
```vb  
Dim mydoc As New XmlDocument()  
' Perform application needs here, like mydoc.Load("myfile");  
' Now save the entire document to a string variable called "xml".  
Dim xml As String = mydoc.OuterXml  
```  
  
```csharp  
XmlDocument mydoc = new XmlDocument();  
// Perform application needs here, like mydoc.Load("myfile");  
// Now save the entire document to a string variable called "xml".  
string xml = mydoc.OuterXml;  
```  
  
 ドキュメント要素だけを保存するコード サンプルを次に示します。  
  
```vb  
' For the content of the Document Element only.  
Dim xml As String = mydoc.DocumentElement.OuterXml  
```  
  
```csharp  
// For the content of the Document Element only.  
string xml = mydoc.DocumentElement.OuterXml;  
```  
  
 一方、子ノードの内容が必要な場合は、<xref:System.Xml.XmlNode.InnerText%2A> プロパティを使用します。  
  
## 参照  
 [XML ドキュメント オブジェクト モデル \(DOM\)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
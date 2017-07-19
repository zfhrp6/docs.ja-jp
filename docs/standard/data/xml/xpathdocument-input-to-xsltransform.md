---
title: "XslTransform への XPathDocument の入力 | Microsoft Docs"
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
ms.assetid: 7d1bbe8b-ed43-4e62-a5ba-d602d244f4ae
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# XslTransform への XPathDocument の入力
<xref:System.Xml.XPath.XPathDocument> は、<xref:System.Xml.Xsl.XslTransform> でドキュメントを処理するための読み取り専用キャッシュです。  <xref:System.Xml.XPath.XPathDocument> は、構造的には XML ドキュメント オブジェクト モデル \(DOM\) に似ていますが、<xref:System.Xml.XPath.XPathNavigator> で XPath 最適化関数を使用することで、XSLT \(Extensible Stylesheet Language for Transformations\) による処理と XPath \(XML Path Language\) データ モデルに高度に最適化されています。  
  
> [!NOTE]
>  [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] では、<xref:System.Xml.Xsl.XslTransform> クラスが廃止されています。  <xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用して XSLT \(Extensible Stylesheet Language for Transformations\) 変換を実行できます。  詳細については、「[XslCompiledTransform クラスの使用](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)」および「[XslTransform クラスからの移行](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)」を参照してください。  
  
 変換への入力として <xref:System.Xml.XPath.XPathDocument> を作成するコード サンプルを次に示します。  
  
```vb  
Dim xslt as XslTransform = new XslTransform()  
Xslt.Load(someStylesheet)  
Dim doc as XPathDocument = New XPathDocument("books.xml")  
Dim fs as StringWriter = new StringWriter()  
Xslt.Transform(doc, Nothing, fs, Nothing);  
  
```  
  
```csharp  
XslTransform xslt = new XslTransform();  
Xslt.Load(someStylesheet);  
XPathDocument doc = XPathDocument("books.xml");  
StringWriter fs = new StringWriter();  
Xslt.Transform(doc, null, fs, null);  
```  
  
## 参照  
 [XslTransform クラスによる XSLT プロセッサの実装](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
---
title: "System.Xml クラスでの型のサポート | Microsoft Docs"
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
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
caps.latest.revision: 4
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 4
---
# System.Xml クラスでの型のサポート
.NET Framework Version 2.0 では、コアの XML クラスが強化され、型サポート機能が追加されています。  <xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter>、および <xref:System.Xml.XPath.XPathNavigator> クラスには、XML スキーマ型と共通言語ランタイム \(CLR\) 型の間の変換機能を含む型サポート機能が含まれています。  
  
 .NET Framework Version 2.0 では、<xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter>、および <xref:System.Xml.XPath.XPathNavigator> クラスが強化され、型サポート機能が追加されています。  
  
-   <xref:System.Xml.XmlReader> および <xref:System.Xml.XPath.XPathNavigator> クラスにはそれぞれ、ノードのスキーマ情報を返す **SchemaInfo** プロパティが含まれています。  
  
-   <xref:System.Xml.XmlReader> クラスの **ReadContentAs** と **ReadElementContentAs** メソッドは、1 回のメソッド呼び出しでテキスト値を読み取り、それを CLR 値に変換します。  
  
-   <xref:System.Xml.XmlWriter> クラスの <xref:System.Xml.XmlWriter.WriteValue%2A> メソッドは、XML の書き出し時に、CLR 型を XML スキーマ型に変換します。  
  
-   <xref:System.Xml.XPath.XPathNavigator> クラスの **ValueAs** および <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> プロパティは、1 回のメソッド呼び出しでノード値を返し、それを CLR 値に変換します。  
  
> [!NOTE]
>  .NET Framework Version 1.0 では、XML スキーマ型と CLR 型の間の変換に <xref:System.Xml.XmlConvert> クラスが必要でした。  
  
## このセクションの内容  
 [XML データ型から CLR 型へのマッピング](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 XML データ型から CLR 型への既定のマッピングについて説明します。  
  
 [XML 型サポートの実装に関するメモ](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 型サポート実装の詳細のいくつかについて説明します。  
  
 [XML データ型の変換](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 XML スキーマ型と CLR 型の間の変換に <xref:System.Xml.XmlConvert> クラスを使用する方法について説明します。  
  
## 関連項目  
 [厳密に型指定された XML データへの XPathNavigator を使用したアクセス](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
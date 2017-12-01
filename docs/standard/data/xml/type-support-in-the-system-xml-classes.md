---
title: "System.Xml クラスでの型のサポート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 14821ef78f20d1ff303afacb42415e4017a92742
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="type-support-in-the-systemxml-classes"></a>System.Xml クラスでの型のサポート
.NET Framework Version 2.0 では、コアの XML クラスが強化され、型サポート機能が追加されています。 <xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter>、および <xref:System.Xml.XPath.XPathNavigator> クラスには、XML スキーマ型と共通言語ランタイム (CLR) 型の間の変換機能を含む型サポート機能が含まれています。  
  
 .NET Framework Version 2.0 では、<xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter>、および <xref:System.Xml.XPath.XPathNavigator> クラスが強化され、型サポート機能が追加されています。  
  
-   <xref:System.Xml.XmlReader>と<xref:System.Xml.XPath.XPathNavigator>各クラスに含まれる、 **SchemaInfo**ノードでスキーマ情報を返します。  
  
-   **ReadContentAs**と**ReadElementContentAs**とメソッドを<xref:System.Xml.XmlReader>クラスは、テキスト値を読み取るし、1 つのメソッドの呼び出しでの CLR 値に変換します。  
  
-   <xref:System.Xml.XmlWriter.WriteValue%2A> クラスの <xref:System.Xml.XmlWriter> メソッドは、XML の書き出し時に、CLR 型を XML スキーマ型に変換します。  
  
-   **ValueAs**と<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>プロパティを<xref:System.Xml.XPath.XPathNavigator>クラスは、ノードの値を返すし、1 つのメソッドの呼び出しでの CLR 値に変換します。  
  
> [!NOTE]
>  .NET Framework Version 1.0 では、XML スキーマ型と CLR 型の間の変換に <xref:System.Xml.XmlConvert> クラスが必要でした。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [CLR 型に XML データ型のマッピング](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 XML データ型から CLR 型への既定のマッピングについて説明します。  
  
 [XML 型サポート実装に関するメモ](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 型サポート実装の詳細のいくつかについて説明します。  
  
 [XML データ型の変換](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 XML スキーマ型と CLR 型の間の変換に <xref:System.Xml.XmlConvert> クラスを使用する方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [XPathNavigator による XML データに型指定された厳密にアクセスします。](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)

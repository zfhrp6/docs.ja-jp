---
title: "XPath クエリで認識されるノード型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d33e22d-18e5-43f8-a466-2e3d0a8dd094
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1c1e48bbfd6388686fdb83f08668f7f0234275a5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="node-types-recognized-with-xpath-queries"></a>XPath クエリで認識されるノード型
XPath クエリで認識されるノードの型は、ドキュメント オブジェクト モデル (DOM) のノード型と同じではありません。  
  
## <a name="w3c-xpath-node-types"></a>W3C XPath のノード型  
 XPath クエリで認識されるノードの型は、ドキュメント オブジェクト モデル (DOM) のノード型ではありません。 以下は、<xref:System.Xml.XPath.XPathNodeType> 列挙体によって表される XPath のノード型です。  
  
-   <xref:System.Xml.XPath.XPathNodeType.All>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Attribute>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Comment>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Element>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Namespace>  
  
-   <xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Root>  
  
-   <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Text>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Whitespace>  
  
 これらのノード型は、XPath データ モデルに基づいており、ノードは XML 情報セットから派生しています。 <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> および <xref:System.Xml.XPath.XPathNodeType.Whitespace> ノード型は、XPath データ モデルに記載されている基本のノード型に対する Microsoft .NET Framework の拡張です。  
  
 XPath における属性ノード型の使用法は DOM と異なります。 XPath データ モデルでは、要素ノードには関連する属性ノードのセットがあり、要素ノードはそれぞれの属性ノードの親になっています。 しかし、DOM では要素ノードは所有者であり、親ではありません。 いずれのモデルにおいても、属性ノードと名前空間ノードは要素ノードの子ノードとは見なされません。  
  
 名前空間ノード型は XPath データ モデルに追加されたノード型であり、DOM で認識されるノード型ではありません。  
  
 要素、属性、および名前空間ノードの移動の詳細については、次を参照してください、[ノード セット ナビゲーションを使用して XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)と[属性および XPathNavigator を使用してノードのナビゲーションを Namespace](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) 。トピックです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [XPath データ モデルを使用した XML データの処理](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [XPathNavigator による XML データを選択します。](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [XPathNavigator による XPath 式を評価します。](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [XPathNavigator によるノードの一致](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [XPath クエリおよび名前空間](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [コンパイルされた XPath 式](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)

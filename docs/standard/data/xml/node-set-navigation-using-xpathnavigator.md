---
title: "XPathNavigator を使用するノード セットのナビゲーション | Microsoft Docs"
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
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
caps.latest.revision: 2
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 2
---
# XPathNavigator を使用するノード セットのナビゲーション
<xref:System.Xml.XPath.XPathNavigator> クラスのノード セット ナビゲーション メソッドを使用して、<xref:System.Xml.XPath.XPathDocument> または <xref:System.Xml.XmlDocument> オブジェクト内のノード間を移動できます。  すべてのノード間の移動、または <xref:System.Xml.XPath.XPathNavigator> クラスの選択メソッドによって返される選択されたノード セット間を移動できます。  
  
## 要素ノード セットのナビゲーション  
 <xref:System.Xml.XPath.XPathNavigator> クラスは、要素ノードの移動に使用されるいくつかのメソッドを提供します。  利用可能なナビゲーション メソッドおよびその移動方法を次の表に示します。これには、属性および名前空間のノードのナビゲートに使用されるメソッドは含まれません。  
  
 <xref:System.Xml.XPath.XPathNavigator> オブジェクトでのノードの選択に関する詳細については、「[XPathNavigator を使用した XML データの選択、評価、および照合](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)」を参照してください。  属性および名前空間の移動に関する詳細については、「[XPathNavigator を使用する属性と名前空間のナビゲーション](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)」を参照してださい。  
  
|メソッド|説明|  
|----------|--------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|<xref:System.Xml.XPath.XPathNavigator> を指定された <xref:System.Xml.XPath.XPathNavigator> と同じ位置に移動します。|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|<xref:System.Xml.XPath.XPathNavigator> を現在のノードの子ノードに移動します。|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|<xref:System.Xml.XPath.XPathNavigator> を現在のノードの最初の兄弟ノードに移動します。|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|<xref:System.Xml.XPath.XPathNavigator> を現在のノードの最初の子ノードに移動します。|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|<xref:System.Xml.XPath.XPathNavigator> をドキュメント順で指定された要素に移動します。|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|<xref:System.Xml.XPath.XPathNavigator> を、与えられた <xref:System.String> に一致する値の `ID` 型の属性を持つノードに移動します。|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|<xref:System.Xml.XPath.XPathNavigator> を現在のノードの次の兄弟ノードに移動します。|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|<xref:System.Xml.XPath.XPathNavigator> を現在のノードの親ノードに移動します。|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|<xref:System.Xml.XPath.XPathNavigator> を現在のノードの前の兄弟ノードに移動します。|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|<xref:System.Xml.XPath.XPathNavigator> を XML ドキュメントのルート ノードに移動します。|  
  
## コメントおよび処理命令ノードのナビゲーション  
 次の <xref:System.Xml.XPath.XPathNavigator> クラスのメソッドは XML ドキュメント内の他のノードからコメントまたは処理命令に移動するのに有効です。  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## 参照  
 <xref:System.Xml.XmlDocument>   
 <xref:System.Xml.XPath.XPathDocument>   
 <xref:System.Xml.XPath.XPathNavigator>   
 [XPath データ モデルを使用した XML データの処理](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)   
 [XPathNavigator を使用する属性と名前空間のナビゲーション](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)   
 [XpathNavigator を使用した XML データの抽出](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)   
 [厳密に型指定された XML データへの XPathNavigator を使用したアクセス](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
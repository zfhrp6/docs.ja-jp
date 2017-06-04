---
title: "変換におけるノード セット | Microsoft Docs"
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
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
caps.latest.revision: 4
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 4
---
# 変換におけるノード セット
ノード セットは、XPath \(XML Path Language\) 式が返す 4 つの基本データ型のうちの 1 つです。 ノード セットは、ドキュメントの順番で作成された、重複がなくソートされていないノードのコレクションであり、スタイル シートの変数に割り当てることができます。  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> では、[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] クラスが廃止されています。<xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用して XSLT \(Extensible Stylesheet Language for Transformations\) 変換を実行できます。 詳細については、「[XslCompiledTransform クラスの使用](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)」および「[XslTransform クラスからの移行](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)」を参照してください。  
  
 ノード セットは、XPath 式が返す 4 つの基本データ型のうちの 1 つです。 ノード セットは、ドキュメントの順番で作成された、重複がなくソートされていないノードのコレクションであり、スタイル シートの変数に割り当てることができます。 変換の `select` 属性で使用される XPath 式の結果であるこのノード セットは、XML ドキュメント オブジェクト モデル \(DOM\) のノード セットと同じ動作をします。 移動に [XPathNavigator を使用するノード セットのナビゲーション](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) を使用する結果ツリー フラグメントと異なり、ノード セットの場合は「<xref:System.Xml.XPath.XPathNodeIterator>」で説明している各種のメソッドを使用してノード セット間を移動します。  
  
 スタイル シートの `variable` 要素または `parameter` 要素がノード セットとして評価される場合のノード セットに対する反復処理を、次のコード サンプルに示します。  
  
## スタイル シート  
  
```  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
    <xsl:variable name="x" select="bookstore/book/title"></xsl:variable>  
  
    <xsl:template match="/">  
        <xsl:for-each select="$x">  
            ******  
            <xsl:value-of select="."></xsl:value-of>  
            ******  
        </xsl:for-each>  
    </xsl:template>  
  
</xsl:stylesheet>  
```  
  
## 入力  
  
```  
<bookstore>  
   <book style="autobiography">  
      <title>Seven Years in Trenton</title>  
   </book>  
  
   <book style="autobiography">  
      <title>Seven Years in Trenton2</title>  
   </book>  
  
   <book style="textbook">  
      <title>History of Trenton Vol 3</title>  
   </book>  
</bookstore>  
```  
  
## 出力  
  
```  
******  
Seven Years in Trenton  
******  
  
******  
Seven Years in Trenton2  
******  
  
******  
History of Trenton Vol 3  
******  
```  
  
## 参照  
 <xref:System.Xml.XPath.XPathNodeIterator>   
 [XslTransform クラスを使用した XSLT 変換](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)   
 [XslTransform クラスによる XSLT プロセッサの実装](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
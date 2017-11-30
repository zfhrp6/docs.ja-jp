---
title: "変換におけるノード セット"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e4d6d2f5a68ce5cef9937edc136e52efcd5366df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="node-sets-in-transformations"></a>変換におけるノード セット
ノード セットは、XPath (XML Path Language) 式が返す 4 つの基本データ型のうちの 1 つです。 ノード セットは、ドキュメントの順番で作成された、重複がなくソートされていないノードのコレクションであり、スタイル シートの変数に割り当てることができます。  
  
> [!NOTE]
>  
          <xref:System.Xml.Xsl.XslTransform> では、[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] クラスが廃止されています。 <xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用して XSLT (Extensible Stylesheet Language for Transformations) 変換を実行できます。 参照してください[XslCompiledTransform クラスを使用して](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)と[XslTransform クラスからの移行](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)詳細についてはします。  
  
 ノード セットは、XPath 式が返す 4 つの基本データ型のうちの 1 つです。 ノード セットは、ドキュメントの順番で作成された、重複がなくソートされていないノードのコレクションであり、スタイル シートの変数に割り当てることができます。 変換の `select` 属性で使用される XPath 式の結果であるこのノード セットは、XML ドキュメント オブジェクト モデル (DOM) のノード セットと同じ動作をします。 示すようにメソッドのセットを使用して設定ノードを移動することができます[ノード セット ナビゲーションを使用して XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)、結果ツリー フラグメントまたはを使用して、結果ツリー フラグメントとは異なり、<xref:System.Xml.XPath.XPathNodeIterator>移動できるようにします。  
  
 スタイル シートの `variable` 要素または `parameter` 要素がノード セットとして評価される場合のノード セットに対する反復処理を、次のコード サンプルに示します。  
  
## <a name="style-sheet"></a>スタイル シート  
  
```xml  
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
  
## <a name="input"></a>入力  
  
```xml  
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
  
## <a name="output"></a>出力  
  
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
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.XPath.XPathNodeIterator>  
 [XslTransform クラスによる XSLT 変換](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [XslTransform クラスによる XSLT プロセッサ](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)

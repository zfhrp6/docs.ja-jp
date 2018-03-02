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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 95df2f2888899093943feda35768694bf414de84
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="node-sets-in-transformations"></a><span data-ttu-id="f55d2-102">変換におけるノード セット</span><span class="sxs-lookup"><span data-stu-id="f55d2-102">Node Sets in Transformations</span></span>
<span data-ttu-id="f55d2-103">ノード セットは、XPath (XML Path Language) 式が返す 4 つの基本データ型のうちの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="f55d2-103">Node sets are one of four basic data types that are returned from XML Path Language (XPath) expressions.</span></span> <span data-ttu-id="f55d2-104">ノード セットは、ドキュメントの順番で作成された、重複がなくソートされていないノードのコレクションであり、スタイル シートの変数に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="f55d2-104">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f55d2-105"><xref:System.Xml.Xsl.XslTransform> では、[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] クラスが廃止されています。</span><span class="sxs-lookup"><span data-stu-id="f55d2-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="f55d2-106"><xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用して XSLT (Extensible Stylesheet Language for Transformations) 変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="f55d2-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="f55d2-107">詳細については、「[XslCompiledTransform クラスの使用](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)」と「[XslTransform クラスからの移行](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f55d2-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="f55d2-108">ノード セットは、XPath 式が返す 4 つの基本データ型のうちの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="f55d2-108">Node sets are one of four basic data types that are returned from XPath expressions.</span></span> <span data-ttu-id="f55d2-109">ノード セットは、ドキュメントの順番で作成された、重複がなくソートされていないノードのコレクションであり、スタイル シートの変数に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="f55d2-109">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span> <span data-ttu-id="f55d2-110">変換の `select` 属性で使用される XPath 式の結果であるこのノード セットは、XML ドキュメント オブジェクト モデル (DOM) のノード セットと同じ動作をします。</span><span class="sxs-lookup"><span data-stu-id="f55d2-110">This node set, which is a result of an XPath expression used in a `select` attribute in a transformation, has the same behavior as a node set from the XML Document Object Model (DOM).</span></span> <span data-ttu-id="f55d2-111">移動に <xref:System.Xml.XPath.XPathNodeIterator> を使用する結果ツリー フラグメントと異なり、ノード セットの場合は「[Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)」で説明している各種のメソッドを使用してノード セット間を移動します。</span><span class="sxs-lookup"><span data-stu-id="f55d2-111">You can navigate a node set using a set of methods shown in [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), unlike a result tree fragment or result tree fragment, which uses the <xref:System.Xml.XPath.XPathNodeIterator> for navigation.</span></span>  
  
 <span data-ttu-id="f55d2-112">スタイル シートの `variable` 要素または `parameter` 要素がノード セットとして評価される場合のノード セットに対する反復処理を、次のコード サンプルに示します。</span><span class="sxs-lookup"><span data-stu-id="f55d2-112">The following code sample shows how to iterate over a node set when a `variable` or `parameter` element in a style sheet evaluates to a node set.</span></span>  
  
## <a name="style-sheet"></a><span data-ttu-id="f55d2-113">スタイル シート</span><span class="sxs-lookup"><span data-stu-id="f55d2-113">Style Sheet</span></span>  
  
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
  
## <a name="input"></a><span data-ttu-id="f55d2-114">入力</span><span class="sxs-lookup"><span data-stu-id="f55d2-114">Input</span></span>  
  
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
  
## <a name="output"></a><span data-ttu-id="f55d2-115">出力</span><span class="sxs-lookup"><span data-stu-id="f55d2-115">Output</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f55d2-116">参照</span><span class="sxs-lookup"><span data-stu-id="f55d2-116">See Also</span></span>  
 <xref:System.Xml.XPath.XPathNodeIterator>  
 [<span data-ttu-id="f55d2-117">XslTransform クラスを使用した XSLT 変換</span><span class="sxs-lookup"><span data-stu-id="f55d2-117">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [<span data-ttu-id="f55d2-118">XslTransform クラスによる XSLT プロセッサの実装</span><span class="sxs-lookup"><span data-stu-id="f55d2-118">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)

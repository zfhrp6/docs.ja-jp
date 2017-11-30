---
title: "XPathNavigator による XML データへのアクセス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c57b46e6-5c77-408f-bc4e-67a5dcc9cc05
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 27f5bccc2ab5f229e8b726b3bff18ea7a590f5c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="accessing-xml-data-using-xpathnavigator"></a><span data-ttu-id="7a0ba-102">XPathNavigator による XML データへのアクセス</span><span class="sxs-lookup"><span data-stu-id="7a0ba-102">Accessing XML Data using XPathNavigator</span></span>
<span data-ttu-id="7a0ba-103"><xref:System.Xml.XPath.XPathNavigator> クラスは、<xref:System.Xml.XPath.XPathDocument> オブジェクトまたは <xref:System.Xml.XmlDocument> オブジェクト内でのノード間の移動、XML データの抽出、および厳密に型指定された XML データにアクセスするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="7a0ba-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to navigate nodes, extract XML data and access strongly typed XML data in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7a0ba-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="7a0ba-104">In This Section</span></span>  
 [<span data-ttu-id="7a0ba-105">XPathNavigator を使用してノード セットのナビゲーション</span><span class="sxs-lookup"><span data-stu-id="7a0ba-105">Node Set Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
 <span data-ttu-id="7a0ba-106"><xref:System.Xml.XPath.XPathNavigator> オブジェクトまたは <xref:System.Xml.XPath.XPathDocument> オブジェクト内で、ノードの移動に使用される <xref:System.Xml.XmlDocument> クラスでのノード セットの移動メソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7a0ba-106">Describes the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class used to navigate nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="7a0ba-107">属性と Namespace XPathNavigator を使用したナビゲーション</span><span class="sxs-lookup"><span data-stu-id="7a0ba-107">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 <span data-ttu-id="7a0ba-108"><xref:System.Xml.XPath.XPathNavigator> クラスにおける属性ノードと名前空間ノードの移動メソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7a0ba-108">Describes the attribute and namespace node navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="7a0ba-109">XPathNavigator による XML データを抽出します。</span><span class="sxs-lookup"><span data-stu-id="7a0ba-109">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="7a0ba-110"><xref:System.Xml.XPath.XPathDocument> オブジェクトまたは <xref:System.Xml.XmlDocument> オブジェクトから XML データを抽出する各種のメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7a0ba-110">Describes the various methods of extracting XML data from an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="7a0ba-111">XPathNavigator による XML データに型指定された厳密にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="7a0ba-111">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="7a0ba-112"><xref:System.Xml.XPath.XPathDocument> オブジェクトまたは <xref:System.Xml.XmlDocument> オブジェクト内で <xref:System.Xml.XPath.XPathNavigator> クラスを使用して、厳密に型指定された XML データにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7a0ba-112">Describes accessing strongly-typed XML data in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="7a0ba-113">ユーザー定義関数および変数</span><span class="sxs-lookup"><span data-stu-id="7a0ba-113">User Defined Functions and Variables</span></span>](../../../../docs/standard/data/xml/user-defined-functions-and-variables.md)  
 <span data-ttu-id="7a0ba-114">カスタム クラス <xref:System.Xml.Xsl.XsltContext> を、拡張関数および変数をサポートする <xref:System.Xml.Xsl.IXsltContextFunction> インターフェイスおよび <xref:System.Xml.Xsl.IXsltContextVariable> インターフェイスと共に実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7a0ba-114">Describes implementing a custom <xref:System.Xml.Xsl.XsltContext> class along with the interfaces <xref:System.Xml.Xsl.IXsltContextFunction> and <xref:System.Xml.Xsl.IXsltContextVariable> that support extension functions and variables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a0ba-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a0ba-115">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="7a0ba-116">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="7a0ba-116">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="7a0ba-117">XPathDocument および XmlDocument を使用して XML データの読み取り</span><span class="sxs-lookup"><span data-stu-id="7a0ba-117">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 [<span data-ttu-id="7a0ba-118">選択、評価、および XPathNavigator を使用して、一致する XML データ</span><span class="sxs-lookup"><span data-stu-id="7a0ba-118">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="7a0ba-119">XPathNavigator による XML データの編集</span><span class="sxs-lookup"><span data-stu-id="7a0ba-119">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="7a0ba-120">XPathNavigator を使用するスキーマの検証</span><span class="sxs-lookup"><span data-stu-id="7a0ba-120">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)

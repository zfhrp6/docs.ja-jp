---
title: "XPathNavigator による XML データの編集"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b1f91616-3115-4264-9821-c66589d11d11
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 488651181aaec34c52f368d8829b1c556e6e746e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="editing-xml-data-using-xpathnavigator"></a><span data-ttu-id="bf8a9-102">XPathNavigator による XML データの編集</span><span class="sxs-lookup"><span data-stu-id="bf8a9-102">Editing XML Data using XPathNavigator</span></span>
<span data-ttu-id="bf8a9-103"><xref:System.Xml.XPath.XPathNavigator> クラスは、<xref:System.Xml.XmlDocument> オブジェクトに含まれる XML ドキュメントでノードと値の挿入、変更、および削除を行うメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="bf8a9-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to insert, modify and remove nodes and values from an XML document contained in an <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="bf8a9-104">ノードと値の挿入、変更、および削除を行うこれらのメソッドを使用するには、<xref:System.Xml.XPath.XPathNavigator> オブジェクトが編集可能である必要があります。つまり、その <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> プロパティを true にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf8a9-104">In order to use any of these methods to insert, modify, and remove nodes and values, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be true.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bf8a9-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="bf8a9-105">In This Section</span></span>  
 [<span data-ttu-id="bf8a9-106">XPathNavigator による XML データを挿入します。</span><span class="sxs-lookup"><span data-stu-id="bf8a9-106">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="bf8a9-107"><xref:System.Xml.XmlDocument> クラスを使用して <xref:System.Xml.XPath.XPathNavigator> オブジェクトに兄弟、子、および属性のノードと値を挿入する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bf8a9-107">Describes how to insert sibling, child, attribute nodes and values in to an <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="bf8a9-108">XPathNavigator による XML データを変更します。</span><span class="sxs-lookup"><span data-stu-id="bf8a9-108">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="bf8a9-109"><xref:System.Xml.XmlDocument> クラスを使用して <xref:System.Xml.XPath.XPathNavigator> オブジェクトのノードと値を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bf8a9-109">Describes how to modify nodes and values in an <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="bf8a9-110">XPathNavigator による XML データを削除します。</span><span class="sxs-lookup"><span data-stu-id="bf8a9-110">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="bf8a9-111"><xref:System.Xml.XmlDocument> クラスを使用して <xref:System.Xml.XPath.XPathNavigator> オブジェクトからノードと値を削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bf8a9-111">Describes how to remove nodes and values from an <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf8a9-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf8a9-112">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="bf8a9-113">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="bf8a9-113">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="bf8a9-114">XPathDocument および XmlDocument を使用して XML データの読み取り</span><span class="sxs-lookup"><span data-stu-id="bf8a9-114">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 [<span data-ttu-id="bf8a9-115">選択、評価、および XPathNavigator を使用して、一致する XML データ</span><span class="sxs-lookup"><span data-stu-id="bf8a9-115">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="bf8a9-116">XPathNavigator による XML データにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="bf8a9-116">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="bf8a9-117">XPathNavigator を使用するスキーマの検証</span><span class="sxs-lookup"><span data-stu-id="bf8a9-117">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)

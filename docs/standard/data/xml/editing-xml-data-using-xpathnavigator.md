---
title: XPathNavigator による XML データの編集
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b1f91616-3115-4264-9821-c66589d11d11
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5c7eb77689c8f7e447ddfb42ff96de3458d3a3b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="editing-xml-data-using-xpathnavigator"></a><span data-ttu-id="3e890-102">XPathNavigator による XML データの編集</span><span class="sxs-lookup"><span data-stu-id="3e890-102">Editing XML Data using XPathNavigator</span></span>
<span data-ttu-id="3e890-103"><xref:System.Xml.XPath.XPathNavigator> クラスは、<xref:System.Xml.XmlDocument> オブジェクトに含まれる XML ドキュメントでノードと値の挿入、変更、および削除を行うメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="3e890-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to insert, modify and remove nodes and values from an XML document contained in an <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="3e890-104">ノードと値の挿入、変更、および削除を行うこれらのメソッドを使用するには、<xref:System.Xml.XPath.XPathNavigator> オブジェクトが編集可能である必要があります。つまり、その <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> プロパティを true にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e890-104">In order to use any of these methods to insert, modify, and remove nodes and values, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be true.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3e890-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="3e890-105">In This Section</span></span>  
 [<span data-ttu-id="3e890-106">XPathNavigator による XML データの挿入</span><span class="sxs-lookup"><span data-stu-id="3e890-106">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="3e890-107"><xref:System.Xml.XmlDocument> クラスを使用して <xref:System.Xml.XPath.XPathNavigator> オブジェクトに兄弟、子、および属性のノードと値を挿入する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3e890-107">Describes how to insert sibling, child, attribute nodes and values in to an <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="3e890-108">XpathNavigator による XML データの変更</span><span class="sxs-lookup"><span data-stu-id="3e890-108">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="3e890-109"><xref:System.Xml.XmlDocument> クラスを使用して <xref:System.Xml.XPath.XPathNavigator> オブジェクトのノードと値を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3e890-109">Describes how to modify nodes and values in an <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="3e890-110">XPathNavigator による XML データの削除</span><span class="sxs-lookup"><span data-stu-id="3e890-110">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="3e890-111"><xref:System.Xml.XmlDocument> クラスを使用して <xref:System.Xml.XPath.XPathNavigator> オブジェクトからノードと値を削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3e890-111">Describes how to remove nodes and values from an <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e890-112">参照</span><span class="sxs-lookup"><span data-stu-id="3e890-112">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="3e890-113">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="3e890-113">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="3e890-114">XPathDocument および XmlDocument を使用した XML データの読み取り</span><span class="sxs-lookup"><span data-stu-id="3e890-114">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 [<span data-ttu-id="3e890-115">XPathNavigator を使用した XML データの選択、評価、および照合</span><span class="sxs-lookup"><span data-stu-id="3e890-115">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="3e890-116">XPathNavigator による XML データへのアクセス</span><span class="sxs-lookup"><span data-stu-id="3e890-116">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="3e890-117">XPathNavigator を使用したスキーマ検証</span><span class="sxs-lookup"><span data-stu-id="3e890-117">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)

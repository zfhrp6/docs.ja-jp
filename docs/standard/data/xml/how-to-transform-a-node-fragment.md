---
title: '方法 : ノード フラグメントを変換する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4cd35e469a16dc2fdb3a7f4afd89d04f67185cd5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568564"
---
# <a name="how-to-transform-a-node-fragment"></a><span data-ttu-id="c481e-102">方法 : ノード フラグメントを変換する</span><span class="sxs-lookup"><span data-stu-id="c481e-102">How to: Transform a Node Fragment</span></span>
<span data-ttu-id="c481e-103"><xref:System.Xml.XmlDocument> オブジェクトまたは <xref:System.Xml.XPath.XPathDocument> オブジェクトに含まれるデータを変換すると、XSLT 変換はドキュメント全体に適用されます。</span><span class="sxs-lookup"><span data-stu-id="c481e-103">When you transform data contained in an <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument> object the XSLT transformations apply to a document as a whole.</span></span> <span data-ttu-id="c481e-104">つまり、ドキュメント ルート ノード以外のノードを指定しても、変換処理では、読み込んだドキュメントのすべてのノードがアクセスされます。</span><span class="sxs-lookup"><span data-stu-id="c481e-104">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="c481e-105">1 つのノード フラグメントを変換するには、ノード フラグメントだけを含むオブジェクトを別に作成し、そのオブジェクトを <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="c481e-105">To transform a node fragment, you must create a separate object containing just the node fragment, and pass that object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="c481e-106">手順</span><span class="sxs-lookup"><span data-stu-id="c481e-106">Procedures</span></span>  
  
#### <a name="to-transform-a-node-fragment"></a><span data-ttu-id="c481e-107">1 つのノード フラグメントを変換するには</span><span class="sxs-lookup"><span data-stu-id="c481e-107">To transform a node fragment</span></span>  
  
1.  <span data-ttu-id="c481e-108">ソース ドキュメントを含むオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="c481e-108">Create an object containing the source document.</span></span>  
  
2.  <span data-ttu-id="c481e-109">変換するノード フラグメントを見つけます。</span><span class="sxs-lookup"><span data-stu-id="c481e-109">Locate the node fragment you wish to transform.</span></span>  
  
3.  <span data-ttu-id="c481e-110">そのノード フラグメントだけの別のオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="c481e-110">Create separate object with just the node fragment.</span></span>  
  
4.  <span data-ttu-id="c481e-111">ノード フラグメントを <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="c481e-111">Pass the node fragment to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c481e-112">例</span><span class="sxs-lookup"><span data-stu-id="c481e-112">Example</span></span>  
 <span data-ttu-id="c481e-113">次の例は、1 つのノード フラグメントを変換して、結果をコンソールに出力します。</span><span class="sxs-lookup"><span data-stu-id="c481e-113">The following example transforms a node fragment and outputs the results to the console.</span></span>  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="c481e-114">入力</span><span class="sxs-lookup"><span data-stu-id="c481e-114">Input</span></span>  
  
##### <a name="booksxml"></a><span data-ttu-id="c481e-115">books.xml</span><span class="sxs-lookup"><span data-stu-id="c481e-115">books.xml</span></span>  
 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a><span data-ttu-id="c481e-116">single.xsl</span><span class="sxs-lookup"><span data-stu-id="c481e-116">single.xsl</span></span>  
 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a><span data-ttu-id="c481e-117">出力</span><span class="sxs-lookup"><span data-stu-id="c481e-117">Output</span></span>  
 <span data-ttu-id="c481e-118">Book title is The Confidence Man.</span><span class="sxs-lookup"><span data-stu-id="c481e-118">Book title is The Confidence Man.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c481e-119">参照</span><span class="sxs-lookup"><span data-stu-id="c481e-119">See Also</span></span>  
 [<span data-ttu-id="c481e-120">XslCompiledTransform クラスの使用</span><span class="sxs-lookup"><span data-stu-id="c481e-120">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)

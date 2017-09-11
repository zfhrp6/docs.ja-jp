---
title: "XML ツリー (LINQ to XML) の変更 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 4ae511a5-4fc9-4178-9c8e-761357deae3f
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9ff0f95afec6248ba7f64812be5f9906c90496d9
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="modifying-xml-trees-linq-to-xml-visual-basic"></a><span data-ttu-id="3ff9d-102">XML ツリー (LINQ to XML) の変更 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ff9d-102">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="3ff9d-103"> は、XML ツリーのメモリ内ストアです。</span><span class="sxs-lookup"><span data-stu-id="3ff9d-103"> is an in-memory store for an XML tree.</span></span> <span data-ttu-id="3ff9d-104">読み込み元の XML ツリーを解析したりした後[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]の場所では、そのツリーを変更し、ファイルに保存したり、リモート サーバーに送信したり、ツリーをシリアル化することができます。</span><span class="sxs-lookup"><span data-stu-id="3ff9d-104">After you load or parse an XML tree from a source, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] lets you modify that tree in place, and then serialize the tree, perhaps saving it to a file or sending it to a remote server.</span></span>  
  
 <span data-ttu-id="3ff9d-105"><xref:System.Xml.Linq.XContainer.Add%2A>。</xref:System.Xml.Linq.XContainer.Add%2A>などの特定のメソッドを使用してツリーを変更するときに</span><span class="sxs-lookup"><span data-stu-id="3ff9d-105">When you modify a tree in place, you use certain methods, such as <xref:System.Xml.Linq.XContainer.Add%2A>.</span></span>  
  
 <span data-ttu-id="3ff9d-106">ただし、これには別の方法もあります。それは、関数型構築を使用して、別の新しいツリーを生成する方法です。</span><span class="sxs-lookup"><span data-stu-id="3ff9d-106">However, there is another approach, which is to use functional construction to generate a new tree with a different shape.</span></span> <span data-ttu-id="3ff9d-107">XML ツリーに対する変更の種類やツリーのサイズによっては、この方法の方が堅牢で、開発も容易になります。</span><span class="sxs-lookup"><span data-stu-id="3ff9d-107">Depending on the types of changes that you need to make to your XML tree, and depending on the size of the tree, this approach can be more robust and easier to develop.</span></span> <span data-ttu-id="3ff9d-108">このセクションの最初のトピックでは、この&2; つの方法を比較します。</span><span class="sxs-lookup"><span data-stu-id="3ff9d-108">The first topic in this section compares these two approaches.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3ff9d-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="3ff9d-109">In This Section</span></span>  
  
|<span data-ttu-id="3ff9d-110">トピック</span><span class="sxs-lookup"><span data-stu-id="3ff9d-110">Topic</span></span>|<span data-ttu-id="3ff9d-111">説明</span><span class="sxs-lookup"><span data-stu-id="3ff9d-111">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="3ff9d-112">メモリ内の XML ツリーの変更と関数型構築 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ff9d-112">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md)|<span data-ttu-id="3ff9d-113">XML ツリーのメモリ内での変更と関数型構築とを比較します。</span><span class="sxs-lookup"><span data-stu-id="3ff9d-113">Compares modifying an XML tree in memory to functional construction.</span></span>|  
|[<span data-ttu-id="3ff9d-114">XML ツリー (Visual Basic) への要素、属性、およびノードの追加</span><span class="sxs-lookup"><span data-stu-id="3ff9d-114">Adding Elements, Attributes, and Nodes to an XML Tree (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/adding-elements-attributes-and-nodes-to-an-xml-tree.md)|<span data-ttu-id="3ff9d-115">XML ツリーへの要素、属性、またはノードの追加に関する情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="3ff9d-115">Provides information about adding elements, attributes, or nodes to an XML tree.</span></span>|  
|[<span data-ttu-id="3ff9d-116">XML ツリー内の要素、属性、およびノードの変更</span><span class="sxs-lookup"><span data-stu-id="3ff9d-116">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|<span data-ttu-id="3ff9d-117">既存の要素、属性、またはノードの変更に関する情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="3ff9d-117">Provides information about modifying existing elements, attributes, or nodes.</span></span>|  
|[<span data-ttu-id="3ff9d-118">XML ツリー (Visual Basic の場合) からの要素、属性、およびノードの削除</span><span class="sxs-lookup"><span data-stu-id="3ff9d-118">Removing Elements, Attributes, and Nodes from an XML Tree (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/removing-elements-attributes-and-nodes-from-an-xml-tree.md)|<span data-ttu-id="3ff9d-119">XML ツリーからの要素、属性、またはノードの削除に関する情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="3ff9d-119">Provides information about removing elements, attributes, or nodes from the XML tree.</span></span>|  
|[<span data-ttu-id="3ff9d-120">(Visual Basic) の名前/値ペアの保持</span><span class="sxs-lookup"><span data-stu-id="3ff9d-120">Maintaining Name/Value Pairs (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/maintaining-name-value-pairs.md)|<span data-ttu-id="3ff9d-121">アプリケーションの情報を名前/値のペアとして保持する方法について説明します。このような情報には、構成情報やグローバル設定があります。</span><span class="sxs-lookup"><span data-stu-id="3ff9d-121">Describes how to maintain application information that is best kept as name/value pairs, such as configuration information or global settings.</span></span>|  
|[<span data-ttu-id="3ff9d-122">方法: Namespace、全体 XML ツリーの変更 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ff9d-122">How to: Change the Namespace for an Entire XML Tree (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-change-the-namespace-for-an-entire-xml-tree.md)|<span data-ttu-id="3ff9d-123">XML ツリーを名前空間の間で移動する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3ff9d-123">Shows how to move an XML tree from one namespace into another.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ff9d-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="3ff9d-124">See Also</span></span>  
 [<span data-ttu-id="3ff9d-125">プログラミング ガイド (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ff9d-125">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)

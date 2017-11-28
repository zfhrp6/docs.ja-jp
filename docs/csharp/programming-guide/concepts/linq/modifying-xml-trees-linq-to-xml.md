---
title: "XML ツリーの変更 (LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 8ec47e6d-2363-4694-be46-8d5ca4d15fc9
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8cf3ffabeb7c3caa5f0e3e38fb6f69551ce791b3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="modifying-xml-trees-linq-to-xml-c"></a><span data-ttu-id="be5c2-102">XML ツリーの変更 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="be5c2-102">Modifying XML Trees (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="be5c2-103"> は、XML ツリーのメモリ内ストアです。</span><span class="sxs-lookup"><span data-stu-id="be5c2-103"> is an in-memory store for an XML tree.</span></span> <span data-ttu-id="be5c2-104">ソースから XML ツリーを読み込んだり解析したりした後に、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] を使用してツリーを直接変更することができます。その後、ツリーをシリアル化して、ファイルに保存したり、リモート サーバーに送信したりできます。</span><span class="sxs-lookup"><span data-stu-id="be5c2-104">After you load or parse an XML tree from a source, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] lets you modify that tree in place, and then serialize the tree, perhaps saving it to a file or sending it to a remote server.</span></span>  
  
 <span data-ttu-id="be5c2-105">ツリーを直接変更する際には、<xref:System.Xml.Linq.XContainer.Add%2A> などの特定のメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="be5c2-105">When you modify a tree in place, you use certain methods, such as <xref:System.Xml.Linq.XContainer.Add%2A>.</span></span>  
  
 <span data-ttu-id="be5c2-106">ただし、これには別の方法もあります。それは、関数型構築を使用して、別の新しいツリーを生成する方法です。</span><span class="sxs-lookup"><span data-stu-id="be5c2-106">However, there is another approach, which is to use functional construction to generate a new tree with a different shape.</span></span> <span data-ttu-id="be5c2-107">XML ツリーに対する変更の種類やツリーのサイズによっては、この方法の方が堅牢で、開発も容易になります。</span><span class="sxs-lookup"><span data-stu-id="be5c2-107">Depending on the types of changes that you need to make to your XML tree, and depending on the size of the tree, this approach can be more robust and easier to develop.</span></span> <span data-ttu-id="be5c2-108">このセクションの最初のトピックでは、この 2 つの方法を比較します。</span><span class="sxs-lookup"><span data-stu-id="be5c2-108">The first topic in this section compares these two approaches.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="be5c2-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="be5c2-109">In This Section</span></span>  
  
|<span data-ttu-id="be5c2-110">トピック</span><span class="sxs-lookup"><span data-stu-id="be5c2-110">Topic</span></span>|<span data-ttu-id="be5c2-111">説明</span><span class="sxs-lookup"><span data-stu-id="be5c2-111">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="be5c2-112">メモリ内の XML ツリーの変更と関数型構築の比較 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="be5c2-112">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)|<span data-ttu-id="be5c2-113">XML ツリーのメモリ内での変更と関数型構築とを比較します。</span><span class="sxs-lookup"><span data-stu-id="be5c2-113">Compares modifying an XML tree in memory to functional construction.</span></span>|  
|[<span data-ttu-id="be5c2-114">XML ツリーへの要素、属性、およびノードの追加</span><span class="sxs-lookup"><span data-stu-id="be5c2-114">Adding Elements, Attributes, and Nodes to an XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/adding-elements-attributes-and-nodes-to-an-xml-tree.md)|<span data-ttu-id="be5c2-115">XML ツリーへの要素、属性、またはノードの追加に関する情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="be5c2-115">Provides information about adding elements, attributes, or nodes to an XML tree.</span></span>|  
|[<span data-ttu-id="be5c2-116">XML ツリー内の要素、属性、およびノードの変更</span><span class="sxs-lookup"><span data-stu-id="be5c2-116">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|<span data-ttu-id="be5c2-117">既存の要素、属性、またはノードの変更に関する情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="be5c2-117">Provides information about modifying existing elements, attributes, or nodes.</span></span>|  
|[<span data-ttu-id="be5c2-118">XML ツリーからの要素、属性、およびノードの削除 (C#)</span><span class="sxs-lookup"><span data-stu-id="be5c2-118">Removing Elements, Attributes, and Nodes from an XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/removing-elements-attributes-and-nodes-from-an-xml-tree.md)|<span data-ttu-id="be5c2-119">XML ツリーからの要素、属性、またはノードの削除に関する情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="be5c2-119">Provides information about removing elements, attributes, or nodes from the XML tree.</span></span>|  
|[<span data-ttu-id="be5c2-120">名前と値のペアの保持 (C#)</span><span class="sxs-lookup"><span data-stu-id="be5c2-120">Maintaining Name/Value Pairs (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/maintaining-name-value-pairs.md)|<span data-ttu-id="be5c2-121">アプリケーションの情報を名前/値のペアとして保持する方法について説明します。このような情報には、構成情報やグローバル設定があります。</span><span class="sxs-lookup"><span data-stu-id="be5c2-121">Describes how to maintain application information that is best kept as name/value pairs, such as configuration information or global settings.</span></span>|  
|[<span data-ttu-id="be5c2-122">方法: XML ツリー全体の名前空間を変更する (C#)</span><span class="sxs-lookup"><span data-stu-id="be5c2-122">How to: Change the Namespace for an Entire XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-change-the-namespace-for-an-entire-xml-tree.md)|<span data-ttu-id="be5c2-123">XML ツリーを名前空間の間で移動する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="be5c2-123">Shows how to move an XML tree from one namespace into another.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="be5c2-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="be5c2-124">See Also</span></span>  
 [<span data-ttu-id="be5c2-125">プログラミング ガイド (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="be5c2-125">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)

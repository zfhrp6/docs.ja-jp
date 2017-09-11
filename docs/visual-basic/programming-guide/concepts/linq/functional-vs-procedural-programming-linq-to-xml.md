---
title: "関数型プログラミングと手続き型プログラミング (LINQ to XML) (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: ea1015a5-d4c8-4d79-8e1e-ba17a40a4f39
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5822ec5f40517b975b786f8c82967e1fbb40decb
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="functional-vs-procedural-programming-linq-to-xml-visual-basic"></a><span data-ttu-id="7fe23-102">関数型プログラミングと手続き型プログラミング (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7fe23-102">Functional vs. Procedural Programming (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="7fe23-103">XML アプリケーションには、次のようにさまざまな種類があります。</span><span class="sxs-lookup"><span data-stu-id="7fe23-103">There are various types of XML applications:</span></span>  
  
-   <span data-ttu-id="7fe23-104">ソース XML ドキュメントを受け取り、そのドキュメントとは構造の異なる新しい XML ドキュメントを生成するアプリケーション</span><span class="sxs-lookup"><span data-stu-id="7fe23-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
-   <span data-ttu-id="7fe23-105">ソース XML ドキュメントを受け取り、HTML や CSV テキスト ファイルなどのまったく異なる形式のドキュメントを生成するアプリケーション</span><span class="sxs-lookup"><span data-stu-id="7fe23-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
-   <span data-ttu-id="7fe23-106">ソース XML ドキュメントを受け取り、データベースにレコードを挿入するアプリケーション</span><span class="sxs-lookup"><span data-stu-id="7fe23-106">Some applications take source XML documents, and insert records into a database.</span></span>  
  
-   <span data-ttu-id="7fe23-107">データベースなどの別のソースからデータを受け取り、そのデータから XML ドキュメントを作成するアプリケーション</span><span class="sxs-lookup"><span data-stu-id="7fe23-107">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="7fe23-108">XML アプリケーションには他にも種類がありますが、上記のアプリケーションは XML プログラマが実装する必要がある代表的な機能です。</span><span class="sxs-lookup"><span data-stu-id="7fe23-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="7fe23-109">上記のすべてのアプリケーションで、開発者は&2; つの対照的な方法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="7fe23-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
-   <span data-ttu-id="7fe23-110">宣言型の方法を使用する関数型構築</span><span class="sxs-lookup"><span data-stu-id="7fe23-110">Functional construction using a declarative approach.</span></span>  
  
-   <span data-ttu-id="7fe23-111">プロシージャ コードを使用するメモリ内の XML ツリーの変更</span><span class="sxs-lookup"><span data-stu-id="7fe23-111">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="7fe23-112">LINQ to XML は両方の方法をサポートします。</span><span class="sxs-lookup"><span data-stu-id="7fe23-112">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="7fe23-113">関数型の方法を使用する場合は、ソース ドキュメントを受け取り、必要な構造を持つ完全に新しいドキュメントが生成される変換を記述します。</span><span class="sxs-lookup"><span data-stu-id="7fe23-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="7fe23-114">XML ツリーを直接変更する場合は、メモリ内の XML ツリーでノード間を移動し、必要に応じてノードを挿入、削除、変更します。</span><span class="sxs-lookup"><span data-stu-id="7fe23-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="7fe23-115">いずれの方法でも LINQ to XML を使用できます。</span><span class="sxs-lookup"><span data-stu-id="7fe23-115">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="7fe23-116">同じクラスを使用し、場合によっては同じメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="7fe23-116">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="7fe23-117">ただし、2 つの方法の構造と目標はかなり異なります。</span><span class="sxs-lookup"><span data-stu-id="7fe23-117">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="7fe23-118">たとえば、これらの方法のうち、どちらのパフォーマンスが優れているか、また使用するメモリ量はどちらが多い (または少ない) かは、状況によって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7fe23-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="7fe23-119">また、どちらの方法が保守性に優れたコードをより簡単に記述し生成できるかも、状況によって異なります。</span><span class="sxs-lookup"><span data-stu-id="7fe23-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="7fe23-120">比較する&2; つの方法を表示するには、次を参照してください。[メモリ内 XML ツリーの変更とします。関数型構築 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md)します。</span><span class="sxs-lookup"><span data-stu-id="7fe23-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md).</span></span>  
  
 <span data-ttu-id="7fe23-121">関数型変換の作成に関するチュートリアルについては、次を参照してください。[純粋関数型変換の XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="7fe23-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fe23-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="7fe23-122">See Also</span></span>  
 [<span data-ttu-id="7fe23-123">LINQ to XML プログラミングの概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7fe23-123">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)

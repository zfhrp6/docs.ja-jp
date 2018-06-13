---
title: 関数型プログラミングと手続き型プログラミング (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: 16d78e967fd5379940ac93c82e3bb59c60941e58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328215"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a><span data-ttu-id="c557b-102">関数型プログラミングと手続き型プログラミング (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c557b-102">Functional vs. Procedural Programming (LINQ to XML) (C#)</span></span>
<span data-ttu-id="c557b-103">XML アプリケーションには、次のようにさまざまな種類があります。</span><span class="sxs-lookup"><span data-stu-id="c557b-103">There are various types of XML applications:</span></span>  
  
-   <span data-ttu-id="c557b-104">ソース XML ドキュメントを受け取り、そのドキュメントとは構造の異なる新しい XML ドキュメントを生成するアプリケーション</span><span class="sxs-lookup"><span data-stu-id="c557b-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
-   <span data-ttu-id="c557b-105">ソース XML ドキュメントを受け取り、HTML や CSV テキスト ファイルなどのまったく異なる形式のドキュメントを生成するアプリケーション</span><span class="sxs-lookup"><span data-stu-id="c557b-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
-   <span data-ttu-id="c557b-106">ソース XML ドキュメントを受け取り、データベースにレコードを挿入するアプリケーション</span><span class="sxs-lookup"><span data-stu-id="c557b-106">Some applications take source XML documents, and insert records into a database.</span></span>  
  
-   <span data-ttu-id="c557b-107">データベースなどの別のソースからデータを受け取り、そのデータから XML ドキュメントを作成するアプリケーション</span><span class="sxs-lookup"><span data-stu-id="c557b-107">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="c557b-108">XML アプリケーションには他にも種類がありますが、上記のアプリケーションは XML プログラマが実装する必要がある代表的な機能です。</span><span class="sxs-lookup"><span data-stu-id="c557b-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="c557b-109">上記のすべてのアプリケーションで、開発者は 2 つの対照的な方法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c557b-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
-   <span data-ttu-id="c557b-110">宣言型の方法を使用する関数型構築</span><span class="sxs-lookup"><span data-stu-id="c557b-110">Functional construction using a declarative approach.</span></span>  
  
-   <span data-ttu-id="c557b-111">プロシージャ コードを使用するメモリ内の XML ツリーの変更</span><span class="sxs-lookup"><span data-stu-id="c557b-111">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="c557b-112">LINQ to XML は両方の方法をサポートします。</span><span class="sxs-lookup"><span data-stu-id="c557b-112">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="c557b-113">関数型の方法を使用する場合は、ソース ドキュメントを受け取り、必要な構造を持つ完全に新しいドキュメントが生成される変換を記述します。</span><span class="sxs-lookup"><span data-stu-id="c557b-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="c557b-114">XML ツリーを直接変更する場合は、メモリ内の XML ツリーでノード間を移動し、必要に応じてノードを挿入、削除、変更します。</span><span class="sxs-lookup"><span data-stu-id="c557b-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="c557b-115">いずれの方法でも LINQ to XML を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c557b-115">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="c557b-116">同じクラスを使用し、場合によっては同じメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="c557b-116">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="c557b-117">ただし、2 つの方法の構造と目標はかなり異なります。</span><span class="sxs-lookup"><span data-stu-id="c557b-117">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="c557b-118">たとえば、これらの方法のうち、どちらのパフォーマンスが優れているか、また使用するメモリ量はどちらが多い (または少ない) かは、状況によって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c557b-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="c557b-119">また、どちらの方法が保守性に優れたコードをより簡単に記述し生成できるかも、状況によって異なります。</span><span class="sxs-lookup"><span data-stu-id="c557b-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="c557b-120">2 つの方法の違いについては、「[メモリ内の XML ツリーの変更と関数型構築の比較 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c557b-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="c557b-121">関数型変換の記述に関するチュートリアルについては、「[XML の純粋関数型変換 (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c557b-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c557b-122">参照</span><span class="sxs-lookup"><span data-stu-id="c557b-122">See Also</span></span>  
 [<span data-ttu-id="c557b-123">LINQ to XML プログラミングの概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="c557b-123">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)

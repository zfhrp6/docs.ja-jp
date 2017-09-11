---
title: "方法: XmlReader (Visual Basic の場合) からの XML フラグメントをストリーム出力 |Microsoft ドキュメント"
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
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c9c60bb4730ef6569390f76f63c40a2cbd1c9524
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a><span data-ttu-id="553d4-102">方法: XML フラグメントをストリームから XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="553d4-102">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span></span>
<span data-ttu-id="553d4-103">大きな XML ファイルを処理する必要があるときに、XML ツリー全体をメモリに読み込むことができない場合があります。</span><span class="sxs-lookup"><span data-stu-id="553d4-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="553d4-104">このトピックは、 <xref:System.Xml.XmlReader>。</xref:System.Xml.XmlReader>を使用してフラグメントをストリーム出力する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="553d4-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="553d4-105">使用する最も効果的な方法のいずれか、<xref:System.Xml.XmlReader>を読み取る<xref:System.Xml.Linq.XElement>オブジェクト、独自のカスタムの軸メソッドを作成する方法です</xref:System.Xml.Linq.XElement></xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="553d4-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="553d4-106">軸メソッド通常コレクションを返しますなど<xref:System.Collections.Generic.IEnumerable%601>の<xref:System.Xml.Linq.XElement>、このトピックの例のように、</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> 。</span><span class="sxs-lookup"><span data-stu-id="553d4-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="553d4-107">カスタムの軸メソッドを呼び出して XML フラグメントを作成した後で、<xref:System.Xml.Linq.XNode.ReadFrom%2A>メソッドを使用してコレクションを返す`yield return`</xref:System.Xml.Linq.XNode.ReadFrom%2A>。</span><span class="sxs-lookup"><span data-stu-id="553d4-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="553d4-108">これにより、カスタムの軸メソッドに遅延実行セマンティクスが付加されます。</span><span class="sxs-lookup"><span data-stu-id="553d4-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="553d4-109">XML ツリーを作成する場合、<xref:System.Xml.XmlReader>オブジェクト、<xref:System.Xml.XmlReader>要素に配置する必要があります</xref:System.Xml.XmlReader></xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="553d4-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="553d4-110"><xref:System.Xml.Linq.XNode.ReadFrom%2A>は、要素の終了タグを読み取るまで、メソッドは返されません</xref:System.Xml.Linq.XNode.ReadFrom%2A>。</span><span class="sxs-lookup"><span data-stu-id="553d4-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="553d4-111">部分ツリーを作成する場合は、インスタンスを作成できる、<xref:System.Xml.XmlReader>に変換するノードのリーダーを配置し、<xref:System.Xml.Linq.XElement>ツリーし、作成、<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XElement></xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="553d4-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
 <span data-ttu-id="553d4-112">トピック[方法: ヘッダー情報 (Visual Basic) にアクセスして XML フラグメントをストリーム](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md)情報より複雑なドキュメントをストリームする方法の例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="553d4-112">The topic [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>  
  
 <span data-ttu-id="553d4-113">トピック[方法: 実行のストリーミング変換の大きな XML ドキュメント (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md)最小メモリ量を低く抑えながら非常に大きな XML ドキュメントに変換する LINQ to XML の使用例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="553d4-113">The topic [How to: Perform Streaming Transform of Large XML Documents (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="553d4-114">例</span><span class="sxs-lookup"><span data-stu-id="553d4-114">Example</span></span>  
 <span data-ttu-id="553d4-115">次の例では、カスタムの軸メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="553d4-115">This example creates a custom axis method.</span></span> <span data-ttu-id="553d4-116">このメソッドに対してクエリを実行するには、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] クエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="553d4-116">You can query it by using a [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query.</span></span> <span data-ttu-id="553d4-117">カスタムの軸メソッド `StreamRootChildDoc` は、`Child` 要素が繰り返し出現するドキュメントを読み取るために特に設計されたメソッドです。</span><span class="sxs-lookup"><span data-stu-id="553d4-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
<span data-ttu-id="553d4-118"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="553d4-118"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="553d4-119">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="553d4-119">This example produces the following output:</span></span>  
  
<span data-ttu-id="553d4-120"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="553d4-120"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="553d4-121">この例のソース ドキュメントは、非常に小さなドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="553d4-121">In this example, the source document is very small.</span></span> <span data-ttu-id="553d4-122">ただし、何百万の `Child` 要素があっても、この例で使用されるメモリは非常に少量です。</span><span class="sxs-lookup"><span data-stu-id="553d4-122">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="553d4-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="553d4-123">See Also</span></span>  
 <span data-ttu-id="553d4-124">[チュートリアル: Visual Basic での IEnumerable(Of T) の実装](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md) </span><span class="sxs-lookup"><span data-stu-id="553d4-124">[Walkthrough: Implementing IEnumerable(Of T) in Visual Basic](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md) </span></span>  
<span data-ttu-id="553d4-125"> [(Visual Basic) の XML の解析](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)</span><span class="sxs-lookup"><span data-stu-id="553d4-125"> [Parsing XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)</span></span>

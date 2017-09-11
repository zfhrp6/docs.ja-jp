---
title: "読み込みまたは XML2 を解析中に空白の維持 |Microsoft ドキュメント"
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
ms.assetid: ef6518e0-2c8d-462c-8b92-a16e9dc737ad
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
ms.openlocfilehash: a2872c1e2354c0a0bd106f7fb945542ce37e7774
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a><span data-ttu-id="46a92-102">XML の読み込み時または解析時の空白の維持</span><span class="sxs-lookup"><span data-stu-id="46a92-102">Preserving White Space while Loading or Parsing XML</span></span>
<span data-ttu-id="46a92-103">このトピックでは、空白に対する [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] の動作を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="46a92-103">This topic describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span></span>  
  
 <span data-ttu-id="46a92-104">一般的なシナリオでは、インデントされた XML を読み取り、メモリ内に空白のテキスト ノードなしで (つまり空白を維持せずに) XML ツリーを作成し、XML に対して何らかの操作を実行し、インデント付きで XML を保存します。</span><span class="sxs-lookup"><span data-stu-id="46a92-104">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="46a92-105">書式を設定して XML をシリアル化する場合は、XML ツリー内の有意の空白のみが維持されます。</span><span class="sxs-lookup"><span data-stu-id="46a92-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="46a92-106">これが [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] の既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="46a92-106">This is the default behavior for [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span></span>  
  
 <span data-ttu-id="46a92-107">もう&1; つのよくあるシナリオは、意図的にインデントされた XML を読み取って変更する場合です。</span><span class="sxs-lookup"><span data-stu-id="46a92-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="46a92-108">場合によっては、このインデントを一切変更しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="46a92-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="46a92-109">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] でこれを実現するには、XML を読み込む際または解析する際に空白を維持し、XML をシリアル化するときに書式設定を無効にします。</span><span class="sxs-lookup"><span data-stu-id="46a92-109">To do this in [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
 <span data-ttu-id="46a92-110">このトピックでは、空白に対する、XML ツリーを設定するメソッドの動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="46a92-110">This topic describes the white space behavior of methods that populate XML trees.</span></span> <span data-ttu-id="46a92-111">XML ツリーをシリアル化する場合は、空白を制御する方法の詳細については、次を参照してください。[維持空白中にシリアル化する](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md)です。</span><span class="sxs-lookup"><span data-stu-id="46a92-111">For information about controlling white space when you serialize XML trees, see [Preserving White Space While Serializing](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).</span></span>  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a><span data-ttu-id="46a92-112">XML ツリーを設定するメソッドの動作</span><span class="sxs-lookup"><span data-stu-id="46a92-112">Behavior of Methods that Populate XML Trees</span></span>  
 <span data-ttu-id="46a92-113">以下の方法で、<xref:System.Xml.Linq.XElement>と<xref:System.Xml.Linq.XDocument>クラスは、XML ツリーを設定します</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="46a92-113">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes populate an XML tree.</span></span> <span data-ttu-id="46a92-114">ファイルから XML ツリーを設定することができます、 <xref:System.IO.TextReader>、 <xref:System.Xml.XmlReader>、または文字列:</xref:System.Xml.XmlReader> </xref:System.IO.TextReader></span><span class="sxs-lookup"><span data-stu-id="46a92-114">You can populate an XML tree from a file, a <xref:System.IO.TextReader>, an <xref:System.Xml.XmlReader>, or a string:</span></span>  
  
-   <span data-ttu-id="46a92-115"><xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="46a92-115"><xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="46a92-116"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="46a92-116"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="46a92-117"><xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="46a92-117"><xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="46a92-118"><xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="46a92-118"><xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName></span></span>  
  
 <span data-ttu-id="46a92-119">メソッドを取らない場合<xref:System.Xml.Linq.LoadOptions>を引数としては維持されません余分な空白</xref:System.Xml.Linq.LoadOptions>。</span><span class="sxs-lookup"><span data-stu-id="46a92-119">If the method does not take <xref:System.Xml.Linq.LoadOptions> as an argument, the method will not preserve insignificant white space.</span></span>  
  
 <span data-ttu-id="46a92-120">ほとんどの場合、メソッドを取る場合<xref:System.Xml.Linq.LoadOptions>を引数として必要に応じてとして維持できます余分な空白、XML ツリー内のテキスト ノード</xref:System.Xml.Linq.LoadOptions>。</span><span class="sxs-lookup"><span data-stu-id="46a92-120">In most cases, if the method takes <xref:System.Xml.Linq.LoadOptions> as an argument, you can optionally preserve insignificant white space as text nodes in the XML tree.</span></span> <span data-ttu-id="46a92-121">ただし、このメソッドがから XML を読み込んでいる場合、 <xref:System.Xml.XmlReader>、<xref:System.Xml.XmlReader>空白を維持するかどうかを決定します</xref:System.Xml.XmlReader></xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="46a92-121">However, if the method is loading the XML from an <xref:System.Xml.XmlReader>, then the <xref:System.Xml.XmlReader> determines whether white space will be preserved or not.</span></span> <span data-ttu-id="46a92-122">設定<xref:System.Xml.Linq.LoadOptions>効果はありません</xref:System.Xml.Linq.LoadOptions>。</span><span class="sxs-lookup"><span data-stu-id="46a92-122">Setting <xref:System.Xml.Linq.LoadOptions> will have no effect.</span></span>  
  
 <span data-ttu-id="46a92-123">これらのメソッドでは、空白を維持すると場合、意味のない空白が挿入として XML ツリーに<xref:System.Xml.Linq.XText>ノード</xref:System.Xml.Linq.XText>。</span><span class="sxs-lookup"><span data-stu-id="46a92-123">With these methods, if white space is preserved, insignificant white space is inserted into the XML tree as <xref:System.Xml.Linq.XText> nodes.</span></span> <span data-ttu-id="46a92-124">空白が維持されない場合、テキスト ノードは挿入されません。</span><span class="sxs-lookup"><span data-stu-id="46a92-124">If white space is not preserved, text nodes are not inserted.</span></span>  
  
 <span data-ttu-id="46a92-125"><xref:System.Xml.XmlWriter>。</xref:System.Xml.XmlWriter>を使用して XML ツリーを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="46a92-125">You can create an XML tree by using an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="46a92-126">書き込まれたノード、<xref:System.Xml.XmlWriter>がツリーに挿入されます</xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="46a92-126">Nodes that are written to the <xref:System.Xml.XmlWriter> are populated in the tree.</span></span> <span data-ttu-id="46a92-127">ただし、このメソッドを使用して XML ツリーを構築すると、ノードが空白かどうかにかかわらず、また空白に意味があるかどうかにかかわらず、すべてのノードが維持されます。</span><span class="sxs-lookup"><span data-stu-id="46a92-127">However, when you build an XML tree using this method, all nodes are preserved, regardless of whether the node is white space or not, or whether the white space is significant or not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46a92-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="46a92-128">See Also</span></span>  
 [<span data-ttu-id="46a92-129">(Visual Basic) の XML の解析</span><span class="sxs-lookup"><span data-stu-id="46a92-129">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)

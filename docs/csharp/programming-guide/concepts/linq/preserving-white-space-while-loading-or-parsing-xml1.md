---
title: XML の読み込み時または解析時の空白の維持1
ms.date: 07/20/2015
ms.assetid: f3ff58c4-55aa-4fcd-b933-e3a2ee6e706c
ms.openlocfilehash: f863a80d3e949ddc2cfe630ae3c309009315d020
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a><span data-ttu-id="79c4d-102">XML の読み込み時または解析時の空白の維持</span><span class="sxs-lookup"><span data-stu-id="79c4d-102">Preserving White Space while Loading or Parsing XML</span></span>
<span data-ttu-id="79c4d-103">このトピックでは、空白に対する [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の動作を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="79c4d-103">This topic describes how to control the white-space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="79c4d-104">一般的なシナリオでは、インデントされた XML を読み取り、メモリ内に空白のテキスト ノードなしで (つまり空白を維持せずに) XML ツリーを作成し、XML に対して何らかの操作を実行し、インデント付きで XML を保存します。</span><span class="sxs-lookup"><span data-stu-id="79c4d-104">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="79c4d-105">書式を設定して XML をシリアル化する場合は、XML ツリー内の有意の空白のみが維持されます。</span><span class="sxs-lookup"><span data-stu-id="79c4d-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="79c4d-106">これが [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="79c4d-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="79c4d-107">もう 1 つのよくあるシナリオは、意図的にインデントされた XML を読み取って変更する場合です。</span><span class="sxs-lookup"><span data-stu-id="79c4d-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="79c4d-108">場合によっては、このインデントを一切変更しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="79c4d-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="79c4d-109">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] でこれを実現するには、XML を読み込む際または解析する際に空白を維持し、XML をシリアル化するときに書式設定を無効にします。</span><span class="sxs-lookup"><span data-stu-id="79c4d-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
 <span data-ttu-id="79c4d-110">このトピックでは、空白に対する、XML ツリーを設定するメソッドの動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="79c4d-110">This topic describes the white-space behavior of methods that populate XML trees.</span></span> <span data-ttu-id="79c4d-111">XML ツリーをシリアル化するときの空白の制御については、「[シリアル化時の空白の維持](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-serializing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79c4d-111">For information about controlling white space when you serialize XML trees, see [Preserving White Space While Serializing](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).</span></span>  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a><span data-ttu-id="79c4d-112">XML ツリーを設定するメソッドの動作</span><span class="sxs-lookup"><span data-stu-id="79c4d-112">Behavior of Methods that Populate XML Trees</span></span>  
 <span data-ttu-id="79c4d-113"><xref:System.Xml.Linq.XElement> クラスと <xref:System.Xml.Linq.XDocument> クラスにある次のメソッドは、XML ツリーを設定します。</span><span class="sxs-lookup"><span data-stu-id="79c4d-113">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes populate an XML tree.</span></span> <span data-ttu-id="79c4d-114">XML ツリーは、ファイル、<xref:System.IO.TextReader>、<xref:System.Xml.XmlReader>、または文字列から設定することができます。</span><span class="sxs-lookup"><span data-stu-id="79c4d-114">You can populate an XML tree from a file, a <xref:System.IO.TextReader>, an <xref:System.Xml.XmlReader>, or a string:</span></span>  
  
-   <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="79c4d-115">メソッドが <xref:System.Xml.Linq.LoadOptions> を引数として受け取らない場合、意味のない空白は維持されません。</span><span class="sxs-lookup"><span data-stu-id="79c4d-115">If the method does not take <xref:System.Xml.Linq.LoadOptions> as an argument, the method will not preserve insignificant white space.</span></span>  
  
 <span data-ttu-id="79c4d-116">ほとんどの場合、メソッドが <xref:System.Xml.Linq.LoadOptions> を引数として受け取ると、意味のない空白を XML ツリー内のテキスト ノードとして維持できます。これは、オプションの動作です。</span><span class="sxs-lookup"><span data-stu-id="79c4d-116">In most cases, if the method takes <xref:System.Xml.Linq.LoadOptions> as an argument, you can optionally preserve insignificant white space as text nodes in the XML tree.</span></span> <span data-ttu-id="79c4d-117">ただし、メソッドが <xref:System.Xml.XmlReader> から XML を読み込んでいる場合は、<xref:System.Xml.XmlReader> によって空白を維持するかどうかが決定されます。</span><span class="sxs-lookup"><span data-stu-id="79c4d-117">However, if the method is loading the XML from an <xref:System.Xml.XmlReader>, then the <xref:System.Xml.XmlReader> determines whether white space will be preserved or not.</span></span> <span data-ttu-id="79c4d-118"><xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> を設定しても効果はありません。</span><span class="sxs-lookup"><span data-stu-id="79c4d-118">Setting <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> will have no effect.</span></span>  
  
 <span data-ttu-id="79c4d-119">これらのメソッドで空白を維持すると、意味のない空白が <xref:System.Xml.Linq.XText> ノードとして XML ツリーに挿入されます。</span><span class="sxs-lookup"><span data-stu-id="79c4d-119">With these methods, if white space is preserved, insignificant white space is inserted into the XML tree as <xref:System.Xml.Linq.XText> nodes.</span></span> <span data-ttu-id="79c4d-120">空白が維持されない場合、テキスト ノードは挿入されません。</span><span class="sxs-lookup"><span data-stu-id="79c4d-120">If white space is not preserved, text nodes are not inserted.</span></span>  
  
 <span data-ttu-id="79c4d-121"><xref:System.Xml.XmlWriter> を使用して、XML ツリーを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="79c4d-121">You can create an XML tree by using an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="79c4d-122"><xref:System.Xml.XmlWriter> に書き込まれたノードが、ツリーに挿入されます。</span><span class="sxs-lookup"><span data-stu-id="79c4d-122">Nodes that are written to the <xref:System.Xml.XmlWriter> are populated in the tree.</span></span> <span data-ttu-id="79c4d-123">ただし、このメソッドを使用して XML ツリーを構築すると、ノードが空白かどうかにかかわらず、また空白に意味があるかどうかにかかわらず、すべてのノードが維持されます。</span><span class="sxs-lookup"><span data-stu-id="79c4d-123">However, when you build an XML tree using this method, all nodes are preserved, regardless of whether the node is white space or not, or whether the white space is significant or not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79c4d-124">参照</span><span class="sxs-lookup"><span data-stu-id="79c4d-124">See Also</span></span>  
 [<span data-ttu-id="79c4d-125">XML の解析 (C#)</span><span class="sxs-lookup"><span data-stu-id="79c4d-125">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)

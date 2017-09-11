---
title: "Serializing2 空白の維持、|Microsoft ドキュメント"
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
ms.assetid: 2d7abbd4-37f4-422b-89dd-0a694b5edc17
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
ms.openlocfilehash: de06e1a5a217644a2eae99f8c7752ee780594d22
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="c75bf-102">シリアル化時の空白の維持</span><span class="sxs-lookup"><span data-stu-id="c75bf-102">Preserving White Space While Serializing</span></span>
<span data-ttu-id="c75bf-103">このトピックでは、XML ツリーをシリアル化するときに空白を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c75bf-103">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="c75bf-104">一般的なシナリオでは、インデントされた XML を読み取り、メモリ内に空白のテキスト ノードなしで (つまり空白を維持せずに) XML ツリーを作成し、XML に対して何らかの操作を実行し、インデント付きで XML を保存します。</span><span class="sxs-lookup"><span data-stu-id="c75bf-104">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="c75bf-105">書式を設定して XML をシリアル化する場合は、XML ツリー内の有意の空白のみが維持されます。</span><span class="sxs-lookup"><span data-stu-id="c75bf-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="c75bf-106">これが [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] の既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="c75bf-106">This is the default behavior for [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span></span>  
  
 <span data-ttu-id="c75bf-107">もう&1; つのよくあるシナリオは、意図的にインデントされた XML を読み取って変更する場合です。</span><span class="sxs-lookup"><span data-stu-id="c75bf-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="c75bf-108">場合によっては、このインデントを一切変更しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c75bf-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="c75bf-109">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] でこれを実現するには、XML を読み込む際または解析する際に空白を維持し、XML をシリアル化するときに書式設定を無効にします。</span><span class="sxs-lookup"><span data-stu-id="c75bf-109">To do this in [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="c75bf-110">XML ツリーをシリアル化するメソッドの空白に関する動作</span><span class="sxs-lookup"><span data-stu-id="c75bf-110">White Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="c75bf-111">以下の方法で、<xref:System.Xml.Linq.XElement>と<xref:System.Xml.Linq.XDocument>クラスは、XML ツリーをシリアル化します</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="c75bf-111">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="c75bf-112">ファイル、XML ツリーをシリアル化することができます、 <xref:System.IO.TextReader>、または<xref:System.Xml.XmlReader>.</xref:System.Xml.XmlReader> </xref:System.IO.TextReader></span><span class="sxs-lookup"><span data-stu-id="c75bf-112">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="c75bf-113">`ToString` メソッドは、文字列にシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="c75bf-113">The `ToString` method serializes to a string.</span></span>  
  
-   <span data-ttu-id="c75bf-114"><xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="c75bf-114"><xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="c75bf-115"><xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="c75bf-115"><xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="c75bf-116"><xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="c75bf-116"><xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="c75bf-117"><xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="c75bf-117"><xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=fullName></span></span>  
  
 <span data-ttu-id="c75bf-118">メソッドを取らない場合<xref:System.Xml.Linq.SaveOptions>を引数として、メソッドは書式設定 (インデント) シリアル化された XML です</xref:System.Xml.Linq.SaveOptions>。</span><span class="sxs-lookup"><span data-stu-id="c75bf-118">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="c75bf-119">この場合、XML ツリー内の意味のない空白はすべて破棄されます。</span><span class="sxs-lookup"><span data-stu-id="c75bf-119">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="c75bf-120">メソッドが受け取る場合<xref:System.Xml.Linq.SaveOptions>を引数として指定できます、メソッドをフォーマットする (インデント) シリアル化された XML です</xref:System.Xml.Linq.SaveOptions>。</span><span class="sxs-lookup"><span data-stu-id="c75bf-120">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="c75bf-121">この場合、XML ツリー内の空白はすべて維持されます。</span><span class="sxs-lookup"><span data-stu-id="c75bf-121">In this case, all white space in the XML tree is preserved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c75bf-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="c75bf-122">See Also</span></span>  
 [<span data-ttu-id="c75bf-123">XML ツリーをシリアル化する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c75bf-123">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)

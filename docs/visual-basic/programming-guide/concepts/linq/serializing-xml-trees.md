---
title: "(Visual Basic) の XML ツリーをシリアル化 |Microsoft ドキュメント"
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
ms.assetid: 2c340695-a726-4030-85be-6975d8a149cf
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
ms.openlocfilehash: a63e875b1c1391ec1bb2b0ae64be9f9cff28d87d
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="serializing-xml-trees-visual-basic"></a><span data-ttu-id="31da5-102">XML ツリーをシリアル化する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31da5-102">Serializing XML Trees (Visual Basic)</span></span>
<span data-ttu-id="31da5-103">XML ツリーのシリアル化とは、XML ツリーから XML を生成することです。</span><span class="sxs-lookup"><span data-stu-id="31da5-103">Serializing an XML tree means generating XML from the XML tree.</span></span> <span data-ttu-id="31da5-104">具象実装へのファイルにシリアル化することができます、<xref:System.IO.TextWriter>クラス、または<xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter>の具体的な実装に</xref:System.IO.TextWriter></span><span class="sxs-lookup"><span data-stu-id="31da5-104">You can serialize to a file, to a concrete implementation of the <xref:System.IO.TextWriter> class, or to a concrete implementation of an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="31da5-105">シリアル化では、</span><span class="sxs-lookup"><span data-stu-id="31da5-105">You can control various aspects of serialization.</span></span> <span data-ttu-id="31da5-106">シリアル化された XML をインデントするかどうかや、XML 宣言を書き込むかどうかなど、さまざまな側面を制御できます。</span><span class="sxs-lookup"><span data-stu-id="31da5-106">For example, you can control whether to indent the serialized XML, and whether to write an XML declaration.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="31da5-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="31da5-107">In This Section</span></span>  
  
|<span data-ttu-id="31da5-108">トピック</span><span class="sxs-lookup"><span data-stu-id="31da5-108">Topic</span></span>|<span data-ttu-id="31da5-109">説明</span><span class="sxs-lookup"><span data-stu-id="31da5-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="31da5-110">シリアル化時の空白の維持</span><span class="sxs-lookup"><span data-stu-id="31da5-110">Preserving White Space While Serializing</span></span>](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md)|<span data-ttu-id="31da5-111">XML ツリーをシリアル化する際の空白の動作を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="31da5-111">Describes how to control white space behavior when you serialize XML trees.</span></span>|  
|[<span data-ttu-id="31da5-112">XML 宣言 (Visual Basic) でシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="31da5-112">Serializing with an XML Declaration (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-with-an-xml-declaration.md)|<span data-ttu-id="31da5-113">XML 宣言を含む XML ツリーをシリアル化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="31da5-113">Describes how to serialize an XML tree that includes an XML declaration.</span></span>|  
|[<span data-ttu-id="31da5-114">ファイル、TextWriter、および XmlWriter へのシリアル化</span><span class="sxs-lookup"><span data-stu-id="31da5-114">Serializing to Files, TextWriters, and XmlWriters</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-to-files-textwriters-and-xmlwriters.md)|<span data-ttu-id="31da5-115">ドキュメントをシリアル化する方法について説明する<xref:System.IO.File>、 <xref:System.IO.TextWriter>、または<xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.IO.TextWriter> </xref:System.IO.File></span><span class="sxs-lookup"><span data-stu-id="31da5-115">Describes how to serialize a document to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="31da5-116">XmlReader (XSLT の呼び出し) にシリアル化する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31da5-116">Serializing to an XmlReader (Invoking XSLT) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-to-an-xmlreader-invoking-xslt.md)|<span data-ttu-id="31da5-117">作成する方法について説明する<xref:System.Xml.XmlReader>XML ツリーの内容を読み取るための別のモジュールを有効にする</xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="31da5-117">Describes how to create a <xref:System.Xml.XmlReader> that enables another module to read the contents of an XML tree.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="31da5-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="31da5-118">See Also</span></span>  
 [<span data-ttu-id="31da5-119">プログラミング ガイド (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31da5-119">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)

---
title: (Visual Basic) の XML ツリーをシリアル化します。
ms.date: 07/20/2015
ms.assetid: 2c340695-a726-4030-85be-6975d8a149cf
ms.openlocfilehash: 009bd3e229ad6debb0f4176c18fc9cb712154197
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645344"
---
# <a name="serializing-xml-trees-visual-basic"></a><span data-ttu-id="581b0-102">(Visual Basic) の XML ツリーをシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="581b0-102">Serializing XML Trees (Visual Basic)</span></span>
<span data-ttu-id="581b0-103">XML ツリーのシリアル化とは、XML ツリーから XML を生成することです。</span><span class="sxs-lookup"><span data-stu-id="581b0-103">Serializing an XML tree means generating XML from the XML tree.</span></span> <span data-ttu-id="581b0-104">ファイル、<xref:System.IO.TextWriter> クラスの具象実装、または <xref:System.Xml.XmlWriter> クラスの具象実装へのシリアル化を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="581b0-104">You can serialize to a file, to a concrete implementation of the <xref:System.IO.TextWriter> class, or to a concrete implementation of an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="581b0-105">シリアル化では、</span><span class="sxs-lookup"><span data-stu-id="581b0-105">You can control various aspects of serialization.</span></span> <span data-ttu-id="581b0-106">シリアル化された XML をインデントするかどうかや、XML 宣言を書き込むかどうかなど、さまざまな側面を制御できます。</span><span class="sxs-lookup"><span data-stu-id="581b0-106">For example, you can control whether to indent the serialized XML, and whether to write an XML declaration.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="581b0-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="581b0-107">In This Section</span></span>  
  
|<span data-ttu-id="581b0-108">トピック</span><span class="sxs-lookup"><span data-stu-id="581b0-108">Topic</span></span>|<span data-ttu-id="581b0-109">説明</span><span class="sxs-lookup"><span data-stu-id="581b0-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="581b0-110">シリアル化時の空白の維持</span><span class="sxs-lookup"><span data-stu-id="581b0-110">Preserving White Space While Serializing</span></span>](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md)|<span data-ttu-id="581b0-111">XML ツリーをシリアル化する際の空白の動作を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="581b0-111">Describes how to control white space behavior when you serialize XML trees.</span></span>|  
|[<span data-ttu-id="581b0-112">XML 宣言 (Visual Basic) でシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="581b0-112">Serializing with an XML Declaration (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-with-an-xml-declaration.md)|<span data-ttu-id="581b0-113">XML 宣言を含む XML ツリーをシリアル化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="581b0-113">Describes how to serialize an XML tree that includes an XML declaration.</span></span>|  
|[<span data-ttu-id="581b0-114">ファイル、TextWriter、および XmlWriter へのシリアル化</span><span class="sxs-lookup"><span data-stu-id="581b0-114">Serializing to Files, TextWriters, and XmlWriters</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-to-files-textwriters-and-xmlwriters.md)|<span data-ttu-id="581b0-115">ドキュメントを <xref:System.IO.File>、<xref:System.IO.TextWriter>、または <xref:System.Xml.XmlWriter> にシリアル化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="581b0-115">Describes how to serialize a document to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="581b0-116">XmlReader (呼び出し元の XSLT) にシリアル化する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="581b0-116">Serializing to an XmlReader (Invoking XSLT) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-to-an-xmlreader-invoking-xslt.md)|<span data-ttu-id="581b0-117"><xref:System.Xml.XmlReader> を作成して、別のモジュールが XML ツリーの内容を読み取れるようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="581b0-117">Describes how to create a <xref:System.Xml.XmlReader> that enables another module to read the contents of an XML tree.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="581b0-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="581b0-118">See Also</span></span>  
 [<span data-ttu-id="581b0-119">プログラミング ガイド (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="581b0-119">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)

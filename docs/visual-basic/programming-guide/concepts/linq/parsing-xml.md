---
title: "(Visual Basic) の XML の解析 |Microsoft ドキュメント"
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
ms.assetid: 5bcbd7e2-d9f1-4c8f-80d6-39915fe17bd1
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
ms.openlocfilehash: af4ecce89f2f45069a48ce62826509f795dcf211
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="parsing-xml-visual-basic"></a><span data-ttu-id="acc2b-102">(Visual Basic) の XML の解析</span><span class="sxs-lookup"><span data-stu-id="acc2b-102">Parsing XML (Visual Basic)</span></span>
<span data-ttu-id="acc2b-103">このセクションのトピックでは、XML ドキュメントを解析する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="acc2b-103">The topics in this section describe how to parse XML documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="acc2b-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="acc2b-104">In This Section</span></span>  
  
|<span data-ttu-id="acc2b-105">トピック</span><span class="sxs-lookup"><span data-stu-id="acc2b-105">Topic</span></span>|<span data-ttu-id="acc2b-106">説明</span><span class="sxs-lookup"><span data-stu-id="acc2b-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="acc2b-107">方法: 文字列 (Visual Basic) を解析</span><span class="sxs-lookup"><span data-stu-id="acc2b-107">How to: Parse a String (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-parse-a-string.md)|<span data-ttu-id="acc2b-108">文字列を解析して XML ツリーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="acc2b-108">Shows how to parse a string to create an XML tree.</span></span>|  
|[<span data-ttu-id="acc2b-109">方法: ファイル (Visual Basic の場合) から XML を読み込む</span><span class="sxs-lookup"><span data-stu-id="acc2b-109">How to: Load XML from a File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md)|<span data-ttu-id="acc2b-110">使用して URI から XML を読み込む方法を示しています、<xref:System.Xml.Linq.XElement.Load%2A>メソッド</xref:System.Xml.Linq.XElement.Load%2A>。</span><span class="sxs-lookup"><span data-stu-id="acc2b-110">Shows how to load XML from a URI using the <xref:System.Xml.Linq.XElement.Load%2A> method.</span></span>|  
|[<span data-ttu-id="acc2b-111">XML の読み込み時または解析時の空白の維持</span><span class="sxs-lookup"><span data-stu-id="acc2b-111">Preserving White Space while Loading or Parsing XML</span></span>](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-loading-or-parsing-xml.md)|<span data-ttu-id="acc2b-112">XML ツリーを読み込む際の、空白に対する [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] の動作を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="acc2b-112">Describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] while loading XML trees.</span></span>|  
|[<span data-ttu-id="acc2b-113">方法: 解析エラー (Visual Basic) をキャッチ</span><span class="sxs-lookup"><span data-stu-id="acc2b-113">How to: Catch Parsing Errors (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-catch-parsing-errors.md)|<span data-ttu-id="acc2b-114">形式が正しくないか無効な XML を検出する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="acc2b-114">Shows how to detect badly formed or invalid XML.</span></span>|  
|[<span data-ttu-id="acc2b-115">方法: XmlReader (Visual Basic の場合) からツリーを作成</span><span class="sxs-lookup"><span data-stu-id="acc2b-115">How to: Create a Tree from an XmlReader (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-tree-from-an-xmlreader.md)|<span data-ttu-id="acc2b-116"><xref:System.Xml.XmlReader>。</xref:System.Xml.XmlReader>から直接 XML ツリーを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="acc2b-116">Shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span>|  
|[<span data-ttu-id="acc2b-117">方法: XML フラグメントをストリームから XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="acc2b-117">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-from-an-xmlreader.md)|<span data-ttu-id="acc2b-118"><xref:System.Xml.XmlReader>。</xref:System.Xml.XmlReader>を使用して XML フラグメントをストリーム出力する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="acc2b-118">Shows how to stream XML fragments by using an <xref:System.Xml.XmlReader>.</span></span><br /><br /> <span data-ttu-id="acc2b-119">非常に大きな XML ファイルを処理する必要があるとき、XML ツリー全体をメモリに読み込むことは不適切な場合があります。</span><span class="sxs-lookup"><span data-stu-id="acc2b-119">When you have to process arbitrarily large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="acc2b-120">その場合は、XML フラグメントをストリーム出力できます。</span><span class="sxs-lookup"><span data-stu-id="acc2b-120">Instead, you can stream XML fragments.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="acc2b-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="acc2b-121">See Also</span></span>  
 [<span data-ttu-id="acc2b-122">XML ツリー (Visual Basic) の作成</span><span class="sxs-lookup"><span data-stu-id="acc2b-122">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)

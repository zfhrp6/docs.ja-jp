---
title: (Visual Basic) の XML の解析
ms.date: 07/20/2015
ms.assetid: 5bcbd7e2-d9f1-4c8f-80d6-39915fe17bd1
ms.openlocfilehash: 3701592fd6160e8f0f858aed15618a6dbcfb3c22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645240"
---
# <a name="parsing-xml-visual-basic"></a><span data-ttu-id="fba1b-102">(Visual Basic) の XML の解析</span><span class="sxs-lookup"><span data-stu-id="fba1b-102">Parsing XML (Visual Basic)</span></span>
<span data-ttu-id="fba1b-103">このセクションのトピックでは、XML ドキュメントを解析する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fba1b-103">The topics in this section describe how to parse XML documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fba1b-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="fba1b-104">In This Section</span></span>  
  
|<span data-ttu-id="fba1b-105">トピック</span><span class="sxs-lookup"><span data-stu-id="fba1b-105">Topic</span></span>|<span data-ttu-id="fba1b-106">説明</span><span class="sxs-lookup"><span data-stu-id="fba1b-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="fba1b-107">方法: 解析 (String) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fba1b-107">How to: Parse a String (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-parse-a-string.md)|<span data-ttu-id="fba1b-108">文字列を解析して XML ツリーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fba1b-108">Shows how to parse a string to create an XML tree.</span></span>|  
|[<span data-ttu-id="fba1b-109">方法: XML ファイルから読み込みます (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fba1b-109">How to: Load XML from a File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md)|<span data-ttu-id="fba1b-110"><xref:System.Xml.Linq.XElement.Load%2A> メソッドを使用して、URI から XML を読み込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fba1b-110">Shows how to load XML from a URI using the <xref:System.Xml.Linq.XElement.Load%2A> method.</span></span>|  
|[<span data-ttu-id="fba1b-111">XML の読み込み時または解析時の空白の維持</span><span class="sxs-lookup"><span data-stu-id="fba1b-111">Preserving White Space while Loading or Parsing XML</span></span>](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-loading-or-parsing-xml.md)|<span data-ttu-id="fba1b-112">XML ツリーを読み込む際の、空白に対する [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の動作を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fba1b-112">Describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] while loading XML trees.</span></span>|  
|[<span data-ttu-id="fba1b-113">方法: 解析エラー (Visual Basic) をキャッチ</span><span class="sxs-lookup"><span data-stu-id="fba1b-113">How to: Catch Parsing Errors (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-catch-parsing-errors.md)|<span data-ttu-id="fba1b-114">形式が正しくないか無効な XML を検出する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fba1b-114">Shows how to detect badly formed or invalid XML.</span></span>|  
|[<span data-ttu-id="fba1b-115">方法: ツリー XmlReader から作成 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fba1b-115">How to: Create a Tree from an XmlReader (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-tree-from-an-xmlreader.md)|<span data-ttu-id="fba1b-116"><xref:System.Xml.XmlReader> から直接 XML ツリーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fba1b-116">Shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span>|  
|[<span data-ttu-id="fba1b-117">方法: XML フラグメントをストリームから XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fba1b-117">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-from-an-xmlreader.md)|<span data-ttu-id="fba1b-118"><xref:System.Xml.XmlReader> を使用して XML フラグメントをストリーム出力する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fba1b-118">Shows how to stream XML fragments by using an <xref:System.Xml.XmlReader>.</span></span><br /><br /> <span data-ttu-id="fba1b-119">非常に大きな XML ファイルを処理する必要があるとき、XML ツリー全体をメモリに読み込むことは不適切な場合があります。</span><span class="sxs-lookup"><span data-stu-id="fba1b-119">When you have to process arbitrarily large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="fba1b-120">その場合は、XML フラグメントをストリーム出力できます。</span><span class="sxs-lookup"><span data-stu-id="fba1b-120">Instead, you can stream XML fragments.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fba1b-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="fba1b-121">See Also</span></span>  
 [<span data-ttu-id="fba1b-122">XML ツリー (Visual Basic) を作成します。</span><span class="sxs-lookup"><span data-stu-id="fba1b-122">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)

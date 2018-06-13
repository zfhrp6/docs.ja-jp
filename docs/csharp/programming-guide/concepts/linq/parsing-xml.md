---
title: XML の解析 (C#)
ms.date: 07/20/2015
ms.assetid: 7ea83f83-a779-423a-9875-4ea4e51f97fc
ms.openlocfilehash: 876cfdf7bd5a82aba75d456d6d5cda57e080fdf0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321705"
---
# <a name="parsing-xml-c"></a><span data-ttu-id="465f4-102">XML の解析 (C#)</span><span class="sxs-lookup"><span data-stu-id="465f4-102">Parsing XML (C#)</span></span>
<span data-ttu-id="465f4-103">このセクションのトピックでは、XML ドキュメントを解析する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="465f4-103">The topics in this section describe how to parse XML documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="465f4-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="465f4-104">In This Section</span></span>  
  
|<span data-ttu-id="465f4-105">トピック</span><span class="sxs-lookup"><span data-stu-id="465f4-105">Topic</span></span>|<span data-ttu-id="465f4-106">説明</span><span class="sxs-lookup"><span data-stu-id="465f4-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="465f4-107">方法: 文字列を解析する (C#) </span><span class="sxs-lookup"><span data-stu-id="465f4-107">How to: Parse a String (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-parse-a-string.md)|<span data-ttu-id="465f4-108">文字列を解析して XML ツリーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="465f4-108">Shows how to parse a string to create an XML tree.</span></span>|  
|[<span data-ttu-id="465f4-109">方法: ファイルから XML を読み込む (C#)</span><span class="sxs-lookup"><span data-stu-id="465f4-109">How to: Load XML from a File (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md)|<span data-ttu-id="465f4-110"><xref:System.Xml.Linq.XElement.Load%2A> メソッドを使用して、URI から XML を読み込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="465f4-110">Shows how to load XML from a URI using the <xref:System.Xml.Linq.XElement.Load%2A> method.</span></span>|  
|[<span data-ttu-id="465f4-111">XML の読み込み時または解析時の空白の維持</span><span class="sxs-lookup"><span data-stu-id="465f4-111">Preserving White Space while Loading or Parsing XML</span></span>](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-loading-or-parsing-xml1.md)|<span data-ttu-id="465f4-112">XML ツリーを読み込む際の、空白に対する [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の動作を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="465f4-112">Describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] while loading XML trees.</span></span>|  
|[<span data-ttu-id="465f4-113">方法: 解析エラーをキャッチする (C#)</span><span class="sxs-lookup"><span data-stu-id="465f4-113">How to: Catch Parsing Errors (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-catch-parsing-errors.md)|<span data-ttu-id="465f4-114">形式が正しくないか無効な XML を検出する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="465f4-114">Shows how to detect badly formed or invalid XML.</span></span>|  
|[<span data-ttu-id="465f4-115">方法: XmlReader からツリーを作成する (C#)</span><span class="sxs-lookup"><span data-stu-id="465f4-115">How to: Create a Tree from an XmlReader (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-create-a-tree-from-an-xmlreader.md)|<span data-ttu-id="465f4-116"><xref:System.Xml.XmlReader> から直接 XML ツリーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="465f4-116">Shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span>|  
|[<span data-ttu-id="465f4-117">方法: XmlReader から XML フラグメントをストリーム出力する (C#)</span><span class="sxs-lookup"><span data-stu-id="465f4-117">How to: Stream XML Fragments from an XmlReader (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-from-an-xmlreader.md)|<span data-ttu-id="465f4-118"><xref:System.Xml.XmlReader> を使用して XML フラグメントをストリーム出力する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="465f4-118">Shows how to stream XML fragments by using an <xref:System.Xml.XmlReader>.</span></span><br /><br /> <span data-ttu-id="465f4-119">非常に大きな XML ファイルを処理する必要があるとき、XML ツリー全体をメモリに読み込むことは不適切な場合があります。</span><span class="sxs-lookup"><span data-stu-id="465f4-119">When you have to process arbitrarily large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="465f4-120">その場合は、XML フラグメントをストリーム出力できます。</span><span class="sxs-lookup"><span data-stu-id="465f4-120">Instead, you can stream XML fragments.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="465f4-121">参照</span><span class="sxs-lookup"><span data-stu-id="465f4-121">See Also</span></span>  
 [<span data-ttu-id="465f4-122">XML ツリーの作成 (C#)</span><span class="sxs-lookup"><span data-stu-id="465f4-122">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)

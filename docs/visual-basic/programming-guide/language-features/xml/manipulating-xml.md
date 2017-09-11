---
title: "Visual Basic で XML を操作する |Microsoft ドキュメント"
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
helpviewer_keywords:
- LINQ to XML [Visual Basic], manipulating XML
- Visual Basic code, XML
- XML [Visual Basic], manipulating
ms.assetid: da32cffb-198d-41b1-9af3-260fe32e3b7d
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 62b955d78eb507aab4c786e84f3044ba54a38ebc
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="manipulating-xml-in-visual-basic"></a><span data-ttu-id="78354-102">Visual Basic での XML の操作</span><span class="sxs-lookup"><span data-stu-id="78354-102">Manipulating XML in Visual Basic</span></span>
<span data-ttu-id="78354-103">使用する*XML リテラル*文字列、ファイル、ストリームなどの外部ソースから XML を読み込めません。</span><span class="sxs-lookup"><span data-stu-id="78354-103">You can use *XML literals* to load XML from an external source such as a string, file, or stream.</span></span> <span data-ttu-id="78354-104">使用することができますし、 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 、XML を操作して[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]XML に対してクエリをします。</span><span class="sxs-lookup"><span data-stu-id="78354-104">You can then use [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] to manipulate the XML and use [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] to query the XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="78354-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="78354-105">In This Section</span></span>  
 [<span data-ttu-id="78354-106">方法 : ファイル、文字列、またはストリームからの XML の読み込み</span><span class="sxs-lookup"><span data-stu-id="78354-106">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)  
 <span data-ttu-id="78354-107">XML を読み込む方法を示しています、<xref:System.Xml.Linq.XDocument>または<xref:System.Xml.Linq.XElement>テキスト ファイル、文字列またはストリームからのオブジェクト</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XDocument>。</span><span class="sxs-lookup"><span data-stu-id="78354-107">Demonstrates how to load XML into an <xref:System.Xml.Linq.XDocument> or <xref:System.Xml.Linq.XElement> object from a text file, string, or stream.</span></span>  
  
 [<span data-ttu-id="78354-108">方法 : LINQ を使用した XML の変換</span><span class="sxs-lookup"><span data-stu-id="78354-108">How to: Transform XML by Using LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-transform-xml-by-using-linq.md)  
 <span data-ttu-id="78354-109">内容を変換する方法を示しています、<xref:System.Xml.Linq.XDocument>して、新しい XML ドキュメント オブジェクト</xref:System.Xml.Linq.XDocument>。</span><span class="sxs-lookup"><span data-stu-id="78354-109">Demonstrates how to transform the contents of an <xref:System.Xml.Linq.XDocument> object into a new XML document.</span></span>  
  
 [<span data-ttu-id="78354-110">方法 : XML リテラルの変更</span><span class="sxs-lookup"><span data-stu-id="78354-110">How to: Modify XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-modify-xml-literals.md)  
 <span data-ttu-id="78354-111">要素、属性、および XML リテラルの値を変更する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="78354-111">Demonstrates how to modify the elements, attributes, and values in an XML literal.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="78354-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="78354-112">Related Sections</span></span>  
 [<span data-ttu-id="78354-113">XML 軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="78354-113">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 <span data-ttu-id="78354-114">さまざまな XML アクセス プロパティを説明するセクションへのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="78354-114">Provides links to sections that describe the various XML access properties.</span></span>  
  
 [<span data-ttu-id="78354-115">Visual Basic における LINQ to XML の概要</span><span class="sxs-lookup"><span data-stu-id="78354-115">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="78354-116">使用の概要については、 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] Visual Basic でします。</span><span class="sxs-lookup"><span data-stu-id="78354-116">Provides an introduction to using [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="78354-117">Visual Basic で XML を作成します。</span><span class="sxs-lookup"><span data-stu-id="78354-117">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="78354-118">Visual Basic で XML リテラルを使用するための概要を提供します。</span><span class="sxs-lookup"><span data-stu-id="78354-118">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="78354-119">Visual Basic における XML へのアクセス</span><span class="sxs-lookup"><span data-stu-id="78354-119">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 <span data-ttu-id="78354-120">XML 要素または Visual Basic でのドキュメントの部分にアクセスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="78354-120">Demonstrates how to access parts of an XML element or document in Visual Basic.</span></span>  
  
 [<span data-ttu-id="78354-121">XML</span><span class="sxs-lookup"><span data-stu-id="78354-121">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="78354-122">使用方法について説明するセクションへのリンクを提供[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]Visual Basic でします。</span><span class="sxs-lookup"><span data-stu-id="78354-122">Provides links to sections that describe how to use [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] in Visual Basic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78354-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="78354-123">See Also</span></span>  
 <span data-ttu-id="78354-124">[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span><span class="sxs-lookup"><span data-stu-id="78354-124">[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span></span>  
<span data-ttu-id="78354-125"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="78354-125"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="78354-126"> [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span><span class="sxs-lookup"><span data-stu-id="78354-126"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span></span>

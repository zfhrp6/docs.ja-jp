---
title: "LINQ to XML プログラミングの概要 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: a7c07d0a-1fae-4610-ae51-56dd7075cc14
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
ms.openlocfilehash: 57d52b1bc46263e4e8e662be6a83bf4718813b43
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="linq-to-xml-programming-overview-visual-basic"></a><span data-ttu-id="1eda0-102">LINQ to XML プログラミングの概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1eda0-102">LINQ to XML Programming Overview (Visual Basic)</span></span>
<span data-ttu-id="1eda0-103">以下のトピックでは、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] クラスに関する概要情報と、最も重要な&3; つのクラスに関する詳細情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="1eda0-103">These topics provide high-level overview information about the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] classes, as well as detailed information about three of the most important classes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1eda0-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="1eda0-104">In This Section</span></span>  
  
|<span data-ttu-id="1eda0-105">トピック</span><span class="sxs-lookup"><span data-stu-id="1eda0-105">Topic</span></span>|<span data-ttu-id="1eda0-106">説明</span><span class="sxs-lookup"><span data-stu-id="1eda0-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="1eda0-107">関数型プログラミングと手続き型プログラミング (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1eda0-107">Functional vs. Procedural Programming (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-vs-procedural-programming-linq-to-xml.md)|<span data-ttu-id="1eda0-108">LINQ to XML アプリケーションを作成する&2; つの主要な方法の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="1eda0-108">Provides a high level view of the two principle approaches to writing LINQ to XML applications.</span></span>|  
|[<span data-ttu-id="1eda0-109">LINQ to XML クラスの概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1eda0-109">LINQ to XML Classes Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-classes-overview.md)|<span data-ttu-id="1eda0-110">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] クラスの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="1eda0-110">Provides an overview of the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] classes.</span></span>|  
|[<span data-ttu-id="1eda0-111">XElement クラスの概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1eda0-111">XElement Class Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md)|<span data-ttu-id="1eda0-112">導入されています、 <xref:System.Xml.Linq.XElement>XML 要素を表すクラス</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="1eda0-112">Introduces the <xref:System.Xml.Linq.XElement> class, which represents XML elements.</span></span> <span data-ttu-id="1eda0-113"><xref:System.Xml.Linq.XElement>基礎クラスの&1; つ、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]クラス階層です。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="1eda0-113"><xref:System.Xml.Linq.XElement> is one of the fundamental classes in the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] class hierarchy.</span></span>|  
|[<span data-ttu-id="1eda0-114">XAttribute クラスの概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1eda0-114">XAttribute Class Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/xattribute-class-overview.md)|<span data-ttu-id="1eda0-115">導入されています、<xref:System.Xml.Linq.XAttribute>クラスで、XML 属性を表します</xref:System.Xml.Linq.XAttribute>。</span><span class="sxs-lookup"><span data-stu-id="1eda0-115">Introduces the <xref:System.Xml.Linq.XAttribute> class, which represents XML attributes.</span></span>|  
|[<span data-ttu-id="1eda0-116">XDocument クラスの概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1eda0-116">XDocument Class Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md)|<span data-ttu-id="1eda0-117">導入されています、<xref:System.Xml.Linq.XDocument>を XML ドキュメントを表すクラス</xref:System.Xml.Linq.XDocument>。</span><span class="sxs-lookup"><span data-stu-id="1eda0-117">Introduces the <xref:System.Xml.Linq.XDocument> class, which represents XML documents.</span></span>|  
|[<span data-ttu-id="1eda0-118">方法: linq TO XML の例 (Visual Basic) をビルド</span><span class="sxs-lookup"><span data-stu-id="1eda0-118">How to: Build LINQ to XML Examples (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-build-linq-to-xml-examples.md)|<span data-ttu-id="1eda0-119">含む、 `Imports` linq TO XML の例をビルドするために必要なステートメントです。</span><span class="sxs-lookup"><span data-stu-id="1eda0-119">Contains the `Imports` statements that are required to build the LINQ to XML examples.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1eda0-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="1eda0-120">See Also</span></span>  
 [<span data-ttu-id="1eda0-121">プログラミング ガイド (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1eda0-121">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)

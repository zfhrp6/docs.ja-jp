---
title: "LINQ to XML プログラミングの概要 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 2dfa9b6f-5890-461d-b81c-316853c7f320
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: bc22991f53920b045280d3e74b9b8dd73e63c944
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="linq-to-xml-programming-overview-c"></a><span data-ttu-id="47c65-102">LINQ to XML プログラミングの概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="47c65-102">LINQ to XML Programming Overview (C#)</span></span>
<span data-ttu-id="47c65-103">以下のトピックでは、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クラスに関する概要情報と、最も重要な 3 つのクラスに関する詳細情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="47c65-103">These topics provide high-level overview information about the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes, as well as detailed information about three of the most important classes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="47c65-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="47c65-104">In This Section</span></span>  
  
|<span data-ttu-id="47c65-105">トピック</span><span class="sxs-lookup"><span data-stu-id="47c65-105">Topic</span></span>|<span data-ttu-id="47c65-106">説明</span><span class="sxs-lookup"><span data-stu-id="47c65-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="47c65-107">関数型プログラミングと手続き型プログラミング (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="47c65-107">Functional vs. Procedural Programming (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-vs-procedural-programming-linq-to-xml.md)|<span data-ttu-id="47c65-108">LINQ to XML アプリケーションを作成する 2 つの主要な方法の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="47c65-108">Provides a high level view of the two principle approaches to writing LINQ to XML applications.</span></span>|  
|[<span data-ttu-id="47c65-109">LINQ to XML クラスの概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="47c65-109">LINQ to XML Classes Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-classes-overview.md)|<span data-ttu-id="47c65-110">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クラスの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="47c65-110">Provides an overview of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes.</span></span>|  
|[<span data-ttu-id="47c65-111">XElement クラスの概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="47c65-111">XElement Class Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/xelement-class-overview.md)|<span data-ttu-id="47c65-112">XML 要素を表す <xref:System.Xml.Linq.XElement> クラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="47c65-112">Introduces the <xref:System.Xml.Linq.XElement> class, which represents XML elements.</span></span> <span data-ttu-id="47c65-113"><xref:System.Xml.Linq.XElement> は、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クラス階層の基礎クラスの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="47c65-113"><xref:System.Xml.Linq.XElement> is one of the fundamental classes in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] class hierarchy.</span></span>|  
|[<span data-ttu-id="47c65-114">XAttribute クラスの概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="47c65-114">XAttribute Class Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/xattribute-class-overview.md)|<span data-ttu-id="47c65-115">XML 属性を表す <xref:System.Xml.Linq.XAttribute> クラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="47c65-115">Introduces the <xref:System.Xml.Linq.XAttribute> class, which represents XML attributes.</span></span>|  
|[<span data-ttu-id="47c65-116">XDocument クラスの概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="47c65-116">XDocument Class Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/xdocument-class-overview.md)|<span data-ttu-id="47c65-117">XML ドキュメントを表す <xref:System.Xml.Linq.XDocument> クラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="47c65-117">Introduces the <xref:System.Xml.Linq.XDocument> class, which represents XML documents.</span></span>|  
|[<span data-ttu-id="47c65-118">方法: LINQ to XML の例をビルドする (C#)</span><span class="sxs-lookup"><span data-stu-id="47c65-118">How to: Build LINQ to XML Examples (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-build-linq-to-xml-examples.md)|<span data-ttu-id="47c65-119">LINQ to XML の例のビルドに必要な `Using` ディレクティブについて説明します。</span><span class="sxs-lookup"><span data-stu-id="47c65-119">Contains the `Using` directives that are required to build the LINQ to XML examples.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="47c65-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="47c65-120">See Also</span></span>  
 [<span data-ttu-id="47c65-121">プログラミング ガイド (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="47c65-121">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)


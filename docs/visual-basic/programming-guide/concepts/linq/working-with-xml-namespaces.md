---
title: "XML 名前空間 (Visual Basic) の使用 |Microsoft ドキュメント"
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
ms.assetid: 428bf4b0-e348-4ffd-986b-d905d5a0e7fa
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4ddbc7a241fa8dee886fb0aeb5951f1ee622efb5
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="working-with-xml-namespaces-visual-basic"></a><span data-ttu-id="4fa08-102">XML 名前空間 (Visual Basic) の使用</span><span class="sxs-lookup"><span data-stu-id="4fa08-102">Working with XML Namespaces (Visual Basic)</span></span>
<span data-ttu-id="4fa08-103">このセクションのトピックで説明する方法[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]名前空間をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="4fa08-103">The topics in this section describe how [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] supports namespaces.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4fa08-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="4fa08-104">In This Section</span></span>  
  
|<span data-ttu-id="4fa08-105">トピック</span><span class="sxs-lookup"><span data-stu-id="4fa08-105">Topic</span></span>|<span data-ttu-id="4fa08-106">説明</span><span class="sxs-lookup"><span data-stu-id="4fa08-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="4fa08-107">名前空間の概要 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="4fa08-107">Namespaces Overview (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md)|<span data-ttu-id="4fa08-108">このトピック<xref:System.Xml.Linq.XName>クラス、および<xref:System.Xml.Linq.XNamespace>クラス</xref:System.Xml.Linq.XNamespace></xref:System.Xml.Linq.XName>の名前空間が導入されています</span><span class="sxs-lookup"><span data-stu-id="4fa08-108">This topic introduces namespaces, the <xref:System.Xml.Linq.XName> class, and the <xref:System.Xml.Linq.XNamespace> class.</span></span>|  
|[<span data-ttu-id="4fa08-109">方法: 名前空間 (LINQ to XML) を持つドキュメントを作成する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4fa08-109">How to: Create a Document with Namespaces (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-document-with-namespaces.md)|<span data-ttu-id="4fa08-110">名前空間を持つドキュメントを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4fa08-110">Shows how to create documents with namespaces.</span></span>|  
|[<span data-ttu-id="4fa08-111">方法: Namespace プレフィックス (Visual Basic) (LINQ to XML) を制御します。</span><span class="sxs-lookup"><span data-stu-id="4fa08-111">How to: Control Namespace Prefixes (Visual Basic) (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-control-namespace-prefixes-linq-to-xml.md)|<span data-ttu-id="4fa08-112">グローバル名前空間を宣言することで名前空間プレフィックスを制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4fa08-112">Shows how to control namespace prefixes by declaring global namespaces.</span></span>|  
|[<span data-ttu-id="4fa08-113">Visual Basic での既定の名前空間のスコープ</span><span class="sxs-lookup"><span data-stu-id="4fa08-113">Scope of Default Namespaces in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/scope-of-default-namespaces.md)|<span data-ttu-id="4fa08-114">既定の名前空間内の XML に対するクエリの適切な記述方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4fa08-114">Demonstrates the appropriate way to write queries for XML in the default namespace.</span></span>|  
|[<span data-ttu-id="4fa08-115">グローバル名前空間 (Visual Basic) (LINQ to XML) の使用</span><span class="sxs-lookup"><span data-stu-id="4fa08-115">Working with Global Namespaces (Visual Basic) (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-global-namespaces-linq-to-xml.md)|<span data-ttu-id="4fa08-116">Visual Basic、およびそれらの使用上の理由から、グローバル名前空間のセマンティクスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4fa08-116">Explains the semantics of global namespaces in Visual Basic, and reasons for using them.</span></span>|  
|[<span data-ttu-id="4fa08-117">方法: 名前空間 (Visual Basic) 内の XML に対するクエリの作成</span><span class="sxs-lookup"><span data-stu-id="4fa08-117">How to: Write Queries on XML in Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-queries-on-xml-in-namespaces.md)|<span data-ttu-id="4fa08-118">Visual Basic の linq to XML クエリの XML 名前空間の指定方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4fa08-118">Demonstrates how to specify XML namespaces in Visual Basic LINQ to XML queries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4fa08-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="4fa08-119">See Also</span></span>  
 [<span data-ttu-id="4fa08-120">プログラミング ガイド (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4fa08-120">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)

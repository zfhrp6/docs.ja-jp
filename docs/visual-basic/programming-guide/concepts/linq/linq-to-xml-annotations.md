---
title: "LINQ to XML Annotations2 |Microsoft ドキュメント"
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
ms.assetid: c3e8b3ff-fceb-4428-b0ca-1ed6f128aac8
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 97f5386630ba687e4401ee0cfb70f7170e273a53
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="d6057-102">LINQ to XML の注釈</span><span class="sxs-lookup"><span data-stu-id="d6057-102">LINQ to XML Annotations</span></span>
<span data-ttu-id="d6057-103">内の注釈[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]任意の型の任意のオブジェクトを XML ツリー内の任意の XML コンポーネントに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="d6057-103">Annotations in [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>  
  
 <span data-ttu-id="d6057-104">など、XML コンポーネントに注釈を追加する、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XAttribute>を呼び出す、<xref:System.Xml.Linq.XObject.AddAnnotation%2A>メソッド</xref:System.Xml.Linq.XObject.AddAnnotation%2A></xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="d6057-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="d6057-105">注釈は型によって取得します。</span><span class="sxs-lookup"><span data-stu-id="d6057-105">You retrieve annotations by type.</span></span>  
  
 <span data-ttu-id="d6057-106">注釈は XML 情報セットの一部ではないことに注意してください。注釈はシリアル化も逆シリアル化もされません。</span><span class="sxs-lookup"><span data-stu-id="d6057-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d6057-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="d6057-107">Methods</span></span>  
 <span data-ttu-id="d6057-108">注釈を操作する場合は、次のメソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d6057-108">You can use the following methods when working with annotations:</span></span>  
  
|<span data-ttu-id="d6057-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="d6057-109">Method</span></span>|<span data-ttu-id="d6057-110">説明</span><span class="sxs-lookup"><span data-stu-id="d6057-110">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="d6057-111"><xref:System.Xml.Linq.XObject.AddAnnotation%2A></xref:System.Xml.Linq.XObject.AddAnnotation%2A></span><span class="sxs-lookup"><span data-stu-id="d6057-111"><xref:System.Xml.Linq.XObject.AddAnnotation%2A></span></span>|<span data-ttu-id="d6057-112"><xref:System.Xml.Linq.XObject>。</xref:System.Xml.Linq.XObject>の注釈の一覧にオブジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="d6057-112">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<span data-ttu-id="d6057-113"><xref:System.Xml.Linq.XObject.Annotation%2A></xref:System.Xml.Linq.XObject.Annotation%2A></span><span class="sxs-lookup"><span data-stu-id="d6057-113"><xref:System.Xml.Linq.XObject.Annotation%2A></span></span>|<span data-ttu-id="d6057-114"><xref:System.Xml.Linq.XObject>。</xref:System.Xml.Linq.XObject>から指定した型の最初の注釈オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="d6057-114">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<span data-ttu-id="d6057-115"><xref:System.Xml.Linq.XObject.Annotations%2A></xref:System.Xml.Linq.XObject.Annotations%2A></span><span class="sxs-lookup"><span data-stu-id="d6057-115"><xref:System.Xml.Linq.XObject.Annotations%2A></span></span>|<span data-ttu-id="d6057-116"><xref:System.Xml.Linq.XObject>。</xref:System.Xml.Linq.XObject>の指定した型の注釈のコレクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="d6057-116">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<span data-ttu-id="d6057-117"><xref:System.Xml.Linq.XObject.RemoveAnnotations%2A></xref:System.Xml.Linq.XObject.RemoveAnnotations%2A></span><span class="sxs-lookup"><span data-stu-id="d6057-117"><xref:System.Xml.Linq.XObject.RemoveAnnotations%2A></span></span>|<span data-ttu-id="d6057-118"><xref:System.Xml.Linq.XObject>。</xref:System.Xml.Linq.XObject>から指定した型の注釈を削除します。</span><span class="sxs-lookup"><span data-stu-id="d6057-118">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d6057-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6057-119">See Also</span></span>  
 [<span data-ttu-id="d6057-120">高度な LINQ to XML のプログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6057-120">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

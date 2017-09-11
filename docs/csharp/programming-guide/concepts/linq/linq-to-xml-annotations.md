---
title: "LINQ to XML の注釈3"
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
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3fa8715deac8776f7a512439ee055be6faf4649f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="6ac84-102">LINQ to XML の注釈</span><span class="sxs-lookup"><span data-stu-id="6ac84-102">LINQ to XML Annotations</span></span>
<span data-ttu-id="6ac84-103">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の注釈を使用すると、任意の型の任意のオブジェクトを XML ツリー内の任意の XML コンポーネントに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="6ac84-103">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>  
  
 <span data-ttu-id="6ac84-104"><xref:System.Xml.Linq.XElement> や <xref:System.Xml.Linq.XAttribute> などの XML コンポーネントに注釈を追加するには、<xref:System.Xml.Linq.XObject.AddAnnotation%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6ac84-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="6ac84-105">注釈は型によって取得します。</span><span class="sxs-lookup"><span data-stu-id="6ac84-105">You retrieve annotations by type.</span></span>  
  
 <span data-ttu-id="6ac84-106">注釈は XML 情報セットの一部ではないことに注意してください。注釈はシリアル化も逆シリアル化もされません。</span><span class="sxs-lookup"><span data-stu-id="6ac84-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6ac84-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="6ac84-107">Methods</span></span>  
 <span data-ttu-id="6ac84-108">注釈を操作する場合は、次のメソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="6ac84-108">You can use the following methods when working with annotations:</span></span>  
  
|<span data-ttu-id="6ac84-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="6ac84-109">Method</span></span>|<span data-ttu-id="6ac84-110">説明</span><span class="sxs-lookup"><span data-stu-id="6ac84-110">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="6ac84-111">オブジェクトを <xref:System.Xml.Linq.XObject> の注釈の一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="6ac84-111">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="6ac84-112">指定された型の最初の注釈オブジェクトを <xref:System.Xml.Linq.XObject> から取得します。</span><span class="sxs-lookup"><span data-stu-id="6ac84-112">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="6ac84-113"><xref:System.Xml.Linq.XObject> について指定された型の注釈のコレクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="6ac84-113">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="6ac84-114">指定された型の注釈を <xref:System.Xml.Linq.XObject> から削除します。</span><span class="sxs-lookup"><span data-stu-id="6ac84-114">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6ac84-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ac84-115">See Also</span></span>  
 [<span data-ttu-id="6ac84-116">高度な LINQ to XML プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="6ac84-116">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)


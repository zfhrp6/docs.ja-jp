---
title: LINQ to XML Annotations2
ms.date: 07/20/2015
ms.assetid: c3e8b3ff-fceb-4428-b0ca-1ed6f128aac8
ms.openlocfilehash: a7b81b8c1856c11cb0c5e777f31986a330cf115f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="5893c-102">LINQ to XML の注釈</span><span class="sxs-lookup"><span data-stu-id="5893c-102">LINQ to XML Annotations</span></span>
<span data-ttu-id="5893c-103">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の注釈を使用すると、任意の型の任意のオブジェクトを XML ツリー内の任意の XML コンポーネントに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="5893c-103">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>  
  
 <span data-ttu-id="5893c-104"><xref:System.Xml.Linq.XElement> や <xref:System.Xml.Linq.XAttribute> などの XML コンポーネントに注釈を追加するには、<xref:System.Xml.Linq.XObject.AddAnnotation%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5893c-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="5893c-105">注釈は型によって取得します。</span><span class="sxs-lookup"><span data-stu-id="5893c-105">You retrieve annotations by type.</span></span>  
  
 <span data-ttu-id="5893c-106">注釈は XML 情報セットの一部ではないことに注意してください。注釈はシリアル化も逆シリアル化もされません。</span><span class="sxs-lookup"><span data-stu-id="5893c-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5893c-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="5893c-107">Methods</span></span>  
 <span data-ttu-id="5893c-108">注釈を操作する場合は、次のメソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5893c-108">You can use the following methods when working with annotations:</span></span>  
  
|<span data-ttu-id="5893c-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="5893c-109">Method</span></span>|<span data-ttu-id="5893c-110">説明</span><span class="sxs-lookup"><span data-stu-id="5893c-110">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="5893c-111">オブジェクトを <xref:System.Xml.Linq.XObject> の注釈の一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="5893c-111">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="5893c-112">指定された型の最初の注釈オブジェクトを <xref:System.Xml.Linq.XObject> から取得します。</span><span class="sxs-lookup"><span data-stu-id="5893c-112">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="5893c-113"><xref:System.Xml.Linq.XObject> について指定された型の注釈のコレクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="5893c-113">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="5893c-114">指定された型の注釈を <xref:System.Xml.Linq.XObject> から削除します。</span><span class="sxs-lookup"><span data-stu-id="5893c-114">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5893c-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="5893c-115">See Also</span></span>  
 [<span data-ttu-id="5893c-116">高度な LINQ to XML プログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5893c-116">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

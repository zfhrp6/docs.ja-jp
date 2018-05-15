---
title: 要素、属性、および XML Tree1 内のノードを変更します。
ms.date: 07/20/2015
ms.assetid: 865cf54e-f8ac-4871-863b-a3e6fc61a4b9
ms.openlocfilehash: 91a7cca2e39e5ddc62d6010fbe4efad9bd7ff3c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="ef764-102">XML ツリー内の要素、属性、およびノードの変更</span><span class="sxs-lookup"><span data-stu-id="ef764-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="ef764-103">次の表は、要素、その子要素、またはその属性の変更に使用できるメソッドとプロパティについてまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="ef764-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="ef764-104">次のメソッドは、<xref:System.Xml.Linq.XElement> を変更します。</span><span class="sxs-lookup"><span data-stu-id="ef764-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="ef764-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ef764-105">Method</span></span>|<span data-ttu-id="ef764-106">説明</span><span class="sxs-lookup"><span data-stu-id="ef764-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="ef764-107">要素を解析された XML に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ef764-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="ef764-108">要素のすべてのコンテンツ (子ノードおよび属性) を削除します。</span><span class="sxs-lookup"><span data-stu-id="ef764-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="ef764-109">要素の属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="ef764-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="ef764-110">要素のすべてのコンテンツ (子ノードおよび属性) を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ef764-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="ef764-111">要素の属性を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ef764-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="ef764-112">属性の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="ef764-112">Sets the value of an attribute.</span></span> <span data-ttu-id="ef764-113">属性が存在しない場合は作成します。</span><span class="sxs-lookup"><span data-stu-id="ef764-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="ef764-114">値に `null` が設定された場合は、属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="ef764-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="ef764-115">子要素の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="ef764-115">Sets the value of a child element.</span></span> <span data-ttu-id="ef764-116">要素が存在しない場合は作成します。</span><span class="sxs-lookup"><span data-stu-id="ef764-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="ef764-117">値に `null` が設定された場合は、要素を削除します。</span><span class="sxs-lookup"><span data-stu-id="ef764-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="ef764-118">要素のコンテンツ (子ノード) を、指定したテキストに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ef764-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="ef764-119">要素の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="ef764-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="ef764-120">次のメソッドは、<xref:System.Xml.Linq.XAttribute> を変更します。</span><span class="sxs-lookup"><span data-stu-id="ef764-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="ef764-121">メソッド</span><span class="sxs-lookup"><span data-stu-id="ef764-121">Method</span></span>|<span data-ttu-id="ef764-122">説明</span><span class="sxs-lookup"><span data-stu-id="ef764-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="ef764-123">属性の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="ef764-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="ef764-124">属性の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="ef764-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="ef764-125">次のメソッドは、<xref:System.Xml.Linq.XNode> (<xref:System.Xml.Linq.XElement> または <xref:System.Xml.Linq.XDocument> を含む) を変更します。</span><span class="sxs-lookup"><span data-stu-id="ef764-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="ef764-126">メソッド</span><span class="sxs-lookup"><span data-stu-id="ef764-126">Method</span></span>|<span data-ttu-id="ef764-127">説明</span><span class="sxs-lookup"><span data-stu-id="ef764-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="ef764-128">ノードを新しいコンテンツに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ef764-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="ef764-129">次のメソッドは、<xref:System.Xml.Linq.XContainer> (<xref:System.Xml.Linq.XElement> または <xref:System.Xml.Linq.XDocument>) を変更します。</span><span class="sxs-lookup"><span data-stu-id="ef764-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="ef764-130">メソッド</span><span class="sxs-lookup"><span data-stu-id="ef764-130">Method</span></span>|<span data-ttu-id="ef764-131">説明</span><span class="sxs-lookup"><span data-stu-id="ef764-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="ef764-132">子ノードを新しいコンテンツに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ef764-132">Replaces the children nodes with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ef764-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="ef764-133">See Also</span></span>  
 [<span data-ttu-id="ef764-134">XML ツリー (LINQ to XML) の変更 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef764-134">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)

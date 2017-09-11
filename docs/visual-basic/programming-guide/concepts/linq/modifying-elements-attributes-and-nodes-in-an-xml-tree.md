---
title: "要素、属性、および XML Tree1 内のノードの変更 |Microsoft ドキュメント"
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
ms.assetid: 865cf54e-f8ac-4871-863b-a3e6fc61a4b9
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 88531f2af88074f4406c4859354860829efda69f
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="540a7-102">XML ツリー内の要素、属性、およびノードの変更</span><span class="sxs-lookup"><span data-stu-id="540a7-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="540a7-103">次の表は、要素、その子要素、またはその属性の変更に使用できるメソッドとプロパティについてまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="540a7-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="540a7-104">次の方法を変更<xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="540a7-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="540a7-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="540a7-105">Method</span></span>|<span data-ttu-id="540a7-106">説明</span><span class="sxs-lookup"><span data-stu-id="540a7-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="540a7-107"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="540a7-107"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></span></span>|<span data-ttu-id="540a7-108">要素を解析された XML に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="540a7-108">Replaces an element with parsed XML.</span></span>|  
|<span data-ttu-id="540a7-109"><xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="540a7-109"><xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></span></span>|<span data-ttu-id="540a7-110">要素のすべてのコンテンツ (子ノードおよび属性) を削除します。</span><span class="sxs-lookup"><span data-stu-id="540a7-110">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<span data-ttu-id="540a7-111"><xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="540a7-111"><xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></span></span>|<span data-ttu-id="540a7-112">要素の属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="540a7-112">Removes the attributes of an element.</span></span>|  
|<span data-ttu-id="540a7-113"><xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="540a7-113"><xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=fullName></span></span>|<span data-ttu-id="540a7-114">要素のすべてのコンテンツ (子ノードおよび属性) を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="540a7-114">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<span data-ttu-id="540a7-115"><xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="540a7-115"><xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=fullName></span></span>|<span data-ttu-id="540a7-116">要素の属性を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="540a7-116">Replaces the attributes of an element.</span></span>|  
|<span data-ttu-id="540a7-117"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="540a7-117"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="540a7-118">属性の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="540a7-118">Sets the value of an attribute.</span></span> <span data-ttu-id="540a7-119">属性が存在しない場合は作成します。</span><span class="sxs-lookup"><span data-stu-id="540a7-119">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="540a7-120">値に `null` が設定された場合は、属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="540a7-120">If the value is set to `null`, removes the attribute.</span></span>|  
|<span data-ttu-id="540a7-121"><xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="540a7-121"><xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="540a7-122">子要素の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="540a7-122">Sets the value of a child element.</span></span> <span data-ttu-id="540a7-123">要素が存在しない場合は作成します。</span><span class="sxs-lookup"><span data-stu-id="540a7-123">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="540a7-124">値に `null` が設定された場合は、要素を削除します。</span><span class="sxs-lookup"><span data-stu-id="540a7-124">If the value is set to `null`, removes the element.</span></span>|  
|<span data-ttu-id="540a7-125"><xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="540a7-125"><xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName></span></span>|<span data-ttu-id="540a7-126">要素のコンテンツ (子ノード) を、指定したテキストに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="540a7-126">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<span data-ttu-id="540a7-127"><xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="540a7-127"><xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="540a7-128">要素の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="540a7-128">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="540a7-129">次の方法を変更<xref:System.Xml.Linq.XAttribute>。</xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="540a7-129">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="540a7-130">メソッド</span><span class="sxs-lookup"><span data-stu-id="540a7-130">Method</span></span>|<span data-ttu-id="540a7-131">説明</span><span class="sxs-lookup"><span data-stu-id="540a7-131">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="540a7-132"><xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="540a7-132"><xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName></span></span>|<span data-ttu-id="540a7-133">属性の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="540a7-133">Sets the value of an attribute.</span></span>|  
|<span data-ttu-id="540a7-134"><xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=fullName></xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="540a7-134"><xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="540a7-135">属性の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="540a7-135">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="540a7-136">次の方法を変更、 <xref:System.Xml.Linq.XNode>(を含め、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>).</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="540a7-136">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="540a7-137">メソッド</span><span class="sxs-lookup"><span data-stu-id="540a7-137">Method</span></span>|<span data-ttu-id="540a7-138">説明</span><span class="sxs-lookup"><span data-stu-id="540a7-138">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="540a7-139"><xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="540a7-139"><xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=fullName></span></span>|<span data-ttu-id="540a7-140">ノードを新しいコンテンツに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="540a7-140">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="540a7-141">次の方法を変更、 <xref:System.Xml.Linq.XContainer>(、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>).</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XContainer></span><span class="sxs-lookup"><span data-stu-id="540a7-141">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="540a7-142">メソッド</span><span class="sxs-lookup"><span data-stu-id="540a7-142">Method</span></span>|<span data-ttu-id="540a7-143">説明</span><span class="sxs-lookup"><span data-stu-id="540a7-143">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="540a7-144"><xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="540a7-144"><xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=fullName></span></span>|<span data-ttu-id="540a7-145">子ノードを新しいコンテンツに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="540a7-145">Replaces the children nodes with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="540a7-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="540a7-146">See Also</span></span>  
 [<span data-ttu-id="540a7-147">XML ツリー (LINQ to XML) の変更 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="540a7-147">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)

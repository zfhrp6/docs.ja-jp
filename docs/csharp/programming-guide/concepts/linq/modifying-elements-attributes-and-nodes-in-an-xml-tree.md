---
title: "XML ツリー内の要素、属性、およびノードの変更"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: da3b31456bc86b547c5174143620f464dc42f35b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="443a0-102">XML ツリー内の要素、属性、およびノードの変更</span><span class="sxs-lookup"><span data-stu-id="443a0-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="443a0-103">次の表は、要素、その子要素、またはその属性の変更に使用できるメソッドとプロパティについてまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="443a0-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="443a0-104">次のメソッドは、<xref:System.Xml.Linq.XElement> を変更します。</span><span class="sxs-lookup"><span data-stu-id="443a0-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="443a0-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="443a0-105">Method</span></span>|<span data-ttu-id="443a0-106">説明</span><span class="sxs-lookup"><span data-stu-id="443a0-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="443a0-107">要素を解析された XML に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="443a0-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="443a0-108">要素のすべてのコンテンツ (子ノードおよび属性) を削除します。</span><span class="sxs-lookup"><span data-stu-id="443a0-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="443a0-109">要素の属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="443a0-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="443a0-110">要素のすべてのコンテンツ (子ノードおよび属性) を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="443a0-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="443a0-111">要素の属性を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="443a0-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="443a0-112">属性の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="443a0-112">Sets the value of an attribute.</span></span> <span data-ttu-id="443a0-113">属性が存在しない場合は作成します。</span><span class="sxs-lookup"><span data-stu-id="443a0-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="443a0-114">値に `null` が設定された場合は、属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="443a0-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="443a0-115">子要素の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="443a0-115">Sets the value of a child element.</span></span> <span data-ttu-id="443a0-116">要素が存在しない場合は作成します。</span><span class="sxs-lookup"><span data-stu-id="443a0-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="443a0-117">値に `null` が設定された場合は、要素を削除します。</span><span class="sxs-lookup"><span data-stu-id="443a0-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="443a0-118">要素のコンテンツ (子ノード) を、指定したテキストに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="443a0-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="443a0-119">要素の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="443a0-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="443a0-120">次のメソッドは、<xref:System.Xml.Linq.XAttribute> を変更します。</span><span class="sxs-lookup"><span data-stu-id="443a0-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="443a0-121">メソッド</span><span class="sxs-lookup"><span data-stu-id="443a0-121">Method</span></span>|<span data-ttu-id="443a0-122">説明</span><span class="sxs-lookup"><span data-stu-id="443a0-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="443a0-123">属性の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="443a0-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="443a0-124">属性の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="443a0-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="443a0-125">次のメソッドは、<xref:System.Xml.Linq.XNode> (<xref:System.Xml.Linq.XElement> または <xref:System.Xml.Linq.XDocument> を含む) を変更します。</span><span class="sxs-lookup"><span data-stu-id="443a0-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="443a0-126">メソッド</span><span class="sxs-lookup"><span data-stu-id="443a0-126">Method</span></span>|<span data-ttu-id="443a0-127">説明</span><span class="sxs-lookup"><span data-stu-id="443a0-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="443a0-128">ノードを新しいコンテンツに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="443a0-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="443a0-129">次のメソッドは、<xref:System.Xml.Linq.XContainer> (<xref:System.Xml.Linq.XElement> または <xref:System.Xml.Linq.XDocument>) を変更します。</span><span class="sxs-lookup"><span data-stu-id="443a0-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="443a0-130">メソッド</span><span class="sxs-lookup"><span data-stu-id="443a0-130">Method</span></span>|<span data-ttu-id="443a0-131">説明</span><span class="sxs-lookup"><span data-stu-id="443a0-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="443a0-132">子ノードを新しいコンテンツに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="443a0-132">Replaces the children nodes with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="443a0-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="443a0-133">See Also</span></span>  
 [<span data-ttu-id="443a0-134">XML ツリーの変更 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="443a0-134">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)

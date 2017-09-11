---
title: "XML 軸プロパティ (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- XML axis properties [Visual Basic]
- Visual Basic code, XML
- XML axis [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 7e400e20-5d1e-4d22-a65c-9df79d5c1621
caps.latest.revision: 9
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
ms.openlocfilehash: 4dd15670eed316552f2f02e4536122a6a110542d
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="xml-axis-properties-visual-basic"></a><span data-ttu-id="9160a-102">XML 軸プロパティ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9160a-102">XML Axis Properties (Visual Basic)</span></span>
<span data-ttu-id="9160a-103">このセクションのトピックで XML 軸プロパティの構文について説明[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="9160a-103">The topics in this section document the syntax of XML axis properties in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="9160a-104">XML 軸プロパティを使用する簡単に XML をコード内で直接アクセスします。</span><span class="sxs-lookup"><span data-stu-id="9160a-104">The XML axis properties make it easy to access XML directly in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9160a-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="9160a-105">In This Section</span></span>  
  
|<span data-ttu-id="9160a-106">トピック</span><span class="sxs-lookup"><span data-stu-id="9160a-106">Topic</span></span>|<span data-ttu-id="9160a-107">説明</span><span class="sxs-lookup"><span data-stu-id="9160a-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="9160a-108">XML 属性軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="9160a-108">XML Attribute Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)|<span data-ttu-id="9160a-109">属性にアクセスする方法について説明する<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="9160a-109">Describes how to access the attributes of an <xref:System.Xml.Linq.XElement> object.</span></span>|  
|[<span data-ttu-id="9160a-110">XML 子軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="9160a-110">XML Child Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)|<span data-ttu-id="9160a-111">子にアクセスする方法について説明する<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="9160a-111">Describes how to access the children of an <xref:System.Xml.Linq.XElement> object.</span></span>|  
|[<span data-ttu-id="9160a-112">XML 子孫軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="9160a-112">XML Descendant Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)|<span data-ttu-id="9160a-113">子孫にアクセスする方法について説明する<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="9160a-113">Describes how to access the descendants of an <xref:System.Xml.Linq.XElement> object.</span></span>|  
|[<span data-ttu-id="9160a-114">拡張インデクサー プロパティ</span><span class="sxs-lookup"><span data-stu-id="9160a-114">Extension Indexer Property</span></span>](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)|<span data-ttu-id="9160a-115">コレクションの個々 の要素にアクセスする方法について説明<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XAttribute>オブジェクト</xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="9160a-115">Describes how to access individual elements in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects.</span></span>|  
|[<span data-ttu-id="9160a-116">XML Value プロパティ</span><span class="sxs-lookup"><span data-stu-id="9160a-116">XML Value Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)|<span data-ttu-id="9160a-117">コレクションの最初の要素の値にアクセスする方法について説明<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XAttribute>オブジェクト</xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="9160a-117">Describes how to access the value of the first element of a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9160a-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="9160a-118">See Also</span></span>  
 [<span data-ttu-id="9160a-119">XML</span><span class="sxs-lookup"><span data-stu-id="9160a-119">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)

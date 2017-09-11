---
title: "Visual Basic における XML にアクセスする |Microsoft ドキュメント"
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
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
caps.latest.revision: 18
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
ms.openlocfilehash: fe096d3686adc2386235944b59b51fb7442dd096
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="f9d8a-102">Visual Basic での XML へのアクセス</span><span class="sxs-lookup"><span data-stu-id="f9d8a-102">Accessing XML in Visual Basic</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="f9d8a-103">XML 軸プロパティにアクセスして、移動[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]構造体。</span><span class="sxs-lookup"><span data-stu-id="f9d8a-103"> provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] structures.</span></span> <span data-ttu-id="f9d8a-104">これらのプロパティは、XML の名前を指定する要素と属性にアクセスするために、特別な構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="f9d8a-104">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="f9d8a-105">次の表に、XML 要素と属性にアクセスするための言語機能[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="f9d8a-105">The following table lists the language features that enable you to access XML elements and attributes in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="f9d8a-106">XML 軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="f9d8a-106">XML Axis Properties</span></span>  
  
|<span data-ttu-id="f9d8a-107">プロパティの説明</span><span class="sxs-lookup"><span data-stu-id="f9d8a-107">Property description</span></span>|<span data-ttu-id="f9d8a-108">例</span><span class="sxs-lookup"><span data-stu-id="f9d8a-108">Example</span></span>|<span data-ttu-id="f9d8a-109">説明</span><span class="sxs-lookup"><span data-stu-id="f9d8a-109">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="f9d8a-110">*child 軸*</span><span class="sxs-lookup"><span data-stu-id="f9d8a-110">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="f9d8a-111">すべてを取得します`phone`要素の子要素である、`contact`要素。</span><span class="sxs-lookup"><span data-stu-id="f9d8a-111">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="f9d8a-112">*attribute 軸*</span><span class="sxs-lookup"><span data-stu-id="f9d8a-112">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="f9d8a-113">すべてを取得します`type`の属性、`phone`要素。</span><span class="sxs-lookup"><span data-stu-id="f9d8a-113">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="f9d8a-114">*子孫軸*</span><span class="sxs-lookup"><span data-stu-id="f9d8a-114">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="f9d8a-115">すべてを取得します`name`の要素、`contacts`に関係なく、発生した階層の深さの要素。</span><span class="sxs-lookup"><span data-stu-id="f9d8a-115">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="f9d8a-116">*拡張機能インデクサー*</span><span class="sxs-lookup"><span data-stu-id="f9d8a-116">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="f9d8a-117">最初の取得`name`シーケンスから要素。</span><span class="sxs-lookup"><span data-stu-id="f9d8a-117">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="f9d8a-118">*value*</span><span class="sxs-lookup"><span data-stu-id="f9d8a-118">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="f9d8a-119">シーケンスの最初のオブジェクトの文字列形式を取得または`Nothing`シーケンスが空の場合。</span><span class="sxs-lookup"><span data-stu-id="f9d8a-119">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="f9d8a-120">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f9d8a-120">In This Section</span></span>  
 [<span data-ttu-id="f9d8a-121">方法: XML 子孫要素にアクセスする</span><span class="sxs-lookup"><span data-stu-id="f9d8a-121">How to: Access XML Descendant Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="f9d8a-122">子孫軸プロパティを使用して、指定の名前を持ち、指定された XML 要素に含まれるすべての XML 要素にアクセスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f9d8a-122">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="f9d8a-123">方法: XML 子要素にアクセスする</span><span class="sxs-lookup"><span data-stu-id="f9d8a-123">How to: Access XML Child Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 <span data-ttu-id="f9d8a-124">軸にアクセスするプロパティを XML 要素で指定した名前を持つすべての XML 子要素の子を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f9d8a-124">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="f9d8a-125">方法: XML 属性にアクセスする</span><span class="sxs-lookup"><span data-stu-id="f9d8a-125">How to: Access XML Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 <span data-ttu-id="f9d8a-126">属性軸プロパティを使用して XML 要素で指定した名前を持つすべての XML 属性にアクセスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f9d8a-126">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="f9d8a-127">方法 : XML 名前空間プレフィックスを宣言して使用する</span><span class="sxs-lookup"><span data-stu-id="f9d8a-127">How to: Declare and Use XML Namespace Prefixes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="f9d8a-128">XML 名前空間プレフィックスを宣言し、これを作成し、XML 要素にアクセスに使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f9d8a-128">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f9d8a-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9d8a-129">Related Sections</span></span>  
 [<span data-ttu-id="f9d8a-130">XML 軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="f9d8a-130">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 <span data-ttu-id="f9d8a-131">さまざまな XML アクセス プロパティを説明するセクションへのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="f9d8a-131">Provides links to sections describing the various XML access properties.</span></span>  
  
 [<span data-ttu-id="f9d8a-132">Visual Basic における LINQ to XML の概要</span><span class="sxs-lookup"><span data-stu-id="f9d8a-132">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="f9d8a-133">使用の概要については、 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] Visual Basic でします。</span><span class="sxs-lookup"><span data-stu-id="f9d8a-133">Provides an introduction to using [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="f9d8a-134">Visual Basic で XML を作成します。</span><span class="sxs-lookup"><span data-stu-id="f9d8a-134">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="f9d8a-135">Visual Basic で XML リテラルを使用するための概要を提供します。</span><span class="sxs-lookup"><span data-stu-id="f9d8a-135">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="f9d8a-136">Visual Basic で XML を操作します。</span><span class="sxs-lookup"><span data-stu-id="f9d8a-136">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 <span data-ttu-id="f9d8a-137">読み込みと Visual Basic における XML の修正についてのセクションへのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="f9d8a-137">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="f9d8a-138">XML</span><span class="sxs-lookup"><span data-stu-id="f9d8a-138">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="f9d8a-139">使用する方法を説明するセクションへのリンクを提供[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]Visual Basic でします。</span><span class="sxs-lookup"><span data-stu-id="f9d8a-139">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] in Visual Basic.</span></span>

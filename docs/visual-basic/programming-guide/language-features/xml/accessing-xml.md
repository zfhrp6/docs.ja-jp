---
title: Visual Basic での XML へのアクセス
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: 064e4b224d37172b8f79e57c73164b90186ef922
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="0555d-102">Visual Basic での XML へのアクセス</span><span class="sxs-lookup"><span data-stu-id="0555d-102">Accessing XML in Visual Basic</span></span>
<span data-ttu-id="0555d-103">Visual Basic XML 軸のプロパティにアクセスして移動するために用意[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]構造体。</span><span class="sxs-lookup"><span data-stu-id="0555d-103">Visual Basic provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] structures.</span></span> <span data-ttu-id="0555d-104">これらのプロパティは、XML の名前を指定する要素と属性にアクセスするために、特別な構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="0555d-104">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="0555d-105">次の表は、XML 要素と Visual Basic における属性にアクセスできるようにする言語機能を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="0555d-105">The following table lists the language features that enable you to access XML elements and attributes in Visual Basic.</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="0555d-106">XML 軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="0555d-106">XML Axis Properties</span></span>  
  
|<span data-ttu-id="0555d-107">プロパティの説明</span><span class="sxs-lookup"><span data-stu-id="0555d-107">Property description</span></span>|<span data-ttu-id="0555d-108">例</span><span class="sxs-lookup"><span data-stu-id="0555d-108">Example</span></span>|<span data-ttu-id="0555d-109">説明</span><span class="sxs-lookup"><span data-stu-id="0555d-109">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="0555d-110">*child 軸*</span><span class="sxs-lookup"><span data-stu-id="0555d-110">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="0555d-111">すべてを取得`phone`要素の子要素である、`contact`要素。</span><span class="sxs-lookup"><span data-stu-id="0555d-111">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="0555d-112">*attribute 軸*</span><span class="sxs-lookup"><span data-stu-id="0555d-112">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="0555d-113">すべてを取得`type`の属性、`phone`要素。</span><span class="sxs-lookup"><span data-stu-id="0555d-113">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="0555d-114">*descendant 軸*</span><span class="sxs-lookup"><span data-stu-id="0555d-114">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="0555d-115">すべてを取得`name`の要素、`contacts`に関係なく発生する階層の深さの要素。</span><span class="sxs-lookup"><span data-stu-id="0555d-115">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="0555d-116">*拡張機能インデクサー*</span><span class="sxs-lookup"><span data-stu-id="0555d-116">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="0555d-117">最初に取得`name`シーケンスから要素。</span><span class="sxs-lookup"><span data-stu-id="0555d-117">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="0555d-118">*値*</span><span class="sxs-lookup"><span data-stu-id="0555d-118">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="0555d-119">シーケンスの最初のオブジェクトの文字列形式を取得または`Nothing`シーケンスが空の場合。</span><span class="sxs-lookup"><span data-stu-id="0555d-119">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="0555d-120">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="0555d-120">In This Section</span></span>  
 [<span data-ttu-id="0555d-121">方法: XML 子孫要素にアクセスする</span><span class="sxs-lookup"><span data-stu-id="0555d-121">How to: Access XML Descendant Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="0555d-122">子孫軸プロパティを使用して、指定した名前を持ち、指定された XML 要素に含まれるすべての XML 要素にアクセスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0555d-122">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="0555d-123">方法: XML 子要素にアクセスする</span><span class="sxs-lookup"><span data-stu-id="0555d-123">How to: Access XML Child Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 <span data-ttu-id="0555d-124">軸のプロパティを XML 要素で指定した名前を持つすべての XML 子要素にアクセスする子を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0555d-124">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="0555d-125">方法: XML 属性にアクセスする</span><span class="sxs-lookup"><span data-stu-id="0555d-125">How to: Access XML Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 <span data-ttu-id="0555d-126">属性軸プロパティを使用して XML 要素で指定した名前を持つすべての XML 属性にアクセスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0555d-126">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="0555d-127">方法 : XML 名前空間プレフィックスを宣言して使用する</span><span class="sxs-lookup"><span data-stu-id="0555d-127">How to: Declare and Use XML Namespace Prefixes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="0555d-128">XML 名前空間プレフィックスを宣言し、それを使用して作成し、XML 要素にアクセスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0555d-128">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0555d-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="0555d-129">Related Sections</span></span>  
 [<span data-ttu-id="0555d-130">XML 軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="0555d-130">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 <span data-ttu-id="0555d-131">さまざまな XML アクセス プロパティを説明するセクションへのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="0555d-131">Provides links to sections describing the various XML access properties.</span></span>  
  
 [<span data-ttu-id="0555d-132">Visual Basic における LINQ to XML の概要</span><span class="sxs-lookup"><span data-stu-id="0555d-132">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="0555d-133">使用する方法について紹介[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Visual Basic でします。</span><span class="sxs-lookup"><span data-stu-id="0555d-133">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="0555d-134">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="0555d-134">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="0555d-135">Visual Basic での XML リテラルの使用の概要を提供します。</span><span class="sxs-lookup"><span data-stu-id="0555d-135">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="0555d-136">Visual Basic での XML の操作</span><span class="sxs-lookup"><span data-stu-id="0555d-136">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 <span data-ttu-id="0555d-137">読み込みと Visual Basic における XML を変更するセクションへのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="0555d-137">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="0555d-138">XML</span><span class="sxs-lookup"><span data-stu-id="0555d-138">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="0555d-139">使用する方法を説明するセクションへのリンクを提供[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Visual Basic でします。</span><span class="sxs-lookup"><span data-stu-id="0555d-139">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>

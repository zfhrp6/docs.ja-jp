---
title: Visual Basic での XML へのアクセス
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: b000b3f6846f800b2a96ce10cdd408a355f78a81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649595"
---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="77a27-102">Visual Basic での XML へのアクセス</span><span class="sxs-lookup"><span data-stu-id="77a27-102">Accessing XML in Visual Basic</span></span>
<span data-ttu-id="77a27-103">Visual Basic XML 軸のプロパティにアクセスして移動するために用意[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]構造体。</span><span class="sxs-lookup"><span data-stu-id="77a27-103">Visual Basic provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] structures.</span></span> <span data-ttu-id="77a27-104">これらのプロパティは、XML の名前を指定する要素と属性にアクセスするために、特別な構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="77a27-104">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="77a27-105">次の表は、XML 要素と Visual Basic における属性にアクセスできるようにする言語機能を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="77a27-105">The following table lists the language features that enable you to access XML elements and attributes in Visual Basic.</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="77a27-106">XML 軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="77a27-106">XML Axis Properties</span></span>  
  
|<span data-ttu-id="77a27-107">プロパティの説明</span><span class="sxs-lookup"><span data-stu-id="77a27-107">Property description</span></span>|<span data-ttu-id="77a27-108">例</span><span class="sxs-lookup"><span data-stu-id="77a27-108">Example</span></span>|<span data-ttu-id="77a27-109">説明</span><span class="sxs-lookup"><span data-stu-id="77a27-109">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="77a27-110">*child 軸*</span><span class="sxs-lookup"><span data-stu-id="77a27-110">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="77a27-111">すべてを取得`phone`要素の子要素である、`contact`要素。</span><span class="sxs-lookup"><span data-stu-id="77a27-111">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="77a27-112">*attribute 軸*</span><span class="sxs-lookup"><span data-stu-id="77a27-112">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="77a27-113">すべてを取得`type`の属性、`phone`要素。</span><span class="sxs-lookup"><span data-stu-id="77a27-113">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="77a27-114">*descendant 軸*</span><span class="sxs-lookup"><span data-stu-id="77a27-114">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="77a27-115">すべてを取得`name`の要素、`contacts`に関係なく発生する階層の深さの要素。</span><span class="sxs-lookup"><span data-stu-id="77a27-115">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="77a27-116">*拡張機能インデクサー*</span><span class="sxs-lookup"><span data-stu-id="77a27-116">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="77a27-117">最初に取得`name`シーケンスから要素。</span><span class="sxs-lookup"><span data-stu-id="77a27-117">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="77a27-118">*値*</span><span class="sxs-lookup"><span data-stu-id="77a27-118">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="77a27-119">シーケンスの最初のオブジェクトの文字列形式を取得または`Nothing`シーケンスが空の場合。</span><span class="sxs-lookup"><span data-stu-id="77a27-119">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="77a27-120">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="77a27-120">In This Section</span></span>  
 [<span data-ttu-id="77a27-121">方法: XML 子孫要素にアクセスする</span><span class="sxs-lookup"><span data-stu-id="77a27-121">How to: Access XML Descendant Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="77a27-122">子孫軸プロパティを使用して、指定した名前を持ち、指定された XML 要素に含まれるすべての XML 要素にアクセスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="77a27-122">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="77a27-123">方法: XML 子要素にアクセスする</span><span class="sxs-lookup"><span data-stu-id="77a27-123">How to: Access XML Child Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 <span data-ttu-id="77a27-124">軸のプロパティを XML 要素で指定した名前を持つすべての XML 子要素にアクセスする子を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="77a27-124">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="77a27-125">方法: XML 属性にアクセスする</span><span class="sxs-lookup"><span data-stu-id="77a27-125">How to: Access XML Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 <span data-ttu-id="77a27-126">属性軸プロパティを使用して XML 要素で指定した名前を持つすべての XML 属性にアクセスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="77a27-126">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="77a27-127">方法 : XML 名前空間プレフィックスを宣言して使用する</span><span class="sxs-lookup"><span data-stu-id="77a27-127">How to: Declare and Use XML Namespace Prefixes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="77a27-128">XML 名前空間プレフィックスを宣言し、それを使用して作成し、XML 要素にアクセスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="77a27-128">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="77a27-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="77a27-129">Related Sections</span></span>  
 [<span data-ttu-id="77a27-130">XML 軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="77a27-130">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 <span data-ttu-id="77a27-131">さまざまな XML アクセス プロパティを説明するセクションへのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="77a27-131">Provides links to sections describing the various XML access properties.</span></span>  
  
 [<span data-ttu-id="77a27-132">Visual Basic における LINQ to XML の概要</span><span class="sxs-lookup"><span data-stu-id="77a27-132">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="77a27-133">使用する方法について紹介[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Visual Basic でします。</span><span class="sxs-lookup"><span data-stu-id="77a27-133">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="77a27-134">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="77a27-134">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="77a27-135">Visual Basic での XML リテラルの使用の概要を提供します。</span><span class="sxs-lookup"><span data-stu-id="77a27-135">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="77a27-136">Visual Basic での XML の操作</span><span class="sxs-lookup"><span data-stu-id="77a27-136">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 <span data-ttu-id="77a27-137">読み込みと Visual Basic における XML を変更するセクションへのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="77a27-137">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="77a27-138">XML</span><span class="sxs-lookup"><span data-stu-id="77a27-138">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="77a27-139">使用する方法を説明するセクションへのリンクを提供[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Visual Basic でします。</span><span class="sxs-lookup"><span data-stu-id="77a27-139">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>

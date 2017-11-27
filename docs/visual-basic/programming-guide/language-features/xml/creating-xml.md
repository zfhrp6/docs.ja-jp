---
title: "Visual Basic での XML の作成"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML [Visual Basic], creating
- LINQ to XML [Visual Basic], creating XML
- XML literals [Visual Basic], creating
ms.assetid: 8ae29ec5-e5fb-4137-9df5-60a288df7045
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 95ab82f2a8ae11b04e3887d5a179931c47346155
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="creating-xml-in-visual-basic"></a><span data-ttu-id="3f053-102">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="3f053-102">Creating XML in Visual Basic</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="3f053-103">使用することができます*XML リテラル*コード内で直接です。</span><span class="sxs-lookup"><span data-stu-id="3f053-103"> enables you to use *XML literals* directly in your code.</span></span> <span data-ttu-id="3f053-104">XML リテラルの構文を表します[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]オブジェクト、およびそれには、XML 1.0 の構文に似ています。</span><span class="sxs-lookup"><span data-stu-id="3f053-104">The XML literal syntax represents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects, and it is similar to the XML 1.0 syntax.</span></span> <span data-ttu-id="3f053-105">これにより、簡単に、コードが、最終的な XML と同じ構造を有して XML 要素、ドキュメント、およびフラグメントをプログラムで作成します。</span><span class="sxs-lookup"><span data-stu-id="3f053-105">This makes it easier to create XML elements, documents, and fragments programmatically because your code has the same structure as the final XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3f053-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="3f053-106">In This Section</span></span>  
  
|<span data-ttu-id="3f053-107">用語</span><span class="sxs-lookup"><span data-stu-id="3f053-107">Term</span></span>|<span data-ttu-id="3f053-108">定義</span><span class="sxs-lookup"><span data-stu-id="3f053-108">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="3f053-109">XML リテラルの概要</span><span class="sxs-lookup"><span data-stu-id="3f053-109">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)|<span data-ttu-id="3f053-110">XML リテラルとどのように関連する概要[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="3f053-110">Introduction to XML literals and how they relate to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>|  
|[<span data-ttu-id="3f053-111">XML での埋め込み式</span><span class="sxs-lookup"><span data-stu-id="3f053-111">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)|<span data-ttu-id="3f053-112">XML リテラルで埋め込み式を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3f053-112">Describes how to use embedded expressions in XML literals.</span></span>|  
|[<span data-ttu-id="3f053-113">方法: XML リテラルを作成する</span><span class="sxs-lookup"><span data-stu-id="3f053-113">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)|<span data-ttu-id="3f053-114">XML リテラルを使用してコードで XML 要素を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3f053-114">Describes how to create an XML element in code by using an XML literal.</span></span>|  
|[<span data-ttu-id="3f053-115">XML リテラルでの空白文字</span><span class="sxs-lookup"><span data-stu-id="3f053-115">White Space in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/white-space-in-xml-literals.md)|<span data-ttu-id="3f053-116">説明方法[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]XML リテラルの空白文字を処理します。</span><span class="sxs-lookup"><span data-stu-id="3f053-116">Describes how [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] treats white space in XML literals.</span></span>|  
|[<span data-ttu-id="3f053-117">XML リテラルと XML 1.0 仕様</span><span class="sxs-lookup"><span data-stu-id="3f053-117">XML Literals and the XML 1.0 Specification</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)|<span data-ttu-id="3f053-118">について説明する方法で XML リテラルの構文[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]が XML 1.0 仕様に関連します。</span><span class="sxs-lookup"><span data-stu-id="3f053-118">Describes how the XML literal syntax in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] relates to the XML 1.0 specification.</span></span>|  
|[<span data-ttu-id="3f053-119">方法 : XML リテラルに式を埋め込む</span><span class="sxs-lookup"><span data-stu-id="3f053-119">How to: Embed Expressions in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-embed-expressions-in-xml-literals.md)|<span data-ttu-id="3f053-120">XML リテラルで埋め込み式を使用して、実行時にコンテンツを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3f053-120">Describes how to use embedded expressions in XML literals to create content at run time.</span></span>|  
|[<span data-ttu-id="3f053-121">宣言する XML 要素と属性の名前</span><span class="sxs-lookup"><span data-stu-id="3f053-121">Names of Declared XML Elements and Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)|<span data-ttu-id="3f053-122">XML 要素と属性の名前付けのガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="3f053-122">Describes guidelines for naming XML elements and attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3f053-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f053-123">See Also</span></span>  
 [<span data-ttu-id="3f053-124">XML</span><span class="sxs-lookup"><span data-stu-id="3f053-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)

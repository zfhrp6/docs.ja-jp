---
title: Visual Basic での XML の作成
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], creating
- LINQ to XML [Visual Basic], creating XML
- XML literals [Visual Basic], creating
ms.assetid: 8ae29ec5-e5fb-4137-9df5-60a288df7045
ms.openlocfilehash: 46f9174e78cc67c1e352d02ac6b5038f5da01086
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="creating-xml-in-visual-basic"></a><span data-ttu-id="a7787-102">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="a7787-102">Creating XML in Visual Basic</span></span>
<span data-ttu-id="a7787-103">Visual Basic では、使用することができます*XML リテラル*コード内で直接です。</span><span class="sxs-lookup"><span data-stu-id="a7787-103">Visual Basic enables you to use *XML literals* directly in your code.</span></span> <span data-ttu-id="a7787-104">XML リテラルの構文を表します[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]オブジェクト、およびそれには、XML 1.0 の構文に似ています。</span><span class="sxs-lookup"><span data-stu-id="a7787-104">The XML literal syntax represents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects, and it is similar to the XML 1.0 syntax.</span></span> <span data-ttu-id="a7787-105">これにより、簡単に、コードが、最終的な XML と同じ構造を有して XML 要素、ドキュメント、およびフラグメントをプログラムで作成します。</span><span class="sxs-lookup"><span data-stu-id="a7787-105">This makes it easier to create XML elements, documents, and fragments programmatically because your code has the same structure as the final XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a7787-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a7787-106">In This Section</span></span>  
  
|<span data-ttu-id="a7787-107">用語</span><span class="sxs-lookup"><span data-stu-id="a7787-107">Term</span></span>|<span data-ttu-id="a7787-108">定義</span><span class="sxs-lookup"><span data-stu-id="a7787-108">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="a7787-109">XML リテラルの概要</span><span class="sxs-lookup"><span data-stu-id="a7787-109">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)|<span data-ttu-id="a7787-110">XML リテラルとどのように関連する概要[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="a7787-110">Introduction to XML literals and how they relate to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>|  
|[<span data-ttu-id="a7787-111">XML での埋め込み式</span><span class="sxs-lookup"><span data-stu-id="a7787-111">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)|<span data-ttu-id="a7787-112">XML リテラルで埋め込み式を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a7787-112">Describes how to use embedded expressions in XML literals.</span></span>|  
|[<span data-ttu-id="a7787-113">方法: XML リテラルを作成する</span><span class="sxs-lookup"><span data-stu-id="a7787-113">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)|<span data-ttu-id="a7787-114">XML リテラルを使用してコードで XML 要素を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a7787-114">Describes how to create an XML element in code by using an XML literal.</span></span>|  
|[<span data-ttu-id="a7787-115">XML リテラルでの空白文字</span><span class="sxs-lookup"><span data-stu-id="a7787-115">White Space in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/white-space-in-xml-literals.md)|<span data-ttu-id="a7787-116">XML リテラル Visual Basic が空白文字を処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a7787-116">Describes how Visual Basic treats white space in XML literals.</span></span>|  
|[<span data-ttu-id="a7787-117">XML リテラルと XML 1.0 仕様</span><span class="sxs-lookup"><span data-stu-id="a7787-117">XML Literals and the XML 1.0 Specification</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)|<span data-ttu-id="a7787-118">Visual Basic で XML リテラルの構文が、XML 1.0 仕様に関連付ける方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a7787-118">Describes how the XML literal syntax in Visual Basic relates to the XML 1.0 specification.</span></span>|  
|[<span data-ttu-id="a7787-119">方法 : XML リテラルに式を埋め込む</span><span class="sxs-lookup"><span data-stu-id="a7787-119">How to: Embed Expressions in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-embed-expressions-in-xml-literals.md)|<span data-ttu-id="a7787-120">XML リテラルで埋め込み式を使用して、実行時にコンテンツを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a7787-120">Describes how to use embedded expressions in XML literals to create content at run time.</span></span>|  
|[<span data-ttu-id="a7787-121">宣言する XML 要素と属性の名前</span><span class="sxs-lookup"><span data-stu-id="a7787-121">Names of Declared XML Elements and Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)|<span data-ttu-id="a7787-122">XML 要素と属性の名前付けのガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="a7787-122">Describes guidelines for naming XML elements and attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7787-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7787-123">See Also</span></span>  
 [<span data-ttu-id="a7787-124">XML</span><span class="sxs-lookup"><span data-stu-id="a7787-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)

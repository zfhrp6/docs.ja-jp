---
title: "Visual Basic で XML を作成する |Microsoft ドキュメント"
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
- XML [Visual Basic], creating
- LINQ to XML [Visual Basic], creating XML
- XML literals [Visual Basic], creating
ms.assetid: 8ae29ec5-e5fb-4137-9df5-60a288df7045
caps.latest.revision: 24
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
ms.openlocfilehash: ec45ab4dc7d4c9282d444c00b0b262b3d8dd4da1
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="creating-xml-in-visual-basic"></a><span data-ttu-id="225c4-102">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="225c4-102">Creating XML in Visual Basic</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="225c4-103">使用できるように*XML リテラル*コード内で直接します。</span><span class="sxs-lookup"><span data-stu-id="225c4-103"> enables you to use *XML literals* directly in your code.</span></span> <span data-ttu-id="225c4-104">XML リテラルの構文を表す[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]オブジェクト、およびそれには、XML 1.0 の構文に似ています。</span><span class="sxs-lookup"><span data-stu-id="225c4-104">The XML literal syntax represents [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objects, and it is similar to the XML 1.0 syntax.</span></span> <span data-ttu-id="225c4-105">これにより、コード、最終的な XML と同じ構造では、XML 要素、ドキュメント、およびフラグメントをプログラムで作成が簡単にします。</span><span class="sxs-lookup"><span data-stu-id="225c4-105">This makes it easier to create XML elements, documents, and fragments programmatically because your code has the same structure as the final XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="225c4-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="225c4-106">In This Section</span></span>  
  
|<span data-ttu-id="225c4-107">用語</span><span class="sxs-lookup"><span data-stu-id="225c4-107">Term</span></span>|<span data-ttu-id="225c4-108">定義</span><span class="sxs-lookup"><span data-stu-id="225c4-108">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="225c4-109">XML リテラルの概要</span><span class="sxs-lookup"><span data-stu-id="225c4-109">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)|<span data-ttu-id="225c4-110">XML リテラルとどのように関連する概要[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="225c4-110">Introduction to XML literals and how they relate to [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span></span>|  
|[<span data-ttu-id="225c4-111">XML での埋め込み式</span><span class="sxs-lookup"><span data-stu-id="225c4-111">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)|<span data-ttu-id="225c4-112">XML リテラルで埋め込み式を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="225c4-112">Describes how to use embedded expressions in XML literals.</span></span>|  
|[<span data-ttu-id="225c4-113">方法: XML リテラルを作成する</span><span class="sxs-lookup"><span data-stu-id="225c4-113">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)|<span data-ttu-id="225c4-114">XML リテラルを使用して、コードで XML 要素を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="225c4-114">Describes how to create an XML element in code by using an XML literal.</span></span>|  
|[<span data-ttu-id="225c4-115">XML リテラルでの空白文字</span><span class="sxs-lookup"><span data-stu-id="225c4-115">White Space in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/white-space-in-xml-literals.md)|<span data-ttu-id="225c4-116">説明方法[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]XML リテラルの空白文字を処理します。</span><span class="sxs-lookup"><span data-stu-id="225c4-116">Describes how [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] treats white space in XML literals.</span></span>|  
|[<span data-ttu-id="225c4-117">XML リテラルと XML 1.0 仕様</span><span class="sxs-lookup"><span data-stu-id="225c4-117">XML Literals and the XML 1.0 Specification</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)|<span data-ttu-id="225c4-118">について説明する方法で XML リテラルの構文[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]が XML 1.0 仕様に関連します。</span><span class="sxs-lookup"><span data-stu-id="225c4-118">Describes how the XML literal syntax in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] relates to the XML 1.0 specification.</span></span>|  
|[<span data-ttu-id="225c4-119">方法 : XML リテラルに式を埋め込む</span><span class="sxs-lookup"><span data-stu-id="225c4-119">How to: Embed Expressions in XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-embed-expressions-in-xml-literals.md)|<span data-ttu-id="225c4-120">XML リテラルで埋め込み式を使用して、実行時にコンテンツを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="225c4-120">Describes how to use embedded expressions in XML literals to create content at run time.</span></span>|  
|[<span data-ttu-id="225c4-121">宣言する XML 要素と属性の名前</span><span class="sxs-lookup"><span data-stu-id="225c4-121">Names of Declared XML Elements and Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)|<span data-ttu-id="225c4-122">XML 要素と属性を名前付けのガイドラインについて説明します。</span><span class="sxs-lookup"><span data-stu-id="225c4-122">Describes guidelines for naming XML elements and attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="225c4-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="225c4-123">See Also</span></span>  
 [<span data-ttu-id="225c4-124">XML</span><span class="sxs-lookup"><span data-stu-id="225c4-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)

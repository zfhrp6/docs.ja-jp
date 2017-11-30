---
title: "宣言する XML 要素と属性の名前 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 846a028e076873d1978f751fdb70e93c7c6a81af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a><span data-ttu-id="78cb7-102">宣言する XML 要素と属性の名前 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78cb7-102">Names of Declared XML Elements and Attributes (Visual Basic)</span></span>
<span data-ttu-id="78cb7-103">このトピックでは[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]XML リテラルの XML 要素および属性の名前付けのガイドライン。</span><span class="sxs-lookup"><span data-stu-id="78cb7-103">This topic provides [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] guidelines for naming XML elements and attributes in XML literals.</span></span>  <span data-ttu-id="78cb7-104">XML リテラルでは、ローカル名または修飾名を指定できます。</span><span class="sxs-lookup"><span data-stu-id="78cb7-104">In an XML literal, you can specify a local name or a qualified name.</span></span> <span data-ttu-id="78cb7-105">XML 名前空間プレフィックス、コロン、およびローカル名の修飾名で構成されます。</span><span class="sxs-lookup"><span data-stu-id="78cb7-105">A qualified name consists of an XML namespace prefix, a colon, and a local name.</span></span> <span data-ttu-id="78cb7-106">XML 名前空間プレフィックスの詳細については、次を参照してください。 [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)です。</span><span class="sxs-lookup"><span data-stu-id="78cb7-106">For more information about XML namespace prefixes, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="78cb7-107">ルール</span><span class="sxs-lookup"><span data-stu-id="78cb7-107">Rules</span></span>  
 <span data-ttu-id="78cb7-108">要素または属性のローカル名[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]次の規則に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="78cb7-108">A local name of an element or attribute in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must adhere to the following rules.</span></span>  
  
-   <span data-ttu-id="78cb7-109">名前空間を開始します。</span><span class="sxs-lookup"><span data-stu-id="78cb7-109">It can begin with a namespace.</span></span> <span data-ttu-id="78cb7-110">英文字またはアンダー スコアで始める必要があります (`_`)。</span><span class="sxs-lookup"><span data-stu-id="78cb7-110">It must begin with an alphabetical character or an underscore (`_`).</span></span>  
  
-   <span data-ttu-id="78cb7-111">それだけアルファベット文字、10 進数字、アンダー スコア、ピリオド (.)、およびハイフンを含める必要があります (-)。</span><span class="sxs-lookup"><span data-stu-id="78cb7-111">It must contain only alphabetical characters, decimal digits, underscores, periods (.), and hyphens (-).</span></span>  
  
-   <span data-ttu-id="78cb7-112">1024 を超える数の文字はできません。</span><span class="sxs-lookup"><span data-stu-id="78cb7-112">It must not be more than 1,024 characters long.</span></span>  
  
-   <span data-ttu-id="78cb7-113">名前に含まれるコロンは、名前空間の区切りを示します。</span><span class="sxs-lookup"><span data-stu-id="78cb7-113">Colons that appear in names indicate namespace demarcation.</span></span> <span data-ttu-id="78cb7-114">したがって、特定の名前の XML 名前空間を指定するだけのコロンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="78cb7-114">Therefore, you can use colons only to specify an XML namespace for a particular name.</span></span>  
  
 <span data-ttu-id="78cb7-115">さらに、次のガイドラインに従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="78cb7-115">In addition, you should adhere to the following guideline.</span></span>  
  
-   <span data-ttu-id="78cb7-116">XML 1.0 仕様では、大文字と小文字バリエーションの 1 つの"xml"、文字列で始まるすべての名前を予約します。</span><span class="sxs-lookup"><span data-stu-id="78cb7-116">The XML 1.0 specification reserves all names starting with the string "xml", of any capitalization variation.</span></span> <span data-ttu-id="78cb7-117">したがって、これらの要素名および属性名は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="78cb7-117">Therefore, do not use those names for your element and attribute names.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="78cb7-118">名前の長さのガイドライン</span><span class="sxs-lookup"><span data-stu-id="78cb7-118">Name Length Guidelines</span></span>  
 <span data-ttu-id="78cb7-119">実際には、名前する必要がありますをできるだけ短く中の要素の特性を明確にします。</span><span class="sxs-lookup"><span data-stu-id="78cb7-119">As a practical matter, a name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="78cb7-120">これにより、コードの読みやすさを向上させ、行の長さとソース ファイルのサイズを削減できます。</span><span class="sxs-lookup"><span data-stu-id="78cb7-120">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="78cb7-121">ただし、自分の名前は、長さを適切に記述しません要素またはコードがそれを使用する方法である必要があります。</span><span class="sxs-lookup"><span data-stu-id="78cb7-121">However, your name should not be so short that it does not adequately describe the element or how your code uses it.</span></span> <span data-ttu-id="78cb7-122">これは、コードの読みやすくするため重要です。</span><span class="sxs-lookup"><span data-stu-id="78cb7-122">This is important for the readability of your code.</span></span> <span data-ttu-id="78cb7-123">理解しようとしている他の人が自分で見ることが、作成した後に長時間場合や、適切な要素名は、時間を節約できます。</span><span class="sxs-lookup"><span data-stu-id="78cb7-123">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, appropriate element names can save time.</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="78cb7-124">名前で大文字小文字の区別</span><span class="sxs-lookup"><span data-stu-id="78cb7-124">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="78cb7-125">XML 要素の名前は大文字小文字を区別します。</span><span class="sxs-lookup"><span data-stu-id="78cb7-125">XML element names are case sensitive.</span></span> <span data-ttu-id="78cb7-126">つまり、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]コンパイラがアルファベットの大文字小文字のみが異なる 2 つの名前を比較し、異なる名前として解釈します。</span><span class="sxs-lookup"><span data-stu-id="78cb7-126">This means that when the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler compares two names that differ in alphabetical case only, it interprets them as different names.</span></span> <span data-ttu-id="78cb7-127">たとえば、解釈`ABC`と`abc`要素を区切るを参照するとします。</span><span class="sxs-lookup"><span data-stu-id="78cb7-127">For example, it interprets `ABC` and `abc` as referring to separate elements.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="78cb7-128">XML 名前空間</span><span class="sxs-lookup"><span data-stu-id="78cb7-128">XML Namespaces</span></span>  
 <span data-ttu-id="78cb7-129">XML 要素リテラルを作成する場合は、要素名の XML 名前空間プレフィックスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="78cb7-129">When creating an XML element literal, you can specify the XML namespace prefix for the element name.</span></span> <span data-ttu-id="78cb7-130">詳細については、次を参照してください。 [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)です。</span><span class="sxs-lookup"><span data-stu-id="78cb7-130">For more information, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78cb7-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="78cb7-131">See Also</span></span>  
 [<span data-ttu-id="78cb7-132">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="78cb7-132">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="78cb7-133">XML 要素リテラル</span><span class="sxs-lookup"><span data-stu-id="78cb7-133">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)

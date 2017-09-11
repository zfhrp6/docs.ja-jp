---
title: "宣言する XML 要素と属性 (Visual Basic) の名前。Microsoft ドキュメント"
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
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
caps.latest.revision: 13
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
ms.openlocfilehash: 2c0bb2350f50138d00e202e2e887a2202d21942f
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a><span data-ttu-id="f1007-102">宣言する XML 要素と属性の名前 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1007-102">Names of Declared XML Elements and Attributes (Visual Basic)</span></span>
<span data-ttu-id="f1007-103">このトピックでは[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]XML リテラルの XML 要素および属性を名前付けのガイドラインです。</span><span class="sxs-lookup"><span data-stu-id="f1007-103">This topic provides [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] guidelines for naming XML elements and attributes in XML literals.</span></span>  <span data-ttu-id="f1007-104">XML リテラルでは、ローカル名または修飾名を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f1007-104">In an XML literal, you can specify a local name or a qualified name.</span></span> <span data-ttu-id="f1007-105">修飾名は、XML 名前空間プレフィックス、コロン、およびローカル名で構成されます。</span><span class="sxs-lookup"><span data-stu-id="f1007-105">A qualified name consists of an XML namespace prefix, a colon, and a local name.</span></span> <span data-ttu-id="f1007-106">XML 名前空間プレフィックスの詳細については、次を参照してください。 [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)します。</span><span class="sxs-lookup"><span data-stu-id="f1007-106">For more information about XML namespace prefixes, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="f1007-107">ルール</span><span class="sxs-lookup"><span data-stu-id="f1007-107">Rules</span></span>  
 <span data-ttu-id="f1007-108">要素または属性のローカル名[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]次の規則に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1007-108">A local name of an element or attribute in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] must adhere to the following rules.</span></span>  
  
-   <span data-ttu-id="f1007-109">名前空間がそれを開始できます。</span><span class="sxs-lookup"><span data-stu-id="f1007-109">It can begin with a namespace.</span></span> <span data-ttu-id="f1007-110">英文字またはアンダー スコアで始まる必要があります (`_`)。</span><span class="sxs-lookup"><span data-stu-id="f1007-110">It must begin with an alphabetical character or an underscore (`_`).</span></span>  
  
-   <span data-ttu-id="f1007-111">のみ英文字、10 進数字、アンダー スコア、ピリオド (.)、およびハイフンを含める必要があります (-)。</span><span class="sxs-lookup"><span data-stu-id="f1007-111">It must contain only alphabetical characters, decimal digits, underscores, periods (.), and hyphens (-).</span></span>  
  
-   <span data-ttu-id="f1007-112">1,024 を超える文字はできません。</span><span class="sxs-lookup"><span data-stu-id="f1007-112">It must not be more than 1,024 characters long.</span></span>  
  
-   <span data-ttu-id="f1007-113">名前に含まれるコロンは、名前空間の区切りを示します。</span><span class="sxs-lookup"><span data-stu-id="f1007-113">Colons that appear in names indicate namespace demarcation.</span></span> <span data-ttu-id="f1007-114">したがって、特定の名前の XML 名前空間を指定する場合のみ、コロンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f1007-114">Therefore, you can use colons only to specify an XML namespace for a particular name.</span></span>  
  
 <span data-ttu-id="f1007-115">さらに、次のガイドラインに従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1007-115">In addition, you should adhere to the following guideline.</span></span>  
  
-   <span data-ttu-id="f1007-116">XML 1.0 仕様では、大文字と小文字のいずれかのバリエーションの"xml"を文字列で始まるすべての名前を予約します。</span><span class="sxs-lookup"><span data-stu-id="f1007-116">The XML 1.0 specification reserves all names starting with the string "xml", of any capitalization variation.</span></span> <span data-ttu-id="f1007-117">したがって、これらの要素名および属性名は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="f1007-117">Therefore, do not use those names for your element and attribute names.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="f1007-118">名前の長さのガイドライン</span><span class="sxs-lookup"><span data-stu-id="f1007-118">Name Length Guidelines</span></span>  
 <span data-ttu-id="f1007-119">実際には、名前する必要がありますできるだけ短く中の要素の特性を明確にします。</span><span class="sxs-lookup"><span data-stu-id="f1007-119">As a practical matter, a name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="f1007-120">これにより、コードの読みやすさを向上し、行の長さとソース ファイルのサイズを小さきます。</span><span class="sxs-lookup"><span data-stu-id="f1007-120">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="f1007-121">ただし、自分の名前は、長さいない適切に記述できる要素かどうか、コードがこれを使用する方法である必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1007-121">However, your name should not be so short that it does not adequately describe the element or how your code uses it.</span></span> <span data-ttu-id="f1007-122">これは、コードの読みやすさにとって重要です。</span><span class="sxs-lookup"><span data-stu-id="f1007-122">This is important for the readability of your code.</span></span> <span data-ttu-id="f1007-123">使い方も理解しようとする他の人がいる場合、または自分で検索する場合に作成した後、長い時間は、適切な要素の名前は、時間を節約できます。</span><span class="sxs-lookup"><span data-stu-id="f1007-123">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, appropriate element names can save time.</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="f1007-124">名前に大文字小文字の区別</span><span class="sxs-lookup"><span data-stu-id="f1007-124">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="f1007-125">XML 要素名は、大文字小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="f1007-125">XML element names are case sensitive.</span></span> <span data-ttu-id="f1007-126">つまり、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラがアルファベットの大文字小文字の表記が異なる&2; つの名前を比較し、異なる名前として解釈します。</span><span class="sxs-lookup"><span data-stu-id="f1007-126">This means that when the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler compares two names that differ in alphabetical case only, it interprets them as different names.</span></span> <span data-ttu-id="f1007-127">たとえば、解釈`ABC`と`abc`要素を区切る参照するものとします。</span><span class="sxs-lookup"><span data-stu-id="f1007-127">For example, it interprets `ABC` and `abc` as referring to separate elements.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="f1007-128">XML 名前空間</span><span class="sxs-lookup"><span data-stu-id="f1007-128">XML Namespaces</span></span>  
 <span data-ttu-id="f1007-129">XML 要素リテラルを作成する場合は、要素名の XML 名前空間プレフィックスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f1007-129">When creating an XML element literal, you can specify the XML namespace prefix for the element name.</span></span> <span data-ttu-id="f1007-130">詳細については、次を参照してください。 [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)します。</span><span class="sxs-lookup"><span data-stu-id="f1007-130">For more information, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1007-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1007-131">See Also</span></span>  
 <span data-ttu-id="f1007-132">[Visual Basic で XML を作成します。](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="f1007-132">[Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="f1007-133"> [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)</span><span class="sxs-lookup"><span data-stu-id="f1007-133"> [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)</span></span>

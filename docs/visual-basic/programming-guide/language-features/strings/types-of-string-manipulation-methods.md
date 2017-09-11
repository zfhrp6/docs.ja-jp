---
title: "Visual Basic で文字列操作メソッドの種類 |Microsoft ドキュメント"
ms.custom: 
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
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
caps.latest.revision: 12
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
ms.openlocfilehash: 9c63ad0931ae2f3760576a792795b9fe0ab6a409
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a><span data-ttu-id="454d4-102">Visual Basic における文字列操作メソッドの種類</span><span class="sxs-lookup"><span data-stu-id="454d4-102">Types of String Manipulation Methods in Visual Basic</span></span>
<span data-ttu-id="454d4-103">分析し、文字列の操作をいくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="454d4-103">There are several different ways to analyze and manipulate your strings.</span></span> <span data-ttu-id="454d4-104">一部である一部のメソッド、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]言語、およびその他のユーザーに内在する、`String`クラスです。</span><span class="sxs-lookup"><span data-stu-id="454d4-104">Some of the methods are a part of the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] language, and others are inherent in the `String` class.</span></span>  
  
## <a name="visual-basic-language-and-the-net-framework"></a><span data-ttu-id="454d4-105">Visual Basic 言語と .NET Framework</span><span class="sxs-lookup"><span data-stu-id="454d4-105">Visual Basic Language and the .NET Framework</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="454d4-106">メソッドは、言語固有の関数として使用されます。</span><span class="sxs-lookup"><span data-stu-id="454d4-106"> methods are used as inherent functions of the language.</span></span> <span data-ttu-id="454d4-107">これらは、コードで修飾しないで使用できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="454d4-107">They may be used without qualification in your code.</span></span> <span data-ttu-id="454d4-108">次の例の一般的な使用方法を示しています、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]文字列操作コマンド。</span><span class="sxs-lookup"><span data-stu-id="454d4-108">The following example shows typical use of a [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] string-manipulation command:</span></span>  
  
 <span data-ttu-id="454d4-109">[!code-vb[VbVbalrStrings #&44;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="454d4-109">[!code-vb[VbVbalrStrings#44](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]</span></span>  
  
 <span data-ttu-id="454d4-110">この例では、`Mid`関数に対して直接操作を実行する`aString`に値を代入し、`bString`します。</span><span class="sxs-lookup"><span data-stu-id="454d4-110">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span></span>  
  
 <span data-ttu-id="454d4-111">Visual Basic の文字列操作メソッドの一覧は、次を参照してください。[文字列操作の概要](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)します。</span><span class="sxs-lookup"><span data-stu-id="454d4-111">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span></span>  
  
### <a name="shared-methods-and-instance-methods"></a><span data-ttu-id="454d4-112">共有メソッドとインスタンス メソッド</span><span class="sxs-lookup"><span data-stu-id="454d4-112">Shared Methods and Instance Methods</span></span>  
 <span data-ttu-id="454d4-113">メソッドを使って文字列を操作することも、`String`クラスです。</span><span class="sxs-lookup"><span data-stu-id="454d4-113">You can also manipulate strings with the methods of the `String` class.</span></span> <span data-ttu-id="454d4-114">におけるメソッドの&2; つの種類がある`String`:*共有*メソッドと*インスタンス*メソッドです。</span><span class="sxs-lookup"><span data-stu-id="454d4-114">There are two types of methods in `String`: *shared* methods and *instance* methods.</span></span>  
  
#### <a name="shared-methods"></a><span data-ttu-id="454d4-115">共有メソッド</span><span class="sxs-lookup"><span data-stu-id="454d4-115">Shared Methods</span></span>  
 <span data-ttu-id="454d4-116">共有メソッドに由来するメソッド、`String`クラス自身と動作するには、そのクラスのインスタンスは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="454d4-116">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span></span> <span data-ttu-id="454d4-117">これらのメソッドは、クラスの名前で修飾することができます (`String`) のインスタンスではなく、`String`クラスです。</span><span class="sxs-lookup"><span data-stu-id="454d4-117">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span></span> <span data-ttu-id="454d4-118">例:</span><span class="sxs-lookup"><span data-stu-id="454d4-118">For example:</span></span>  
  
 <span data-ttu-id="454d4-119">[!code-vb[VbVbalrStrings #&45;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="454d4-119">[!code-vb[VbVbalrStrings#45](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]</span></span>  
  
 <span data-ttu-id="454d4-120">上記の例では、<xref:System.String.Copy%2A?displayProperty=fullName>メソッドが静的メソッドで、式に対して機能することが指定されに結果として得られる値を代入`bString`</xref:System.String.Copy%2A?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="454d4-120">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=fullName> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span></span>  
  
#### <a name="instance-methods"></a><span data-ttu-id="454d4-121">インスタンス メソッド</span><span class="sxs-lookup"><span data-stu-id="454d4-121">Instance Methods</span></span>  
 <span data-ttu-id="454d4-122">特定のインスタンスのインスタンス メソッドがこれに対し、原因`String`インスタンス名で修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="454d4-122">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span></span> <span data-ttu-id="454d4-123">例:</span><span class="sxs-lookup"><span data-stu-id="454d4-123">For example:</span></span>  
  
 <span data-ttu-id="454d4-124">[!code-vb[VbVbalrStrings&#46;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="454d4-124">[!code-vb[VbVbalrStrings#46](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]</span></span>  
  
 <span data-ttu-id="454d4-125">この例では、<xref:System.String.Substring%2A?displayProperty=fullName>メソッドは、メソッドのインスタンスの`String`(つまり、 `aString`).</xref:System.String.Substring%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="454d4-125">In this example, the <xref:System.String.Substring%2A?displayProperty=fullName> method is a method of the instance of `String` (that is, `aString`).</span></span> <span data-ttu-id="454d4-126">操作を実行`aString`にその値を代入し、`bString`します。</span><span class="sxs-lookup"><span data-stu-id="454d4-126">It performs an operation on `aString` and assigns that value to `bString`.</span></span>  
  
 <span data-ttu-id="454d4-127">詳細については、<xref:System.String>クラス</xref:System.String>のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="454d4-127">For more information, see the documentation for the <xref:System.String> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="454d4-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="454d4-128">See Also</span></span>  
 [<span data-ttu-id="454d4-129">Visual Basic における文字列の概要</span><span class="sxs-lookup"><span data-stu-id="454d4-129">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)

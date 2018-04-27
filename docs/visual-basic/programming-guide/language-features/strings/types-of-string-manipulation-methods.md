---
title: Visual Basic における文字列操作メソッドの種類
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3677c8a23e956716af4357fe79041fc96f4014f2
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a><span data-ttu-id="8a91c-102">Visual Basic における文字列操作メソッドの種類</span><span class="sxs-lookup"><span data-stu-id="8a91c-102">Types of String Manipulation Methods in Visual Basic</span></span>
<span data-ttu-id="8a91c-103">いくつかの方法を分析し、文字列の操作があります。</span><span class="sxs-lookup"><span data-stu-id="8a91c-103">There are several different ways to analyze and manipulate your strings.</span></span> <span data-ttu-id="8a91c-104">Visual Basic 言語の一部である一部のメソッドと他の人は気にせずに、`String`クラスです。</span><span class="sxs-lookup"><span data-stu-id="8a91c-104">Some of the methods are a part of the Visual Basic language, and others are inherent in the `String` class.</span></span>  
  
## <a name="visual-basic-language-and-the-net-framework"></a><span data-ttu-id="8a91c-105">Visual Basic 言語と .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8a91c-105">Visual Basic Language and the .NET Framework</span></span>  
 <span data-ttu-id="8a91c-106">Visual Basic のメソッドは、言語固有の関数として使用されます。</span><span class="sxs-lookup"><span data-stu-id="8a91c-106">Visual Basic methods are used as inherent functions of the language.</span></span> <span data-ttu-id="8a91c-107">これらは、コードで修飾しないで使用できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8a91c-107">They may be used without qualification in your code.</span></span> <span data-ttu-id="8a91c-108">次の例は、Visual Basic の文字列操作コマンドの一般的な使用を示しています。</span><span class="sxs-lookup"><span data-stu-id="8a91c-108">The following example shows typical use of a Visual Basic string-manipulation command:</span></span>  
  
 [!code-vb[VbVbalrStrings#44](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]  
  
 <span data-ttu-id="8a91c-109">この例では、`Mid`関数を直接操作を実行する`aString`に値を代入し、`bString`です。</span><span class="sxs-lookup"><span data-stu-id="8a91c-109">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span></span>  
  
 <span data-ttu-id="8a91c-110">Visual Basic の文字列操作メソッドの一覧は、次を参照してください。[文字列操作の概要](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)です。</span><span class="sxs-lookup"><span data-stu-id="8a91c-110">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span></span>  
  
### <a name="shared-methods-and-instance-methods"></a><span data-ttu-id="8a91c-111">共有メソッドとインスタンス メソッド</span><span class="sxs-lookup"><span data-stu-id="8a91c-111">Shared Methods and Instance Methods</span></span>  
 <span data-ttu-id="8a91c-112">メソッドを使って文字列を操作することも、`String`クラスです。</span><span class="sxs-lookup"><span data-stu-id="8a91c-112">You can also manipulate strings with the methods of the `String` class.</span></span> <span data-ttu-id="8a91c-113">内のメソッドの 2 種類があります`String`:*共有*メソッドおよび*インスタンス*メソッドです。</span><span class="sxs-lookup"><span data-stu-id="8a91c-113">There are two types of methods in `String`: *shared* methods and *instance* methods.</span></span>  
  
#### <a name="shared-methods"></a><span data-ttu-id="8a91c-114">共有メソッド</span><span class="sxs-lookup"><span data-stu-id="8a91c-114">Shared Methods</span></span>  
 <span data-ttu-id="8a91c-115">共有メソッドに由来するメソッド、`String`クラス自体および操作するには、そのクラスのインスタンスは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="8a91c-115">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span></span> <span data-ttu-id="8a91c-116">これらのメソッドは、クラスの名前で修飾することができます (`String`) のインスタンスではなく、`String`クラスです。</span><span class="sxs-lookup"><span data-stu-id="8a91c-116">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span></span> <span data-ttu-id="8a91c-117">例えば:</span><span class="sxs-lookup"><span data-stu-id="8a91c-117">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#45](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]  
  
 <span data-ttu-id="8a91c-118">前の例で、<xref:System.String.Copy%2A?displayProperty=nameWithType>メソッドは、静的メソッドを式に対して機能することが指定され、結果の値を割り当てます`bString`です。</span><span class="sxs-lookup"><span data-stu-id="8a91c-118">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=nameWithType> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span></span>  
  
#### <a name="instance-methods"></a><span data-ttu-id="8a91c-119">インスタンス メソッド</span><span class="sxs-lookup"><span data-stu-id="8a91c-119">Instance Methods</span></span>  
 <span data-ttu-id="8a91c-120">インスタンス メソッド、これに対し、によって生じる特定のインスタンスの`String`インスタンス名で修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a91c-120">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span></span> <span data-ttu-id="8a91c-121">例えば:</span><span class="sxs-lookup"><span data-stu-id="8a91c-121">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#46](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]  
  
 <span data-ttu-id="8a91c-122">この例では、<xref:System.String.Substring%2A?displayProperty=nameWithType>メソッドは、メソッドのインスタンスの`String`(つまり、 `aString`)。</span><span class="sxs-lookup"><span data-stu-id="8a91c-122">In this example, the <xref:System.String.Substring%2A?displayProperty=nameWithType> method is a method of the instance of `String` (that is, `aString`).</span></span> <span data-ttu-id="8a91c-123">操作を実行`aString`し、その値を割り当てます`bString`です。</span><span class="sxs-lookup"><span data-stu-id="8a91c-123">It performs an operation on `aString` and assigns that value to `bString`.</span></span>  
  
 <span data-ttu-id="8a91c-124">詳細については、ドキュメントを参照して、<xref:System.String>クラスです。</span><span class="sxs-lookup"><span data-stu-id="8a91c-124">For more information, see the documentation for the <xref:System.String> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a91c-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a91c-125">See Also</span></span>  
 [<span data-ttu-id="8a91c-126">Visual Basic の文字列の概要</span><span class="sxs-lookup"><span data-stu-id="8a91c-126">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)

---
title: 文字データ型 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: afd368c00444f136c6d69b02a733c82f0c8eafe0
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="2e0bb-102">文字データ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e0bb-102">Character Data Types (Visual Basic)</span></span>
<span data-ttu-id="2e0bb-103">Visual Basic では*文字データ型*文字や表示可能な文字を処理します。</span><span class="sxs-lookup"><span data-stu-id="2e0bb-103">Visual Basic provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="2e0bb-104">Unicode 文字を扱う両者間`Char`一方、1 つの文字を保持している`String`不特定数文字にはが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2e0bb-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="2e0bb-105">Visual Basic データ型のサイド バイ サイドの比較を表示するテーブル、次を参照してください。[データ型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)です。</span><span class="sxs-lookup"><span data-stu-id="2e0bb-105">For a table that displays a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="2e0bb-106">Char 型</span><span class="sxs-lookup"><span data-stu-id="2e0bb-106">Char Type</span></span>  
 <span data-ttu-id="2e0bb-107">`Char`データ型は単一 2 バイト (16 ビット) の Unicode 文字。</span><span class="sxs-lookup"><span data-stu-id="2e0bb-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="2e0bb-108">変数は、常に正確に 1 つの文字を保存する場合として宣言`Char`です。</span><span class="sxs-lookup"><span data-stu-id="2e0bb-108">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="2e0bb-109">例えば:</span><span class="sxs-lookup"><span data-stu-id="2e0bb-109">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 <span data-ttu-id="2e0bb-110">使用可能な各値、`Char`または`String`変数は、*コード ポイントが*、または Unicode 文字セット内の文字コード。</span><span class="sxs-lookup"><span data-stu-id="2e0bb-110">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="2e0bb-111">Unicode 文字には、基本的な ASCII 文字セット、さまざまな他のアルファベット文字、アクセント記号、通貨記号、分数、分音文字、および数学と技術的な記号が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2e0bb-111">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2e0bb-112">Unicode 文字セットは、コード ポイント D800 ~ DFFF (55551 を通じて 55296) の*サロゲート ペア*、1 つのコード ポイントを表す 2 つの 16 ビット値を必要とします。</span><span class="sxs-lookup"><span data-stu-id="2e0bb-112">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="2e0bb-113">A`Char`変数は、サロゲート ペアを保持できないと`String`2 つの位置を使用してこのようなペアを保持します。</span><span class="sxs-lookup"><span data-stu-id="2e0bb-113">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="2e0bb-114">詳細については、次を参照してください。 [Char データ型](../../../../visual-basic/language-reference/data-types/char-data-type.md)です。</span><span class="sxs-lookup"><span data-stu-id="2e0bb-114">For more information, see [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="2e0bb-115">文字列型</span><span class="sxs-lookup"><span data-stu-id="2e0bb-115">String Type</span></span>  
 <span data-ttu-id="2e0bb-116">`String`データ型は、0 個以上 2 バイト (16 ビット) の Unicode 文字のシーケンス。</span><span class="sxs-lookup"><span data-stu-id="2e0bb-116">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="2e0bb-117">場合は、変数は、不特定数の文字を含めることができます、宣言として`String`です。</span><span class="sxs-lookup"><span data-stu-id="2e0bb-117">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="2e0bb-118">例えば:</span><span class="sxs-lookup"><span data-stu-id="2e0bb-118">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 <span data-ttu-id="2e0bb-119">詳細については、次を参照してください。[文字列データ型](../../../../visual-basic/language-reference/data-types/string-data-type.md)です。</span><span class="sxs-lookup"><span data-stu-id="2e0bb-119">For more information, see [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e0bb-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="2e0bb-120">See Also</span></span>  
 [<span data-ttu-id="2e0bb-121">基本データ型</span><span class="sxs-lookup"><span data-stu-id="2e0bb-121">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="2e0bb-122">複合データ型</span><span class="sxs-lookup"><span data-stu-id="2e0bb-122">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="2e0bb-123">Visual Basic におけるジェネリック型</span><span class="sxs-lookup"><span data-stu-id="2e0bb-123">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="2e0bb-124">値型と参照型</span><span class="sxs-lookup"><span data-stu-id="2e0bb-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="2e0bb-125">Visual Basic での型変換</span><span class="sxs-lookup"><span data-stu-id="2e0bb-125">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="2e0bb-126">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="2e0bb-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="2e0bb-127">型文字</span><span class="sxs-lookup"><span data-stu-id="2e0bb-127">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)

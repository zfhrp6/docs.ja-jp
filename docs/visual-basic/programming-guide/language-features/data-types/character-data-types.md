---
title: "文字データ型 (Visual Basic) |Microsoft ドキュメント"
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
- data types [Visual Basic], character
- String data type, character data types
- character data types [Visual Basic]
- Char data type, character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
caps.latest.revision: 23
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
ms.openlocfilehash: 3407f614d5898f4fccf04e0363ec31669661b60a
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="ef218-102">文字データ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef218-102">Character Data Types (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="ef218-103">提供*文字データ型*文字や表示可能な文字を処理します。</span><span class="sxs-lookup"><span data-stu-id="ef218-103"> provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="ef218-104">Unicode 文字を扱う、どちらも、`Char`が単一の文字を保持して`String`不特定数文字にはが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ef218-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="ef218-105">サイド バイ サイドの比較を表示するテーブルの[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]データ型を参照してください[データ型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)します。</span><span class="sxs-lookup"><span data-stu-id="ef218-105">For a table that displays a side-by-side comparison of the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types, see [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="ef218-106">Char 型</span><span class="sxs-lookup"><span data-stu-id="ef218-106">Char Type</span></span>  
 <span data-ttu-id="ef218-107">`Char`データ型は、1 つの&2; バイト (16 ビット) Unicode 文字。</span><span class="sxs-lookup"><span data-stu-id="ef218-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="ef218-108">変数は、常に正確に&1; つの文字を保存する場合のように宣言`Char`します。</span><span class="sxs-lookup"><span data-stu-id="ef218-108">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="ef218-109">例:</span><span class="sxs-lookup"><span data-stu-id="ef218-109">For example:</span></span>  
  
 <span data-ttu-id="ef218-110">[!code-vb[VbVbalrCharTypes&#1;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ef218-110">[!code-vb[VbVbalrCharTypes#1](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_1.vb)]</span></span>  
  
 <span data-ttu-id="ef218-111">使用可能な各値、`Char`または`String`変数は、*コード ポイントが*、または Unicode 文字セット内の文字コード。</span><span class="sxs-lookup"><span data-stu-id="ef218-111">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="ef218-112">Unicode 文字には、基本的な ASCII 文字セット、さまざまなその他のアルファベット文字、アクセント記号、通貨記号、分数、分音文字、および数学と技術的な記号が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ef218-112">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef218-113">Unicode 文字セットは、コード ポイント D800 ~ DFFF (55551 を通じて 55296) の*サロゲート ペア*、2 つの 16 ビット値が 1 つのコード ポイントを表す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef218-113">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="ef218-114">A`Char`変数は、サロゲート ペアを保持できません、`String`は、2 つの位置を使用して、そのような組み合わせを保持します。</span><span class="sxs-lookup"><span data-stu-id="ef218-114">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="ef218-115">詳細については、次を参照してください。 [Char データ型](../../../../visual-basic/language-reference/data-types/char-data-type.md)します。</span><span class="sxs-lookup"><span data-stu-id="ef218-115">For more information, see [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="ef218-116">文字列型</span><span class="sxs-lookup"><span data-stu-id="ef218-116">String Type</span></span>  
 <span data-ttu-id="ef218-117">`String`データ型は、0 個以上の&2; バイト (16 ビット) の Unicode 文字のシーケンス。</span><span class="sxs-lookup"><span data-stu-id="ef218-117">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="ef218-118">変数が、不特定数の文字を含んでいる可能性がある場合として宣言`String`します。</span><span class="sxs-lookup"><span data-stu-id="ef218-118">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="ef218-119">例:</span><span class="sxs-lookup"><span data-stu-id="ef218-119">For example:</span></span>  
  
 <span data-ttu-id="ef218-120">[!code-vb[VbVbalrCharTypes&#2;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="ef218-120">[!code-vb[VbVbalrCharTypes#2](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_2.vb)]</span></span>  
  
 <span data-ttu-id="ef218-121">詳細については、次を参照してください。[文字列データ型](../../../../visual-basic/language-reference/data-types/string-data-type.md)します。</span><span class="sxs-lookup"><span data-stu-id="ef218-121">For more information, see [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef218-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="ef218-122">See Also</span></span>  
 <span data-ttu-id="ef218-123">[基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="ef218-123">[Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span></span>  
<span data-ttu-id="ef218-124"> [複合データ型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="ef218-124"> [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) </span></span>  
<span data-ttu-id="ef218-125"> [Visual Basic におけるジェネリック型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span><span class="sxs-lookup"><span data-stu-id="ef218-125"> [Generic Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span></span>  
<span data-ttu-id="ef218-126"> [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="ef218-126"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
<span data-ttu-id="ef218-127"> [Visual Basic における型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="ef218-127"> [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="ef218-128"> [データ型のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="ef218-128"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="ef218-129"> [型文字](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)</span><span class="sxs-lookup"><span data-stu-id="ef218-129"> [Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)</span></span>

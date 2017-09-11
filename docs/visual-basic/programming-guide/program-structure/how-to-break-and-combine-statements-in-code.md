---
title: "方法: 分割およびコード (Visual Basic) 内のステートメントを連結する |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb._
dev_langs:
- VB
helpviewer_keywords:
- colons (:)
- line continuation
- _ line-continuation character
- ': line separator character'
- Visual Basic code, line breaks in
- Visual Basic code, line breaks
- Visual Basic code, line continuation
- long lines of code
- line terminator
- line-continuation sequence
- underscores, in code
- statements [Visual Basic], line continuation in
- line breaks, in code
- line-continuation character
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2ca281035a0bd81a9b52cdd60f2bc59724852709
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a><span data-ttu-id="9b7e0-102">方法: コード内でステートメントを分割および連結する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b7e0-102">How to: Break and Combine Statements in Code (Visual Basic)</span></span>
<span data-ttu-id="9b7e0-103">コードを記述する場合は、コード エディターでを水平方向にスクロールを必要とするステートメントが長くなりも作成できます。</span><span class="sxs-lookup"><span data-stu-id="9b7e0-103">When writing your code, you might at times create lengthy statements that necessitate horizontal scrolling in the Code Editor.</span></span> <span data-ttu-id="9b7e0-104">方法は、これには影響しませんが、コードを実行、困難の作成者やその他のユーザーをモニターされているとおり、コードを読み取る。</span><span class="sxs-lookup"><span data-stu-id="9b7e0-104">Although this doesn't affect the way your code runs, it makes it difficult for you or anyone else to read the code as it appears on the monitor.</span></span> <span data-ttu-id="9b7e0-105">このような場合は、単一の長いステートメントを複数の行に分割を検討してください。</span><span class="sxs-lookup"><span data-stu-id="9b7e0-105">In such cases, you should consider breaking the single long statement into several lines.</span></span>  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a><span data-ttu-id="9b7e0-106">複数の行に単一のステートメントを分割するには</span><span class="sxs-lookup"><span data-stu-id="9b7e0-106">To break a single statement into multiple lines</span></span>  
  
-   <span data-ttu-id="9b7e0-107">アンダー スコアは、行連結文字を使用 (`_`)、行を分割する時点。</span><span class="sxs-lookup"><span data-stu-id="9b7e0-107">Use the line-continuation character, which is an underscore (`_`), at the point at which you want the line to break.</span></span> <span data-ttu-id="9b7e0-108">アンダースコアは、スペースの直後、および行終端記号 (キャリッジ リターン) の直前に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b7e0-108">The underscore must be immediately preceded by a space and immediately followed by a line terminator (carriage return).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9b7e0-109">場合によっては、行連結文字を省略した場合、Visual Basic コンパイラに暗黙的には引き続きステートメント次のコード行にします。</span><span class="sxs-lookup"><span data-stu-id="9b7e0-109">In some cases, if you omit the line-continuation character, the Visual Basic compiler will implicitly continue the statement on the next line of code.</span></span> <span data-ttu-id="9b7e0-110">行連結文字を省略できます構文要素については、「暗黙的な行継続」を参照してください[ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)します。</span><span class="sxs-lookup"><span data-stu-id="9b7e0-110">For a list of syntax elements for which you can omit the line-continuation character, see "Implicit Line Continuation" in [Statements](../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
     <span data-ttu-id="9b7e0-111">次の例では、ステートメントは末尾行連結文字の&4; つの行が最後の行に分割されます。</span><span class="sxs-lookup"><span data-stu-id="9b7e0-111">In the following example, the statement is broken into four lines with line-continuation characters terminating all but the last line.</span></span>  
  
     <span data-ttu-id="9b7e0-112">[!code-vb[VbVbcnConventions&#20;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="9b7e0-112">[!code-vb[VbVbcnConventions#20](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_1.vb)]</span></span>  
  
     <span data-ttu-id="9b7e0-113">このシーケンスを使用して、コード読みやすく、オンラインとタイミングを印刷します。</span><span class="sxs-lookup"><span data-stu-id="9b7e0-113">Using this sequence makes your code easier to read, both online and when printed.</span></span>  
  
     <span data-ttu-id="9b7e0-114">行連結文字は、行の最後の文字である必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b7e0-114">The line-continuation character must be the last character on a line.</span></span> <span data-ttu-id="9b7e0-115">アイテムと同じ行に、それをフォローできません。</span><span class="sxs-lookup"><span data-stu-id="9b7e0-115">You can't follow it with anything else on the same line.</span></span>  
  
     <span data-ttu-id="9b7e0-116">行連結文字を使用するに関していくつかの制限があります。たとえば、引数の名前の途中では使用できません。</span><span class="sxs-lookup"><span data-stu-id="9b7e0-116">Some limitations exist as to where you can use the line-continuation character; for example, you can't use it in the middle of an argument name.</span></span> <span data-ttu-id="9b7e0-117">行連結文字で、引数リストを分割することができますが、個々 の引数の名前が残す必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b7e0-117">You can break an argument list with the line-continuation character, but the individual names of the arguments must remain intact.</span></span>  
  
     <span data-ttu-id="9b7e0-118">行連結文字を使用して、コメントを続行できません。</span><span class="sxs-lookup"><span data-stu-id="9b7e0-118">You can't continue a comment by using a line-continuation character.</span></span> <span data-ttu-id="9b7e0-119">コンパイラは、特別な意味のコメント内の文字を調べるしません。</span><span class="sxs-lookup"><span data-stu-id="9b7e0-119">The compiler doesn't examine the characters in a comment for special meaning.</span></span> <span data-ttu-id="9b7e0-120">複数行にコメントを記述する場合は、コメント記号を繰り返します (`'`)&1; 行にします。</span><span class="sxs-lookup"><span data-stu-id="9b7e0-120">For a multiple-line comment, repeat the comment symbol (`'`) on each line.</span></span>  
  
 <span data-ttu-id="9b7e0-121">推奨される方法は、別々 の行に各ステートメントを配置することが[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]同じ行に複数のステートメントを配置することもできます。</span><span class="sxs-lookup"><span data-stu-id="9b7e0-121">Although placing each statement on a separate line is the recommended method, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] also allows you to place multiple statements on the same line.</span></span>  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a><span data-ttu-id="9b7e0-122">同じ行に複数のステートメントを配置するには</span><span class="sxs-lookup"><span data-stu-id="9b7e0-122">To place multiple statements on the same line</span></span>  
  
-   <span data-ttu-id="9b7e0-123">ステートメントをコロンで区切ります (`:`)、次の例のようにします。</span><span class="sxs-lookup"><span data-stu-id="9b7e0-123">Separate the statements with a colon (`:`), as in the following example.</span></span>  
  
     <span data-ttu-id="9b7e0-124">[!code-vb[VbVbcnConventions&#10;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="9b7e0-124">[!code-vb[VbVbcnConventions#10](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b7e0-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b7e0-125">See Also</span></span>  
 <span data-ttu-id="9b7e0-126">[プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="9b7e0-126">[Program Structure and Code Conventions](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span></span>  
<span data-ttu-id="9b7e0-127"> [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)</span><span class="sxs-lookup"><span data-stu-id="9b7e0-127"> [Statements](../../../visual-basic/programming-guide/language-features/statements.md)</span></span>

---
title: '方法: コード内でステートメントを分割および連結する (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb._
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
- underscores [Visual Basic], in code
- statements [Visual Basic], line continuation in
- line breaks [Visual Basic], in code
- line-continuation character [Visual Basic]
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
ms.openlocfilehash: 6bca3d62cb3e886ee08b9169d63d4c3a38247f3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a><span data-ttu-id="9b31b-102">方法: コード内でステートメントを分割および連結する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b31b-102">How to: Break and Combine Statements in Code (Visual Basic)</span></span>
<span data-ttu-id="9b31b-103">コードを書くときにも必要になるは、水平方向にスクロール コード エディターでステートメントが長くなりを作成する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9b31b-103">When writing your code, you might at times create lengthy statements that necessitate horizontal scrolling in the Code Editor.</span></span> <span data-ttu-id="9b31b-104">方法は、これには影響しませんが、コードの実行、困難の作成者やその他のユーザーをモニターに表示されるようにコードを読み取る。</span><span class="sxs-lookup"><span data-stu-id="9b31b-104">Although this doesn't affect the way your code runs, it makes it difficult for you or anyone else to read the code as it appears on the monitor.</span></span> <span data-ttu-id="9b31b-105">このような場合は、単一の長いステートメントを複数の行に分割することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="9b31b-105">In such cases, you should consider breaking the single long statement into several lines.</span></span>  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a><span data-ttu-id="9b31b-106">複数の行に単一のステートメントを分割するには</span><span class="sxs-lookup"><span data-stu-id="9b31b-106">To break a single statement into multiple lines</span></span>  
  
-   <span data-ttu-id="9b31b-107">行連結文字、つまりアンダー スコアを使用して (`_`)、行を分割する時点。</span><span class="sxs-lookup"><span data-stu-id="9b31b-107">Use the line-continuation character, which is an underscore (`_`), at the point at which you want the line to break.</span></span> <span data-ttu-id="9b31b-108">アンダースコアは、スペースの直後、および行終端記号 (キャリッジ リターン) の直前に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b31b-108">The underscore must be immediately preceded by a space and immediately followed by a line terminator (carriage return).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9b31b-109">場合によっては、行連結文字を省略した場合、Visual Basic コンパイラは暗黙的に続行ステートメント コードの次の行にします。</span><span class="sxs-lookup"><span data-stu-id="9b31b-109">In some cases, if you omit the line-continuation character, the Visual Basic compiler will implicitly continue the statement on the next line of code.</span></span> <span data-ttu-id="9b31b-110">行連結文字を省略できる構文要素の一覧を参照してください「暗黙的な行の連結」[ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9b31b-110">For a list of syntax elements for which you can omit the line-continuation character, see "Implicit Line Continuation" in [Statements](../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
     <span data-ttu-id="9b31b-111">次の例では、ステートメントは行連結文字をすべて終了して 4 つの行が最後の行に分割されます。</span><span class="sxs-lookup"><span data-stu-id="9b31b-111">In the following example, the statement is broken into four lines with line-continuation characters terminating all but the last line.</span></span>  
  
     [!code-vb[VbVbcnConventions#20](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_1.vb)]  
  
     <span data-ttu-id="9b31b-112">このシーケンスを使用して、コードを見やすく、オンラインとときに出力されます。</span><span class="sxs-lookup"><span data-stu-id="9b31b-112">Using this sequence makes your code easier to read, both online and when printed.</span></span>  
  
     <span data-ttu-id="9b31b-113">行連結文字は、行の最後の文字である必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b31b-113">The line-continuation character must be the last character on a line.</span></span> <span data-ttu-id="9b31b-114">他の何らかの同じ行にたどってすることはできません。</span><span class="sxs-lookup"><span data-stu-id="9b31b-114">You can't follow it with anything else on the same line.</span></span>  
  
     <span data-ttu-id="9b31b-115">行連結文字を使用するに関していくつかの制限があります。たとえば、引数名の途中では使用できません。</span><span class="sxs-lookup"><span data-stu-id="9b31b-115">Some limitations exist as to where you can use the line-continuation character; for example, you can't use it in the middle of an argument name.</span></span> <span data-ttu-id="9b31b-116">行連結文字の引数リストを中断することができますが、個々 の引数の名前はそのまま保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b31b-116">You can break an argument list with the line-continuation character, but the individual names of the arguments must remain intact.</span></span>  
  
     <span data-ttu-id="9b31b-117">行連結文字を使用してコメントを続行することはできません。</span><span class="sxs-lookup"><span data-stu-id="9b31b-117">You can't continue a comment by using a line-continuation character.</span></span> <span data-ttu-id="9b31b-118">コンパイラには、特別な意味のコメント内の文字を確認しません。</span><span class="sxs-lookup"><span data-stu-id="9b31b-118">The compiler doesn't examine the characters in a comment for special meaning.</span></span> <span data-ttu-id="9b31b-119">複数行にコメントを記述する場合は、コメント記号を繰り返します (`'`) 行ごとにします。</span><span class="sxs-lookup"><span data-stu-id="9b31b-119">For a multiple-line comment, repeat the comment symbol (`'`) on each line.</span></span>  
  
 <span data-ttu-id="9b31b-120">行ごとに各ステートメントを配置することは推奨される方法が、Visual Basic することもできますが同じ直線上に複数のステートメントを配置します。</span><span class="sxs-lookup"><span data-stu-id="9b31b-120">Although placing each statement on a separate line is the recommended method, Visual Basic also allows you to place multiple statements on the same line.</span></span>  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a><span data-ttu-id="9b31b-121">同じ行に複数のステートメントを配置するには</span><span class="sxs-lookup"><span data-stu-id="9b31b-121">To place multiple statements on the same line</span></span>  
  
-   <span data-ttu-id="9b31b-122">ステートメントをコロンで区切ります (`:`)、次の例のようにします。</span><span class="sxs-lookup"><span data-stu-id="9b31b-122">Separate the statements with a colon (`:`), as in the following example.</span></span>  
  
     [!code-vb[VbVbcnConventions#10](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9b31b-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b31b-123">See Also</span></span>  
 [<span data-ttu-id="9b31b-124">プログラム構造とコード規則</span><span class="sxs-lookup"><span data-stu-id="9b31b-124">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="9b31b-125">ステートメント</span><span class="sxs-lookup"><span data-stu-id="9b31b-125">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)

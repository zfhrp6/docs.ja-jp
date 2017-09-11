---
title: "コード (Visual Basic) 内のコメント |Microsoft ドキュメント"
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
- Uncomment button
- REM statement
- comments, in code
- comments, Visual Basic code
- Comment button
- buttons, Uncomment
- buttons, Comment
- code comments, Visual Basic
- Visual Basic code, comments
- comments
- code comments
ms.assetid: 90136fba-22eb-49f9-ba81-63db629b4a47
caps.latest.revision: 17
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
ms.openlocfilehash: e872c9bb67835573aadcc1016f2c6a98d434201e
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="comments-in-code-visual-basic"></a><span data-ttu-id="42f40-102">コード内のコメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42f40-102">Comments in Code (Visual Basic)</span></span>
<span data-ttu-id="42f40-103">コード例にはコメント記号 (`'`) がしばしば見られます。</span><span class="sxs-lookup"><span data-stu-id="42f40-103">As you read the code examples, you often encounter the comment symbol (`'`).</span></span> <span data-ttu-id="42f40-104">この記号はように指示、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラ、それに続くテキストは無視する、または*コメント*します。</span><span class="sxs-lookup"><span data-stu-id="42f40-104">This symbol tells the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler to ignore the text following it, or the *comment*.</span></span> <span data-ttu-id="42f40-105">コメントは、コードを読むユーザーに役立つように追加される簡単な説明です。</span><span class="sxs-lookup"><span data-stu-id="42f40-105">Comments are brief explanatory notes added to code for the benefit of those reading it.</span></span>  
  
 <span data-ttu-id="42f40-106">プロシージャの先頭に、そのプロシージャの機能の特性 (何を実行するか) について説明する簡単なコメントを常に配置するのは、推奨されるプログラミング方法です。</span><span class="sxs-lookup"><span data-stu-id="42f40-106">It is good programming practice to begin all procedures with a brief comment describing the functional characteristics of the procedure (what it does).</span></span> <span data-ttu-id="42f40-107">コードを作成した本人にとっても、コードを調べる他人にとっても、この説明は役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="42f40-107">This is for your own benefit and the benefit of anyone else who examines the code.</span></span> <span data-ttu-id="42f40-108">実装の詳細 (プロシージャの実行手順) は、機能の特性を説明するコメントとは別に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="42f40-108">You should separate the implementation details (how the procedure does it) from comments that describe the functional characteristics.</span></span> <span data-ttu-id="42f40-109">実装の詳細を記述に入れる場合は、関数を更新するときにその説明も更新してください。</span><span class="sxs-lookup"><span data-stu-id="42f40-109">When you include implementation details in the description, remember to update them when you update the function.</span></span>  
  
 <span data-ttu-id="42f40-110">同じ行のステートメントの後にコメントを入れたり、1 行全体をコメントにしたりできます。</span><span class="sxs-lookup"><span data-stu-id="42f40-110">Comments can follow a statement on the same line, or occupy an entire line.</span></span> <span data-ttu-id="42f40-111">両方の例を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="42f40-111">Both are illustrated in the following code.</span></span>  
  
 <span data-ttu-id="42f40-112">[!code-vb[VbVbcnConventions&#16;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="42f40-112">[!code-vb[VbVbcnConventions#16](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_1.vb)]</span></span>  
  
 <span data-ttu-id="42f40-113">コメントを複数行に記述する必要がある場合は、以下に例を示すとおりに、各行にコメント記号を記述します。</span><span class="sxs-lookup"><span data-stu-id="42f40-113">If your comment requires more than one line, use the comment symbol on each line, as the following example illustrates.</span></span>  
  
 <span data-ttu-id="42f40-114">[!code-vb[VbVbcnConventions&17;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="42f40-114">[!code-vb[VbVbcnConventions#17](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_2.vb)]</span></span>  
  
## <a name="commenting-guidelines"></a><span data-ttu-id="42f40-115">コメントのガイドライン</span><span class="sxs-lookup"><span data-stu-id="42f40-115">Commenting Guidelines</span></span>  
 <span data-ttu-id="42f40-116">次の表は、どの種類のコメントをコードのセクションの前に配置できるかに関する一般的なガイドラインを示しています。</span><span class="sxs-lookup"><span data-stu-id="42f40-116">The following table provides general guidelines for what types of comments can precede a section of code.</span></span> <span data-ttu-id="42f40-117">これらは推奨であり、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ではコメントの追加に規則はありません。</span><span class="sxs-lookup"><span data-stu-id="42f40-117">These are suggestions; [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] does not enforce rules for adding comments.</span></span> <span data-ttu-id="42f40-118">コードの作成者自身およびコードを読む他のユーザーに最適な内容を記述してください。</span><span class="sxs-lookup"><span data-stu-id="42f40-118">Write what works best, both for you and for anyone else who reads your code.</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="42f40-119">コメント タイプ</span><span class="sxs-lookup"><span data-stu-id="42f40-119">Comment type</span></span>|<span data-ttu-id="42f40-120">コメントの説明</span><span class="sxs-lookup"><span data-stu-id="42f40-120">Comment description</span></span>|  
|<span data-ttu-id="42f40-121">目的</span><span class="sxs-lookup"><span data-stu-id="42f40-121">Purpose</span></span>|<span data-ttu-id="42f40-122">プロシージャが行う内容 (手順ではありません) を説明します。</span><span class="sxs-lookup"><span data-stu-id="42f40-122">Describes what the procedure does (not how it does it)</span></span>|  
|<span data-ttu-id="42f40-123">外部からの影響</span><span class="sxs-lookup"><span data-stu-id="42f40-123">Assumptions</span></span>|<span data-ttu-id="42f40-124">各外部変数、コントロール、開いているファイル、またはプロシージャからアクセスされるその他の要素の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="42f40-124">Lists each external variable, control, open file, or other element accessed by the procedure</span></span>|  
|<span data-ttu-id="42f40-125">効果</span><span class="sxs-lookup"><span data-stu-id="42f40-125">Effects</span></span>|<span data-ttu-id="42f40-126">影響を受ける外部変数、コントロール、またはファイル、およびその効果 (明白でない場合のみ) の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="42f40-126">Lists each affected external variable, control, or file, and the effect it has (only if it is not obvious)</span></span>|  
|<span data-ttu-id="42f40-127">受け取る値</span><span class="sxs-lookup"><span data-stu-id="42f40-127">Inputs</span></span>|<span data-ttu-id="42f40-128">引数の目的を指定します。</span><span class="sxs-lookup"><span data-stu-id="42f40-128">Specifies the purpose of the argument</span></span>|  
|<span data-ttu-id="42f40-129">戻り値</span><span class="sxs-lookup"><span data-stu-id="42f40-129">Returns</span></span>|<span data-ttu-id="42f40-130">プロシージャから返される値について説明します。</span><span class="sxs-lookup"><span data-stu-id="42f40-130">Explains the values returned by the procedure</span></span>|  
  
 <span data-ttu-id="42f40-131">次のことに留意してください。</span><span class="sxs-lookup"><span data-stu-id="42f40-131">Remember the following points:</span></span>  
  
-   <span data-ttu-id="42f40-132">重要な変数を宣言する場合は、宣言した変数の用途を説明するためのインライン コメントを必ず前に配置します。</span><span class="sxs-lookup"><span data-stu-id="42f40-132">Every important variable declaration should be preceded by a comment describing the use of the variable being declared.</span></span>  
  
-   <span data-ttu-id="42f40-133">コメントには複雑な実装の詳細だけを記述して済むように、変数、コントロール、およびプロシージャにはわかりやすい名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="42f40-133">Variables, controls, and procedures should be named clearly enough that commenting is needed only for complex implementation details.</span></span>  
  
-   <span data-ttu-id="42f40-134">同じ行の行連結シーケンスの後にコメントを付けることはできません。</span><span class="sxs-lookup"><span data-stu-id="42f40-134">Comments cannot follow a line-continuation sequence on the same line.</span></span>  
  
 <span data-ttu-id="42f40-135">追加したり、コードのブロックのコメント記号を削除するには、1 つまたは複数の行のコードを選択し、選択、**コメント**(![VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.gif "vaCommentButton")) と**コメントから外して**(![VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.gif "vaUncommentButton")) ボタンを**編集**ツールバーです。</span><span class="sxs-lookup"><span data-stu-id="42f40-135">You can add or remove comment symbols for a block of code by selecting one or more lines of code and choosing the **Comment** (![VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.gif "vaCommentButton")) and **Uncomment** (![VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.gif "vaUncommentButton")) buttons on the **Edit** toolbar.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42f40-136">テキストの前に `REM` キーワードを付けて、コードにコメントを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="42f40-136">You can also add comments to your code by preceding the text with the `REM` keyword.</span></span> <span data-ttu-id="42f40-137">ただし、`'`シンボルと**コメント**/**コメントから外して**ボタンは簡単に使用し、小さい領域とメモリを必要とします。</span><span class="sxs-lookup"><span data-stu-id="42f40-137">However, the `'` symbol and the **Comment**/**Uncomment** buttons are easier to use and require less space and memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42f40-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="42f40-138">See Also</span></span>  
 <span data-ttu-id="42f40-139">[XML コメントを使用してコードを文書化します。](http://msdn.microsoft.com/magazine/dd722812.aspx) </span><span class="sxs-lookup"><span data-stu-id="42f40-139">[Documenting Your Code With XML Comments](http://msdn.microsoft.com/magazine/dd722812.aspx) </span></span>  
<span data-ttu-id="42f40-140"> [方法: XML ドキュメントを作成](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md) </span><span class="sxs-lookup"><span data-stu-id="42f40-140"> [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md) </span></span>  
<span data-ttu-id="42f40-141"> [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) </span><span class="sxs-lookup"><span data-stu-id="42f40-141"> [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) </span></span>  
<span data-ttu-id="42f40-142"> [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="42f40-142"> [Program Structure and Code Conventions](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span></span>  
<span data-ttu-id="42f40-143"> [REM ステートメント](../../../visual-basic/language-reference/statements/rem-statement.md)</span><span class="sxs-lookup"><span data-stu-id="42f40-143"> [REM Statement](../../../visual-basic/language-reference/statements/rem-statement.md)</span></span>

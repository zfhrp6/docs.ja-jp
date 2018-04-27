---
title: コード内のコメント (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Uncomment button
- REM statement [Visual Basic]
- comments [Visual Basic], in code
- comments [Visual Basic], Visual Basic code
- Comment button
- buttons [Visual Basic], Uncomment
- buttons [Visual Basic], Comment
- code comments [Visual Basic], Visual Basic
- Visual Basic code, comments
- comments
- code comments
ms.assetid: 90136fba-22eb-49f9-ba81-63db629b4a47
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9cd3277ea61ac9b46d8d20028bd100811988f611
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="comments-in-code-visual-basic"></a><span data-ttu-id="6a6c5-102">コード内のコメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a6c5-102">Comments in Code (Visual Basic)</span></span>
<span data-ttu-id="6a6c5-103">コード例にはコメント記号 (`'`) がしばしば見られます。</span><span class="sxs-lookup"><span data-stu-id="6a6c5-103">As you read the code examples, you often encounter the comment symbol (`'`).</span></span> <span data-ttu-id="6a6c5-104">このシンボルをそれに続くテキストを無視する Visual Basic コンパイラに指示または*コメント*です。</span><span class="sxs-lookup"><span data-stu-id="6a6c5-104">This symbol tells the Visual Basic compiler to ignore the text following it, or the *comment*.</span></span> <span data-ttu-id="6a6c5-105">コメントは、コードを読むユーザーに役立つように追加される簡単な説明です。</span><span class="sxs-lookup"><span data-stu-id="6a6c5-105">Comments are brief explanatory notes added to code for the benefit of those reading it.</span></span>  
  
 <span data-ttu-id="6a6c5-106">プロシージャの先頭に、そのプロシージャの機能の特性 (何を実行するか) について説明する簡単なコメントを常に配置するのは、推奨されるプログラミング方法です。</span><span class="sxs-lookup"><span data-stu-id="6a6c5-106">It is good programming practice to begin all procedures with a brief comment describing the functional characteristics of the procedure (what it does).</span></span> <span data-ttu-id="6a6c5-107">コードを作成した本人にとっても、コードを調べる他人にとっても、この説明は役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="6a6c5-107">This is for your own benefit and the benefit of anyone else who examines the code.</span></span> <span data-ttu-id="6a6c5-108">実装の詳細 (プロシージャの実行手順) は、機能の特性を説明するコメントとは別に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a6c5-108">You should separate the implementation details (how the procedure does it) from comments that describe the functional characteristics.</span></span> <span data-ttu-id="6a6c5-109">実装の詳細を記述に入れる場合は、関数を更新するときにその説明も更新してください。</span><span class="sxs-lookup"><span data-stu-id="6a6c5-109">When you include implementation details in the description, remember to update them when you update the function.</span></span>  
  
 <span data-ttu-id="6a6c5-110">同じ行のステートメントの後にコメントを入れたり、1 行全体をコメントにしたりできます。</span><span class="sxs-lookup"><span data-stu-id="6a6c5-110">Comments can follow a statement on the same line, or occupy an entire line.</span></span> <span data-ttu-id="6a6c5-111">両方の例を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="6a6c5-111">Both are illustrated in the following code.</span></span>  
  
 [!code-vb[VbVbcnConventions#16](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_1.vb)]  
  
 <span data-ttu-id="6a6c5-112">コメントを複数行に記述する必要がある場合は、以下に例を示すとおりに、各行にコメント記号を記述します。</span><span class="sxs-lookup"><span data-stu-id="6a6c5-112">If your comment requires more than one line, use the comment symbol on each line, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbcnConventions#17](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_2.vb)]  
  
## <a name="commenting-guidelines"></a><span data-ttu-id="6a6c5-113">コメントのガイドライン</span><span class="sxs-lookup"><span data-stu-id="6a6c5-113">Commenting Guidelines</span></span>  
 <span data-ttu-id="6a6c5-114">次の表は、どの種類のコメントをコードのセクションの前に配置できるかに関する一般的なガイドラインを示しています。</span><span class="sxs-lookup"><span data-stu-id="6a6c5-114">The following table provides general guidelines for what types of comments can precede a section of code.</span></span> <span data-ttu-id="6a6c5-115">これらは推奨です。Visual Basic では、コメントを追加するための規則は適用されません。</span><span class="sxs-lookup"><span data-stu-id="6a6c5-115">These are suggestions; Visual Basic does not enforce rules for adding comments.</span></span> <span data-ttu-id="6a6c5-116">コードの作成者自身およびコードを読む他のユーザーに最適な内容を記述してください。</span><span class="sxs-lookup"><span data-stu-id="6a6c5-116">Write what works best, both for you and for anyone else who reads your code.</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="6a6c5-117">コメント タイプ</span><span class="sxs-lookup"><span data-stu-id="6a6c5-117">Comment type</span></span>|<span data-ttu-id="6a6c5-118">コメントの説明</span><span class="sxs-lookup"><span data-stu-id="6a6c5-118">Comment description</span></span>|  
|<span data-ttu-id="6a6c5-119">目的</span><span class="sxs-lookup"><span data-stu-id="6a6c5-119">Purpose</span></span>|<span data-ttu-id="6a6c5-120">プロシージャが行う内容 (手順ではありません) を説明します。</span><span class="sxs-lookup"><span data-stu-id="6a6c5-120">Describes what the procedure does (not how it does it)</span></span>|  
|<span data-ttu-id="6a6c5-121">外部からの影響</span><span class="sxs-lookup"><span data-stu-id="6a6c5-121">Assumptions</span></span>|<span data-ttu-id="6a6c5-122">各外部変数、コントロール、開いているファイル、またはプロシージャからアクセスされるその他の要素の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="6a6c5-122">Lists each external variable, control, open file, or other element accessed by the procedure</span></span>|  
|<span data-ttu-id="6a6c5-123">効果</span><span class="sxs-lookup"><span data-stu-id="6a6c5-123">Effects</span></span>|<span data-ttu-id="6a6c5-124">影響を受ける外部変数、コントロール、またはファイル、およびその効果 (明白でない場合のみ) の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="6a6c5-124">Lists each affected external variable, control, or file, and the effect it has (only if it is not obvious)</span></span>|  
|<span data-ttu-id="6a6c5-125">受け取る値</span><span class="sxs-lookup"><span data-stu-id="6a6c5-125">Inputs</span></span>|<span data-ttu-id="6a6c5-126">引数の目的を指定します。</span><span class="sxs-lookup"><span data-stu-id="6a6c5-126">Specifies the purpose of the argument</span></span>|  
|<span data-ttu-id="6a6c5-127">戻り値</span><span class="sxs-lookup"><span data-stu-id="6a6c5-127">Returns</span></span>|<span data-ttu-id="6a6c5-128">プロシージャから返される値について説明します。</span><span class="sxs-lookup"><span data-stu-id="6a6c5-128">Explains the values returned by the procedure</span></span>|  
  
 <span data-ttu-id="6a6c5-129">次のことに留意してください。</span><span class="sxs-lookup"><span data-stu-id="6a6c5-129">Remember the following points:</span></span>  
  
-   <span data-ttu-id="6a6c5-130">重要な変数を宣言する場合は、宣言した変数の用途を説明するためのインライン コメントを必ず前に配置します。</span><span class="sxs-lookup"><span data-stu-id="6a6c5-130">Every important variable declaration should be preceded by a comment describing the use of the variable being declared.</span></span>  
  
-   <span data-ttu-id="6a6c5-131">コメントには複雑な実装の詳細だけを記述して済むように、変数、コントロール、およびプロシージャにはわかりやすい名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="6a6c5-131">Variables, controls, and procedures should be named clearly enough that commenting is needed only for complex implementation details.</span></span>  
  
-   <span data-ttu-id="6a6c5-132">同じ行の行連結シーケンスの後にコメントを付けることはできません。</span><span class="sxs-lookup"><span data-stu-id="6a6c5-132">Comments cannot follow a line-continuation sequence on the same line.</span></span>  
  
 <span data-ttu-id="6a6c5-133">追加するか、コードのブロックのコメント記号を削除するには、1 つまたは複数の行のコードを選択し、選択、**コメント**(![VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.gif "vaCommentButton")) および**コメント解除**(![VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.gif "vaUncommentButton")) ボタンを**編集**ツールバー。</span><span class="sxs-lookup"><span data-stu-id="6a6c5-133">You can add or remove comment symbols for a block of code by selecting one or more lines of code and choosing the **Comment** (![VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.gif "vaCommentButton")) and **Uncomment** (![VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.gif "vaUncommentButton")) buttons on the **Edit** toolbar.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6a6c5-134">テキストの前に `REM` キーワードを付けて、コードにコメントを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="6a6c5-134">You can also add comments to your code by preceding the text with the `REM` keyword.</span></span> <span data-ttu-id="6a6c5-135">ただし、`'`シンボルと**コメント**/**コメント解除**ボタンは簡単に使用し、小さい領域とメモリを必要とします。</span><span class="sxs-lookup"><span data-stu-id="6a6c5-135">However, the `'` symbol and the **Comment**/**Uncomment** buttons are easier to use and require less space and memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a6c5-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="6a6c5-136">See Also</span></span>  
 [<span data-ttu-id="6a6c5-137">XML コメントに、コードの説明</span><span class="sxs-lookup"><span data-stu-id="6a6c5-137">Documenting Your Code With XML Comments</span></span>](http://msdn.microsoft.com/magazine/dd722812.aspx)  
 [<span data-ttu-id="6a6c5-138">方法: XML ドキュメントを作成する</span><span class="sxs-lookup"><span data-stu-id="6a6c5-138">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [<span data-ttu-id="6a6c5-139">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="6a6c5-139">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
 [<span data-ttu-id="6a6c5-140">プログラム構造とコード規則</span><span class="sxs-lookup"><span data-stu-id="6a6c5-140">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="6a6c5-141">REM ステートメント</span><span class="sxs-lookup"><span data-stu-id="6a6c5-141">REM Statement</span></span>](../../../visual-basic/language-reference/statements/rem-statement.md)

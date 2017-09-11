---
title: "エラーの種類 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors, Visual Basic
- run-time errors, types of errors
- syntax errors, Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
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
ms.openlocfilehash: 51cf5820e79ff9467357619d4f5b067bc4168bfb
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="error-types-visual-basic"></a><span data-ttu-id="e0940-102">エラーの種類 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0940-102">Error Types (Visual Basic)</span></span>
<span data-ttu-id="e0940-103">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]、エラー (とも呼ばれます*例外*) は&3; つのカテゴリに分類します。 構文エラー、実行時エラー、および論理エラーです。</span><span class="sxs-lookup"><span data-stu-id="e0940-103">In [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], errors (also called *exceptions*) fall into one of three categories: syntax errors, run-time errors, and logic errors.</span></span>  
  
## <a name="syntax-errors"></a><span data-ttu-id="e0940-104">構文エラー</span><span class="sxs-lookup"><span data-stu-id="e0940-104">Syntax Errors</span></span>  
 <span data-ttu-id="e0940-105">*構文エラー*はコードを記述するときに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e0940-105">*Syntax errors* are those that appear while you write code.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="e0940-106">入力して、コードを確認、**コード エディター**ウィンドウなど、word のスペルが間違ってまたは言語要素を正しく使用して、操作を誤った場合、アラートが生成されます。</span><span class="sxs-lookup"><span data-stu-id="e0940-106"> checks your code as you type it in the **Code Editor** window and alerts you if you make a mistake, such as misspelling a word or using a language element improperly.</span></span> <span data-ttu-id="e0940-107">構文エラーは、エラーの最も一般的な種類です。</span><span class="sxs-lookup"><span data-stu-id="e0940-107">Syntax errors are the most common type of errors.</span></span> <span data-ttu-id="e0940-108">簡単に修正できますコーディング環境で発生するとすぐにします。</span><span class="sxs-lookup"><span data-stu-id="e0940-108">You can fix them easily in the coding environment as soon as they occur.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e0940-109">`Option Explicit`ステートメントが構文エラーを回避する&1; つのことを意味します。</span><span class="sxs-lookup"><span data-stu-id="e0940-109">The `Option Explicit` statement is one means of avoiding syntax errors.</span></span> <span data-ttu-id="e0940-110">アプリケーションで使用するすべての変数を事前に宣言するように強制します。</span><span class="sxs-lookup"><span data-stu-id="e0940-110">It forces you to declare, in advance, all the variables to be used in the application.</span></span> <span data-ttu-id="e0940-111">したがって、コードでそれらの変数を使用している場合、入力ミスがすぐに検出され、修正することができます。</span><span class="sxs-lookup"><span data-stu-id="e0940-111">Therefore, when those variables are used in the code, any typographic errors are caught immediately and can be fixed.</span></span>  
  
## <a name="run-time-errors"></a><span data-ttu-id="e0940-112">実行時エラー</span><span class="sxs-lookup"><span data-stu-id="e0940-112">Run-Time Errors</span></span>  
 <span data-ttu-id="e0940-113">*実行時エラー*をコンパイルして、コードを実行するまでは表示されません。</span><span class="sxs-lookup"><span data-stu-id="e0940-113">*Run-time errors* are those that appear only after you compile and run your code.</span></span> <span data-ttu-id="e0940-114">これらには、構文エラーがないのに実行できない点で、正しいように表示されるコードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e0940-114">These involve code that may appear to be correct in that it has no syntax errors, but that will not execute.</span></span> <span data-ttu-id="e0940-115">たとえば、ファイルを開くコード行を正しく記述できます。</span><span class="sxs-lookup"><span data-stu-id="e0940-115">For example, you might correctly write a line of code to open a file.</span></span> <span data-ttu-id="e0940-116">ファイルが壊れている場合は、アプリケーションを実行できませんが、`Open`関数、およびその実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="e0940-116">But if the file is corrupted, the application cannot carry out the `Open` function, and it stops running.</span></span> <span data-ttu-id="e0940-117">問題のあるコードの書き直しを再コンパイルし、再実行することで、ほとんどの実行時エラーを修正できます。</span><span class="sxs-lookup"><span data-stu-id="e0940-117">You can fix most run-time errors by rewriting the faulty code, and then recompiling and rerunning it.</span></span>  
  
## <a name="logic-errors"></a><span data-ttu-id="e0940-118">論理エラー</span><span class="sxs-lookup"><span data-stu-id="e0940-118">Logic Errors</span></span>  
 <span data-ttu-id="e0940-119">*論理エラー*は、アプリケーションが使用すると表示されます。</span><span class="sxs-lookup"><span data-stu-id="e0940-119">*Logic errors* are those that appear once the application is in use.</span></span> <span data-ttu-id="e0940-120">ユーザー操作に応じてほとんどの多くの場合望ましくないか予期しない結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e0940-120">They are most often unwanted or unexpected results in response to user actions.</span></span> <span data-ttu-id="e0940-121">たとえば、入力の間違いキーまたはなどの外的要因があります、アプリケーションで予測されるパラメーター内での作業を停止するなったりします。</span><span class="sxs-lookup"><span data-stu-id="e0940-121">For example, a mistyped key or other outside influence might cause your application to stop working within expected parameters, or altogether.</span></span> <span data-ttu-id="e0940-122">論理エラーは、通常ではないため常に明確ではないを解決する最も困難な型です。</span><span class="sxs-lookup"><span data-stu-id="e0940-122">Logic errors are generally the hardest type to fix, since it is not always clear where they originate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0940-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="e0940-123">See Also</span></span>  
 <span data-ttu-id="e0940-124">[Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) </span><span class="sxs-lookup"><span data-stu-id="e0940-124">[Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) </span></span>  
<span data-ttu-id="e0940-125"> [デバッガーの基本事項](https://docs.microsoft.com/visualstudio/debugger/debugger-basics)</span><span class="sxs-lookup"><span data-stu-id="e0940-125"> [Debugger Basics](https://docs.microsoft.com/visualstudio/debugger/debugger-basics)</span></span>

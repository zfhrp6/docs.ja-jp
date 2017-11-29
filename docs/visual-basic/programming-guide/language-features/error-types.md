---
title: "エラーの種類 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors [Visual Basic], Visual Basic
- run-time errors [Visual Basic], types of errors
- syntax errors [Visual Basic], Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e01ed588d284a475a537a5fcf5ca506d25ca69f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="error-types-visual-basic"></a><span data-ttu-id="80c69-102">エラーの種類 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80c69-102">Error Types (Visual Basic)</span></span>
<span data-ttu-id="80c69-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]、エラー (とも呼ばれます*例外*) は 3 つのカテゴリに分類されます。 構文エラー、実行時エラー、および論理エラー。</span><span class="sxs-lookup"><span data-stu-id="80c69-103">In [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], errors (also called *exceptions*) fall into one of three categories: syntax errors, run-time errors, and logic errors.</span></span>  
  
## <a name="syntax-errors"></a><span data-ttu-id="80c69-104">構文エラー</span><span class="sxs-lookup"><span data-stu-id="80c69-104">Syntax Errors</span></span>  
 <span data-ttu-id="80c69-105">*構文エラー*コードを記述するときに表示されることです。</span><span class="sxs-lookup"><span data-stu-id="80c69-105">*Syntax errors* are those that appear while you write code.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="80c69-106">入力すると、コードを確認、**コード エディター**ウィンドウを間違えた、単語のスペルが間違ってなどの言語要素を使用して不適切な場合、アラートが生成されます。</span><span class="sxs-lookup"><span data-stu-id="80c69-106"> checks your code as you type it in the **Code Editor** window and alerts you if you make a mistake, such as misspelling a word or using a language element improperly.</span></span> <span data-ttu-id="80c69-107">構文エラーは、エラーの最も一般的な種類です。</span><span class="sxs-lookup"><span data-stu-id="80c69-107">Syntax errors are the most common type of errors.</span></span> <span data-ttu-id="80c69-108">簡単に修正できますコーディングの環境で発生するとすぐにします。</span><span class="sxs-lookup"><span data-stu-id="80c69-108">You can fix them easily in the coding environment as soon as they occur.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80c69-109">`Option Explicit`ステートメントは構文エラーを回避する 1 つのことを意味します。</span><span class="sxs-lookup"><span data-stu-id="80c69-109">The `Option Explicit` statement is one means of avoiding syntax errors.</span></span> <span data-ttu-id="80c69-110">アプリケーションで使用するすべての変数を事前に宣言するように強制します。</span><span class="sxs-lookup"><span data-stu-id="80c69-110">It forces you to declare, in advance, all the variables to be used in the application.</span></span> <span data-ttu-id="80c69-111">したがって、コードでそれらの変数を使用している場合、入力ミスはすぐに検出され、修正することができます。</span><span class="sxs-lookup"><span data-stu-id="80c69-111">Therefore, when those variables are used in the code, any typographic errors are caught immediately and can be fixed.</span></span>  
  
## <a name="run-time-errors"></a><span data-ttu-id="80c69-112">実行時エラー</span><span class="sxs-lookup"><span data-stu-id="80c69-112">Run-Time Errors</span></span>  
 <span data-ttu-id="80c69-113">*実行時エラー*コンパイルして、コードの実行後にのみ表示されることです。</span><span class="sxs-lookup"><span data-stu-id="80c69-113">*Run-time errors* are those that appear only after you compile and run your code.</span></span> <span data-ttu-id="80c69-114">これらには、構文エラーがないのに実行できない点で、正しいように表示されるコードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="80c69-114">These involve code that may appear to be correct in that it has no syntax errors, but that will not execute.</span></span> <span data-ttu-id="80c69-115">たとえば、ファイルを開くためのコードの行を正しく記述可能性があります。</span><span class="sxs-lookup"><span data-stu-id="80c69-115">For example, you might correctly write a line of code to open a file.</span></span> <span data-ttu-id="80c69-116">ファイルが破損している場合、アプリケーションを実行できませんが、`Open`関数、およびが実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="80c69-116">But if the file is corrupted, the application cannot carry out the `Open` function, and it stops running.</span></span> <span data-ttu-id="80c69-117">ほとんどの実行時エラーを修正するには、欠陥のあるコードの再書き換えを再コンパイルし、再実行することによってです。</span><span class="sxs-lookup"><span data-stu-id="80c69-117">You can fix most run-time errors by rewriting the faulty code, and then recompiling and rerunning it.</span></span>  
  
## <a name="logic-errors"></a><span data-ttu-id="80c69-118">論理エラー</span><span class="sxs-lookup"><span data-stu-id="80c69-118">Logic Errors</span></span>  
 <span data-ttu-id="80c69-119">*論理エラー*アプリケーションは使用中に表示されることです。</span><span class="sxs-lookup"><span data-stu-id="80c69-119">*Logic errors* are those that appear once the application is in use.</span></span> <span data-ttu-id="80c69-120">これらは、ユーザーの操作への応答でほとんどの多くの場合、不要なまたは予期しない結果です。</span><span class="sxs-lookup"><span data-stu-id="80c69-120">They are most often unwanted or unexpected results in response to user actions.</span></span> <span data-ttu-id="80c69-121">たとえば、入力の間違いキーまたはその他の外部の影響を与えることがあります、アプリケーションで必要なパラメーターは、内での作業を停止するなったりします。</span><span class="sxs-lookup"><span data-stu-id="80c69-121">For example, a mistyped key or other outside influence might cause your application to stop working within expected parameters, or altogether.</span></span> <span data-ttu-id="80c69-122">論理エラーは、通常、最も困難な型ではないため常に明確ではないを修正します。</span><span class="sxs-lookup"><span data-stu-id="80c69-122">Logic errors are generally the hardest type to fix, since it is not always clear where they originate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80c69-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="80c69-123">See Also</span></span>  
 [<span data-ttu-id="80c69-124">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="80c69-124">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="80c69-125">デバッガーの基本事項</span><span class="sxs-lookup"><span data-stu-id="80c69-125">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)

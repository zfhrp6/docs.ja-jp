---
title: "REM ステートメント (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d64ce970e3e74437f5e8c63c8a4d578900902192
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="34fa8-102">REM ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34fa8-102">REM Statement (Visual Basic)</span></span>
<span data-ttu-id="34fa8-103">プログラムのソース コードにコメントを記述するために使用します。</span><span class="sxs-lookup"><span data-stu-id="34fa8-103">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34fa8-104">構文</span><span class="sxs-lookup"><span data-stu-id="34fa8-104">Syntax</span></span>  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="34fa8-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="34fa8-105">Parts</span></span>  
 `comment`  
 <span data-ttu-id="34fa8-106">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="34fa8-106">Optional.</span></span> <span data-ttu-id="34fa8-107">含めるコメントのテキストです。</span><span class="sxs-lookup"><span data-stu-id="34fa8-107">The text of any comment you want to include.</span></span> <span data-ttu-id="34fa8-108">スペースは間で必要な`REM`キーワードと`comment`です。</span><span class="sxs-lookup"><span data-stu-id="34fa8-108">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34fa8-109">コメント</span><span class="sxs-lookup"><span data-stu-id="34fa8-109">Remarks</span></span>  
 <span data-ttu-id="34fa8-110">配置することができます、`REM`するか、行に単独でステートメントを使用すると別のステートメントを次の行に記述できます。</span><span class="sxs-lookup"><span data-stu-id="34fa8-110">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="34fa8-111">`REM`ステートメントは行の最後のステートメントである必要があります。</span><span class="sxs-lookup"><span data-stu-id="34fa8-111">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="34fa8-112">別のステートメントが続く場合、`REM`からそのステートメントをスペースで区切る必要があります。</span><span class="sxs-lookup"><span data-stu-id="34fa8-112">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="34fa8-113">単一引用符を使用することができます (`'`) の代わりに`REM`です。</span><span class="sxs-lookup"><span data-stu-id="34fa8-113">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="34fa8-114">これはコメントが同じ行の別のステートメントに依存してまたはを行に単独で上に存在するかどうかに当てはまります。</span><span class="sxs-lookup"><span data-stu-id="34fa8-114">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34fa8-115">続行することはできません、`REM`行連結シーケンスを使用してステートメント (`_`)。</span><span class="sxs-lookup"><span data-stu-id="34fa8-115">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="34fa8-116">コメントが開始されると、コンパイラは特別な意味の文字を検査しません。</span><span class="sxs-lookup"><span data-stu-id="34fa8-116">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="34fa8-117">複数行にコメントを記述する場合は、別の操作を使用して`REM`ステートメントまたはコメント記号 (`'`) 行ごとにします。</span><span class="sxs-lookup"><span data-stu-id="34fa8-117">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34fa8-118">例</span><span class="sxs-lookup"><span data-stu-id="34fa8-118">Example</span></span>  
 <span data-ttu-id="34fa8-119">次の例を示しています、`REM`ステートメントでは、プログラムにコメントを記述するために使用します。</span><span class="sxs-lookup"><span data-stu-id="34fa8-119">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="34fa8-120">単一引用符文字を使用する方法も示しています (`'`) の代わりに`REM`です。</span><span class="sxs-lookup"><span data-stu-id="34fa8-120">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 [!code-vb[VbVbalrStatements#6](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/rem-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="34fa8-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="34fa8-121">See Also</span></span>  
 [<span data-ttu-id="34fa8-122">コード内のコメント</span><span class="sxs-lookup"><span data-stu-id="34fa8-122">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 [<span data-ttu-id="34fa8-123">方法 : コード内でステートメントを分割および連結する</span><span class="sxs-lookup"><span data-stu-id="34fa8-123">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)

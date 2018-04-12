---
title: Continue ステートメント (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a47819600a6c1d58f09c2f8ed3443632e9dab68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="625fc-102">Continue ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="625fc-102">Continue Statement (Visual Basic)</span></span>
<span data-ttu-id="625fc-103">ループの次のイテレーションにすぐに制御を転送します。</span><span class="sxs-lookup"><span data-stu-id="625fc-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="625fc-104">構文</span><span class="sxs-lookup"><span data-stu-id="625fc-104">Syntax</span></span>  
  
```  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="625fc-105">コメント</span><span class="sxs-lookup"><span data-stu-id="625fc-105">Remarks</span></span>  
 <span data-ttu-id="625fc-106">転送できます内、 `Do`、 `For`、または`While`ループを使用して、ループの次の反復処理します。</span><span class="sxs-lookup"><span data-stu-id="625fc-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="625fc-107">すぐに転送するのにはループの条件のテストにパスを制御、`For`または`While`ステートメント、または、`Do`または`Loop`ステートメントを含む、`Until`または`While`句。</span><span class="sxs-lookup"><span data-stu-id="625fc-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="625fc-108">使用することができます`Continue`転送を許可するループ内の任意の場所でします。</span><span class="sxs-lookup"><span data-stu-id="625fc-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="625fc-109">同じで、制御の転送を許可する規則は、 [GoTo ステートメント](../../../visual-basic/language-reference/statements/goto-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="625fc-109">The rules allowing transfer of control are the same as with the [GoTo Statement](../../../visual-basic/language-reference/statements/goto-statement.md).</span></span>  
  
 <span data-ttu-id="625fc-110">たとえば、ループ処理が完全に含まれている場合、`Try`ブロック、`Catch`ブロック、または`Finally`ブロック、使用することができます`Continue`ループの外に転送します。</span><span class="sxs-lookup"><span data-stu-id="625fc-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="625fc-111">その一方の場合、`Try`しています.`End Try` 、ループ内に含まれる構造体では使用できません`Continue`out の制御を転送する、`Finally`ブロックして、転送に使用できるの`Try`または`Catch`ブロックするを完全に転送する場合にのみ、`Try`...`End Try`構造体。</span><span class="sxs-lookup"><span data-stu-id="625fc-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="625fc-112">たとえば、同じ型での入れ子になったループがあるかどうか、`Do`別内でループ`Do`ループ、`Continue Do`ステートメントでは、最も内側の次のイテレーションへスキップ`Do`それを含むループ。</span><span class="sxs-lookup"><span data-stu-id="625fc-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="625fc-113">使用することはできません`Continue`同じ種類の外側のループの次のイテレーションにスキップします。</span><span class="sxs-lookup"><span data-stu-id="625fc-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="625fc-114">たとえば、さまざまな種類の入れ子になったループがあるかどうか、`Do`内でループ、`For`ループにスキップできますいずれかのループの次のイテレーションを使用して`Continue Do`または`Continue For`です。</span><span class="sxs-lookup"><span data-stu-id="625fc-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="625fc-115">例</span><span class="sxs-lookup"><span data-stu-id="625fc-115">Example</span></span>  
 <span data-ttu-id="625fc-116">次のコード例では、`Continue While`除数がゼロの場合は、配列の次の列をスキップするステートメント。</span><span class="sxs-lookup"><span data-stu-id="625fc-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="625fc-117">`Continue While`内部にある、`For`ループします。</span><span class="sxs-lookup"><span data-stu-id="625fc-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="625fc-118">転送します。、`While col < lastcol`ステートメントでは、最も内側の次のイテレーションである`While`ループを含む、`For`ループします。</span><span class="sxs-lookup"><span data-stu-id="625fc-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/continue-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="625fc-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="625fc-119">See Also</span></span>  
 [<span data-ttu-id="625fc-120">Do...Loop ステートメント</span><span class="sxs-lookup"><span data-stu-id="625fc-120">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [<span data-ttu-id="625fc-121">For...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="625fc-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="625fc-122">While...End While ステートメント</span><span class="sxs-lookup"><span data-stu-id="625fc-122">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [<span data-ttu-id="625fc-123">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="625fc-123">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)

---
title: Throw ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Throw
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement [Visual Basic], about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement [Visual Basic], throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement [Visual Basic]
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
ms.openlocfilehash: cfa53b3585846da25711739fb7af4bde21746b29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602854"
---
# <a name="throw-statement-visual-basic"></a><span data-ttu-id="ae39a-102">Throw ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae39a-102">Throw Statement (Visual Basic)</span></span>
<span data-ttu-id="ae39a-103">プロシージャ内で例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="ae39a-103">Throws an exception within a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae39a-104">構文</span><span class="sxs-lookup"><span data-stu-id="ae39a-104">Syntax</span></span>  
  
```  
Throw [ expression ]  
```  
  
## <a name="part"></a><span data-ttu-id="ae39a-105">パーツ</span><span class="sxs-lookup"><span data-stu-id="ae39a-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="ae39a-106">スローする例外に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="ae39a-106">Provides information about the exception to be thrown.</span></span> <span data-ttu-id="ae39a-107">内に存在する場合はオプション、`Catch`ステートメントでは、それ以外の場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="ae39a-107">Optional when residing in a `Catch` statement, otherwise required.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae39a-108">コメント</span><span class="sxs-lookup"><span data-stu-id="ae39a-108">Remarks</span></span>  
 <span data-ttu-id="ae39a-109">`Throw`構造化例外処理コードで処理できる例外をスローするステートメント (`Try`.`Catch`...`Finally`) または非構造化例外処理コード (`On Error GoTo`)。</span><span class="sxs-lookup"><span data-stu-id="ae39a-109">The `Throw` statement throws an exception that you can handle with structured exception-handling code (`Try`...`Catch`...`Finally`) or unstructured exception-handling code (`On Error GoTo`).</span></span> <span data-ttu-id="ae39a-110">使用することができます、 `Throw` Visual Basic は、適切な例外処理コードが見つかるまで、呼び出し履歴を移動するために、コード内でエラーをトラップするステートメント。</span><span class="sxs-lookup"><span data-stu-id="ae39a-110">You can use the `Throw` statement to trap errors within your code because Visual Basic moves up the call stack until it finds the appropriate exception-handling code.</span></span>  
  
 <span data-ttu-id="ae39a-111">A`Throw`式を指定しないステートメントでのみ使用できます、`Catch`ステートメントでは、case ステートメントが現在処理中の例外を再スロー、`Catch`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="ae39a-111">A `Throw` statement with no expression can only be used in a `Catch` statement, in which case the statement rethrows the exception currently being handled by the `Catch` statement.</span></span>  
  
 <span data-ttu-id="ae39a-112">`Throw`ステートメントの呼び出し履歴をリセットする、`expression`例外。</span><span class="sxs-lookup"><span data-stu-id="ae39a-112">The `Throw` statement resets the call stack for the `expression` exception.</span></span> <span data-ttu-id="ae39a-113">場合`expression`が指定されていない、呼び出し履歴は変更されません。</span><span class="sxs-lookup"><span data-stu-id="ae39a-113">If `expression` is not provided, the call stack is left unchanged.</span></span> <span data-ttu-id="ae39a-114">例外の呼び出し履歴を表示する、<xref:System.Exception.StackTrace%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="ae39a-114">You can access the call stack for the exception through the <xref:System.Exception.StackTrace%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae39a-115">例</span><span class="sxs-lookup"><span data-stu-id="ae39a-115">Example</span></span>  
 <span data-ttu-id="ae39a-116">次のコードでは、`Throw`例外をスローするステートメント。</span><span class="sxs-lookup"><span data-stu-id="ae39a-116">The following code uses the `Throw` statement to throw an exception:</span></span>  
  
 [!code-vb[VbVbalrStatements#84](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/throw-statement_1.vb)]  
  
## <a name="requirements"></a><span data-ttu-id="ae39a-117">要件</span><span class="sxs-lookup"><span data-stu-id="ae39a-117">Requirements</span></span>  
 <span data-ttu-id="ae39a-118">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="ae39a-118">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="ae39a-119">**モジュール:** `Interaction`</span><span class="sxs-lookup"><span data-stu-id="ae39a-119">**Module:** `Interaction`</span></span>  
  
 <span data-ttu-id="ae39a-120">**アセンブリ:** Visual Basic Runtime Library (Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="ae39a-120">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae39a-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae39a-121">See Also</span></span>  
 [<span data-ttu-id="ae39a-122">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="ae39a-122">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="ae39a-123">On Error ステートメント</span><span class="sxs-lookup"><span data-stu-id="ae39a-123">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)

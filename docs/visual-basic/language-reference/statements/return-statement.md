---
title: Return ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: 2f614045be1b91b9c747d961cdefd526ba1bab98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603523"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="02ba8-102">Return ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02ba8-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="02ba8-103">呼び出したコードに制御を返す、 `Function`、 `Sub`、 `Get`、 `Set`、または`Operator`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="02ba8-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02ba8-104">構文</span><span class="sxs-lookup"><span data-stu-id="02ba8-104">Syntax</span></span>  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="02ba8-105">パーツ</span><span class="sxs-lookup"><span data-stu-id="02ba8-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="02ba8-106">必要な`Function`、 `Get`、または`Operator`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="02ba8-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="02ba8-107">呼び出し元のコードに返される値を表す式です。</span><span class="sxs-lookup"><span data-stu-id="02ba8-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02ba8-108">コメント</span><span class="sxs-lookup"><span data-stu-id="02ba8-108">Remarks</span></span>  
 <span data-ttu-id="02ba8-109">`Sub`または`Set`プロシージャ、`Return`ステートメントは等価、`Exit Sub`または`Exit Property`ステートメント、および`expression`を指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="02ba8-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="02ba8-110">`Function`、 `Get`、または`Operator`プロシージャ、`Return`ステートメントを含める必要があります`expression`、および`expression`プロシージャの戻り値の型に変換できるデータ型に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="02ba8-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="02ba8-111">`Function`または`Get`プロシージャもがある場合、戻り値として機能するように、プロシージャ名に式を割り当てると、実行しても、`Exit Function`または`Exit Property`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="02ba8-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="02ba8-112">`Operator`使用する必要がありますプロシージャ、`Return``expression`です。</span><span class="sxs-lookup"><span data-stu-id="02ba8-112">In an `Operator` procedure, you must use `Return``expression`.</span></span>  
  
 <span data-ttu-id="02ba8-113">多くとして含めることができます`Return`同じプロシージャ内に適切なステートメントです。</span><span class="sxs-lookup"><span data-stu-id="02ba8-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02ba8-114">内のコード、`Finally`ブロックが実行した後、`Return`内のステートメント、`Try`または`Catch`ブロックが発生した場合は、その前に`Return`ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="02ba8-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="02ba8-115">A`Return`にステートメントを含めることはできません、`Finally`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="02ba8-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02ba8-116">例</span><span class="sxs-lookup"><span data-stu-id="02ba8-116">Example</span></span>  
 <span data-ttu-id="02ba8-117">次の例では、`Return`ステートメント、プロシージャが何を持っていない場合に、呼び出し元のコードに戻るに複数回です。</span><span class="sxs-lookup"><span data-stu-id="02ba8-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/return-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="02ba8-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="02ba8-118">See Also</span></span>  
 [<span data-ttu-id="02ba8-119">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="02ba8-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="02ba8-120">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="02ba8-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="02ba8-121">Get ステートメント</span><span class="sxs-lookup"><span data-stu-id="02ba8-121">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="02ba8-122">Set ステートメント</span><span class="sxs-lookup"><span data-stu-id="02ba8-122">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)  
 [<span data-ttu-id="02ba8-123">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="02ba8-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="02ba8-124">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="02ba8-124">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="02ba8-125">Exit ステートメント</span><span class="sxs-lookup"><span data-stu-id="02ba8-125">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [<span data-ttu-id="02ba8-126">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="02ba8-126">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)

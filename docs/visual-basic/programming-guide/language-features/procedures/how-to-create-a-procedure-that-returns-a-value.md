---
title: "方法: 値を返すプロシージャを作成する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 787eddc1fd1cdb9dd6b655a8556b75044b2a49dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="fa928-102">方法: 値を返すプロシージャを作成する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa928-102">How to: Create a Procedure that Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="fa928-103">使用する、`Function`呼び出しコードに値を返すプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="fa928-103">You use a `Function` procedure to return a value to the calling code.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="fa928-104">値を返すプロシージャを作成するのには</span><span class="sxs-lookup"><span data-stu-id="fa928-104">To create a procedure that returns a value</span></span>  
  
1.  <span data-ttu-id="fa928-105">その他のすべてのプロシージャの外側を使用して、`Function`ステートメントの後に、`End Function`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="fa928-105">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2.  <span data-ttu-id="fa928-106">`Function`ステートメントでは、以下の`Function`キーワード、プロシージャとし、かっこで囲まれたパラメーター リストの名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="fa928-106">In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.</span></span>  
  
3.  <span data-ttu-id="fa928-107">かっこの後に、`As`句を戻り値のデータ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="fa928-107">Follow the parentheses with an `As` clause to specify the data type of the returned value.</span></span>  
  
4.  <span data-ttu-id="fa928-108">間に、プロシージャのコード ステートメントを配置、`Function`と`End Function`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="fa928-108">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
5.  <span data-ttu-id="fa928-109">使用して、`Return`ステートメントを呼び出し元のコードに値を返します。</span><span class="sxs-lookup"><span data-stu-id="fa928-109">Use a `Return` statement to return the value to the calling code.</span></span>  
  
     <span data-ttu-id="fa928-110">次`Function`最長側では、やの他の 2 つの辺の値を指定、直角三角形の斜辺を計算します。</span><span class="sxs-lookup"><span data-stu-id="fa928-110">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_1.vb)]  
  
     <span data-ttu-id="fa928-111">次の例では、一般的な呼び出しを`hypotenuse`です。</span><span class="sxs-lookup"><span data-stu-id="fa928-111">The following example shows a typical call to `hypotenuse`.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fa928-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa928-112">See Also</span></span>  
 [<span data-ttu-id="fa928-113">手順</span><span class="sxs-lookup"><span data-stu-id="fa928-113">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="fa928-114">Sub プロシージャ</span><span class="sxs-lookup"><span data-stu-id="fa928-114">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="fa928-115">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="fa928-115">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="fa928-116">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="fa928-116">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="fa928-117">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="fa928-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="fa928-118">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="fa928-118">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="fa928-119">方法 : プロシージャから値を返す</span><span class="sxs-lookup"><span data-stu-id="fa928-119">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)  
 [<span data-ttu-id="fa928-120">方法: 値を返すプロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="fa928-120">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)

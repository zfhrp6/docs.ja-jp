---
title: "方法: プロシージャを作成する (Visual Basic)"
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
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 56a44918b7a1426d215cee0ff2981f5763432a48
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-procedure-visual-basic"></a><span data-ttu-id="70c55-102">方法: プロシージャを作成する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70c55-102">How to: Create a Procedure (Visual Basic)</span></span>
<span data-ttu-id="70c55-103">開始宣言ステートメントの間のプロシージャを囲みます (`Sub`または`Function`) と終了の宣言ステートメント (`End Sub`または`End Function`)。</span><span class="sxs-lookup"><span data-stu-id="70c55-103">You enclose a procedure between a starting declaration statement (`Sub` or `Function`) and an ending declaration statement (`End Sub` or `End Function`).</span></span> <span data-ttu-id="70c55-104">これらのステートメント、プロシージャのすべてのコードの範囲です。</span><span class="sxs-lookup"><span data-stu-id="70c55-104">All the procedure's code lies between these statements.</span></span>  
  
 <span data-ttu-id="70c55-105">最初と最後のステートメントが、他のプロシージャの外側にある必要がありますので、プロシージャは別のプロシージャを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="70c55-105">A procedure cannot contain another procedure, so its starting and ending statements must be outside any other procedure.</span></span>  
  
 <span data-ttu-id="70c55-106">別の場所で同じタスクを実行するコードがある場合は、プロシージャとして 1 回タスクを記述し、コード内の異なる場所から呼び出すできます。</span><span class="sxs-lookup"><span data-stu-id="70c55-106">If you have code that performs the same task in different places, you can write the task once as a procedure and then call it from different places in your code.</span></span>  
  
### <a name="to-create-a-procedure-that-does-not-return-a-value"></a><span data-ttu-id="70c55-107">値を返さないプロシージャを作成するには</span><span class="sxs-lookup"><span data-stu-id="70c55-107">To create a procedure that does not return a value</span></span>  
  
1.  <span data-ttu-id="70c55-108">その他のすべてのプロシージャの外側を使用して、`Sub`ステートメントの後に、`End Sub`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="70c55-108">Outside any other procedure, use a `Sub` statement, followed by an `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="70c55-109">`Sub`ステートメントでは、以下の`Sub`パラメーター リストをかっこで、プロシージャの名前を持つキーワード。</span><span class="sxs-lookup"><span data-stu-id="70c55-109">In the `Sub` statement, follow the `Sub` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>  
  
3.  <span data-ttu-id="70c55-110">間に、プロシージャのコード ステートメントを配置、`Sub`と`End Sub`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="70c55-110">Place the procedure's code statements between the `Sub` and `End Sub` statements.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="70c55-111">値を返すプロシージャを作成するのには</span><span class="sxs-lookup"><span data-stu-id="70c55-111">To create a procedure that returns a value</span></span>  
  
1.  <span data-ttu-id="70c55-112">その他のすべてのプロシージャの外側を使用して、`Function`ステートメントの後に、`End Function`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="70c55-112">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2.  <span data-ttu-id="70c55-113">`Function`ステートメントでは、以下の`Function`パラメーター リストをかっこで、プロシージャの名前を持つキーワードし、`As`戻り値のデータ型を指定する句。</span><span class="sxs-lookup"><span data-stu-id="70c55-113">In the `Function` statement, follow the `Function` keyword with the name of the procedure, then the parameter list in parentheses, and then an `As` clause specifying the data type of the return value.</span></span>  
  
3.  <span data-ttu-id="70c55-114">間に、プロシージャのコード ステートメントを配置、`Function`と`End Function`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="70c55-114">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
4.  <span data-ttu-id="70c55-115">使用して、`Return`ステートメントを呼び出し元のコードに値を返します。</span><span class="sxs-lookup"><span data-stu-id="70c55-115">Use a `Return` statement to return the value to the calling code.</span></span>  
  
### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a><span data-ttu-id="70c55-116">古い、反復的なコード ブロックで、新しいプロシージャを接続するには</span><span class="sxs-lookup"><span data-stu-id="70c55-116">To connect your new procedure with the old, repetitive blocks of code</span></span>  
  
1.  <span data-ttu-id="70c55-117">古いコードがへのアクセス権を持つ場所に、新しいプロシージャを定義することを確認してください。</span><span class="sxs-lookup"><span data-stu-id="70c55-117">Make sure you define the new procedure in a place where the old code has access to it.</span></span>  
  
2.  <span data-ttu-id="70c55-118">反復的な古いコード ブロックで、単一のステートメントを呼び出す反復的なタスクを実行しているステートメントを置き換える、`Sub`または`Function`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="70c55-118">In your old, repetitive code block, replace the statements that perform the repetitive task with a single statement that calls the `Sub` or `Function` procedure.</span></span>  
  
3.  <span data-ttu-id="70c55-119">プロシージャで置き換える場合、`Function`値を返す、ある呼び出し元のステートメントが変数に格納するなど、戻り値を使ってアクションを実行するか、値は失われますことを確認します。</span><span class="sxs-lookup"><span data-stu-id="70c55-119">If your procedure is a `Function` that returns a value, ensure that your calling statement performs an action with the returned value, such as storing it in a variable, or else the value will be lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70c55-120">例</span><span class="sxs-lookup"><span data-stu-id="70c55-120">Example</span></span>  
 <span data-ttu-id="70c55-121">次`Function`最長側では、やの他の 2 つの辺の値を指定、直角三角形の斜辺を計算します。</span><span class="sxs-lookup"><span data-stu-id="70c55-121">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="70c55-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="70c55-122">See Also</span></span>  
 [<span data-ttu-id="70c55-123">手順</span><span class="sxs-lookup"><span data-stu-id="70c55-123">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="70c55-124">Sub プロシージャ</span><span class="sxs-lookup"><span data-stu-id="70c55-124">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="70c55-125">Function プロシージャ</span><span class="sxs-lookup"><span data-stu-id="70c55-125">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="70c55-126">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="70c55-126">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="70c55-127">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="70c55-127">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="70c55-128">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="70c55-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="70c55-129">再帰プロシージャ</span><span class="sxs-lookup"><span data-stu-id="70c55-129">Recursive Procedures</span></span>](./recursive-procedures.md)  
 [<span data-ttu-id="70c55-130">プロシージャのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="70c55-130">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="70c55-131">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="70c55-131">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="70c55-132">オブジェクト指向プログラミング</span><span class="sxs-lookup"><span data-stu-id="70c55-132">Object-Oriented Programming</span></span>](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)

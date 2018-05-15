---
title: '方法: 値を返すプロシージャを呼び出す (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 35f757609b6d0b36652db3b14e62ecd299a063ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="5ae2a-102">方法: 値を返すプロシージャを呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ae2a-102">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="5ae2a-103">A`Function`プロシージャが呼び出し元のコードに値を返します。</span><span class="sxs-lookup"><span data-stu-id="5ae2a-103">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="5ae2a-104">これを呼び出す、名前と引数を含む式、または代入ステートメントの右側にあるいずれか。</span><span class="sxs-lookup"><span data-stu-id="5ae2a-104">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="5ae2a-105">式の中で関数のプロシージャを呼び出しています</span><span class="sxs-lookup"><span data-stu-id="5ae2a-105">To call a Function procedure within an expression</span></span>  
  
1.  <span data-ttu-id="5ae2a-106">使用して、`Function`プロシージャ名の変数を使用すると同じ方法です。</span><span class="sxs-lookup"><span data-stu-id="5ae2a-106">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="5ae2a-107">使用することができます、`Function`プロシージャを呼び出す任意の場所の変数または定数を式で使用できます。</span><span class="sxs-lookup"><span data-stu-id="5ae2a-107">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2.  <span data-ttu-id="5ae2a-108">プロシージャ名を引数リストを囲むかっこに従ってください。</span><span class="sxs-lookup"><span data-stu-id="5ae2a-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="5ae2a-109">引数がない場合は、かっこを省略することができます。</span><span class="sxs-lookup"><span data-stu-id="5ae2a-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="5ae2a-110">ただし、かっこを使用して、コードを読みやすくします。</span><span class="sxs-lookup"><span data-stu-id="5ae2a-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="5ae2a-111">コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。</span><span class="sxs-lookup"><span data-stu-id="5ae2a-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="5ae2a-112">同じ順序で引数を指定する必要がありますする、`Function`プロシージャが、対応するパラメーターを定義します。</span><span class="sxs-lookup"><span data-stu-id="5ae2a-112">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="5ae2a-113">また、名前で 1 つまたは複数の引数を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="5ae2a-113">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="5ae2a-114">詳細については、次を参照してください。[位置と名前による引数を渡す](./passing-arguments-by-position-and-by-name.md)です。</span><span class="sxs-lookup"><span data-stu-id="5ae2a-114">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4.  <span data-ttu-id="5ae2a-115">プロシージャから返される値、変数の値と同様に、式または定数します。</span><span class="sxs-lookup"><span data-stu-id="5ae2a-115">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="5ae2a-116">プロシージャを呼び出す関数、代入ステートメントで</span><span class="sxs-lookup"><span data-stu-id="5ae2a-116">To call a Function procedure in an assignment statement</span></span>  
  
1.  <span data-ttu-id="5ae2a-117">使用して、`Function`プロシージャ名の後に続く (`=`) 代入ステートメントにサインインします。</span><span class="sxs-lookup"><span data-stu-id="5ae2a-117">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2.  <span data-ttu-id="5ae2a-118">プロシージャ名を引数リストを囲むかっこに従ってください。</span><span class="sxs-lookup"><span data-stu-id="5ae2a-118">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="5ae2a-119">引数がない場合は、かっこを省略することができます。</span><span class="sxs-lookup"><span data-stu-id="5ae2a-119">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="5ae2a-120">ただし、かっこを使用して、コードを読みやすくします。</span><span class="sxs-lookup"><span data-stu-id="5ae2a-120">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="5ae2a-121">コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。</span><span class="sxs-lookup"><span data-stu-id="5ae2a-121">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="5ae2a-122">同じ順序で引数を指定する必要がありますする、`Function`名前で渡すことがない限り、プロシージャが、対応するパラメーターを定義します。</span><span class="sxs-lookup"><span data-stu-id="5ae2a-122">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4.  <span data-ttu-id="5ae2a-123">プロシージャから返される値は、変数または代入ステートメントの左側にあるプロパティに格納されます。</span><span class="sxs-lookup"><span data-stu-id="5ae2a-123">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ae2a-124">例</span><span class="sxs-lookup"><span data-stu-id="5ae2a-124">Example</span></span>  
 <span data-ttu-id="5ae2a-125">次の例では、Visual Basic<xref:Microsoft.VisualBasic.Interaction.Environ%2A>オペレーティング システム環境変数の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="5ae2a-125">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="5ae2a-126">最初の行呼び出し`Environ`代入ステートメントでその行の式、および 2 つ目の呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="5ae2a-126">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> <span data-ttu-id="5ae2a-127">`Environ` その唯一の引数として変数名を使用します。</span><span class="sxs-lookup"><span data-stu-id="5ae2a-127">`Environ` takes the variable name as its sole argument.</span></span> <span data-ttu-id="5ae2a-128">呼び出し元のコードに変数の値を返します。</span><span class="sxs-lookup"><span data-stu-id="5ae2a-128">It returns the variable's value to the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#7](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5ae2a-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ae2a-129">See Also</span></span>  
 [<span data-ttu-id="5ae2a-130">Function プロシージャ</span><span class="sxs-lookup"><span data-stu-id="5ae2a-130">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="5ae2a-131">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="5ae2a-131">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="5ae2a-132">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="5ae2a-132">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="5ae2a-133">方法 : 値を返すプロシージャを作成する</span><span class="sxs-lookup"><span data-stu-id="5ae2a-133">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="5ae2a-134">方法 : プロシージャから値を返す</span><span class="sxs-lookup"><span data-stu-id="5ae2a-134">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)  
 [<span data-ttu-id="5ae2a-135">方法 : 値を返さないプロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="5ae2a-135">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)

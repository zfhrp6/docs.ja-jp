---
title: Optional (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3aa01c2c1ae731c8fe00fdee24521760db69e624
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="optional-visual-basic"></a><span data-ttu-id="e54be-102">Optional (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e54be-102">Optional (Visual Basic)</span></span>
<span data-ttu-id="e54be-103">プロシージャが呼び出されたときにプロシージャの引数を省略できますを指定します。</span><span class="sxs-lookup"><span data-stu-id="e54be-103">Specifies that a procedure argument can be omitted when the procedure is called.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e54be-104">コメント</span><span class="sxs-lookup"><span data-stu-id="e54be-104">Remarks</span></span>  
 <span data-ttu-id="e54be-105">省略可能なパラメーターごとに、そのパラメーターの既定値として定数式を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e54be-105">For each optional parameter, you must specify a constant expression as the default value of that parameter.</span></span> <span data-ttu-id="e54be-106">式が評価された場合[Nothing](../../../visual-basic/language-reference/nothing.md)値のデータ型の既定値は、パラメーターの既定値として使用します。</span><span class="sxs-lookup"><span data-stu-id="e54be-106">If the expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the default value of the value data type is used as the default value of the parameter.</span></span>  
  
 <span data-ttu-id="e54be-107">パラメーター リストには、省略可能なパラメーターが含まれています、それに続くすべてのパラメーターは省略可能な必要があります。</span><span class="sxs-lookup"><span data-stu-id="e54be-107">If the parameter list contains an optional parameter, every parameter that follows it must also be optional.</span></span>  
  
 <span data-ttu-id="e54be-108">`Optional` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="e54be-108">The `Optional` modifier can be used in these contexts:</span></span>  
  
-   [<span data-ttu-id="e54be-109">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="e54be-109">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [<span data-ttu-id="e54be-110">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="e54be-110">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="e54be-111">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="e54be-111">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [<span data-ttu-id="e54be-112">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="e54be-112">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  <span data-ttu-id="e54be-113">省略可能なパラメーターの有無のプロシージャを呼び出すときに、位置または名前で引数を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="e54be-113">When calling a procedure with or without optional parameters, you can pass arguments by position or by name.</span></span> <span data-ttu-id="e54be-114">詳細については、次を参照してください。[位置と名前による引数を渡す](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)です。</span><span class="sxs-lookup"><span data-stu-id="e54be-114">For more information, see [Passing Arguments by Position and by Name](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e54be-115">オーバー ロードを使用して、省略可能なパラメーターを持つプロシージャを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="e54be-115">You can also define a procedure with optional parameters by using overloading.</span></span> <span data-ttu-id="e54be-116">1 つの省略可能なパラメーターがある場合は、プロシージャ パラメーターを受け取る、しない 2 つのオーバー ロードされたバージョンを定義できます。</span><span class="sxs-lookup"><span data-stu-id="e54be-116">If you have one optional parameter, you can define two overloaded versions of the procedure, one that accepts the parameter and one that doesn’t.</span></span> <span data-ttu-id="e54be-117">詳細については、次を参照してください。[プロシージャのオーバー ロード](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)です。</span><span class="sxs-lookup"><span data-stu-id="e54be-117">For more information, see [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e54be-118">例</span><span class="sxs-lookup"><span data-stu-id="e54be-118">Example</span></span>  
 <span data-ttu-id="e54be-119">次の例では、省略可能なパラメーターを持つプロシージャを定義します。</span><span class="sxs-lookup"><span data-stu-id="e54be-119">The following example defines a procedure that has an optional parameter.</span></span>  
  
```  
Public Function FindMatches(ByRef values As List(Of String),  
                            ByVal searchString As String,  
                            Optional ByVal matchCase As Boolean = False) As List(Of String)  
  
    Dim results As IEnumerable(Of String)  
  
    If matchCase Then  
        results = From v In values  
                  Where v.Contains(searchString)  
    Else  
        results = From v In values  
                  Where UCase(v).Contains(UCase(searchString))  
    End If  
  
    Return results.ToList()  
End Function  
```  
  
## <a name="example"></a><span data-ttu-id="e54be-120">例</span><span class="sxs-lookup"><span data-stu-id="e54be-120">Example</span></span>  
 <span data-ttu-id="e54be-121">次の例では、位置によって渡される引数を指定して、名前によって渡される引数を使用してプロシージャを呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e54be-121">The following example demonstrates how to call a procedure with arguments passed by position and with arguments passed by name.</span></span> <span data-ttu-id="e54be-122">プロシージャは、2 つの省略可能なパラメーターを持ちます。</span><span class="sxs-lookup"><span data-stu-id="e54be-122">The procedure has two optional parameters.</span></span>  
  
 [!code-vb[VbVbalrKeywords#21](../../../visual-basic/language-reference/codesnippet/VisualBasic/optional_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e54be-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="e54be-123">See Also</span></span>  
 [<span data-ttu-id="e54be-124">パラメーター リスト</span><span class="sxs-lookup"><span data-stu-id="e54be-124">Parameter List</span></span>](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [<span data-ttu-id="e54be-125">省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="e54be-125">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [<span data-ttu-id="e54be-126">キーワード</span><span class="sxs-lookup"><span data-stu-id="e54be-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)

---
title: "方法: 値 (Visual Basic) を返すプロシージャを呼び出す |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- procedure calls, returning values
- Visual Basic code, procedures
- procedures, calling
- procedures, returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
caps.latest.revision: 15
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
ms.openlocfilehash: cc1e274a705618213c830d7cf4f61a5e64afd980
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="0b8ca-102">方法: 値を返すプロシージャを呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b8ca-102">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="0b8ca-103">A`Function`プロシージャが呼び出し元のコードに値を返します。</span><span class="sxs-lookup"><span data-stu-id="0b8ca-103">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="0b8ca-104">名前に、名前と引数を含めることによって、代入ステートメントまたは式の右側にあるいずれかです。</span><span class="sxs-lookup"><span data-stu-id="0b8ca-104">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="0b8ca-105">式の中で関数のプロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="0b8ca-105">To call a Function procedure within an expression</span></span>  
  
1.  <span data-ttu-id="0b8ca-106">使用して、`Function`プロシージャ名の変数を使用すると同じ方法です。</span><span class="sxs-lookup"><span data-stu-id="0b8ca-106">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="0b8ca-107">使用することができます、`Function`プロシージャを呼び出す任意の場所が式の中で変数または定数を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="0b8ca-107">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2.  <span data-ttu-id="0b8ca-108">次のプロシージャ名の引数リストを囲むかっこを使用します。</span><span class="sxs-lookup"><span data-stu-id="0b8ca-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="0b8ca-109">引数がない場合は、かっこを省略することができます。</span><span class="sxs-lookup"><span data-stu-id="0b8ca-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="0b8ca-110">ただし、かっこを使用して、コードを読みやすくします。</span><span class="sxs-lookup"><span data-stu-id="0b8ca-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="0b8ca-111">コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。</span><span class="sxs-lookup"><span data-stu-id="0b8ca-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="0b8ca-112">同じ順序で引数を指定する必要があります`Function`プロシージャは、対応するパラメーターを定義します。</span><span class="sxs-lookup"><span data-stu-id="0b8ca-112">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="0b8ca-113">または、名前によって&1; つまたは複数の引数を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="0b8ca-113">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="0b8ca-114">詳細については、次を参照してください。[位置と名前による引数を渡す](./passing-arguments-by-position-and-by-name.md)します。</span><span class="sxs-lookup"><span data-stu-id="0b8ca-114">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4.  <span data-ttu-id="0b8ca-115">プロシージャから返される値、変数の値と同じように式または定数します。</span><span class="sxs-lookup"><span data-stu-id="0b8ca-115">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="0b8ca-116">プロシージャを呼び出す関数、代入ステートメントで</span><span class="sxs-lookup"><span data-stu-id="0b8ca-116">To call a Function procedure in an assignment statement</span></span>  
  
1.  <span data-ttu-id="0b8ca-117">使用して、`Function`プロシージャ名の後に続く (`=`) 代入ステートメントは、サインインします。</span><span class="sxs-lookup"><span data-stu-id="0b8ca-117">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2.  <span data-ttu-id="0b8ca-118">次のプロシージャ名の引数リストを囲むかっこを使用します。</span><span class="sxs-lookup"><span data-stu-id="0b8ca-118">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="0b8ca-119">引数がない場合は、かっこを省略することができます。</span><span class="sxs-lookup"><span data-stu-id="0b8ca-119">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="0b8ca-120">ただし、かっこを使用して、コードを読みやすくします。</span><span class="sxs-lookup"><span data-stu-id="0b8ca-120">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="0b8ca-121">コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。</span><span class="sxs-lookup"><span data-stu-id="0b8ca-121">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="0b8ca-122">同じ順序で引数を指定する必要があります`Function`名で渡すことがない限り、プロシージャが対応するパラメーターを定義します。</span><span class="sxs-lookup"><span data-stu-id="0b8ca-122">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4.  <span data-ttu-id="0b8ca-123">プロシージャから返される値は、変数または代入ステートメントの左側にあるプロパティに格納されます。</span><span class="sxs-lookup"><span data-stu-id="0b8ca-123">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b8ca-124">例</span><span class="sxs-lookup"><span data-stu-id="0b8ca-124">Example</span></span>  
 <span data-ttu-id="0b8ca-125">次の例では、 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.Environ%2A>、オペレーティング システム環境変数の値を取得します</xref:Microsoft.VisualBasic.Interaction.Environ%2A>。</span><span class="sxs-lookup"><span data-stu-id="0b8ca-125">The following example calls the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="0b8ca-126">最初の行呼び出し`Environ`代入ステートメントでその行の式であり、2 番目の呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="0b8ca-126">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> <span data-ttu-id="0b8ca-127">`Environ`単一の引数として変数名を取得します。</span><span class="sxs-lookup"><span data-stu-id="0b8ca-127">`Environ` takes the variable name as its sole argument.</span></span> <span data-ttu-id="0b8ca-128">呼び出し元のコードに変数の値を返します。</span><span class="sxs-lookup"><span data-stu-id="0b8ca-128">It returns the variable's value to the calling code.</span></span>  
  
 <span data-ttu-id="0b8ca-129">[!code-vb[VbVbcnProcedures&#7;](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="0b8ca-129">[!code-vb[VbVbcnProcedures#7](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b8ca-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b8ca-130">See Also</span></span>  
 <span data-ttu-id="0b8ca-131">[Function プロシージャ](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="0b8ca-131">[Function Procedures](./function-procedures.md) </span></span>  
<span data-ttu-id="0b8ca-132"> [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="0b8ca-132"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="0b8ca-133"> [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="0b8ca-133"> [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="0b8ca-134"> [方法: 値を返すプロシージャを作成します。](./how-to-create-a-procedure-that-returns-a-value.md) </span><span class="sxs-lookup"><span data-stu-id="0b8ca-134"> [How to: Create a Procedure that Returns a Value](./how-to-create-a-procedure-that-returns-a-value.md) </span></span>  
<span data-ttu-id="0b8ca-135"> [方法: プロシージャから値を返す](./how-to-return-a-value-from-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="0b8ca-135"> [How to: Return a Value from a Procedure](./how-to-return-a-value-from-a-procedure.md) </span></span>  
<span data-ttu-id="0b8ca-136"> [方法 : 値を返さないプロシージャを呼び出す](./how-to-call-a-procedure-that-does-not-return-a-value.md)</span><span class="sxs-lookup"><span data-stu-id="0b8ca-136"> [How to: Call a Procedure that Does Not Return a Value](./how-to-call-a-procedure-that-does-not-return-a-value.md)</span></span>

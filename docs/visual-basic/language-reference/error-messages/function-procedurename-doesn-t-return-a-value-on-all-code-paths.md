---
title: 関数&#39; &lt;procedurename&gt; &#39;しません&#39;t は、すべてのコード パスで値を返しません
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: 4c18c6229eb170e8a688aaa2734ae8fbfa081061
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589985"
---
# <a name="function-39ltprocedurenamegt39-doesn39t-return-a-value-on-all-code-paths"></a><span data-ttu-id="66aca-102">関数&#39; &lt;procedurename&gt; &#39;しません&#39;t は、すべてのコード パスで値を返しません</span><span class="sxs-lookup"><span data-stu-id="66aca-102">Function &#39;&lt;procedurename&gt;&#39; doesn&#39;t return a value on all code paths</span></span>
<span data-ttu-id="66aca-103">関数 '\<procedurename >' は、すべてのコード パスで値を返しません。</span><span class="sxs-lookup"><span data-stu-id="66aca-103">Function '\<procedurename>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="66aca-104">'Return' ステートメントが見当たりませんか。</span><span class="sxs-lookup"><span data-stu-id="66aca-104">Are you missing a 'Return' statement?</span></span>  
  
 <span data-ttu-id="66aca-105">A`Function`手順では、値を返さないコードに少なくとも 1 つの可能なパスです。</span><span class="sxs-lookup"><span data-stu-id="66aca-105">A `Function` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="66aca-106">値を返すことができます、`Function`次の方法のいずれかの手順。</span><span class="sxs-lookup"><span data-stu-id="66aca-106">You can return a value from a `Function` procedure in any of the following ways:</span></span>  
  
-   <span data-ttu-id="66aca-107">値を含む、 [Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="66aca-107">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
-   <span data-ttu-id="66aca-108">値を割り当てる、`Function`プロシージャ名前を指定しを実行して、`Exit Function`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="66aca-108">Assign the value to the `Function` procedure name and then perform an `Exit Function` statement.</span></span>  
  
-   <span data-ttu-id="66aca-109">値を割り当てる、`Function`プロシージャ名前を指定しを実行して、`End Function`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="66aca-109">Assign the value to the `Function` procedure name and then perform the `End Function` statement.</span></span>  
  
 <span data-ttu-id="66aca-110">コントロールに渡します`Exit Function`または`End Function`プロシージャの名前を任意の値が割り当てられていないと、プロシージャは、戻り値のデータ型の既定値を返します。</span><span class="sxs-lookup"><span data-stu-id="66aca-110">If control passes to `Exit Function` or `End Function` and you have not assigned any value to the procedure name, the procedure returns the default value of the return data type.</span></span> <span data-ttu-id="66aca-111">詳細については、「動作」を参照してください[関数ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="66aca-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="66aca-112">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="66aca-112">By default, this message is a warning.</span></span> <span data-ttu-id="66aca-113">警告を非表示や、警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)です。</span><span class="sxs-lookup"><span data-stu-id="66aca-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="66aca-114">**エラー ID:** BC42105</span><span class="sxs-lookup"><span data-stu-id="66aca-114">**Error ID:** BC42105</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="66aca-115">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="66aca-115">To correct this error</span></span>  
  
-   <span data-ttu-id="66aca-116">制御フローのロジックを確認し、戻り値の原因となるすべてのステートメントの前に値を代入するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="66aca-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="66aca-117">すべてを返すプロシージャが常に使用する場合に、値を返すことを保証しやすく、`Return`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="66aca-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="66aca-118">この場合、最後のステートメントの前に`End Function`する必要があります、`Return`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="66aca-118">If you do this, the last statement before `End Function` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66aca-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="66aca-119">See Also</span></span>  
 [<span data-ttu-id="66aca-120">Function プロシージャ</span><span class="sxs-lookup"><span data-stu-id="66aca-120">Function Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)  
 [<span data-ttu-id="66aca-121">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="66aca-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 <span data-ttu-id="66aca-122">[[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="66aca-122">[Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)</span></span>

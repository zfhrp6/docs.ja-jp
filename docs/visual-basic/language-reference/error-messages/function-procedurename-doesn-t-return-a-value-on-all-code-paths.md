---
title: "関数 &quot;&lt;procedurename&gt;&quot; すべてのコード パスで値が返されない |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42105
- vbc42105
dev_langs:
- VB
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
caps.latest.revision: 12
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
ms.openlocfilehash: cec047644bfbf82c5c3c206b23af6b0fc37f834d
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="function-39ltprocedurenamegt39-doesn39t-return-a-value-on-all-code-paths"></a><span data-ttu-id="691fa-102">関数 '&lt;procedurename&gt;' すべてのコード パスで値が返されない</span><span class="sxs-lookup"><span data-stu-id="691fa-102">Function &#39;&lt;procedurename&gt;&#39; doesn&#39;t return a value on all code paths</span></span>
<span data-ttu-id="691fa-103">関数 '\<procedurename >' すべてのコード パスで値を返しません。</span><span class="sxs-lookup"><span data-stu-id="691fa-103">Function '\<procedurename>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="691fa-104">'Return' ステートメントが不足していますか。</span><span class="sxs-lookup"><span data-stu-id="691fa-104">Are you missing a 'Return' statement?</span></span>  
  
 <span data-ttu-id="691fa-105">A`Function`手順では、値を返さないことをコードから少なくとも&1; つの可能なパスです。</span><span class="sxs-lookup"><span data-stu-id="691fa-105">A `Function` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="691fa-106">値を返すことができます、`Function`次の方法のいずれかの手順。</span><span class="sxs-lookup"><span data-stu-id="691fa-106">You can return a value from a `Function` procedure in any of the following ways:</span></span>  
  
-   <span data-ttu-id="691fa-107">値を含む、 [Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="691fa-107">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
-   <span data-ttu-id="691fa-108">値を代入します、`Function`プロシージャ名前を指定し、実行、`Exit Function`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="691fa-108">Assign the value to the `Function` procedure name and then perform an `Exit Function` statement.</span></span>  
  
-   <span data-ttu-id="691fa-109">値を代入します、`Function`プロシージャ名前を指定し、実行、`End Function`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="691fa-109">Assign the value to the `Function` procedure name and then perform the `End Function` statement.</span></span>  
  
 <span data-ttu-id="691fa-110">制御が移るかどうか`Exit Function`または`End Function`プロシージャ名に任意の値が割り当てられていないと、プロシージャは、戻り値のデータ型の既定値を返します。</span><span class="sxs-lookup"><span data-stu-id="691fa-110">If control passes to `Exit Function` or `End Function` and you have not assigned any value to the procedure name, the procedure returns the default value of the return data type.</span></span> <span data-ttu-id="691fa-111">詳細については、「動作」を参照してください[Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="691fa-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="691fa-112">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="691fa-112">By default, this message is a warning.</span></span> <span data-ttu-id="691fa-113">警告を非表示や警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)します。</span><span class="sxs-lookup"><span data-stu-id="691fa-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="691fa-114">**エラー ID:** BC42105</span><span class="sxs-lookup"><span data-stu-id="691fa-114">**Error ID:** BC42105</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="691fa-115">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="691fa-115">To correct this error</span></span>  
  
-   <span data-ttu-id="691fa-116">制御フローのロジックを確認し、すべてのステートメントが値を返す前に値を代入するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="691fa-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="691fa-117">常に使用する場合に、プロシージャからリターンごとに値を返すことを保証する方が簡単、`Return`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="691fa-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="691fa-118">この場合、最後のステートメントの前に`End Function`する必要があります、`Return`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="691fa-118">If you do this, the last statement before `End Function` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="691fa-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="691fa-119">See Also</span></span>  
 <span data-ttu-id="691fa-120">[Function プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="691fa-120">[Function Procedures](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) </span></span>  
<span data-ttu-id="691fa-121"> [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="691fa-121"> [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="691fa-122"> [[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="691fa-122"> [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)</span></span>

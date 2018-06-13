---
title: 暗黙的な変換&#39; &lt;typename1&gt; &#39;に&#39; &lt;typename2&gt; &#39;の値をコピー中&#39;ByRef&#39;パラメーター &#39; &lt;parametername&gt; &#39; 、一致する引数にします。
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: b1f772598b18f8edfe0198f62d78854d30f993ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590001"
---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a><span data-ttu-id="0ded0-102">暗黙的な変換&#39; &lt;typename1&gt; &#39;に&#39; &lt;typename2&gt; &#39;の値をコピー中&#39;ByRef&#39;パラメーター &#39; &lt;parametername&gt; &#39; 、一致する引数にします。</span><span class="sxs-lookup"><span data-stu-id="0ded0-102">Implicit conversion from &#39;&lt;typename1&gt;&#39; to &#39;&lt;typename2&gt;&#39; in copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument.</span></span>
<span data-ttu-id="0ded0-103">プロシージャが呼び出される、 [ByRef](../../../visual-basic/language-reference/modifiers/byref.md)対応するパラメーターとは異なる型の引数。</span><span class="sxs-lookup"><span data-stu-id="0ded0-103">A procedure is called with a [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argument of a different type than that of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="0ded0-104">引数を渡す場合`ByRef`、Visual Basic は、参照を渡す代わりにプロシージャ内のローカル変数に引数の値をコピーすることがあります。</span><span class="sxs-lookup"><span data-stu-id="0ded0-104">If you pass an argument `ByRef`, Visual Basic sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="0ded0-105">このような場合は、プロシージャが戻るとき、Visual Basic 必要がありますにコピーしてローカル変数の値戻す呼び出し元のコードの引数。</span><span class="sxs-lookup"><span data-stu-id="0ded0-105">In such a case, when the procedure returns, Visual Basic must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="0ded0-106">`ByRef` 引数の値がプロシージャにコピーされ、引数とパラメーターが同じ型である場合、変換は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="0ded0-106">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="0ded0-107">型が異なる場合は、Visual Basic が双方向で変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ded0-107">But if the types are different, Visual Basic must convert in both directions.</span></span> <span data-ttu-id="0ded0-108">使用できないため`CType`または暗黙的なプロシージャ引数、またはパラメーター、そのような変換でその他の変換キーワードのいずれかが常にします。</span><span class="sxs-lookup"><span data-stu-id="0ded0-108">Because you cannot use `CType` or any of the other conversion keywords on a procedure argument or parameter, such a conversion is always implicit.</span></span>  
  
 <span data-ttu-id="0ded0-109">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="0ded0-109">By default, this message is a warning.</span></span> <span data-ttu-id="0ded0-110">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ded0-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="0ded0-111">**エラー ID:** BC41999</span><span class="sxs-lookup"><span data-stu-id="0ded0-111">**Error ID:** BC41999</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0ded0-112">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="0ded0-112">To correct this error</span></span>  
  
-   <span data-ttu-id="0ded0-113">可能であれば、ので Visual Basic は、変換を行う必要はありませんは、プロシージャのパラメーターと同じ型の呼び出し元の引数を使用します。</span><span class="sxs-lookup"><span data-stu-id="0ded0-113">If possible, use a calling argument of the same type as the procedure parameter, so Visual Basic does not need to do any conversion.</span></span>  
  
-   <span data-ttu-id="0ded0-114">パラメーターの型の異なる型引数を持つプロシージャを呼び出す必要がある場合は、呼び出し元の引数に値を返す、パラメーターを定義する必要はありません[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)の代わりに`ByRef`です。</span><span class="sxs-lookup"><span data-stu-id="0ded0-114">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) instead of `ByRef`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ded0-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ded0-115">See Also</span></span>  
 [<span data-ttu-id="0ded0-116">手順</span><span class="sxs-lookup"><span data-stu-id="0ded0-116">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="0ded0-117">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="0ded0-117">Procedure Parameters and Arguments</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="0ded0-118">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="0ded0-118">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="0ded0-119">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="0ded0-119">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)

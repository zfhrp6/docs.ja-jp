---
title: "暗黙的に変換 &quot;&lt;&quot; typename1 &quot;&gt;&quot;to&quot;&lt;typename2&gt;&quot;ByRef&quot; パラメーターの値をコピーするには&quot; in&lt;parametername&gt;&quot; に一致する引数。 | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc41999
- bc41999
dev_langs:
- VB
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
caps.latest.revision: 7
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
ms.openlocfilehash: 0d69bc5074ed5ef2f58010b3477752d3aa6a4b26
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a><span data-ttu-id="a6557-103">暗黙的に変換 '&lt;' typename1 '&gt;'to'&lt;typename2&gt;'ByRef' パラメーターの値をコピーするには' in&lt;parametername&gt;' に一致する引数。</span><span class="sxs-lookup"><span data-stu-id="a6557-103">Implicit conversion from &#39;&lt;typename1&gt;&#39; to &#39;&lt;typename2&gt;&#39; in copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument.</span></span>
<span data-ttu-id="a6557-104">プロシージャが呼び出される、 [ByRef](../../../visual-basic/language-reference/modifiers/byref.md)を対応するパラメーターとは異なる型の引数。</span><span class="sxs-lookup"><span data-stu-id="a6557-104">A procedure is called with a [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argument of a different type than that of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="a6557-105">引数を渡す場合`ByRef`、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]の参照を渡す代わりに、手順でローカル変数に引数の値をコピーすることがあります。</span><span class="sxs-lookup"><span data-stu-id="a6557-105">If you pass an argument `ByRef`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="a6557-106">このような場合は、プロシージャから制御が戻るとき[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]呼び出し元のコードで引数にローカル変数の値をコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6557-106">In such a case, when the procedure returns, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="a6557-107">`ByRef` 引数の値がプロシージャにコピーされ、引数とパラメーターが同じ型である場合、変換は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="a6557-107">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="a6557-108">種類が異なる場合が[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]双方向で変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6557-108">But if the types are different, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] must convert in both directions.</span></span> <span data-ttu-id="a6557-109">使用できないため`CType`または暗黙的なプロシージャの引数やパラメーターには、このような変換でその他の変換キーワードのいずれかが常にします。</span><span class="sxs-lookup"><span data-stu-id="a6557-109">Because you cannot use `CType` or any of the other conversion keywords on a procedure argument or parameter, such a conversion is always implicit.</span></span>  
  
 <span data-ttu-id="a6557-110">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="a6557-110">By default, this message is a warning.</span></span> <span data-ttu-id="a6557-111">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6557-111">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="a6557-112">**エラー ID:** BC41999</span><span class="sxs-lookup"><span data-stu-id="a6557-112">**Error ID:** BC41999</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a6557-113">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="a6557-113">To correct this error</span></span>  
  
-   <span data-ttu-id="a6557-114">したがってプロシージャのパラメーターとして、同じ型の呼び出し元の引数を使用可能であれば、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]変換する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a6557-114">If possible, use a calling argument of the same type as the procedure parameter, so [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] does not need to do any conversion.</span></span>  
  
-   <span data-ttu-id="a6557-115">引数を使ってプロシージャを呼び出す必要がある場合に、パラメーターの型の異なる型が、呼び出し元の引数に値を返す、パラメーターを定義する必要はありません[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)の代わりに`ByRef`します。</span><span class="sxs-lookup"><span data-stu-id="a6557-115">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) instead of `ByRef`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6557-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6557-116">See Also</span></span>  
 <span data-ttu-id="a6557-117">[手順](../../../visual-basic/programming-guide/language-features/procedures/index.md) </span><span class="sxs-lookup"><span data-stu-id="a6557-117">[Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md) </span></span>  
<span data-ttu-id="a6557-118"> [プロシージャのパラメーターと引数](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="a6557-118"> [Procedure Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="a6557-119"> [値渡しと参照による引数渡し](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="a6557-119"> [Passing Arguments by Value and by Reference](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="a6557-120"> [暗黙の型変換と明示的な型変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)</span><span class="sxs-lookup"><span data-stu-id="a6557-120"> [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)</span></span>

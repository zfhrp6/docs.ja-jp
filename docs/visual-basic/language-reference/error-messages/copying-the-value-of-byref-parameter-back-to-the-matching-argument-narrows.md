---
title: "&quot;ByRef&quot; パラメーターの値をコピー &quot;&lt;parametername&gt;&quot;に一致する引数の型から限定&quot;&lt;&quot; typename1 &quot;&gt;&quot; type&quot; に&lt;typename2&gt;&quot; |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32053
- vbc32053
dev_langs:
- VB
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
caps.latest.revision: 8
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
ms.openlocfilehash: 10ad4af689c11f3e4defe43c4fed9ed579ba5305
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument-narrows-from-type-39lttypename1gt39-to-type-39lttypename2gt39"></a><span data-ttu-id="b8c8d-102">'ByRef' パラメーターの値をコピー '&lt;parametername&gt;'に一致する引数の型から限定'&lt;' typename1 '&gt;' type' に&lt;typename2&gt;'</span><span class="sxs-lookup"><span data-stu-id="b8c8d-102">Copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument narrows from type &#39;&lt;typename1&gt;&#39; to type &#39;&lt;typename2&gt;&#39;</span></span>
<span data-ttu-id="b8c8d-103">拡大変換後の対応するパラメーターの型引数を持つプロシージャが呼び出され、パラメーターから引数への変換を縮小します。</span><span class="sxs-lookup"><span data-stu-id="b8c8d-103">A procedure is called with an argument that widens to the corresponding parameter type, and the conversion from the parameter to the argument is narrowing.</span></span>  
  
 <span data-ttu-id="b8c8d-104">クラスまたは構造体を定義するときは、そのクラスまたは構造体の型を他の型に変換する&1; つまたは複数の変換演算子を定義できます。</span><span class="sxs-lookup"><span data-stu-id="b8c8d-104">When you define a class or structure, you can define one or more conversion operators to convert that class or structure type to other types.</span></span> <span data-ttu-id="b8c8d-105">その他の型をクラスまたは構造体の型に変換する逆の変換演算子を定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="b8c8d-105">You can also define reverse conversion operators to convert those other types back to your class or structure type.</span></span> <span data-ttu-id="b8c8d-106">プロシージャ呼び出しで、クラスまたは構造体の型を使用すると[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]の引数の型を対応するパラメーターの型に変換するこれらの変換演算子を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="b8c8d-106">When you use your class or structure type in a procedure call, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] can use these conversion operators to convert the type of an argument to the type of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="b8c8d-107">引数を渡した場合[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]の参照を渡す代わりに、手順でローカル変数に引数の値をコピーすることがあります。</span><span class="sxs-lookup"><span data-stu-id="b8c8d-107">If you pass the argument [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="b8c8d-108">このような場合は、プロシージャから制御が戻るとき[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]呼び出し元のコードで引数にローカル変数の値をコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8c8d-108">In such a case, when the procedure returns, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="b8c8d-109">`ByRef` 引数の値がプロシージャにコピーされ、引数とパラメーターが同じ型である場合、変換は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="b8c8d-109">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="b8c8d-110">種類が異なる場合が[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]双方向で変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8c8d-110">But if the types are different, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] must convert in both directions.</span></span> <span data-ttu-id="b8c8d-111">型のいずれかが型の場合、クラスまたは構造体、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]両方と、他の型から変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8c8d-111">If one of the types is your class or structure type, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] must convert it both to and from the other type.</span></span> <span data-ttu-id="b8c8d-112">これらの変換のいずれかを拡大すると場合、は、逆の変換が縮小可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b8c8d-112">If one of these conversions is widening, the reverse conversion might be narrowing.</span></span>  
  
 <span data-ttu-id="b8c8d-113">**エラー ID:** BC32053</span><span class="sxs-lookup"><span data-stu-id="b8c8d-113">**Error ID:** BC32053</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b8c8d-114">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="b8c8d-114">To correct this error</span></span>  
  
-   <span data-ttu-id="b8c8d-115">したがってプロシージャのパラメーターとして、同じ型の呼び出し元の引数を使用可能であれば、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]変換する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b8c8d-115">If possible, use a calling argument of the same type as the procedure parameter, so [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] does not need to do any conversion.</span></span>  
  
-   <span data-ttu-id="b8c8d-116">引数を使ってプロシージャを呼び出す必要がある場合に、パラメーターの型の異なる型が、呼び出し元の引数に値を返す、パラメーターを定義する必要はありません[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)の代わりに`ByRef`します。</span><span class="sxs-lookup"><span data-stu-id="b8c8d-116">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) instead of `ByRef`.</span></span>  
  
-   <span data-ttu-id="b8c8d-117">呼び出し元の引数に値を返す必要がある場合は、逆変換演算子を定義[拡大変換](../../../visual-basic/language-reference/modifiers/widening.md)可能であれば、します。</span><span class="sxs-lookup"><span data-stu-id="b8c8d-117">If you need to return a value into the calling argument, define the reverse conversion operator as [Widening](../../../visual-basic/language-reference/modifiers/widening.md), if possible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8c8d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8c8d-118">See Also</span></span>  
 <span data-ttu-id="b8c8d-119">[手順](../../../visual-basic/programming-guide/language-features/procedures/index.md) </span><span class="sxs-lookup"><span data-stu-id="b8c8d-119">[Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md) </span></span>  
<span data-ttu-id="b8c8d-120"> [プロシージャのパラメーターと引数](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="b8c8d-120"> [Procedure Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="b8c8d-121"> [値渡しと参照による引数渡し](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="b8c8d-121"> [Passing Arguments by Value and by Reference](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="b8c8d-122"> [演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="b8c8d-122"> [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md) </span></span>  
<span data-ttu-id="b8c8d-123"> [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md) </span><span class="sxs-lookup"><span data-stu-id="b8c8d-123"> [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md) </span></span>  
<span data-ttu-id="b8c8d-124"> [方法: 演算子を定義](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md) </span><span class="sxs-lookup"><span data-stu-id="b8c8d-124"> [How to: Define an Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md) </span></span>  
<span data-ttu-id="b8c8d-125"> [方法: 変換演算子を定義します。](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md) </span><span class="sxs-lookup"><span data-stu-id="b8c8d-125"> [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md) </span></span>  
<span data-ttu-id="b8c8d-126"> [Visual Basic における型変換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="b8c8d-126"> [Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="b8c8d-127"> [拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)</span><span class="sxs-lookup"><span data-stu-id="b8c8d-127"> [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)</span></span>

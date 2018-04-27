---
title: 値をコピー &#39;ByRef&#39;パラメーター &#39; &lt;parametername&gt; &#39;型から縮小変換を一致する引数に戻して&#39; &lt;typename1&gt; &#39;型&#39; &lt;typename2&gt;&#39;
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 18c72e56e4b2cc9c2251de2417a9f12a6688323f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument-narrows-from-type-39lttypename1gt39-to-type-39lttypename2gt39"></a><span data-ttu-id="966ec-102">値をコピー &#39;ByRef&#39;パラメーター &#39; &lt;parametername&gt; &#39;型から縮小変換を一致する引数に戻して&#39; &lt;typename1&gt; &#39;型&#39; &lt;typename2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="966ec-102">Copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument narrows from type &#39;&lt;typename1&gt;&#39; to type &#39;&lt;typename2&gt;&#39;</span></span>
<span data-ttu-id="966ec-103">プロシージャが、対応するパラメーターの型に拡大変換する引数によって呼び出され、引数には、パラメーターからの変換は縮小します。</span><span class="sxs-lookup"><span data-stu-id="966ec-103">A procedure is called with an argument that widens to the corresponding parameter type, and the conversion from the parameter to the argument is narrowing.</span></span>  
  
 <span data-ttu-id="966ec-104">クラスまたは構造体を定義するときは、そのクラスまたは構造体の型を他の型に変換する 1 つまたは複数の変換演算子を定義できます。</span><span class="sxs-lookup"><span data-stu-id="966ec-104">When you define a class or structure, you can define one or more conversion operators to convert that class or structure type to other types.</span></span> <span data-ttu-id="966ec-105">その他の型をクラスまたは構造体の型に変換する逆の変換演算子を定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="966ec-105">You can also define reverse conversion operators to convert those other types back to your class or structure type.</span></span> <span data-ttu-id="966ec-106">プロシージャ呼び出しでクラスまたは構造体の型を使用すると、Visual Basic は、引数の型を対応するパラメーターの型に変換するのにこれらの変換演算子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="966ec-106">When you use your class or structure type in a procedure call, Visual Basic can use these conversion operators to convert the type of an argument to the type of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="966ec-107">引数を渡す場合[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)、Visual Basic は、参照を渡す代わりにプロシージャ内のローカル変数に引数の値をコピーすることがあります。</span><span class="sxs-lookup"><span data-stu-id="966ec-107">If you pass the argument [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="966ec-108">このような場合は、プロシージャが戻るとき、Visual Basic 必要がありますにコピーしてローカル変数の値戻す呼び出し元のコードの引数。</span><span class="sxs-lookup"><span data-stu-id="966ec-108">In such a case, when the procedure returns, Visual Basic must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="966ec-109">`ByRef` 引数の値がプロシージャにコピーされ、引数とパラメーターが同じ型である場合、変換は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="966ec-109">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="966ec-110">型が異なる場合は、Visual Basic が双方向で変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="966ec-110">But if the types are different, Visual Basic must convert in both directions.</span></span> <span data-ttu-id="966ec-111">型のいずれかがクラスまたは構造体の型の場合は、Visual Basic 必要があります変換との間、他の型。</span><span class="sxs-lookup"><span data-stu-id="966ec-111">If one of the types is your class or structure type, Visual Basic must convert it both to and from the other type.</span></span> <span data-ttu-id="966ec-112">これらの変換のいずれかを拡大すると場合、逆変換は縮小可能性があります。</span><span class="sxs-lookup"><span data-stu-id="966ec-112">If one of these conversions is widening, the reverse conversion might be narrowing.</span></span>  
  
 <span data-ttu-id="966ec-113">**エラー ID:** BC32053</span><span class="sxs-lookup"><span data-stu-id="966ec-113">**Error ID:** BC32053</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="966ec-114">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="966ec-114">To correct this error</span></span>  
  
-   <span data-ttu-id="966ec-115">可能であれば、ので Visual Basic は、変換を行う必要はありませんは、プロシージャのパラメーターと同じ型の呼び出し元の引数を使用します。</span><span class="sxs-lookup"><span data-stu-id="966ec-115">If possible, use a calling argument of the same type as the procedure parameter, so Visual Basic does not need to do any conversion.</span></span>  
  
-   <span data-ttu-id="966ec-116">パラメーターの型の異なる型引数を持つプロシージャを呼び出す必要がある場合は、呼び出し元の引数に値を返す、パラメーターを定義する必要はありません[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)の代わりに`ByRef`です。</span><span class="sxs-lookup"><span data-stu-id="966ec-116">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) instead of `ByRef`.</span></span>  
  
-   <span data-ttu-id="966ec-117">呼び出し元の引数に値を返す必要がある場合、逆変換演算子を定義として[Widening](../../../visual-basic/language-reference/modifiers/widening.md)可能であれば、します。</span><span class="sxs-lookup"><span data-stu-id="966ec-117">If you need to return a value into the calling argument, define the reverse conversion operator as [Widening](../../../visual-basic/language-reference/modifiers/widening.md), if possible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="966ec-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="966ec-118">See Also</span></span>  
 [<span data-ttu-id="966ec-119">手順</span><span class="sxs-lookup"><span data-stu-id="966ec-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="966ec-120">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="966ec-120">Procedure Parameters and Arguments</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="966ec-121">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="966ec-121">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="966ec-122">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="966ec-122">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [<span data-ttu-id="966ec-123">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="966ec-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="966ec-124">方法 : 演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="966ec-124">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="966ec-125">方法 : 変換演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="966ec-125">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="966ec-126">Visual Basic での型変換</span><span class="sxs-lookup"><span data-stu-id="966ec-126">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="966ec-127">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="966ec-127">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)

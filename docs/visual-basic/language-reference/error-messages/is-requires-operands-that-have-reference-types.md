---
title: '&#39;&#39;オペランドを必要と参照型を持つことがこのオペランドの値の型&#39; &lt;typename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: 07838e62bd6b180f7dece79355ea7aa1d6c4527a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585581"
---
# <a name="39is39-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-39lttypenamegt39"></a><span data-ttu-id="1af8c-102">&#39;&#39;オペランドを必要と参照型を持つことがこのオペランドの値の型&#39; &lt;typename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="1af8c-102">&#39;Is&#39; requires operands that have reference types, but this operand has the value type &#39;&lt;typename&gt;&#39;</span></span>
<span data-ttu-id="1af8c-103">`Is`比較演算子は、2 つのオブジェクト変数が、同じインスタンスを参照しているかどうかを判定します。</span><span class="sxs-lookup"><span data-stu-id="1af8c-103">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="1af8c-104">この比較は、値型に対して定義されていません。</span><span class="sxs-lookup"><span data-stu-id="1af8c-104">This comparison is not defined for value types.</span></span>  
  
 <span data-ttu-id="1af8c-105">**エラー ID:** BC30020</span><span class="sxs-lookup"><span data-stu-id="1af8c-105">**Error ID:** BC30020</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1af8c-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="1af8c-106">To correct this error</span></span>  
  
-   <span data-ttu-id="1af8c-107">適切な算術比較演算子を使用して、または`Like`2 つの値の型を比較する演算子です。</span><span class="sxs-lookup"><span data-stu-id="1af8c-107">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1af8c-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="1af8c-108">See Also</span></span>  
 [<span data-ttu-id="1af8c-109">Is 演算子</span><span class="sxs-lookup"><span data-stu-id="1af8c-109">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="1af8c-110">Like 演算子</span><span class="sxs-lookup"><span data-stu-id="1af8c-110">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)  
 [<span data-ttu-id="1af8c-111">比較演算子</span><span class="sxs-lookup"><span data-stu-id="1af8c-111">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)

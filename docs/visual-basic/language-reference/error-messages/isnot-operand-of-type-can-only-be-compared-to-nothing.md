---
title: '&#39;IsNot&#39;型のオペランド&#39;typename&#39;のみと比較できます&#39;Nothing&#39;ので、 &#39;typename&#39; null 許容型は、'
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: 44cc17c73b476e5e322b9b58b021bc7bcd63167f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="39isnot39-operand-of-type-39typename39-can-only-be-compared-to-39nothing39-because-39typename39-is-a-nullable-type"></a><span data-ttu-id="0f198-102">&#39;IsNot&#39;型のオペランド&#39;typename&#39;のみと比較できます&#39;Nothing&#39;ので、 &#39;typename&#39; null 許容型は、</span><span class="sxs-lookup"><span data-stu-id="0f198-102">&#39;IsNot&#39; operand of type &#39;typename&#39; can only be compared to &#39;Nothing&#39;, because &#39;typename&#39; is a nullable type</span></span>
<span data-ttu-id="0f198-103">式に null 許容型として宣言された変数が以外の場合に比較`Nothing`を使用して、`IsNot`演算子。</span><span class="sxs-lookup"><span data-stu-id="0f198-103">A variable declared as nullable has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>  
  
 <span data-ttu-id="0f198-104">**エラー ID:** BC32128</span><span class="sxs-lookup"><span data-stu-id="0f198-104">**Error ID:** BC32128</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0f198-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="0f198-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="0f198-106">以外の式を null 許容型を比較する`Nothing`を使用して、`IsNot`演算子、呼び出し、`GetType`比較結果を次の例で示すように、式、null 許容型のメソッドです。</span><span class="sxs-lookup"><span data-stu-id="0f198-106">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>  
  
```vb  
Dim number? As Integer = 5  
  
If number IsNot Nothing Then  
  If number.GetType() IsNot Type.GetType("System.Int32") Then   
  
  End If  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f198-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="0f198-107">See Also</span></span>  
 [<span data-ttu-id="0f198-108">null 許容値型</span><span class="sxs-lookup"><span data-stu-id="0f198-108">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [<span data-ttu-id="0f198-109">IsNot 演算子</span><span class="sxs-lookup"><span data-stu-id="0f198-109">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)

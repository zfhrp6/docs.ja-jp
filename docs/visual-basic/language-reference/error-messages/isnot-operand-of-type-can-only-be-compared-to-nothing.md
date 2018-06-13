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
ms.locfileid: "33587597"
---
# <a name="39isnot39-operand-of-type-39typename39-can-only-be-compared-to-39nothing39-because-39typename39-is-a-nullable-type"></a>&#39;IsNot&#39;型のオペランド&#39;typename&#39;のみと比較できます&#39;Nothing&#39;ので、 &#39;typename&#39; null 許容型は、
式に null 許容型として宣言された変数が以外の場合に比較`Nothing`を使用して、`IsNot`演算子。  
  
 **エラー ID:** BC32128  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  以外の式を null 許容型を比較する`Nothing`を使用して、`IsNot`演算子、呼び出し、`GetType`比較結果を次の例で示すように、式、null 許容型のメソッドです。  
  
```vb  
Dim number? As Integer = 5  
  
If number IsNot Nothing Then  
  If number.GetType() IsNot Type.GetType("System.Int32") Then   
  
  End If  
End If  
```  
  
## <a name="see-also"></a>関連項目  
 [null 許容値型](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [IsNot 演算子](../../../visual-basic/language-reference/operators/isnot-operator.md)

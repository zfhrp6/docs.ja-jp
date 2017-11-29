---
title: "&#39; IsNot &#39;オペランド型 &#39; typename &#39; ののみと比較する (& a) #39 です。何も &#39; であるため &#39; typename &#39;null 許容型は、します。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords: BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ec0ae1561bfbee998e7c65f6023012c0f982a8a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="39isnot39-operand-of-type-39typename39-can-only-be-compared-to-39nothing39-because-39typename39-is-a-nullable-type"></a>&#39; IsNot &#39;オペランド型 &#39; typename &#39; ののみと比較する (& a) #39 です。何も &#39; であるため &#39; typename &#39;null 許容型は、します。
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

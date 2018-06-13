---
title: Null 許容型の推論はこのコンテキストではサポートされていません
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: ea531c7be676e940a263b019a66cc80cf280a772
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593192"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a>Null 許容型の推論はこのコンテキストではサポートされていません
値の型と構造体宣言できます null 値を許容します。  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 ただし、型の推定と組み合わせて、null 許容型の宣言を使用することはできません。 次の例では、このエラーが発生します。  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 **エラー ID:** BC36629  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   使用して、`As`句を null 値許容と変数を宣言します。  
  
## <a name="see-also"></a>関連項目  
 [null 許容値型](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [ローカル型の推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)

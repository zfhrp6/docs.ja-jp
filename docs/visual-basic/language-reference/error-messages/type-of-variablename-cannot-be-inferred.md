---
title: 入力&#39; &lt;variablename&gt; &#39;ループの境界とステップ変数が同じ型に変換されないために、推論できません
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: d6fdd9445b5336773d150c643c7bf1ca58a0c87a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597153"
---
# <a name="type-of-39ltvariablenamegt39-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>入力&#39; &lt;variablename&gt; &#39;ループの境界とステップ変数が同じ型に変換されないために、推論できません
記述した、`For...Next`ループをコンパイラを推論できません for loop コントロール変数のデータ型は次の条件に当てはまるため。  
  
-   ループ コントロール変数のデータ型が `As` 句で指定されていません。  
  
-   ループ境界とステップ変数に少なくとも 2 つのデータ型が含まれています。  
  
-   データ型の間で変換する標準変換が存在しません。  
  
 したがって、コンパイラは、ループ コントロール変数のデータ型を推論できません。  
  
 次の例では、ステップの変数は文字であり、ループの境界は、両方の整数。 文字および整数間の標準変換がないため、このエラーは報告されます。  
  
```vb  
Dim stepVar = "1"c  
Dim m = 0  
Dim n = 20  
  
' Not valid.  
' For i = 1 To 10 Step stepVar  
    ' Loop processing  
' Next  
```  
  
 **エラー ID:** BC30982  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   少なくとも 1 つが、他のユーザーに拡大変換する型であるために、ループの境界と必要に応じて、ステップの変数の型を変更します。 上記の例では、変更の種類`stepVar`に`Integer`です。  
  
    ```  
    Dim stepVar = 1  
    ```  
  
     または  
  
    ```  
    Dim stepVar As Integer = 1  
    ```  
  
-   ループの境界とステップ変数を適切な型に変換するのにには、明示的な変換関数を使用します。 前の例では、適用、`Val`関数`stepVar`です。  
  
    ```  
    For i = 1 To 10 Step Val(stepVar)  
        ' Loop processing  
    Next  
    ```  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>  
 [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [暗黙の型変換と明示的な型変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [ローカル型の推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Option Infer ステートメント](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)

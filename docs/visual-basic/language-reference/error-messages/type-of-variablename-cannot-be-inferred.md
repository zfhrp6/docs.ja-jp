---
title: "Type of &#39;&lt;variablename&gt;&#39; cannot be inferred because the loop bounds and the step variable do not widen to the same type | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30982"
  - "vbc30982"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30982"
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 30
---
# Type of &#39;&lt;variablename&gt;&#39; cannot be inferred because the loop bounds and the step variable do not widen to the same type
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`For...Next` ループを記述しましたが、次の条件が満たされているため、コンパイラはそのループの中でループ制御変数のデータ型を推論できません。  
  
-   ループ コントロール変数のデータ型が `As` 句で指定されていません。  
  
-   ループ境界とステップ変数に少なくとも 2 つのデータ型が含まれています。  
  
-   標準的なデータ型変換が存在しません。  
  
 したがって、コンパイラはループ コントロール変数のデータ型を推論できません。  
  
 以下の例では、ステップ変数が文字、両方のループ境界が整数になっています。  文字と整数の間には標準的な変換がないので、このエラーが生成されます。  
  
```vb#  
Dim stepVar = "1"c  
Dim m = 0  
Dim n = 20  
  
' Not valid.  
' For i = 1 To 10 Step stepVar  
    ' Loop processing  
' Next  
```  
  
 **エラー ID:** BC30982  
  
### このエラーを解決するには  
  
-   必要に応じてループ境界とステップ変数の型を変更し、少なくともいずれか 1 つの型が、他の型から見て拡大変換に相当する型になるようにします。  上の例では、`stepVar` の型を `Integer` に変換します。  
  
    ```  
    Dim stepVar = 1  
    ```  
  
     または  
  
    ```  
    Dim stepVar As Integer = 1  
    ```  
  
-   明示的な変換関数を使用して、ループ境界とステップ変数を適切な型に変換します。  上の例では、`Val` 関数を `stepVar` に適用します。  
  
    ```  
    For i = 1 To 10 Step Val(stepVar)  
        ' Loop processing  
    Next  
    ```  
  
## 参照  
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>   
 [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
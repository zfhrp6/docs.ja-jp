---
title: "Lambda expressions are not valid in the first expression of a &#39;Select Case&#39; statement | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36635"
  - "vbc36635"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36635"
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Lambda expressions are not valid in the first expression of a &#39;Select Case&#39; statement
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`Select Case` ステートメントのテスト式としてラムダ式を使用することはできません。  ラムダ式の定義からは関数が返されますが、`Select Case` ステートメントのテスト式は基本データ型でなければなりません。  
  
 このエラーが発生するコード例を次に示します。  
  
```vb#  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 **エラー ID:** BC36635  
  
### このエラーを解決するには  
  
-   コードを調べて、`If...Then...Else` ステートメントなどの別の条件構造を利用できるかどうかを確認します。  
  
-   次のコードに示すように、関数を呼び出そうとした可能性があります。  
  
    ```vb#  
    Dim num? As Integer  
    Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
        ' List of the cases  
    End Select  
    ```  
  
## 参照  
 [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md)
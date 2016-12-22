---
title: "First operand in a binary &#39;If&#39; expression must be nullable or a reference type | Microsoft Docs"
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
  - "bc33107"
  - "vbc33107"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC33107"
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# First operand in a binary &#39;If&#39; expression must be nullable or a reference type
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`If` 式は、2 つまたは 3 つの引数を受け取ることができます。  2 つの引数を送る場合は、最初の引数が参照型または Null 許容型である必要があります。  1 番目の引数が `Nothing` 以外であると評価されると、その値が返されます。  1 番目の引数が `Nothing` と評価されると、2 番目の引数が評価され、その値が返されます。  
  
 たとえば、次のコード例には、2 つの `If` 式が含まれています。1 つ目の式には 3 つの引数が使用され、次の式には 2 つの引数が使用されています。  この式は、計算後、同じ値を返します。  
  
```vb#  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 次の式はエラーになります。  
  
```vb#  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 **Error ID:** BC33107  
  
### このエラーを解決するには  
  
-   最初の引数を Null 許容型または参照型になるようにコードを変更できない場合、3 つの引数を持つ `If` 式か `If...Then...Else` ステートメントに変換します。  
  
    ```vb#  
    Console.WriteLine(If(choice1 < choice2, 1, 2))  
    Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
    ```  
  
## 参照  
 [If Operator](../../../visual-basic/language-reference/operators/if-operator.md)   
 [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [Nullable Value Types](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
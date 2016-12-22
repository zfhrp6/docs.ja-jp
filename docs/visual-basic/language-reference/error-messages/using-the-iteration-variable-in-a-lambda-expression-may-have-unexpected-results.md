---
title: "Using the iteration variable in a lambda expression may have unexpected results | Microsoft Docs"
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
  - "vbc42324"
  - "bc42324"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42324"
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Using the iteration variable in a lambda expression may have unexpected results
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

ラムダ式内で繰り返し変数を使用すると、予期しない結果が発生する可能性があります。代わりに、ループ内にローカル変数を作成して繰り返し変数の値を割り当ててください。  
  
 この警告は、ループ内で宣言されたラムダ式内でループ繰り返し変数が使用されている場合に発生します。  たとえば、次の例では警告が発生します。  
  
```vb#  
For i As Integer = 1 To 10  
    ' The warning is given for the use of i.  
    Dim exampleFunc As Func(Of Integer) = Function() i  
Next  
```  
  
 次の例では、発生する可能性のある予期しない結果を示します。  
  
```vb#  
Module Module1  
    Sub Main()  
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}  
  
        For i As Integer = 0 To 4  
            array1(i) = Function() i  
        Next  
  
        For Each funcElement In array1  
            System.Console.WriteLine(funcElement())  
        Next  
  
    End Sub  
End Module  
```  
  
 `For` ループがラムダ式の配列を作成し、そのそれぞれが、ループ繰り返し変数 `i` の値を返します。  ラムダ式が `For Each` ループで評価されるとき、`For` ループ内の `i` の連続する値として 0、1、2、3、および 4 が表示されるものと思われますが、  `i` の最終値が 5 回表示されています。  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 既定では、このメッセージは警告です。  警告を表示しない方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](/visual-studio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **Error ID:** BC42324  
  
### このエラーを解決するには  
  
-   繰り返し変数の値をローカル変数に割り当てて、そのローカル変数をラムダ式で使用します。  
  
    ```vb#  
    Module Module1  
        Sub Main()  
            Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}  
  
            For i As Integer = 0 To 4  
                Dim j = i  
                array1(i) = Function() j  
            Next  
  
            For Each funcElement In array1  
                System.Console.WriteLine(funcElement())  
            Next  
  
        End Sub  
    End Module  
    ```  
  
## 参照  
 [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
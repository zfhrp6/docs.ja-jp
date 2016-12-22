---
title: "Methods of &#39;System.Nullable(Of T)&#39; cannot be used as operands of the &#39;AddressOf&#39; operator | Microsoft Docs"
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
  - "vbc32126"
  - "bc32126"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32126"
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Methods of &#39;System.Nullable(Of T)&#39; cannot be used as operands of the &#39;AddressOf&#39; operator
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

ステートメントに `AddressOf` 演算子が使用され、<xref:System.Nullable%601> 構造体のプロシージャを表すオペランドが指定されています。  
  
 **Error ID:** BC32126  
  
### このエラーを解決するには  
  
-   `AddressOf` 句のプロシージャ名を、<xref:System.Nullable%601> のメンバーでないオペランドで置き換えます。  
  
-   使用する <xref:System.Nullable%601> のメソッドをラップするクラスを記述します。  以下の例では、`NullableWrapper` クラスで `GetValueOrDefault` という新しいメソッドを定義します。  この新しいメソッドは <xref:System.Nullable%601> のメンバーではないので、Null 許容型のインスタンスである `nullInstance` に適用して、`AddressOf` の引数を生成できます。  
  
    ```vb#  
    Module Module1  
  
        Delegate Function Deleg() As Integer  
  
        Sub Main()  
            Dim nullInstance As New Nullable(Of Integer)(1)  
  
            Dim del As Deleg  
  
            ' GetValueOrDefault is a method of the Nullable generic  
            ' type. It cannot be used as an operand of AddressOf.  
            ' del = AddressOf nullInstance.GetValueOrDefault  
  
            ' The following line uses the GetValueOrDefault method  
            ' defined in the NullableWrapper class.  
            del = AddressOf (New NullableWrapper(  
                Of Integer)(nullInstance)).GetValueOrDefault  
  
            Console.WriteLine(del.Invoke())  
        End Sub  
  
        Class NullableWrapper(Of T As Structure)  
            Private m_Value As Nullable(Of T)  
  
            Sub New(ByVal Value As Nullable(Of T))  
                m_Value = Value  
            End Sub  
  
            Public Function GetValueOrDefault() As T  
                Return m_Value.Value  
            End Function  
        End Class  
    End Module  
    ```  
  
## 参照  
 <xref:System.Nullable%601>   
 [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Nullable Value Types](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)   
 [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
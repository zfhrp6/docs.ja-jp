---
title: "変数 &quot;&lt;variablename&gt;&quot; の型は、外側のスコープ内のフィールドにバインドされているため、推論できません。 | Microsoft Docs"
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
  - "vbc42110"
  - "bc42110"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42110"
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
caps.latest.revision: 33
caps.handback.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 変数 &quot;&lt;variablename&gt;&quot; の型は、外側のスコープ内のフィールドにバインドされているため、推論できません。
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

変数 "\<variablename\>" の型は、外側のスコープ内のフィールドにバインドされているため、推論できません。"\<variablename\>" の名前を変更するか、完全修飾名 \(例: "Me.variablename" や "MyBase.variablename"\) を使用してください。  
  
 コードのループ制御変数は、クラスまたは他の外側のスコープ内のフィールドと同じ名前を持っています。  制御変数は、`As` 句なしで使用されるため、外側のスコープ内のフィールドにバインドされ、コンパイラがこれに対して新しい変数を作成したり、その型を推論したりすることはありません。  
  
 次の例では、`Index` \(`For` ステートメントの制御変数\) が、`Customer` クラスの `Index` フィールドにバインドされています。  コンパイラが制御変数 `Index` に対して新しい変数を作成したり、その型を推論したりすることはありません。  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
    ' The following line will raise this warning.  
        For Index = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
  
```  
  
 既定では、このメッセージは警告です。  警告を表示しない方法や、警告をエラーとして扱う方法については、「[Visual Basic での警告の構成](/visual-studio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **Error ID:** BC42110  
  
### この警告に対処するには  
  
-   ループ制御変数の名前を、クラスのフィールドの名前とは異なる識別子に変更して、この変数をローカルにします。  
  
    ```  
    For I = 1 To 10  
    ```  
  
-   変数名の前に `Me.` を付けることにより、クラス フィールドにループ制御変数がバインドされていることを明確にします。  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
-   ローカル型の推定ではなく `As` 句を使用して、ループ制御変数に型を指定します。  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## 使用例  
 次のコードは、上の例に最初の修正を行ったものです。  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
        For I = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
## 参照  
 [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [How to: Refer to the Current Instance of an Object](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)   
 [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Me, My, MyBase, and MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
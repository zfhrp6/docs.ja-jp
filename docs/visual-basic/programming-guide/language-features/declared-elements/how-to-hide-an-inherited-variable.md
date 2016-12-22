---
title: "How to: Hide an Inherited Variable (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "qualification, of element names"
  - "element names, qualification"
  - "references, declared elements"
  - "declaration statements, declared elements"
  - "referencing declared elements"
  - "declared elements, referencing"
  - "declared elements, about declared elements"
  - "variables [Visual Basic], hiding inherited"
ms.assetid: 765728d9-7351-4a30-999d-b5f34f024412
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Hide an Inherited Variable (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

派生クラスは、基本クラスのすべての定義を継承します。  基本クラスの要素として同じ名前を使用して変数を定義する場合、派生クラスに変数を定義する際に、基本クラスの要素を非表示にしたり、*シャドウ*にできます。  これを行う場合、シャドウ機構を明示的にバイパスしない限り、派生クラス内のコードはその変数にアクセスします。  
  
 継承された変数を非表示にするもう 1 つの理由は、基本クラスのリビジョン変更から保護することです。  継承している要素を変更するように、基本クラスを変えることもできます。  このような変更があった場合、`Shadows` 修飾子は、派生クラスからの参照を、基本クラスの要素に解決するのではなく、継承された変数に解決します。  
  
### 継承された変数を隠すには  
  
1.  隠す変数がクラス レベル \(プロシージャの外\) で宣言されていることを確認します。  そうでない場合、これを隠す必要がありません。  
  
2.  派生クラス内で、変数を宣言する [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) を記述します。  継承された変数の名前と同じ名前を使用します。  
  
3.  宣言には [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) キーワードを含めます。  
  
     派生クラスのコードによって変数名が参照されているとき、変数への参照をコンパイラが解決します。  
  
     継承された変数のシャドウの例を次に示します。  
  
    ```  
    Public Class shadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class shadowDerivedClass  
        Inherits shadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub showStrings()  
            Dim s As String = "Unqualified shadowString: " & shadowString &  
                vbCrLf & "MyBase.shadowString: " & MyBase.shadowString  
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     上の例では、基本クラスで `shadowString` 変数を宣言し、派生クラスでシャドウしています。  名前 `shadowString` が修飾されていない場合、派生クラスの `showStrings` プロシージャには、文字列のシャドウ バージョンが表示されます。  次に、`shadowString` が `MyBase` キーワードで修飾されている場合には、シャドウされたバージョンが表示されます。  
  
## 信頼性の高いプログラミング  
 シャドウにより、同じ名前の複数の変数が追加されます。  コード ステートメントによって変数名が参照されているとき、コンパイラによって参照が解決されるバージョンは、コード ステートメントの位置および修飾する文字列の存在などの要因より決まります。  これにより、意図しないバージョンのシャドウされた変数を参照するリスクが増加する可能性があります。  シャドウされた変数へのすべての参照を完全修飾することによって、このリスクを低減させることができます。  
  
## 参照  
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)   
 [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)   
 [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)   
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
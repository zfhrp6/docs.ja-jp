---
title: "How to: Hide a Variable with the Same Name as Your Variable (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "qualification, of element names"
  - "declarations, elements"
  - "element names, qualification"
  - "references, declared elements"
  - "declaration statements, declared elements"
  - "declaring elements"
  - "referencing declared elements"
  - "declared elements, referencing"
  - "declared elements, about declared elements"
ms.assetid: e39c0752-f19f-4d2e-a453-00df1b5fc7ee
caps.latest.revision: 25
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 25
---
# How to: Hide a Variable with the Same Name as Your Variable (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

*シャドウ*することで、変数を隠すことができます。シャドウとは、同じ名前の変数を使用して、変数を再定義することです。  以下のいずれかの方法で、隠す変数をシャドウできます。  
  
-   **スコープによるシャドウ。**隠す変数が含まれる領域のサブ領域内で再宣言することにより、スコープによるシャドウを行うことができます。  
  
-   **継承によるシャドウ。**隠す変数がクラス レベルで定義されている場合、派生クラスで [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) キーワードを使用して再宣言することにより、継承によるシャドウを行うことができます。  
  
## 変数を隠す 2 つの方法  
  
#### スコープによるシャドウを行って、変数を隠すには  
  
1.  隠す変数を定義する領域を決め、変数を使用して再定義するサブ領域を決めます。  
  
    |変数の領域|再定義が許可されたサブ領域|  
    |-----------|-------------------|  
    |Module|モジュール内のクラス|  
    |Class|クラス内のサブクラス<br /><br /> クラス内のプロシージャ|  
  
     たとえば、`If`...`End If` 構造または `For` ループ内など、プロシージャ内のブロックにあるプロシージャ変数は再定義できません。  
  
2.  サブ領域が既に存在していない場合は、作成します。  
  
3.  サブ領域内で、変数をシャドウする [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) 宣言を記述します。  
  
     サブ領域内のコードによって変数名が参照されているとき、変数のシャドウへの参照をコンパイラが解決します。  
  
     スコープによるシャドウ、およびシャドウを使用しない参照の例を次に示します。  
  
    ```  
    Module shadowByScope  
        ' The following statement declares num as a module-level variable.  
        Public num As Integer  
        Sub show()  
            ' The following statement declares num as a local variable.  
            Dim num As Integer  
            ' The following statement sets the value of the local variable.  
            num = 2  
            ' The following statement displays the module-level variable.  
            MsgBox(CStr(shadowByScope.num))  
        End Sub  
        Sub useModuleLevelNum()  
            ' The following statement sets the value of the module-level variable.  
            num = 1  
            show()  
        End Sub  
    End Module  
    ```  
  
     上の例では、モジュール レベルおよびプロシージャ レベル \(プロシージャ `show` 内\) の両方で、`num` 変数が宣言されています。  `show` 内では、ローカル変数 `num` がモジュール レベルの変数 `num` をシャドウします。したがって、ローカル変数が 2 に設定されます。  一方、`useModuleLevelNum` プロシージャ内の `num` をシャドウするローカル変数はありません。  したがって、`useModuleLevelNum` によって、モジュール レベルの変数の値が 1 に設定されます。  
  
     `show` 内部の `MsgBox` 呼び出しは、モジュール名を使用して `num` を修飾することにより、シャドウ機構を使用しないようにします。  したがって、ローカル変数ではなく、モジュール レベルの変数が表示されます。  
  
#### 継承によるシャドウを行って、変数を隠すには  
  
1.  隠す変数が、クラスおよびクラス レベル \(プロシージャの外部\) で宣言されているようにします。  そうしないと、継承によるシャドウを行うことができません。  
  
2.  変数のクラスから派生したクラスが既に存在しない場合、定義します。  
  
3.  派生クラスの内部で、変数を宣言する `Dim` ステートメントを記述します。  宣言には [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) キーワードを含めます。  
  
     派生クラスのコードによって変数名が参照されているとき、変数への参照をコンパイラが解決します。  
  
     継承によるシャドウの例を次に示します。  これにより 2 つの参照が作成されます。1 つはシャドウ変数にアクセスする参照、もう 1 つはシャドウを使用しない参照です。  
  
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
 [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)   
 [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)   
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
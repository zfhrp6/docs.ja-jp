---
title: "How to: Access a Variable Hidden by a Derived Class (Visual Basic) | Microsoft Docs"
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
  - "base classes, accessing elements"
  - "element names, qualification"
  - "references, declared elements"
  - "declared elements, referencing"
  - "variables [Visual Basic], accessing hidden"
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# How to: Access a Variable Hidden by a Derived Class (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

派生クラスのコードが変数にアクセスする場合、通常はコンパイラによって、アクセス可能な最も近いバージョンに参照が解決されます。つまり、アクセスするクラスから、最小の派生ステップを戻ってアクセスできるバージョンに参照が解決されます。  変数が派生クラスで定義されている場合、通常、コードはその定義にアクセスします。  
  
 派生クラスの変数によって基本クラスの変数がシャドウされる場合、基本クラスのバージョンは非表示になります。  しかし、`MyBase` キーワードで修飾することにより、基本クラスの変数にアクセスできます。  
  
### 派生クラスによって非表示になっている基本クラスの変数にアクセスするには  
  
-   式または代入ステートメントでは、変数名の前に `MyBase` キーワードおよびピリオド \(`.`\) を記述します。  
  
     コンパイラによって、変数の基本クラスのバージョンへの参照が解決されます。  
  
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
  
     上の例では、基本クラスで `shadowString` 変数を宣言し、派生クラスでシャドウしています。  名前 `shadowString` が修飾されていない場合、派生クラスの `showStrings` プロシージャには、文字列のシャドウ バージョンが表示されます。  次に、`shadowString` が `MyBase`  キーワードで修飾されたときに、シャドウされた文字列が表示されます。  
  
## 信頼性の高いプログラミング  
 シャドウされた変数へのすべての参照を完全に修飾することで、シャドウされた変数の意図しないバージョンを参照するリスクを軽減できます。  シャドウにより、同じ名前の複数の変数が追加されます。  コード ステートメントによって変数名が参照されているとき、コンパイラによって参照が解決されるバージョンは、コード ステートメントの位置および修飾する文字列の存在などの要因より決まります。  これにより、誤った変数を参照するリスクが増加する可能性があります。  
  
## 参照  
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)   
 [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)   
 [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)   
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
---
title: "Shadowing in Visual Basic | Microsoft Docs"
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
  - "inheritance, shadowing"
  - "overriding, and shadowing"
  - "shadowing"
  - "duplicate names"
  - "shadowing, by inheritance"
  - "declared elements, referencing"
  - "shadowing, by scope"
  - "declared elements, hiding"
  - "naming conflicts, shadowing"
  - "declared elements, shadowing"
  - "shadowing, and overriding"
  - "scope, shadowing"
  - "Shadows keyword, about"
  - "objects [Visual Basic], names"
  - "names, shadowing"
ms.assetid: 54bb4c25-12c4-4181-b4a0-93546053964e
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 24
---
# Shadowing in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

2 つのプログラミング要素が同じ名前を持つときに、一方の要素によってもう一方の要素が隠されることがあります。これを*シャドウ*と呼びます。  そのような場合、シャドウで隠された要素は参照できません。要素の名前をコードで使用すると、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コンパイラはそれをシャドウする要素 \(隠されていない方の要素\) に解決します。  
  
## 目的  
 シャドウの主な目的は、派生クラスのメンバー定義を保護することにあります。  基本クラスは、既に定義されている要素と同じ名前の要素を作成するように変更される可能性もあります。  このような場合、`Shadows` 修飾子を指定してあると、派生クラスを通じた参照は新しい基本クラスの要素に解決されず、派生クラスで定義したメンバーに解決されます。  
  
## シャドウの種類  
 要素が他の要素をシャドウするのは、次の 2 つの場合です。  シャドウする方の要素が、シャドウされる要素を含む領域のサブ領域の内部で宣言されていると、*スコープによって*シャドウが発生します。  または、派生クラスが基本クラスのメンバーを再定義すると、*継承によって*シャドウが発生します。  
  
### スコープによるシャドウ  
 同じモジュール、クラス、または構造体の中に、名前が同じでスコープが異なるプログラミング要素を含めることができます。  このように宣言した 2 つの要素によって共有されている名前をコードが参照すると、スコープが狭い方の要素がもう一方の要素をシャドウします \(最も狭いのはブロック スコープです\)。  
  
 たとえば、モジュールで `temp` という名前の `Public` 変数を定義し、そのモジュール内のプロシージャで同じ `temp` という名前のローカル変数を宣言したとします。  このプロシージャ内で `temp` を参照するとローカル変数へのアクセスとなり、プロシージャの外で `temp` を参照すると `Public` 変数へのアクセスとなります。  この場合、プロシージャの変数 `temp` がモジュールの変数 `temp` をシャドウしています。  
  
 次の図は、同じ `temp` という名前を持つ 2 つの変数を示しています。  ローカル変数 `temp` に、この変数が宣言されているプロシージャ `p` 内でアクセスした場合、メンバー変数 `temp` がシャドウされます。  ただし、`MyClass` キーワードを使用すると、シャドウをバイパスしてメンバー変数にアクセスできます。  
  
 ![スコープによるシャドウのグラフィック ダイアグラム](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowscope.gif "ShadowScope")  
スコープによるシャドウ  
  
 スコープによるシャドウの例については、「[How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)」を参照してください。  
  
### 継承によるシャドウ  
 基本クラスから継承したプログラミング要素を派生クラスで再定義すると、再定義した要素が元の要素をシャドウします。  任意の型の宣言された要素 \(またはオーバーロードされた要素の集合\) を他の任意の型でシャドウできます。  たとえば、`Integer` 型の変数が `Function` プロシージャをシャドウできます。  プロシージャを他のプロシージャでシャドウすると、異なるパラメーター リストおよび異なる戻り値の型を使用できます。  
  
 次の図は、基本クラス `b` と、`b` を継承した派生クラス `d` を示しています。  基本クラスに `proc` という名前のプロシージャが定義してあり、派生クラスでは同じ名前の別のプロシージャでこれをシャドウしています。  最初の `Call` ステートメントは、シャドウしている派生クラスの `proc` にアクセスします。  ただし、`MyBase` キーワードを使用すると、シャドウをバイパスして、シャドウされた基本クラスのプロシージャにアクセスできます。  
  
 ![継承によるシャドウのグラフィック ダイアグラム](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowinherit.gif "ShadowInherit")  
継承によるシャドウ  
  
 継承によるシャドウの例については、「[How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)」および「[How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)」を参照してください。  
  
#### シャドウとアクセス レベル  
 派生クラスを使用しても、シャドウする要素にコードから必ずアクセスできるとは限りません。  たとえば、シャドウする要素が `Private` で宣言されている場合があります。  このような場合、シャドウは行われません。コンパイラは参照を、シャドウが行われない場合と同じ要素に解決します。  この要素は、シャドウするクラスから最小の継承ステップを戻ってアクセスできる要素です。  シャドウされる要素がプロシージャの場合、同じ名前、同じパラメーター リスト、および同じ戻り値の型を持つ最も近いアクセス可能なバージョンに参照が解決されます。  
  
 次の例は 3 つのクラスの継承階層を示します。  各クラスが `display` という `Sub` プロシージャを定義し、各派生クラスが、それぞれの基本クラスの `display` プロシージャをシャドウしています。  
  
```  
Public Class firstClass  
    Public Sub display()  
        MsgBox("This is firstClass")  
    End Sub  
End Class  
Public Class secondClass  
    Inherits firstClass  
    Private Shadows Sub display()  
        MsgBox("This is secondClass")  
    End Sub  
End Class  
Public Class thirdClass  
    Inherits secondClass  
    Public Shadows Sub display()  
        MsgBox("This is thirdClass")  
    End Sub  
End Class  
Module callDisplay  
    Dim first As New firstClass  
    Dim second As New secondClass  
    Dim third As New thirdClass  
    Public Sub callDisplayProcedures()  
        ' The following statement displays "This is firstClass".  
        first.display()  
        ' The following statement displays "This is firstClass".  
        second.display()  
        ' The following statement displays "This is thirdClass".  
        third.display()  
    End Sub  
End Module  
```  
  
 上の例では、派生クラス `secondClass` は、`Private` なプロシージャによって `display` をシャドウします。  `callDisplay` モジュールが `secondClass` の `display` を呼び出す場合、この呼び出し元のコードは `secondClass` の外側にあるため、プライベートな `display` プロシージャにアクセスできません。  シャドウは行われず、コンパイラは、参照を基本クラスの `display` プロシージャに解決します。  
  
 一方、さらなる派生クラス `thirdClass` では `display` が `Public` として宣言されているため、`callDisplay` 内のコードからこれにアクセスできます。  
  
## シャドウとオーバーライド  
 シャドウをオーバーライドと混同しないでください。  どちらも、派生クラスが基本クラスから継承するときに使用され、宣言された要素を他の要素で再定義します。  しかし、シャドウとオーバーライドの間には大きな違いがあります。  比較については、「[Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)」を参照してください。  
  
## シャドウとオーバーロード  
 基本クラスの同じ要素を、派生クラスの複数の要素でシャドウする場合、シャドウする要素はその要素のオーバーロードされたバージョンになります。  詳細については、「[Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)」を参照してください。  
  
## シャドウされた要素へのアクセス  
 派生クラスから要素にアクセスする場合は、通常、要素名を `Me` キーワードで修飾することによって、派生クラスの現在のインスタンスを通じてアクセスします。  派生クラスが基本クラスの要素をシャドウしている場合、基本クラスの要素にアクセスするには、要素名を `MyBase` キーワードで修飾します。  
  
 シャドウされた要素にアクセスする方法の例については、「[How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)」を参照してください。  
  
### オブジェクト変数の宣言  
 派生クラスがシャドウする要素にアクセスするか、シャドウされる要素にアクセスするかは、オブジェクト変数を作成する方法によっても変わります。  次の例では、派生クラスから 2 つのオブジェクトを作成していますが、1 つのオブジェクトは基本クラスとして、もう 1 つは派生クラスとして宣言しています。  
  
```  
Public Class baseCls  
    ' The following statement declares the element that is to be shadowed.  
    Public z As Integer = 100  
End Class  
Public Class dervCls  
    Inherits baseCls  
    ' The following statement declares the shadowing element.  
    Public Shadows z As String = "*"  
End Class  
Public Class useClasses  
    ' The following statement creates the object declared as the base class.  
    Dim basObj As baseCls = New dervCls()  
    ' Note that dervCls widens to its base class baseCls.  
    ' The following statement creates the object declared as the derived class.  
    Dim derObj As dervCls = New dervCls()  
    Public Sub showZ()   
    ' The following statement outputs 100 (the shadowed element).  
        MsgBox("Accessed through base class: " & basObj.z)  
    ' The following statement outputs "*" (the shadowing element).  
        MsgBox("Accessed through derived class: " & derObj.z)  
    End Sub  
End Class  
```  
  
 上の例では、変数 `basObj` は基本クラスとして宣言されています。  この変数に `dervCls` オブジェクトを代入することは、拡大変換となるため有効です。  ただし、基本クラスは派生クラス内のシャドウする変数 `z` にアクセスできないため、コンパイラは `basObj.z` を元の基本クラス値に解決します。  
  
## 参照  
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
---
title: '方法: 自分で宣言した変数と同じ名前の変数を隠す (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- declarations [Visual Basic], elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
ms.assetid: e39c0752-f19f-4d2e-a453-00df1b5fc7ee
ms.openlocfilehash: a7ebc4eb44592800decd5ef943750f0cd845afb4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653119"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a>方法: 自分で宣言した変数と同じ名前の変数を隠す (Visual Basic)
変数を非表示にすることができます*シャドウ*は、これによって、同じ名前の変数で再定義します。 2 つの方法で非表示に変数をシャドウすることができます。  
  
-   **スコープによるシャドウします。** その操作は、非表示に変数を含む領域のサブ領域内で再宣言することによってスコープによるシャドウできます。  
  
-   **継承によるシャドウします。** 非表示にする、変数がクラス レベルで定義されている場合することができます、継承によるシャドウで再宣言することによって、 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)派生クラス内のキーワードです。  
  
## <a name="two-ways-to-hide-a-variable"></a>2 つの方法で変数を隠す  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a>スコープによるシャドウで変数を非表示にするには  
  
1.  を非表示にする変数の定義のリージョンを特定し、変数を使用してを再定義するでサブ地域を決定します。  
  
    |変数の領域|再定義が許容されるサブ地域|  
    |-----------------------|-------------------------------------------|  
    |Module|モジュール内のクラス|  
    |クラス|クラス内のサブクラス<br /><br /> クラス内の手順|  
  
     再定義できませんそのプロシージャ内のブロックでプロシージャの変数などの`If`しています.`End If`構築または`For`ループします。  
  
2.  既に存在しない場合は、サブ領域を作成します。  
  
3.  その地区内では、書き込み、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)シャドウ変数を宣言します。  
  
     サブ領域内のコードは、変数名が参照されているとき、コンパイラは変数のシャドウへの参照を解決します。  
  
     次の例では、シャドウ参照と同様に、スコープによるシャドウを示します。  
  
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
  
     前の例は、変数を宣言して`num`モジュール レベルとプロシージャ レベルの両方 (の手順で`show`)。 ローカル変数`num`モジュール レベル変数をシャドウ`num`内`show`でローカル変数が 2 に設定されているため、します。 ただし、シャドウをローカル変数がない`num`で、`useModuleLevelNum`プロシージャです。 したがって、`useModuleLevelNum`モジュール レベル変数の値を 1 に設定します。  
  
     `MsgBox`内で呼び出す`show`修飾することにより、シャドウ機構をバイパスする`num`モジュール名を使用します。 そのため、ローカル変数の代わりに、モジュール レベル変数を表示します。  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a>継承によるシャドウで変数を非表示にするには  
  
1.  必ず、クラスでは、および (プロシージャ) の外側のクラス レベルで非表示にする、変数が宣言されてください。 それ以外の場合継承によるシャドウすることはできません。  
  
2.  既に存在しない場合、変数のクラスから派生するクラスを定義します。  
  
3.  派生クラス内の書き込み、`Dim`変数を宣言するステートメント。 含める、 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)宣言でキーワード。  
  
     派生クラス内のコードは、変数名が参照されているとき、コンパイラは、変数への参照を解決します。  
  
     次の例では、継承によるシャドウを示します。 これにより、2 つの参照変数のシャドウにアクセスして、シャドウをバイパスできるようになります。  
  
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
  
     前の例は、変数を宣言`shadowString`基底クラスと派生クラスでシャドウできます。 プロシージャ`showStrings`シャドウのバージョンの文字列が表示されます、派生クラスでときに名前`shadowString`が修飾されていません。 影付きのバージョンを次に、表示と`shadowString`で修飾されて、`MyBase`キーワード。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 シャドウ処理には、1 つ以上のバージョンの同じ名前の変数が導入されています。 コードのステートメントは、変数名が参照されているときに、コンパイラが参照を解決するバージョンは、コードのステートメントの場所が存在している修飾文字列のなどの要因によって異なります。 これにより、意図しないシャドウされた変数のバージョンを参照するリスクが増加することができます。 シャドウされた変数へのすべての参照を完全に修飾することによってそのリスクを減らすことができます。  
  
## <a name="see-also"></a>関連項目  
 [宣言された要素の参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Visual Basic におけるシャドウ](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [シャドウとオーバーライドの違い](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [方法: 継承された変数を隠す](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [方法: 派生クラスによって非表示になっている変数にアクセスする](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [継承の基本](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)

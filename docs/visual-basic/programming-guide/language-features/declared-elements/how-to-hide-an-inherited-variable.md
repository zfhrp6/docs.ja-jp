---
title: '方法: 継承された変数を隠す (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
- variables [Visual Basic], hiding inherited
ms.assetid: 765728d9-7351-4a30-999d-b5f34f024412
ms.openlocfilehash: c59fdd8c6c6d2444b8d687c78c61f4e0d4bf9a52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649140"
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a>方法: 継承された変数を隠す (Visual Basic)
派生クラスでは、その基本クラスのすべての定義を継承します。 基本クラスの要素として同じ名前を使用して変数を定義する場合は、非表示にできます、または*シャドウ*、派生クラスで変数を定義するときにその基本クラスの要素。 これを行うと、派生クラス内のコードにアクセスする場合、変数シャドウ機構が明示的にバイパスされる場合を除き、します。  
  
 継承された変数を非表示にすることができます別の理由は、基本クラスのリビジョンから保護するためです。 基本クラスには、継承している要素を変更する変更を行うこともします。 この場合、`Shadows`修飾子は、基底クラス要素の代わりに、変数を解決する派生クラスからの参照。  
  
### <a name="to-hide-an-inherited-variable"></a>継承された変数を非表示にするには  
  
1.  (プロシージャ) の外側のクラス レベルで非表示にする、変数が宣言されていることを確認します。 それ以外の場合、非表示にする必要はありません。  
  
2.  クラス内で、派生書き込み、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)変数を宣言します。 継承された変数のと同じ名前を使用します。  
  
3.  含める、 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)宣言でキーワード。  
  
     派生クラス内のコードは、変数名が参照されているとき、コンパイラは、変数への参照を解決します。  
  
     次の例では、継承された変数のシャドウを示します。  
  
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
 [方法: 自分で宣言した変数と同じ名前の変数を隠す](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [方法: 派生クラスによって非表示になっている変数にアクセスする](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [継承の基本](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)

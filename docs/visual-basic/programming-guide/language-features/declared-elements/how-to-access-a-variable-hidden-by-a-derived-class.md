---
title: "方法: 派生クラスによって非表示になっている変数にアクセスする (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f94e45fcb0a26b0d59789e101c37aceba219250
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a>方法: 派生クラスによって非表示になっている変数にアクセスする (Visual Basic)
派生クラス内のコードは、変数にアクセスするときに、コンパイラ通常参照が解決を最も近いアクセス可能なバージョンにアクセス可能なバージョンは、少ない継承旧バージョンとのステップにアクセスするクラス。 変数が派生クラスで定義されている場合、コードでその定義が正常にアクセスします。  
  
 派生クラスの変数が、基底クラス内の変数をシャドウする場合は、基底クラスのバージョンが表示されません。 ただしで修飾基底クラスの変数にアクセスすることができます、`MyBase`キーワード。  
  
### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a>派生クラスによって非表示に基本クラスの変数にアクセスするには  
  
-   式または代入ステートメントの場合は、変数名の前に、`MyBase`キーワードとピリオド (`.`)。  
  
     コンパイラは、変数の基本クラスのバージョンへの参照を解決します。  
  
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
 シャドウされた変数の意図しないバージョンを参照するリスクを低減するためには、シャドウされた変数へのすべての参照を完全に修飾することができます。 シャドウ処理には、1 つ以上のバージョンの同じ名前の変数が導入されています。 コードのステートメントは、変数名が参照されているときに、コンパイラが参照を解決するバージョンは、コードのステートメントの場所が存在している修飾文字列のなどの要因によって異なります。 これにより、間違ったバージョンの変数を参照するリスクが増加することができます。  
  
## <a name="see-also"></a>関連項目  
 [宣言された要素の参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Visual Basic におけるシャドウ](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [シャドウとオーバーライドの違い](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [方法: 自分で宣言した変数と同じ名前の変数を隠す](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [方法: 継承された変数を隠す](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [継承の基本](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)

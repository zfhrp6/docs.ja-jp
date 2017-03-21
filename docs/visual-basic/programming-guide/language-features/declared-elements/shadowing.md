---
title: "Visual Basic におけるシャドウ |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- inheritance, shadowing
- overriding, and shadowing
- shadowing
- duplicate names
- shadowing, by inheritance
- declared elements, referencing
- shadowing, by scope
- declared elements, hiding
- naming conflicts, shadowing
- declared elements, shadowing
- shadowing, and overriding
- scope, shadowing
- Shadows keyword, about
- objects [Visual Basic], names
- names, shadowing
ms.assetid: 54bb4c25-12c4-4181-b4a0-93546053964e
caps.latest.revision: 24
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5f4053de05f0a7a42fccdade1714e08f8eb172e6
ms.lasthandoff: 03/13/2017

---
# <a name="shadowing-in-visual-basic"></a>Visual Basic におけるシャドウ
2 つのプログラミング要素は、同じ名前を共有する場合の&1; つ非表示にできます、または*シャドウ*、もう&1; つです。 このような場合は、影付きの要素は参照できません。代わりに、コードが、要素名を使用する場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラでは、それを解決する要素。  
  
## <a name="purpose"></a>目的  
 シャドウの主な目的は、クラス メンバーの定義を保護します。 基本クラスには、既に定義されているいずれかと同じ名前の要素を作成する変更が行われること可能性があります。 このような場合、`Shadows`修飾子フォースをするメンバーに解決するのには、クラスを参照する基本クラスの新しい要素の代わりに定義された、します。  
  
## <a name="types-of-shadowing"></a>シャドウの種類  
 要素は、2 つの方法で別の要素をシャドウすることができます。 シャドウ ケースを行う影付きの要素を含む領域のサブ領域内に要素を宣言できます*スコープによる*します。 派生クラスが場合は、シャドウは、基本クラスのメンバーを再*継承によって*します。  
  
### <a name="shadowing-through-scope"></a>スコープによるシャドウ  
 プログラミングのモジュール、クラスまたは構造体に名前が同じでは異なるスコープ内の要素のことができます。 狭いスコープを持つ要素が他の要素をシャドウする&2; つの要素がこのような方法で宣言されているし、コードが共有されている名前を指す、(ブロック スコープは最も狭いです)。  
  
 たとえば、モジュールを定義できます、`Public`という名前の変数`temp`、モジュール内のプロシージャもという名前のローカル変数を宣言および`temp`です。 参照`temp`プロシージャ内からへの参照中に、ローカル変数にアクセス`temp`からプロシージャへのアクセスの外側、`Public`変数です。 この場合、プロシージャの変数`temp`モジュール変数のシャドウ`temp`します。  
  
 次の図は、2 つの変数、という名前を`temp`します。 ローカル変数`temp`メンバー変数のシャドウ`temp`独自のプロシージャ内からアクセスしたときに`p`します。 ただし、`MyClass`キーワードがシャドウをバイパスし、メンバー変数にアクセスします。  
  
 ![スコープによるシャドウのグラフィック ダイアグラム](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowscope.gif "ShadowScope")  
スコープによるシャドウ  
  
 スコープによるシャドウの例は、次を参照してください。[する方法: 変数のと同じ名前の変数を隠す](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)します。  
  
### <a name="shadowing-through-inheritance"></a>継承によるシャドウ  
 派生クラスは、基本クラスから継承したプログラミングの要素を再定義を再定義する要素は、元の要素をシャドウします。 他の種類と、宣言された要素の任意の型、または一連のオーバー ロードされた要素をシャドウすることができます。 たとえば、`Integer`変数をシャドウする、`Function`プロシージャです。 別のプロシージャを使ってプロシージャをシャドウする場合は、別のパラメーター リストと異なる戻り値の型を使用できます。  
  
 次の図は、基本クラス`b`と派生クラス`d`から継承する`b`です。 基本クラスという名前のプロシージャを定義する`proc`と派生クラスは、同じ名前の別のプロシージャでシャドウします。 最初の`Call`シャドウ ステートメントにアクセスする`proc`派生クラスにします。 ただし、`MyBase`キーワードがシャドウをバイパスし、基本クラスで影付きのプロシージャにアクセスします。  
  
 ![継承によるシャドウのグラフィック ダイアグラム](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowinherit.gif "ShadowInherit")  
継承によるシャドウ  
  
 継承によるシャドウの例は、次を参照してください。[方法:、変数と同じ名前の変数を隠す](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)と[方法:、継承された変数を非表示に](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)します。  
  
#### <a name="shadowing-and-access-level"></a>シャドウとアクセス レベル  
 要素は、常に、派生クラスを使用して、コードからアクセスできません。 たとえば、宣言することがあります`Private`します。 このような場合は、シャドウが無効化し、コンパイラは同じになります。 要素への参照を解決が行われていない場合のシャドウします。 この要素は、最小の継承はステップ後方シャドウするクラスからアクセス可能な要素です。 影付きの要素が、プロシージャの場合は、解像度は、最も近い利用可能なバージョンと同じ名前、パラメーター リストし、型を返します。  
  
 次の例では、3 つのクラスの継承階層を示します。 各クラスを定義、`Sub`プロシージャ`display`、および各派生したクラスの影、`display`基本クラスのプロシージャです。  
  
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
  
 前の例では、派生クラスで`secondClass`シャドウ`display`で、`Private`プロシージャです。 ときにモジュール`callDisplay`呼び出し`display`で`secondClass`、呼び出し元のコードが範囲外です`secondClass`ため秘密にアクセスできない`display`プロシージャです。 シャドウは行われず、およびコンパイラは、基底クラスへの参照を解決`display`プロシージャです。  
  
 ただし、さらに、派生クラス`thirdClass`を宣言`display`として`Public`ため、コードで`callDisplay`にアクセスできます。  
  
## <a name="shadowing-and-overriding"></a>シャドウとオーバーライド  
 シャドウとオーバーライドを混同しないでください。 派生クラスを基本クラスから継承し、再定義を別の&1; つの宣言された要素両方使用されます。 2 つの主な違いがあります。 比較では、次を参照してください。[シャドウの間の相違点と優先する](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)です。  
  
## <a name="shadowing-and-overloading"></a>シャドウとオーバー ロード  
 派生クラスで複数の要素と同じ基本クラスの要素をシャドウする場合は、その要素のオーバー ロードされたバージョンがシャドウする要素になります。 詳細については、次を参照してください。[プロシージャのオーバー ロード](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)します。  
  
## <a name="accessing-a-shadowed-element"></a>シャドウされた要素へのアクセス  
 派生クラスからの要素をアクセスするときに通常これを行う、派生クラスの現在のインスタンスを要素名を修飾することにより、`Me`キーワードです。 修飾基本クラスの要素にアクセスする場合は、派生クラスでは、基本クラスで要素をシャドウ、`MyBase`キーワードです。  
  
 シャドウされた要素へのアクセスの例は、次を参照してください。[方法: 派生クラスによって非表示変数にアクセス](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)します。  
  
### <a name="declaration-of-the-object-variable"></a>オブジェクト変数の宣言  
 オブジェクト変数を作成する方法と、派生クラスは、シャドウ要素または影付きの要素にアクセスするかどうかが影響ことができます。 次の例では、2 つのオブジェクトを作成、派生クラスからが、基本クラスと派生クラスとして、その他の&1; つのオブジェクトが宣言されています。  
  
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
  
 上記の例では、変数`basObj`基本クラスとして宣言します。 割り当て、`dervCls`オブジェクトをそれには、拡大変換し、ため有効です。 ただし、基本クラスがシャドウされた変数をアクセスできない`z`派生クラスでそのため、コンパイラは解決`basObj.z`値は、元の基本クラスにします。  
  
## <a name="see-also"></a>関連項目  
 [宣言された要素への参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [シャドウ](../../../../visual-basic/language-reference/modifiers/shadows.md)   
 [オーバーライド](../../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [継承の基本](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)

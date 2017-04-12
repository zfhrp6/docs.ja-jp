---
title: "制御構造 (Visual Basic) を入れ子になった |Microsoft ドキュメント"
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
- Visual Basic code, control flow
- control structures, nested
- conditional statements, nested
- statements [Visual Basic], control flow
- control flow, nested control statements
- structures, nested control
- nested control statements
ms.assetid: cf60b061-65d9-44a8-81f2-b0bdccd23a05
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 4afc0afc2ad63d03f2c4251640d3682b2b184504
ms.lasthandoff: 03/13/2017

---
# <a name="nested-control-structures-visual-basic"></a>入れ子になった制御構造 (Visual Basic)
次に例を他のコントロール ステートメント内の制御ステートメントを配置することができます、`If...Then...Else`ブロック内で、`For...Next`ループします。 制御ステートメントの中に別のコントロール ステートメントの配置はモード*入れ子になった*します。  
  
## <a name="nesting-levels"></a>入れ子のレベル  
 制御構造の[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]複数のレベルに入れ子にすることができます。 入れ子になった構造体を&1; つずつの本体をインデントして読みやすくするための一般的な方法です。 統合開発環境 (IDE) のエディターに自動的に行われます。  
  
 次の例では、プロシージャ`sumRows`マトリックスの行ごとの正の要素を一緒に追加します。  
  
```  
Public Sub sumRows(ByVal a(,) As Double, ByRef r() As Double)  
    Dim i, j As Integer  
    For i = 0 To UBound(a, 1)  
        r(i) = 0  
        For j = 0 To UBound(a, 2)  
            If a(i, j) > 0 Then  
                r(i) = r(i) + a(i, j)  
            End If  
        Next j  
    Next i  
End Sub  
```  
  
 前の例で最初の`Next`文は、内部を閉じます`For`ループし、最後`Next`ステートメントによって、外部クローズ`For`ループします。  
  
 同様に、入れ子になった`If`、ステートメント、`End If`ステートメントは、最も近い前に自動的に適用`If`ステートメントです。 入れ子になった`Do`で同様に、最も内側のループが`Loop`最も内側に一致するステートメント`Do`ステートメントです。  
  
> [!NOTE]
>  多くの制御構造のキーワードをクリックすると、すべての構造のキーワードが強調表示されます。 クリックすると、`If`で、`If...Then...Else`構築のすべてのインスタンス`If`、 `Then`、 `ElseIf`、 `Else`、および`End If`構造で強調表示されます。 前または次の強調表示されているキーワードに移動するには、ctrl キーと shift キーを押しながら下方向キーまたは ctrl キーと shift キーを押しながら上方向をキーを押します。  
  
## <a name="nesting-different-kinds-of-control-structures"></a>さまざまな種類の制御構造の入れ子  
 1 つの種類の他の種類内の制御構造の入れ子にすることができます。 次の例では、`With`ブロック内、`For Each`ループを入れ子になった`If`の内部ブロック、`With`ブロックします。  
  
```  
For Each ctl As System.Windows.Forms.Control In Me.Controls  
    With ctl  
        .BackColor = System.Drawing.Color.Yellow  
        .ForeColor = System.Drawing.Color.Black  
        If .CanFocus Then  
            .Text = "Colors changed"  
            If Not .Focus() Then  
                ' Insert code to process failed focus.  
            End If  
        End If  
    End With  
Next ctl  
```  
  
## <a name="overlapping-control-structures"></a>重複する制御構造  
 制御構造を重ねることはできません。 つまり、入れ子になった構造を完全に次の最も内側の構造内に必要です。 たとえば、次の配置は有効なため、`For`内側の前にループが終了した`With`ブロックが終了します。  
  
 ![無効な入れ子のグラフィック ダイアグラム](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")  
構造体を使用して無効な入れ子  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラはこのような重複する制御構造体し、コンパイル時エラーが通知を検出します。  
  
## <a name="see-also"></a>関連項目  
 [制御フロー](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [条件判断構造](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [ループ構造](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [その他の制御構造](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)

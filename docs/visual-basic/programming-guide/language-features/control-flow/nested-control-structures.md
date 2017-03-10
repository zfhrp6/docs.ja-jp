---
title: "Nested Control Structures (Visual Basic) | Microsoft Docs"
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
  - "Visual Basic code, control flow"
  - "control structures, nested"
  - "conditional statements, nested"
  - "statements [Visual Basic], control flow"
  - "control flow, nested control statements"
  - "structures, nested control"
  - "nested control statements"
ms.assetid: cf60b061-65d9-44a8-81f2-b0bdccd23a05
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# Nested Control Structures (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`For...Next` ループの中に `If...Then...Else` ブロックを配置するなど、制御ステートメントの中に別の制御ステートメントを配置できます。  制御ステートメントの中に別の制御ステートメントを配置することを*入れ子にする*と言います。  
  
## 入れ子のレベル  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] には、制御構造を入れ子にするときのレベルに制限はありません。  構造を入れ子にする場合は、コードを読みやすくするために、レベルごとにインデントして記述するのが一般的です。  これは、統合開発環境 \(IDE: Integrated Development Environment\) エディターによって、自動的に行われます。  
  
 次の例では、`sumRows` プロシージャによって、行列の各行の正の要素が合計されます。  
  
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
  
 上の例では、最初の `Next` ステートメントによって、内部 `For` ループが閉じられ、最後の `Next` ステートメントによって、外部 `For` ループが閉じられます。  
  
 同様に、入れ子になった `If` ステートメントの `End If` ステートメントは、先行する最も近い `If` ステートメントに対して自動的に適用されます。  入れ子になった `Do` ループの動作も同様であり、最も内側の `Loop` ステートメントが最も内側の `Do` ステートメントに対応します。  
  
> [!NOTE]
>  多くの制御構造では、キーワードをクリックすると、その構造体のキーワードがすべて強調表示されます。  たとえば、`If...Then...Else` 構造の `If` をクリックすると、その構造の `If`、`Then`、`ElseIf`、`Else`、および `End If` のすべてのインスタンスが強調表示されます。  強調表示された次のキーワード、または前のキーワードに移動するには、Ctrl キーと Shift キーを押しながら↑キーを押すか、Ctrl キーと Shift キーを押しながら↓キーを押します。  
  
## 異なる種類の制御構造を入れ子にする  
 他の種類の制御構造内で、ある種類の制御構造を入れ子にできます。  `For Each` ループ内部で `With` ブロックを使用し、`With` ブロック内部で、入れ子になった `If` ブロックを使用しているコード例を次に示します。  
  
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
  
## 制御構造の重なり  
 制御構造は重ねることはできません。  つまり、入れ子になった構造体は、次の最も内側の構造体の中に完全に含まれる必要があります。  たとえば、次の配置は、内部の `With` ブロックが終了する前に `For` ループが終了するため、無効です。  
  
 ![無効な入れ子のグラフィック ダイアグラム](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")  
For および With 構造体の無効な入れ子  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コンパイラによって、そのような制御構造の重なりが検出され、コンパイル エラーが通知されます。  
  
## 参照  
 [Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Decision Structures](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Other Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
---
title: Shared (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Shared
helpviewer_keywords:
- Shared keyword [Visual Basic]
- members [Visual Basic], shared
- shared members
- nonshared
- shared [elements VB]
- elements [Visual Basic], shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
ms.openlocfilehash: b15dd08d69f372317b9140001e8072eeb66d44ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="shared-visual-basic"></a>Shared (Visual Basic)
1 つまたは複数の宣言されたプログラミング要素がクラスまたは構造体全体、いないに関連付けられているクラスまたは構造体の特定のインスタンスを指定します。  
  
## <a name="remarks"></a>コメント  
  
## <a name="when-to-use-shared"></a>共有を使用する場合  
 クラスまたは構造体のメンバーを共有できるように、すべてのインスタンスではなくより*非共有*、各インスタンスが独自のコピーを保持します。 これは、変数の値は、アプリケーション全体に適用される場合に便利です。 その変数を宣言する場合`Shared`、すべてのインスタンスが同じストレージの場所にアクセスし、およびすべてのインスタンスにアクセス、更新された値が 1 つのインスタンスは、変数の値を変更する場合。  
  
 共有しても、メンバーのアクセス レベルは変わりません。 たとえば、クラス メンバーを共有できるおよびプライベート (クラス内からのみアクセスできる)、または非共有と公開します。 詳細については、次を参照してください。 [Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。  
  
## <a name="rules"></a>ルール  
  
-   **宣言コンテキスト。** `Shared` は、モジュール レベルでのみ使用できます。 つまりの宣言コンテキスト、`Shared`要素は、クラスまたは構造体にある必要があるあり、ソース ファイル、名前空間、またはプロシージャにすることはできません。  
  
-   **結合された修飾子。** 指定することはできません`Shared`と共に[オーバーライド](../../../visual-basic/language-reference/modifiers/overrides.md)、 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)、 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)、 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)、または[静的](../../../visual-basic/language-reference/modifiers/static.md)同じ宣言内で。  
  
-   **アクセスします。** 共有要素にアクセスするには、そのクラスまたは構造体の特定のインスタンスの変数名ではなく、そのクラスまたは構造体の名前を修飾します。 でも、クラスまたはその共有メンバーにアクセスする構造体のインスタンスを作成する必要はありません。  
  
     次の例には、共有プロシージャが呼び出される<xref:System.Double.IsNaN%2A>によって公開されている、<xref:System.Double>構造体。  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
-   **暗黙の型を共有します。** 使用することはできません、`Shared`の修飾子、 [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)定数が暗黙的に共有しますが、できます。 同様に、するには、モジュールまたはインターフェイスのメンバーを宣言することはできません`Shared`、暗黙的に共有されますが、します。  
  
## <a name="behavior"></a>動作  
  
-   **記憶域。** 共有変数またはイベントは、そのクラスまたは構造体の数またはいくつかのインスタンスに関係なくを作成する、1 回だけメモリに格納されます。 同様に、共有プロシージャまたはプロパティには、ローカル変数の 1 つだけのセットを保持します。  
  
-   **アクセスするインスタンス変数を使用します。** クラスまたは構造体の特定のインスタンスを格納する変数の名前で修飾することにより共有要素にアクセスすることができます。 この動作は通常どおり、コンパイラは警告メッセージを生成し、変数ではなく、クラスまたは構造体の名前を使ってアクセスします。  
  
-   **インスタンス式からアクセスします。** 共有要素をそのクラスまたは構造体のインスタンスを返す式を使用してアクセスする場合、コンパイラで式を評価するのではなく、クラスまたは構造体の名前を使ってアクセスを行います。 その他のアクションだけでなく、インスタンスを返すことを実行する式を対象とした場合、予期しない結果が生成されます。 次に例を示します。  
  
    ```  
    Sub main()  
        shareTotal.total = 10  
        ' The preceding line is the preferred way to access total.  
        Dim instanceVar As New shareTotal  
        instanceVar.total += 100  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of through  
        ' the variable instanceVar. This works as expected and adds  
        ' 100 to total.  
        returnClass().total += 1000  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of calling  
        ' returnClass(). This adds 1000 to total but does not work as  
        ' expected, because the MsgBox in returnClass() does not run.  
        MsgBox("Value of total is " & CStr(shareTotal.total))  
    End Sub  
    Public Function returnClass() As shareTotal  
        MsgBox("Function returnClass() called")  
        Return New shareTotal  
    End Function  
    Public Class shareTotal  
        Public Shared total As Integer  
    End Class  
    ```  
  
     上記の例では、コンパイラ警告メッセージを生成、共有変数にアクセスするコードのどちらの時刻`total`インスタンスを経由します。 クラスから直接アクセスは、各ケース`shareTotal`を行わないと、インスタンスを使用します。 プロシージャに目的の呼び出しの場合`returnClass`、つまりへの呼び出しも生成しません`returnClass`ので、"関数 returnClass() と呼ばれる"を表示する追加のアクションは実行されません。  
  
 `Shared` 修飾子は、次のコンテキストで使用できます。  
  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Static](../../../visual-basic/language-reference/modifiers/static.md)  
 [Visual Basic における有効期間](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [手順](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)

---
title: '方法: 変数のスコープを制御する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], scope
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- variables [Visual Basic], visibility
- scope [Visual Basic], declared elements
- scope [Visual Basic], variables
- scope [Visual Basic], Visual Basic
- declared elements [Visual Basic], visibility
- visibility [Visual Basic], variables
ms.assetid: 44b7f62a-cb5c-4d50-bce9-60ae68f87072
ms.openlocfilehash: 6e8d1178398711226b88fee7e6defd5162b91fcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649192"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a>方法: 変数のスコープを制御する (Visual Basic)
変数が、通常、*スコープ*、リファレンスについては、それを宣言する領域全体で表示します。 場合によっては、変数の*アクセス レベル*そのスコープに影響を与えることができます。  
  
 詳細については、次を参照してください。 [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)です。  
  
## <a name="scope-at-block-or-procedure-level"></a>ブロックまたはプロシージャ レベルのスコープ  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a>変数をブロック内でのみ表示されるようにするには  
  
-   場所、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)の開始との間など、そのブロックの宣言ステートメントを終了して、変数、`For`と`Next`のステートメント、`For`ループします。  
  
     ブロック内からのみ、変数を参照することができます。  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a>変数をプロシージャ内でのみ表示されるようにするには  
  
-   場所、 `Dim` 、変数、プロシージャ内では、任意のブロックの外側のステートメント (など、 `With`.`End With`ブロック) します。  
  
     プロシージャに含まれているすべてのブロックの内側など、プロシージャ内からのみ、変数を参照することができます。  
  
## <a name="scope-at-module-or-namespace-level"></a>モジュールまたは Namespace レベルのスコープ  
 便宜上、1 つの用語*モジュール レベル*モジュール、クラス、および構造体に適用されます。 モジュール レベルの変数のアクセス レベルでは、そのスコープを決定します。 モジュール、クラスまたは構造体を含む名前空間もスコープに影響します。  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a>変数をモジュール、クラスまたは構造体全体にわたって表示されるようにするには  
  
1.  場所、`Dim`変数、プロシージャの外部ではなく、モジュール、クラス、または構造体、内部のステートメント。  
  
2.  含める、[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)キーワード、`Dim`ステートメントです。  
  
3.  ではなく、モジュール、クラス、または構造内で任意の場所から変数を参照することが外側にします。  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a>変数を名前空間全体にわたって表示されるようにするには  
  
1.  場所、`Dim`変数、プロシージャの外部ではなく、モジュール、クラス、または構造体、内部のステートメント。  
  
2.  含める、[フレンド](../../../../visual-basic/language-reference/modifiers/friend.md)または[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)キーワード、`Dim`ステートメントです。  
  
3.  任意の場所から変数を参照できるモジュール、クラスまたは構造体を含む名前空間内で。  
  
## <a name="example"></a>例  
 次の例では、モジュール レベル変数を宣言し、モジュール内のコードを可視性を制限します。  
  
```  
Module demonstrateScope  
    Private strMsg As String  
    Sub initializePrivateVariable()  
        strMsg = "This variable cannot be used outside this module."  
    End Sub  
    Sub usePrivateVariable()  
        MsgBox(strMsg)  
    End Sub  
End Module  
```  
  
 前の例では、モジュールで定義されたすべてのプロシージャ`demonstrateScope`を参照できる、`String`変数`strMsg`です。 ときに、`usePrivateVariable`プロシージャが呼び出されると、文字列変数の内容を表示`strMsg` ダイアログ ボックス。  
  
 次の部分を変更前の例では、文字列変数に`strMsg`宣言の名前空間内の任意の場所のコードによって参照することができます。  
  
```  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 同じ名前の別の変数の代わりに誤って参照することがある可能性は少なく、変数より狭いスコープ 参照の対応付けの問題を最小限に抑えることができますも。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 変数のスコープが狭い、される可能性が少なく悪意のあるコードが不正にそれを使用します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Visual Basic における有効期間](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Visual Basic でのアクセス レベル](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [変数](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)

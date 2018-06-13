---
title: '方法: 構造体を宣言する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: 6128addd60609bfc88a1409648fb320bc7089974
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650028"
---
# <a name="how-to-declare-a-structure-visual-basic"></a>方法: 構造体を宣言する (Visual Basic)
ある構造体の宣言を開始する、 [Structure ステートメント](../../../../visual-basic/language-reference/statements/structure-statement.md)で終了して、 `End` `Structure`ステートメントです。 これら 2 つのステートメントの間で、少なくとも 1 つを宣言する必要があります*要素*です。 任意のデータ型の要素を指定できますが、非共有変数または非共有、非カスタム イベントのいずれかにするには、少なくとも 1 つ必要があります。  
  
 構造体の宣言で構造体の要素を初期化することはできません。 構造型の変数を宣言するときに、要素に、変数にアクセスすることにより値を割り当てます。  
  
 構造体とクラス間の違いの詳細については、次を参照してください。[構造体とクラス](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)です。  
  
 デモの目的の従業員の名前、内線番号、および給与を追跡するような状況を検討してください。 構造体では、これは 1 つの変数で実行することができます。  
  
### <a name="to-declare-a-structure"></a>構造体を宣言するには  
  
1.  最初と最後のステートメントの構造を作成します。  
  
     使用して、構造体のアクセス レベルを指定することができます、[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)、 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)、[フレンド](../../../../visual-basic/language-reference/modifiers/friend.md)、または[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)キーワード、またはすることができますできます既定で`Public`です。  
  
    ```  
    Private Structure employee  
    End Structure  
    ```  
  
2.  構造体の本体に要素を追加します。  
  
     構造体には、少なくとも 1 つの要素が必要です。 すべての要素を宣言し、ファイルのアクセス レベルを指定する必要があります。 使用する場合、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)、キーワードのないユーザー補助機能の既定値`Public`です。  
  
    ```  
    Private Structure employee  
        Public givenName As String  
        Public familyName As String  
        Public phoneExtension As Long  
        Private salary As Decimal  
        Public Sub giveRaise(raise As Double)  
            salary *= raise  
        End Sub  
        Public Event salaryReviewTime()  
    End Structure  
    ```  
  
     `salary`フィールド前の例では`Private`、これは外側のクラスからでも、構造体の外部アクセスできません。 ただし、`giveRaise`プロシージャは`Public`ので、構造体の外部から呼び出すことができます。 同様に上げることができます、`salaryReviewTime`構造の外部からのイベントです。  
  
     変数だけでなく`Sub`プロシージャ、およびイベント、定数を定義することもできます。`Function`プロシージャ、および構造のプロパティです。 として最大で 1 つのプロパティを指定することができます、*既定プロパティ*に少なくとも 1 つの引数を受け取る提供します。 イベントを処理することができます、 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub`プロシージャです。 詳細については、次を参照してください。[する方法: Visual Basic の既定のプロパティを呼び出してくださいを宣言し](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)です。  
  
## <a name="see-also"></a>関連項目  
 [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [複合データ型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [構造体](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [構造体変数](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 [構造体とその他のプログラミング要素](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [構造体とクラス](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [ユーザー定義型](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)

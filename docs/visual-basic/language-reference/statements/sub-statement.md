---
title: Sub ステートメント (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Sub
helpviewer_keywords:
- Public keyword [Visual Basic], Sub statements
- procedures [Visual Basic], creating
- declaring procedures [Visual Basic], Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword [Visual Basic], Sub statements
- Optional keyword [Visual Basic], Sub statements
- declarations [Visual Basic], procedures
- Sub keyword [Visual Basic]
- Handles keyword [Visual Basic], Sub statements
- Protected Friend keyword [Visual Basic]
- ParamArray keyword [Visual Basic], Sub statements
- Implements keyword [Visual Basic], Sub statements
- Sub statement [Visual Basic]
- subroutines
- ByRef keyword [Visual Basic], Sub statements
- Sub procedures [Visual Basic], Sub statement
- recursive procedures
- Private keyword [Visual Basic], Sub statements
- Friend keyword [Visual Basic], Sub statements
- Exit statement [Visual Basic], Sub statements
- procedures [Visual Basic], Sub
- End keyword [Visual Basic], Sub statements
- ByVal keyword [Visual Basic], Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
ms.openlocfilehash: 08be38cdbec82914b567ab5b86eed71181efcf57
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="sub-statement-visual-basic"></a>Sub ステートメント (Visual Basic)
宣言名、パラメーター、およびコードを定義する、`Sub`プロシージャです。  
  
## <a name="syntax"></a>構文  
  
```  
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]  
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Sub ]  
    [ statements ]  
End Sub  
```  
  
## <a name="parts"></a>指定項目  
  
-   `attributelist`  
  
     任意。 参照してください[属性一覧](attribute-list.md)です。  
  
-   `Partial`  
  
     任意。 部分メソッドの定義を示します。 参照してください[部分メソッド](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)です。  
  
-   `accessmodifier`  
  
     任意。 次のいずれかの値を指定します。  
  
    -   [Public](../modifiers/public.md)  
  
    -   [Protected](../modifiers/protected.md)  
  
    -   [Friend](../modifiers/friend.md)  
  
    -   [Private](../modifiers/private.md)  
  
    - [保護されたフレンド](../../language-reference/modifiers/protected-friend.md)

    - [保護されたプライベート](../../language-reference/modifiers/private-protected.md)
  
     参照してください[Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。  
  
-   `proceduremodifiers`  
  
     任意。 次のいずれかの値を指定します。  
  
    -   [オーバーロード](../modifiers/overloads.md)  
  
    -   [Overrides](../modifiers/overrides.md)  
  
    -   [Overridable](../modifiers/overridable.md)  
  
    -   [NotOverridable](../modifiers/notoverridable.md)  
  
    -   [MustOverride](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     任意。 参照してください[共有](../modifiers/shared.md)です。  
  
-   `Shadows`  
  
     任意。 参照してください[Shadows](../modifiers/shadows.md)です。  
  
-   `Async`  
  
     任意。 参照してください[Async](../modifiers/async.md)です。  
  
-   `name`  
  
     必須。 プロシージャの名前。 参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。 クラスのコンス トラクターのプロシージャを作成するには、名前を設定、`Sub`する手順、`New`キーワード。 詳細については、次を参照してください。[オブジェクトの有効期間: オブジェクトが作成と破棄にはどのように](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)です。  
  
-   `typeparamlist`  
  
     任意。 ジェネリック プロシージャの型パラメーターの一覧です。 参照してください[のリストを入力](type-list.md)です。  
  
-   `parameterlist`  
  
     任意。 このプロシージャのパラメーターを表すローカル変数名の一覧です。 参照してください[パラメーター リスト](parameter-list.md)です。  
  
-   `Implements`  
  
     任意。 この手順には、1 つまたは複数が実装されていることを示します`Sub`プロシージャ、このプロシージャの包含クラスまたは構造体によって実装されるインターフェイスで定義されている 1 つずつです。 参照してください[ステートメントを実装します](implements-statement.md)です。  
  
-   `implementslist`  
  
     `Implements` を指定する場合は、必ず指定します。 実装される `Sub` プロシージャのリストです。  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     `implementedprocedure` の構文と指定項目は次のとおりです。  
  
     `interface.definedname`  
  
    |パーツ|説明|  
    |---|---|  
    |`interface`|必須。 このプロシージャによって実装されるインターフェイスの名前には、クラスまたは構造体を含むのです。|  
    |`definedname`|必須。 `interface` の中でプロシージャを定義するために使用する名前。|  
  
-   `Handles`  
  
     任意。 この手順が 1 つまたは複数の特定のイベントを処理できることを示します。 参照してください[処理](handles-clause.md)です。  
  
-   `eventlist`  
  
     `Handles` を指定する場合は、必ず指定します。 このプロシージャを処理するイベントの一覧です。  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     `eventspecifier` の構文と指定項目は次のとおりです。  
  
     `eventvariable.event`  
  
    |パーツ|説明|  
    |---|---|  
    |`eventvariable`|必須。 クラスまたはイベントを発生させる構造体のデータ型で宣言されたオブジェクト変数です。|  
    |`event`|必須。 このプロシージャを処理するイベントの名前。|  
  
-   `statements`  
  
     任意。 このプロシージャ内で実行するステートメントのブロックです。  
  
-   `End Sub`  
  
     このプロシージャの定義を終了します。  
  
## <a name="remarks"></a>コメント  
 すべての実行可能コードは、プロシージャ内でなければなりません。 使用して、`Sub`呼び出し元のコードに値を返すしたくない場合、そのプロシージャです。 使用して、`Function`値を取得する場合、そのプロシージャです。  
  
## <a name="defining-a-sub-procedure"></a>Sub プロシージャの定義  
 定義することができます、`Sub`手順モジュール レベルでのみです。 Sub プロシージャの宣言コンテキストは、そのため、必要があります、クラス、構造体、モジュールの場合、またはインターフェイスと、ソース ファイル、名前空間、プロシージャ、またはブロックすることはできません。 詳細については、「[宣言コンテキストと既定のアクセス レベル](declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 `Sub` パブリック アクセスにプロシージャの既定値です。 アクセス修飾子を使用して、これらのアクセス レベルを調整できます。  
  
 プロシージャで使用する場合、`Implements`キーワードを含むクラスまたは構造体があります、`Implements`直後に続くステートメント、`Class`または`Structure`ステートメントです。 `Implements`ステートメントで指定されている各インターフェイスを含める必要があります`implementslist`です。 ただし、インターフェイスを定義する名前、 `Sub` (で`definedname`) このプロシージャの名前と一致する必要はありません (で`name`)。  
  
## <a name="returning-from-a-sub-procedure"></a>Sub プロシージャから返す処理  
 ときに、`Sub`その呼び出し元ステートメントの後にステートメントを使用して、プロシージャ呼び出し元のコードに戻ると、実行が継続します。  
  
 次の例の戻り値を示しています、`Sub`プロシージャです。  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 `Exit Sub`と`Return`ステートメントからすぐに終了が発生する、`Sub`プロシージャです。 任意の数の`Exit Sub`と`Return`ステートメントがどこにでも表示、プロシージャとを混在させること`Exit Sub`と`Return`ステートメントです。  
  
## <a name="calling-a-sub-procedure"></a>Sub プロシージャの呼び出し  
 呼び出す、`Sub`ステートメントで、プロシージャ名を使用し、かっこ内に、引数リストでその名前でプロシージャです。 引数を指定しない場合にのみ、かっこを省略することができます。 ただし、コードは、常にかっこを含める場合より読みやすいです。  
  
 A`Sub`プロシージャおよび`Function`プロシージャがパラメーターを持つし、一連のステートメントを実行します。 ただし、`Function`値、およびプロシージャを返します`Sub`プロシージャしません。 したがって、使用することはできません、`Sub`式」の手順です。  
  
 使用することができます、`Call`キーワードを呼び出すとき、`Sub`プロシージャが、そのキーワードはほとんどの用途をお勧めしません。 詳細については、次を参照してください。 [Call ステートメント](call-statement.md)です。  
  
 Visual Basic では、算術式内部の効率を向上させることがあります再配置します。 そのため、引数リストには、他のプロシージャを呼び出す式が含まれている場合を前提にしないでそれらの式が特定の順序で呼び出されます。  
  
## <a name="async-sub-procedures"></a>Async Sub プロシージャ  
 非同期機能を使用すると、明示的なコールバックの使用や複数の関数やラムダ式で、コードを手動で分割を行わず非同期関数を呼び出すことができます。  
  
 使用するプロシージャをマークする場合、 [Async](../modifiers/async.md)修飾子、行うこともできます、 [Await](../../../visual-basic/language-reference/operators/await-operator.md)演算子プロシージャにします。 達するとを制御すると、`Await`内の式、`Async`プロシージャは、呼び出し元に制御が戻るし、待機中のタスクが完了するまでの手順で進行状況は中断します。 タスクが完了したら、プロシージャで実行を再開できます。  
  
> [!NOTE]
>  `Async`プロシージャにどちらか最初待機中のオブジェクトが完了していないことが検出されたときに、呼び出し元のまたは末尾を返します、`Async`プロシージャに達すると、先に生じた方です。  
  
 マークすることも、[関数ステートメント](function-statement.md)で、`Async`修飾子です。 `Async`関数の戻り値の型を持つことができます<xref:System.Threading.Tasks.Task%601>または<xref:System.Threading.Tasks.Task>です。 例を後でのこのトピックでは、`Async`関数の戻り値の型を持つ<xref:System.Threading.Tasks.Task%601>します。  
  
 `Async` `Sub` プロシージャは、主に、値が返されることはできません、イベント ハンドラーを使用します。 `Async``Sub`プロシージャを待機することはできませんとの呼び出し元、`Async``Sub`プロシージャは、例外をキャッチできませんを`Sub`プロシージャがスローされます。  
  
 `Async`プロシージャは、いずれかを宣言できません[ByRef](../modifiers/byref.md)パラメーター。  
  
 詳細については`Async`プロシージャを参照してください[Async および Await を使用した非同期プログラミング](../../../visual-basic/programming-guide/concepts/async/index.md)、[非同期プログラムにおける制御フロー](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)、および[Async 戻り値の型](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="example"></a>例  
 次の例では、`Sub`を名前、パラメーター、およびの本体を構成するコードを定義するステートメント、`Sub`プロシージャです。  
  
 [!code-vb[VbVbalrStatements#58](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]  
  
## <a name="example"></a>例  
 次の例では、`DelayAsync`は、`Async``Function`の戻り値の型を持つ<xref:System.Threading.Tasks.Task%601>します。 `DelayAsync` には、整数を返す `Return` ステートメントがあります。 したがって、関数宣言の`DelayAsync`の戻り値の型を持つ必要があります`Task(Of Integer)`です。 戻り値の型があるため`Task(Of Integer)`の評価、`Await`式`DoSomethingAsync`ステートメントを次に示すように整数が生成されます:`Dim result As Integer = Await delayTask`です。  
  
 `startButton_Click`プロシージャは、の例、`Async Sub`プロシージャです。 `DoSomethingAsync`は、`Async`関数では、タスクへの呼び出しを`DoSomethingAsync`ステートメントを次に示すように待機する必要があります:`Await DoSomethingAsync()`です。 `startButton_Click``Sub`でプロシージャを定義する必要があります、`Async`修飾子があるため、`Await`式。  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Implements ステートメント](implements-statement.md)  
 [Function ステートメント](function-statement.md)  
 [パラメーター リスト](parameter-list.md)  
 [Dim ステートメント](dim-statement.md)  
 [Call ステートメント](call-statement.md)  
 [Of](of-clause.md)  
 [パラメーター配列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [方法 : ジェネリック クラスを使用する](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [プロシージャのトラブルシューティング](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [部分メソッド](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)

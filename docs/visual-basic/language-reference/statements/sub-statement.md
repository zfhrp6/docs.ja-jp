---
title: "Sub ステートメント (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Sub
dev_langs:
- VB
helpviewer_keywords:
- Public keyword, Sub statements
- procedures, creating
- declaring procedures, Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword, Sub statements
- Optional keyword, Sub statements
- declarations, procedures
- Sub keyword
- Handles keyword, Sub statements
- Protected Friend keyword
- ParamArray keyword, Sub statements
- Implements keyword, Sub statements
- Sub statement
- subroutines
- ByRef keyword, Sub statements
- Sub procedures, Sub statement
- recursive procedures
- Private keyword, Sub statements
- Friend keyword, Sub statements
- Exit statement, Sub statements
- procedures, Sub
- End keyword, Sub statements
- ByVal keyword, Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
caps.latest.revision: 52
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
ms.openlocfilehash: 0eb78f92f22502d9e8595051361b45d9bf53ed64
ms.lasthandoff: 03/13/2017

---
# <a name="sub-statement-visual-basic"></a>Sub ステートメント (Visual Basic)
名前、パラメーター、および定義するコードを宣言して、`Sub`プロシージャです。  
  
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
  
     省略可能です。 参照してください[属性一覧](attribute-list.md)します。  
  
-   `Partial`  
  
     省略可能です。 部分メソッドの定義を示します。 参照してください[部分メソッド](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)します。  
  
-   `accessmodifier`  
  
     省略可能です。 次のいずれかの値を指定します。  
  
    -   [Public](../modifiers/public.md)  
  
    -   [Protected](../modifiers/protected.md)  
  
    -   [Friend](../modifiers/friend.md)  
  
    -   [Private](../modifiers/private.md)  
  
    -   `Protected Friend`  
  
     参照してください[Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)します。  
  
-   `proceduremodifiers`  
  
     省略可能です。 次のいずれかの値を指定します。  
  
    -   [オーバーロード](../modifiers/overloads.md)  
  
    -   [Overrides](../modifiers/overrides.md)  
  
    -   [Overridable](../modifiers/overridable.md)  
  
    -   [NotOverridable](../modifiers/notoverridable.md)  
  
    -   [MustOverride](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     省略可能です。 参照してください[共有](../modifiers/shared.md)します。  
  
-   `Shadows`  
  
     省略可能です。 参照してください[シャドウ](../modifiers/shadows.md)します。  
  
-   `Async`  
  
     省略可能です。 参照してください[Async](../modifiers/async.md)します。  
  
-   `name`  
  
     必須です。 プロシージャの名前。 参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)します。 クラスのコンス トラクターのプロシージャを作成するには、設定の名前、`Sub`する手順、`New`キーワードです。 詳細については、次を参照してください。[オブジェクトの有効期間: オブジェクトが作成と破棄方法](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)します。  
  
-   `typeparamlist`  
  
     省略可能です。 手順については、ジェネリック型パラメーターの一覧です。 参照してください[のリストを入力](type-list.md)します。  
  
-   `parameterlist`  
  
     省略可能です。 このプロシージャのパラメーターを表すローカル変数名の一覧です。 参照してください[パラメーター リスト](parameter-list.md)します。  
  
-   `Implements`  
  
     省略可能です。 この手順が&1; つまたは複数を実装することを示します`Sub`の手順は、この手順を含むクラスまたは構造体によって実装されるインターフェイスで定義されている&1; つずつです。 参照してください[ステートメントを実装します](implements-statement.md)します。  
  
-   `implementslist`  
  
     `Implements` を指定する場合は、必ず指定します。 実装される `Sub` プロシージャのリストです。  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     `implementedprocedure` の構文と指定項目は次のとおりです。  
  
     `interface.definedname`  
  
    |パーツ|説明|  
    |---|---|  
    |`interface`|必須です。 このプロシージャによって実装されるインターフェイスの名前には、クラスまたは構造体を含むのです。|  
    |`definedname`|必須です。 `interface` の中でプロシージャを定義するために使用する名前。|  
  
-   `Handles`  
  
     省略可能です。 この手順が&1; つまたは複数の特定のイベントを処理できることを示します。 参照してください[処理](handles-clause.md)します。  
  
-   `eventlist`  
  
     `Handles` を指定する場合は、必ず指定します。 このプロシージャを処理するイベントのリスト。  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     `eventspecifier` の構文と指定項目は次のとおりです。  
  
     `eventvariable.event`  
  
    |パーツ|説明|  
    |---|---|  
    |`eventvariable`|必須です。 オブジェクト変数がクラスまたはイベントを発生させる構造体のデータ型で宣言します。|  
    |`event`|必須です。 このプロシージャを処理するイベントの名前。|  
  
-   `statements`  
  
     省略可能です。 このプロシージャ内で実行するステートメントのブロックです。  
  
-   `End Sub`  
  
     このプロシージャの定義を終了します。  
  
## <a name="remarks"></a>コメント  
 すべての実行可能コードは、プロシージャの中にする必要があります。 使用して、`Sub`プロシージャは、呼び出し元のコードに値を返すしたくない場合。 使用して、`Function`プロシージャは、値を取得する場合。  
  
## <a name="defining-a-sub-procedure"></a>Sub プロシージャの定義  
 定義する、`Sub`手順をモジュール レベルでのみです。 Sub プロシージャの宣言コンテキストは、そのため、必要があります、クラス、構造体、モジュールの場合、またはインターフェイスとソース ファイル、名前空間、プロシージャ、またはブロックすることはできません。 詳細については、次を参照してください。[宣言コンテキストとアクセス レベルの既定の](declaration-contexts-and-default-access-levels.md)です。  
  
 `Sub`パブリック アクセスを既定値をプロシージャです。 アクセス修飾子を使用して、これらのアクセス レベルを調整できます。  
  
 プロシージャで使用する場合、`Implements`キーワードを含むクラスまたは構造体が必要、`Implements`直後に続くステートメントの`Class`または`Structure`ステートメントです。 `Implements`ステートメントで指定されている各インターフェイスを含める必要があります`implementslist`します。 ただし、インターフェイスを定義する名前、 `Sub` (で`definedname`) このプロシージャの名前と一致する必要はありません (で`name`)。  
  
## <a name="returning-from-a-sub-procedure"></a>Sub プロシージャから返す処理  
 ときに、`Sub`その呼び出し元ステートメントの後にステートメントを使用して、プロシージャ呼び出し元のコードに戻ると、実行が継続します。  
  
 次の例から戻るとき、`Sub`プロシージャです。  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 `Exit Sub`と`Return`ステートメントからすぐに終了が発生する、`Sub`プロシージャです。 任意の数の`Exit Sub`と`Return`ステートメントが任意の場所で、手順と混在させることが`Exit Sub`と`Return`ステートメントです。  
  
## <a name="calling-a-sub-procedure"></a>Sub プロシージャの呼び出し  
 呼び出す、`Sub`をステートメントで、プロシージャ名を使用し、かっこで囲まれた、引数リストでその名前を次の手順です。 すべての引数を指定しない場合にのみ、かっこを省略することができます。 ただし、コードが読みやすく、かっこを挿入する場合です。  
  
 A`Sub`プロシージャと`Function`プロシージャはパラメーターを持つし、一連のステートメントを実行します。 ただし、`Function`値、およびプロシージャを返します。`Sub`プロシージャがありません。 したがって、使用することはできません、`Sub`式」の手順です。  
  
 使用することができます、`Call`キーワードを呼び出したときに、`Sub`プロシージャが、そのキーワードは、ほとんどの用途をお勧めしません。 詳細については、次を参照してください。 [Call ステートメント](call-statement.md)します。  
  
 Visual Basic では、算術式内部の効率を向上させることがあります再配置します。 そのため、引数リストには、その他のプロシージャを呼び出す式が含まれている場合を前提にしないでこれらの式が特定の順序で呼び出されます。  
  
## <a name="async-sub-procedures"></a>Async Sub プロシージャ  
 非同期機能を使用すると、明示的なコールバックの使用や複数の関数やラムダ式で、コードを手動で分割を行わず非同期関数を呼び出すことができます。  
  
 使用してプロシージャをマークした場合、 [Async](../modifiers/async.md)修飾子は、使用できます、 [Await](../../../visual-basic/language-reference/operators/await-operator.md)プロシージャ内の演算子です。 達するとを制御すると、`Await`内の式、`Async`手順が、呼び出し元に制御が戻るし、待機中のタスクが完了するまでの手順で進行状況が中断します。 タスクが完了したら、プロシージャの実行を再開できます。  
  
> [!NOTE]
>  `Async`のいずれか最初待機中のオブジェクトが完了していないことが検出された場合、呼び出し元へを返し、`Async`プロシージャに達すると、どちらかがします。  
  
 マークすることも、 [Function ステートメント](function-statement.md)で、`Async`修飾子です。 `Async`関数<xref:System.Threading.Tasks.Task%601>または<xref:System.Threading.Tasks.Task>.</xref:System.Threading.Tasks.Task></xref:System.Threading.Tasks.Task%601>の戻り値の型を設定できます 例を後で、このトピックでは、 `Async` <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601>の戻り値の型を持つ関数  
  
 `Async``Sub`プロシージャは、主に使用、イベント ハンドラーの値が返されることはできません。 `Async``Sub`プロシージャを待機することはできないと、呼び出し元の`Async``Sub`プロシージャは、例外をキャッチできませんを`Sub`プロシージャがスローされます。  
  
 `Async`プロシージャは、いずれかを宣言できません[ByRef](../modifiers/byref.md)パラメーター。  
  
 詳細については`Async`の手順を参照してください[Async および Await を使用した非同期プログラミング](../../../visual-basic/programming-guide/concepts/async/index.md)、[非同期プログラムにおける制御のフロー](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)、および[Async を返す型](../../../visual-basic/programming-guide/concepts/async/async-return-types.md)します。  
  
## <a name="example"></a>例  
 次の例では、`Sub`名、パラメーター、およびの本体を形成するコードを定義するステートメント、`Sub`プロシージャです。  
  
 [!code-vb[VbVbalrStatements #&58;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]  
  
## <a name="example"></a>例  
 次の例で`DelayAsync`、 `Async``Function` <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601>の戻り値の型を持つ `DelayAsync` には、整数を返す `Return` ステートメントがあります。 したがって、関数宣言の`DelayAsync`の戻り値の型を持つ必要があります`Task(Of Integer)`します。 戻り値の型である`Task(Of Integer)`の評価、`Await`式`DoSomethingAsync`として次のステートメントに示す整数を生成する:`Dim result As Integer = Await delayTask`です。  
  
 `startButton_Click`手順の例は、`Async Sub`プロシージャです。 `DoSomethingAsync`は、`Async`関数への呼び出しのタスク`DoSomethingAsync`として次のステートメントに示す、待機する必要があります:`Await DoSomethingAsync()`です。 `startButton_Click``Sub`でプロシージャを定義する必要があります、`Async`修飾子があるため、`Await`式です。  
  
 [!code-vb[csAsyncMethod&1;](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Implements ステートメント](implements-statement.md)   
 [Function ステートメント](function-statement.md)   
 [パラメーター リスト](parameter-list.md)   
 [Dim ステートメント](dim-statement.md)   
 [Call ステートメント](call-statement.md)   
 [Of](of-clause.md)   
 [パラメーター配列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [方法: ジェネリック クラスを使用して](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [トラブルシューティングの手順](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [部分メソッド](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)

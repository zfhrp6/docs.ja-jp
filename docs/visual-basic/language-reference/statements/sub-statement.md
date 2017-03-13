---
title: "Sub ステートメント (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Sub"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Public キーワード、Sub ステートメント"
  - "手順については、作成します。"
  - "手順については、Sub ステートメントを宣言します。"
  - "Sub プロシージャの引数 [Visual Basic]"
  - "As キーワード、Sub ステートメント"
  - "省略可能なキーワード、Sub ステートメント"
  - "プロシージャの宣言"
  - "Sub キーワード"
  - "Handles キーワード、Sub ステートメント"
  - "Protected Friend キーワード"
  - "ParamArray キーワード、Sub ステートメント"
  - "Implements キーワード、Sub ステートメント"
  - "Sub ステートメント"
  - "サブルーチン"
  - "ByRef キーワード、Sub ステートメント"
  - "Sub ステートメントに、sub プロシージャ"
  - "再帰プロシージャ"
  - "Private キーワード、Sub ステートメント"
  - "Friend キーワード、Sub ステートメント"
  - "Exit ステートメント、Sub ステートメント"
  - "Sub プロシージャ"
  - "End キーワード、Sub ステートメント"
  - "ByVal キーワード、Sub ステートメント"
  - "Visual Basic コード、Sub プロシージャ"
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
caps.latest.revision: 52
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 52
---
# Sub ステートメント (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

名前、パラメーター、および定義するコードを宣言して、 `Sub` プロシージャです。  
  
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
  
     省略可能です。 参照してください [属性一覧](../../../visual-basic/language-reference/statements/attribute-list.md)します。  
  
-   `Partial`  
  
     省略可能です。 部分メソッドの定義を示します。 参照してください [部分メソッド](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)します。  
  
-   `accessmodifier`  
  
     省略可能です。 次のいずれかの値を指定します。  
  
    -   [パブリック](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [保護されています。](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [プライベート](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     「 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。  
  
-   `proceduremodifiers`  
  
     省略可能です。 次のいずれかの値を指定します。  
  
    -   [オーバーロード](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [オーバーライド](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [オーバーライド可能です](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     省略可能です。 参照してください [共有](../../../visual-basic/language-reference/modifiers/shared.md)します。  
  
-   `Shadows`  
  
     省略可能です。 参照してください [シャドウ](../../../visual-basic/language-reference/modifiers/shadows.md)します。  
  
-   `Async`  
  
     省略可能です。 参照してください [Async](../../../visual-basic/language-reference/modifiers/async.md)します。  
  
-   `name`  
  
     必須です。 プロシージャの名前。 「 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。 クラスのコンス トラクターのプロシージャを作成するには、設定の名前、 `Sub` する手順、 `New` キーワードです。 詳細については、次を参照してください。 [オブジェクトの有効期間: オブジェクトが作成と破棄方法](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)します。  
  
-   `typeparamlist`  
  
     省略可能です。 手順については、ジェネリック型パラメーターの一覧です。 参照してください [のリストを入力](../../../visual-basic/language-reference/statements/type-list.md)します。  
  
-   `parameterlist`  
  
     省略可能です。 このプロシージャのパラメーターを表すローカル変数名の一覧です。 参照してください [パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)します。  
  
-   `Implements`  
  
     省略可能です。 この手順が 1 つまたは複数を実装することを示します `Sub` の手順は、この手順を含むクラスまたは構造体によって実装されるインターフェイスで定義されている 1 つずつです。 参照してください [ステートメントを実装します](../../../visual-basic/language-reference/statements/implements-statement.md)します。  
  
-   `implementslist`  
  
     `Implements` を指定する場合は、必ず指定します。 実装される `Sub` プロシージャのリストです。  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     `implementedprocedure` の構文と指定項目は次のとおりです。  
  
     `interface.definedname`  
  
    |||  
    |-|-|  
    |パーツ|説明|  
    |`interface`|必須です。 このプロシージャによって実装されるインターフェイスの名前には、クラスまたは構造体を含むのです。|  
    |`definedname`|必須です。 `interface` の中でプロシージャを定義するために使用する名前。|  
  
-   `Handles`  
  
     省略可能です。 この手順が 1 つまたは複数の特定のイベントを処理できることを示します。 参照してください [処理](../../../visual-basic/language-reference/statements/handles-clause.md)します。  
  
-   `eventlist`  
  
     `Handles` を指定する場合は、必ず指定します。 このプロシージャを処理するイベントのリスト。  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     `eventspecifier` の構文と指定項目は次のとおりです。  
  
     `eventvariable.event`  
  
    |||  
    |-|-|  
    |パーツ|説明|  
    |`eventvariable`|必須です。 オブジェクト変数がクラスまたはイベントを発生させる構造体のデータ型で宣言します。|  
    |`event`|必須です。 このプロシージャを処理するイベントの名前。|  
  
-   `statements`  
  
     省略可能です。 このプロシージャ内で実行するステートメントのブロックです。  
  
-   `End Sub`  
  
     このプロシージャの定義を終了します。  
  
## <a name="remarks"></a>コメント  
 すべての実行可能コードは、プロシージャの中にする必要があります。 使用して、 `Sub` プロシージャは、呼び出し元のコードに値を返すしたくない場合。 使用して、 `Function` プロシージャは、値を取得する場合。  
  
## <a name="defining-a-sub-procedure"></a>Sub プロシージャの定義  
 定義する、 `Sub` 手順をモジュール レベルでのみです。 Sub プロシージャの宣言コンテキストは、そのため、必要があります、クラス、構造体、モジュールの場合、またはインターフェイスとソース ファイル、名前空間、プロシージャ、またはブロックすることはできません。 詳細については、次を参照してください。 [宣言コンテキストとアクセス レベルの既定の](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)です。  
  
 `Sub` パブリック アクセスを既定値をプロシージャです。 アクセス修飾子を使用して、これらのアクセス レベルを調整できます。  
  
 プロシージャで使用する場合、 `Implements` キーワードを含むクラスまたは構造体が必要、 `Implements` 直後に続くステートメントの `Class` または `Structure` ステートメントです。  `Implements` ステートメントで指定されている各インターフェイスを含める必要があります `implementslist`します。 ただし、インターフェイスを定義する名前、 `Sub` (で `definedname`) このプロシージャの名前と一致する必要はありません (で `name`)。  
  
## <a name="returning-from-a-sub-procedure"></a>Sub プロシージャから返す処理  
 ときに、 `Sub` その呼び出し元ステートメントの後にステートメントを使用して、プロシージャ呼び出し元のコードに戻ると、実行が継続します。  
  
 次の例から戻るとき、 `Sub` プロシージャです。  
  
```vb#  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
  `Exit Sub` と `Return` ステートメントからすぐに終了が発生する、 `Sub` プロシージャです。 任意の数の `Exit Sub` と `Return` ステートメントが任意の場所で、手順と混在させることが `Exit Sub` と `Return` ステートメントです。  
  
## <a name="calling-a-sub-procedure"></a>Sub プロシージャの呼び出し  
 呼び出す、 `Sub` をステートメントで、プロシージャ名を使用し、かっこで囲まれた、引数リストでその名前を次の手順です。 すべての引数を指定しない場合にのみ、かっこを省略することができます。 ただし、コードは常にかっこを含める場合は、読みやすくします。  
  
 A `Sub` プロシージャと `Function` プロシージャはパラメーターを持つし、一連のステートメントを実行します。 ただし、 `Function` 値、およびプロシージャを返します。 `Sub` プロシージャがありません。 したがって、使用することはできません、 `Sub` 式」の手順です。  
  
 使用することができます、 `Call` キーワードを呼び出したときに、 `Sub` プロシージャが、そのキーワードは、ほとんどの用途をお勧めしません。 詳細については、次を参照してください。 [Call ステートメント](../../../visual-basic/language-reference/statements/call-statement.md)します。  
  
 Visual Basic では、算術式内部の効率を向上させることがあります再配置します。 そのため、引数リストには、その他のプロシージャを呼び出す式が含まれている場合を前提にしないでこれらの式が特定の順序で呼び出されます。  
  
## <a name="async-sub-procedures"></a>Async Sub プロシージャ  
 非同期機能を使用すると、明示的なコールバックの使用や複数の関数やラムダ式で、コードを手動で分割を行わず非同期関数を呼び出すことができます。  
  
 使用してプロシージャをマークした場合、 [Async](../../../visual-basic/language-reference/modifiers/async.md) 修飾子は、使用できます、 [Await](../../../visual-basic/language-reference/operators/await-operator.md) プロシージャ内の演算子です。 達するとを制御すると、 `Await` 内の式、 `Async` 手順が、呼び出し元に制御が戻るし、待機中のタスクが完了するまでの手順で進行状況が中断します。 タスクが完了したら、プロシージャの実行を再開できます。  
  
> [!NOTE]
>   `Async` のいずれか最初待機中のオブジェクトが完了していないことが検出された場合、呼び出し元へを返し、 `Async` プロシージャに達すると、どちらかがします。  
  
 マークすることも、 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md) で、 `Async` 修飾子です。  `Async` 関数の戻り値の型を設定できます <xref:System.Threading.Tasks.Task%601> または <xref:System.Threading.Tasks.Task>します。 例を後で、このトピックでは、 `Async` 関数の戻り値の型を持つ <xref:System.Threading.Tasks.Task%601>します。  
  
 `Async` `Sub` プロシージャは、主に使用、イベント ハンドラーの値が返されることはできません。  `Async``Sub` プロシージャを待機することはできないと、呼び出し元の `Async``Sub` プロシージャは、例外をキャッチできませんを `Sub` プロシージャがスローされます。  
  
  `Async` プロシージャは、いずれかを宣言できません [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) パラメーター。  
  
 詳細については `Async` の手順を参照してください [Async および Await を使用した非同期プログラミング](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md), 、[非同期プログラムにおける制御のフロー](../Topic/Control%20Flow%20in%20Async%20Programs%20\(C%23%20and%20Visual%20Basic\).md), 、および [Async を返す型](../Topic/Async%20Return%20Types%20\(C%23%20and%20Visual%20Basic\).md)します。  
  
## <a name="example"></a>例  
 次の例では、 `Sub` 名、パラメーター、およびの本体を形成するコードを定義するステートメント、 `Sub` プロシージャです。  
  
 [!code-vb[VbVbalrStatements#58](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]  
  
## <a name="example"></a>例  
 次の例で `DelayAsync` 、 `Async``Function` の戻り値の型を持つ <xref:System.Threading.Tasks.Task%601>します。 `DelayAsync` には、整数を返す `Return` ステートメントがあります。 したがって、関数宣言の `DelayAsync` の戻り値の型を持つ必要があります `Task(Of Integer)`します。 戻り値の型である `Task(Of Integer)`, の評価、 `Await` 式 `DoSomethingAsync` として次のステートメントに示す整数を生成する: `Dim result As Integer = Await delayTask`です。  
  
  `startButton_Click` 手順の例は、 `Async Sub` プロシージャです。  `DoSomethingAsync` は、 `Async` 関数への呼び出しのタスク `DoSomethingAsync` として次のステートメントに示す、待機する必要があります: `Await DoSomethingAsync()`です。  `startButton_Click``Sub` でプロシージャを定義する必要があります、 `Async` 修飾子があるため、 `Await` 式です。  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Implements ステートメント](../../../visual-basic/language-reference/statements/implements-statement.md)   
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)   
 [パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)   
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Call ステートメント](../../../visual-basic/language-reference/statements/call-statement.md)   
 [の](../../../visual-basic/language-reference/statements/of-clause.md)   
 [パラメーター配列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [方法: ジェネリック クラスを使用して](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [トラブルシューティングの手順](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [部分メソッド](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
---
title: "Function ステートメント (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Function
helpviewer_keywords:
- procedures [Visual Basic], creating
- Function procedures [Visual Basic], Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword [Visual Basic], Function statements
- Private keyword [Visual Basic], Function statements
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- Public keyword [Visual Basic], in Function statement
- ByVal keyword [Visual Basic], Function statements
- procedures [Visual Basic], recursive
- Implements keyword [Visual Basic], Function statements
- procedures [Visual Basic], returning values
- Exit statement [Visual Basic], in Function procedures
- recursive procedures
- As keyword [Visual Basic], in Function statement
- Optional keyword [Visual Basic], Function statements
- Function statement [Visual Basic]
- Visual Basic code, Function procedures
- procedures [Visual Basic], function
- ByRef keyword [Visual Basic], Function statements
- Friend keyword [Visual Basic], Function statements
- End keyword [Visual Basic], Function statements
- Handles keyword [Visual Basic], Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
caps.latest.revision: "62"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 667ab7ceb54e1f339fd645883ca2686c0cbb72b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="function-statement-visual-basic"></a>Function ステートメント (Visual Basic)
宣言名、パラメーター、およびコードを定義する、`Function`プロシージャです。  
  
## <a name="syntax"></a>構文  
  
```  
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]  
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Function ]  
    [ statements ]  
End Function  
```  
  
## <a name="parts"></a>指定項目  
  
-   `attributelist`  
  
     省略可能です。 参照してください[属性一覧](attribute-list.md)です。  
  
-   `accessmodifier`  
  
     省略可能です。 次のいずれかの値を指定します。  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     参照してください[Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。  
  
-   `proceduremodifiers`  
  
     省略可能です。 次のいずれかの値を指定します。  
  
    -   [オーバーロード](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     省略可能です。 参照してください[共有](../../../visual-basic/language-reference/modifiers/shared.md)です。  
  
-   `Shadows`  
  
     省略可能です。 参照してください[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)です。  
  
-   `Async`  
  
     省略可能です。 参照してください[Async](../../../visual-basic/language-reference/modifiers/async.md)です。  
  
-   `Iterator`  
  
     省略可能です。 参照してください[反復子](../../../visual-basic/language-reference/modifiers/iterator.md)です。  
  
-   `name`  
  
     必須です。 プロシージャの名前。 参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。  
  
-   `typeparamlist`  
  
     省略可能です。 ジェネリック プロシージャの型パラメーターの一覧です。 参照してください[のリストを入力](type-list.md)です。  
  
-   `parameterlist`  
  
     省略可能です。 このプロシージャのパラメーターを表すローカル変数名の一覧です。 参照してください[パラメーター リスト](parameter-list.md)です。  
  
-   `returntype`  
  
     場合は必須`Option Strict`は`On`します。 このプロシージャによって返される値のデータ型。  
  
-   `Implements`  
  
     省略可能です。 この手順には、1 つまたは複数が実装されていることを示します`Function`プロシージャ、このプロシージャの包含クラスまたは構造体によって実装されるインターフェイスで定義されている 1 つずつです。 参照してください[ステートメントを実装します](implements-statement.md)です。  
  
-   `implementslist`  
  
     `Implements` を指定する場合は、必ず指定します。 実装される `Function` プロシージャのリストです。  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     `implementedprocedure` の構文と指定項目は次のとおりです。  
  
     `interface.definedname`  
  
    |パーツ|説明|  
    |---|---|  
    |`interface`|必須です。 このプロシージャによって実装されるインターフェイスの名前には、クラスまたは構造体を含むのです。|  
    |`definedname`|必須です。 `interface` の中でプロシージャを定義するために使用する名前。|  
  
-   `Handles`  
  
     省略可能です。 この手順が 1 つまたは複数の特定のイベントを処理できることを示します。 参照してください[処理](handles-clause.md)です。  
  
-   `eventlist`  
  
     `Handles` を指定する場合は、必ず指定します。 このプロシージャを処理するイベントの一覧です。  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     `eventspecifier` の構文と指定項目は次のとおりです。  
  
     `eventvariable.event`  
  
    |パーツ|説明|  
    |---|---|  
    |`eventvariable`|必須です。 クラスまたはイベントを発生させる構造体のデータ型で宣言されたオブジェクト変数です。|  
    |`event`|必須です。 このプロシージャを処理するイベントの名前。|  
  
-   `statements`  
  
     省略可能です。 このプロシージャ内で実行されるステートメントのブロックです。  
  
-   `End Function`  
  
     このプロシージャの定義を終了します。  
  
## <a name="remarks"></a>コメント  
 すべての実行可能コードは、プロシージャ内でなければなりません。 さらに、各プロシージャはクラス、構造体、または親のクラス、構造体、またはモジュールとして参照されるモジュール内で宣言されます。  
  
 呼び出し元のコードに値を返すを使用して、`Function`プロシージャです。 それ以外の場合、を使用して、`Sub`プロシージャです。  
  
## <a name="defining-a-function"></a>関数を定義します。  
 定義することができます、`Function`手順モジュール レベルでのみです。 そのため、関数の宣言コンテキストは、クラス、構造体、モジュールの場合、またはインターフェイスにする必要があり、ソース ファイル、名前空間、プロシージャ、またはブロックすることはできません。 詳細については、「[宣言コンテキストと既定のアクセス レベル](declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 `Function`パブリック アクセスにプロシージャの既定値です。 アクセス修飾子を使用してこれらのアクセス レベルを調整できます。  
  
 A`Function`プロシージャがプロシージャが返す値のデータ型を宣言できます。 任意のデータ型または列挙型、構造体、クラスまたはインターフェイスの名前を指定することができます。 指定しない場合は、`returntype`プロシージャは、パラメーターを返します`Object`です。  
  
 この手順で使用する場合、`Implements`キーワードを含むクラスまたは構造体も必要、`Implements`直後に続くステートメント、`Class`または`Structure`ステートメントです。 `Implements`ステートメントで指定されている各インターフェイスを含める必要があります`implementslist`です。 ただし、インターフェイスを定義する名前、 `Function` (で`definedname`) このプロシージャの名前と一致する必要はありません (で`name`)。  
  
> [!NOTE]
>  関数の式をインラインで定義するのに、ラムダ式を使用することができます。 詳細については、次を参照してください。[関数式](../../../visual-basic/language-reference/operators/function-expression.md)と[ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)です。  
  
## <a name="returning-from-a-function"></a>関数から戻る  
 ときに、`Function`プロシージャを呼び出したステートメントに続くステートメントを使用して、プロシージャは、呼び出し元のコードを返します、実行が継続します。  
  
 関数から値を返す、関数名に値を割り当てるか、含めることで、`Return`ステートメントです。  
  
 `Return`ステートメントは、同時に戻り値を割り当てるし、次の例のように、関数を終了します。  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_1.vb)]  
  
 次の例では、戻り値を割り当てて、関数名に`myFunction`しを使用して、`Exit Function`を返すステートメントです。  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_2.vb)]  
  
 `Exit Function`と`Return`ステートメントからすぐに終了が発生する、`Function`プロシージャです。 任意の数の`Exit Function`と`Return`ステートメントがどこにでも表示、プロシージャとを混在させること`Exit Function`と`Return`ステートメントです。  
  
 使用する場合`Exit Function`、値を割り当てることがなく`name`、プロシージャがで指定されているデータ型の既定値を返します`returntype`です。 場合`returntype`が指定されていない、プロシージャが返されます`Nothing`の既定値は`Object`します。  
  
## <a name="calling-a-function"></a>関数の呼び出し  
 呼び出す、`Function`プロシージャ名、式内のかっこ内の引数リストを使用してプロシージャです。 任意の引数を指定していない場合にのみ、かっこを省略することができます。 ただし、コードは、常にかっこを含める場合より読みやすいです。  
  
 呼び出す、`Function`任意のライブラリを呼び出すことと同様の機能などの手順`Sqrt`、 `Cos`、または`ChrW`です。  
  
 使用して関数を呼び出すことができますも、`Call`キーワード。 その場合は、戻り値は無視されます。 使用、`Call`キーワードはほとんどの場合にお勧めしません。 詳細については、次を参照してください。 [Call ステートメント](call-statement.md)です。  
  
 Visual Basic では、算術式内部の効率を向上させることがあります再配置します。 そのため、使用しないでください、`Function`算術式、関数には、同じ式の変数の値が変更されたときの手順です。  
  
## <a name="async-functions"></a>非同期関数  
 *Async*機能は、明示的なコールバックの使用や複数の関数やラムダ式で、コードを手動で分割せずに非同期関数を呼び出すことができます。  
  
 持つ関数をマークする場合、 [Async](../../../visual-basic/language-reference/modifiers/async.md)修飾子、行うこともできます、 [Await](../../../visual-basic/language-reference/operators/await-operator.md)関数内の演算子。 達するとを制御すると、`Await`内の式、`Async`関数が、呼び出し元に制御が戻るし、待機中のタスクが完了するまで、関数の進行状況は中断されます。 タスクが完了したら、関数で実行を再開できます。  
  
> [!NOTE]
>  `Async`がまだ完了していない最初の待機中のオブジェクトを検出すると、プロシージャが呼び出し元に返しますまたはの末尾に達して、`Async`プロシージャ、先に生じた方です。  
  
 `Async`関数の戻り値の型を持つことができます<xref:System.Threading.Tasks.Task%601>または<xref:System.Threading.Tasks.Task>です。 例、`Async`関数の戻り値の型を持つ<xref:System.Threading.Tasks.Task%601>以下に示します。  
  
 `Async`関数は、いずれかを宣言できません[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)パラメーター。  
  
 A [Sub ステートメント](sub-statement.md)でマークできるも、`Async`修飾子です。 これは主に使用するイベント ハンドラーの値が返されることはできません。 `Async``Sub`プロシージャを待機することはできませんとの呼び出し元、`Async``Sub`プロシージャによってスローされる例外をキャッチできません、`Sub`プロシージャです。  
  
 詳細については`Async`関数を参照してください[Async および Await を使用した非同期プログラミング](../../../visual-basic/programming-guide/concepts/async/index.md)、[非同期プログラムにおける制御フロー](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)、および[Async 戻り値の型](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="iterator-functions"></a>反復子関数  
 *反復子*関数は、リストや配列など、コレクションに対するカスタム イテレーションを実行します。 Iterator 関数を使用して、 [Yield](yield-statement.md)を一度に 1 つの各要素を返すステートメントです。 ときに、 [Yield](yield-statement.md)ステートメントに達すると、コードの現在の場所が記憶されます。 次回、iterator 関数が呼び出されると、この位置から実行が再開されます。  
  
 使用して、クライアント コードから反復子を呼び出す、[ごとにしています.[次へ]](for-each-next-statement.md)ステートメントです。  
  
 反復子関数の戻り値の型を指定できます<xref:System.Collections.IEnumerable>、 <xref:System.Collections.Generic.IEnumerable%601>、 <xref:System.Collections.IEnumerator>、または<xref:System.Collections.Generic.IEnumerator%601>です。  
  
 詳細については、「[反復子](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)」をご覧ください。  
  
## <a name="example"></a>例  
 次の例では、`Function`名、パラメーター、およびの本体を構成するコードを宣言するステートメント、`Function`プロシージャです。 `ParamArray`修飾子により、可変個の引数を受け入れるように機能します。  
  
 [!code-vb[VbVbalrStatements#25](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_3.vb)]  
  
## <a name="example"></a>例  
 次の例では、前の例で宣言された関数を呼び出します。  
  
 [!code-vb[VbVbalrStatements#26](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_4.vb)]  
  
## <a name="example"></a>例  
 次の例では、`DelayAsync`は、`Async``Function`の戻り値の型を持つ<xref:System.Threading.Tasks.Task%601>します。 `DelayAsync` には、整数を返す `Return` ステートメントがあります。 そのため、関数宣言の`DelayAsync`の戻り値の型を持つ必要がある`Task(Of Integer)`です。 戻り値の型があるため`Task(Of Integer)`の評価、`Await`式`DoSomethingAsync`整数が生成されます。 これはこのステートメントではデモンストレーション:`Dim result As Integer = Await delayTask`です。  
  
 `startButton_Click`プロシージャは、の例、`Async Sub`プロシージャです。 `DoSomethingAsync`は、`Async`関数では、タスクへの呼び出しを`DoSomethingAsync`、次のステートメントで示すように待機する必要があります:`Await DoSomethingAsync()`です。 `startButton_Click``Sub`でプロシージャを定義する必要があります、`Async`修飾子があるため、`Await`式。  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/function-statement_5.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Sub ステートメント](sub-statement.md)  
 [Function プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)  
 [パラメーター リスト](parameter-list.md)  
 [Dim ステートメント](dim-statement.md)  
 [Call ステートメント](call-statement.md)  
 [Of](of-clause.md)  
 [パラメーター配列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [方法 : ジェネリック クラスを使用する](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [プロシージャのトラブルシューティング](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [Function 式](../../../visual-basic/language-reference/operators/function-expression.md)

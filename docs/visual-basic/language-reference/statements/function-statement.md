---
title: "ステートメント (Visual Basic) の機能 |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Function
dev_langs:
- VB
helpviewer_keywords:
- procedures, creating
- Function procedures, Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword, Function statements
- Private keyword, Function statements
- declarations, procedures
- procedures, declaration
- Public keyword, in Function statement
- ByVal keyword, Function statements
- procedures, recursive
- Implements keyword, Function statements
- procedures, returning values
- Exit statement, in Function procedures
- recursive procedures
- As keyword, in Function statement
- Optional keyword, Function statements
- Function statement
- Visual Basic code, Function procedures
- procedures, function
- ByRef keyword, Function statements
- Friend keyword, Function statements
- End keyword, Function statements
- Handles keyword, Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
caps.latest.revision: 62
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: af87477f81fab8406d726ebc8c81260b371d71c8
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="function-statement-visual-basic"></a>Function ステートメント (Visual Basic)
名前、パラメーター、および定義するコードを宣言して、`Function`プロシージャです。  
  
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
  
     省略可能です。 参照してください[属性一覧](attribute-list.md)します。  
  
-   `accessmodifier`  
  
     省略可能です。 次のいずれかの値を指定します。  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     参照してください[Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)します。  
  
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
  
     省略可能です。 参照してください[共有](../../../visual-basic/language-reference/modifiers/shared.md)します。  
  
-   `Shadows`  
  
     省略可能です。 参照してください[シャドウ](../../../visual-basic/language-reference/modifiers/shadows.md)します。  
  
-   `Async`  
  
     省略可能です。 参照してください[Async](../../../visual-basic/language-reference/modifiers/async.md)します。  
  
-   `Iterator`  
  
     省略可能です。 参照してください[反復子](../../../visual-basic/language-reference/modifiers/iterator.md)します。  
  
-   `name`  
  
     必須です。 プロシージャの名前。 参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)します。  
  
-   `typeparamlist`  
  
     省略可能です。 手順については、ジェネリック型パラメーターの一覧です。 参照してください[のリストを入力](type-list.md)します。  
  
-   `parameterlist`  
  
     省略可能です。 このプロシージャのパラメーターを表すローカル変数名の一覧です。 参照してください[パラメーター リスト](parameter-list.md)します。  
  
-   `returntype`  
  
     必要な場合`Option Strict`は`On`です。 このプロシージャによって返される値のデータ型。  
  
-   `Implements`  
  
     省略可能です。 この手順が&1; つまたは複数を実装することを示します`Function`の手順は、この手順を含むクラスまたは構造体によって実装されるインターフェイスで定義されている&1; つずつです。 参照してください[ステートメントを実装します](implements-statement.md)します。  
  
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
  
     省略可能です。 このプロシージャ内で実行されるステートメントのブロックです。  
  
-   `End Function`  
  
     このプロシージャの定義を終了します。  
  
## <a name="remarks"></a>コメント  
 すべての実行可能コードは、プロシージャの中にする必要があります。 さらに、各プロシージャは、クラス、構造体またはクラス、構造体、またはモジュールとして参照されているモジュール内で宣言されます。  
  
 呼び出し元のコードに値を返すには使用、`Function`プロシージャです。 それ以外の場合、を使用して、`Sub`プロシージャです。  
  
## <a name="defining-a-function"></a>関数を定義します。  
 定義する、`Function`手順をモジュール レベルでのみです。 そのため、関数の宣言コンテキストを使用して、クラス、構造体、モジュールの場合、またはインターフェイスがあります、ソース ファイル、名前空間、プロシージャ、またはブロックすることはできません。 詳細については、次を参照してください。[宣言コンテキストとアクセス レベルの既定の](declaration-contexts-and-default-access-levels.md)です。  
  
 `Function`パブリック アクセスを既定値をプロシージャです。 アクセス修飾子を使用してこれらのアクセス レベルを調整できます。  
  
 A`Function`プロシージャがプロシージャが返す値のデータ型を宣言できます。 任意のデータ型または列挙体、構造体、クラスまたはインターフェイスの名前を指定することができます。 指定しない場合、`returntype`プロシージャは、パラメーターを返します`Object`します。  
  
 この手順で使用する場合、`Implements`キーワードを含むクラスまたは構造体があります、`Implements`直後に続くステートメントの`Class`または`Structure`ステートメントです。 `Implements`ステートメントで指定されている各インターフェイスを含める必要があります`implementslist`します。 ただし、インターフェイスを定義する名前、 `Function` (で`definedname`) このプロシージャの名前と一致する必要はありません (で`name`)。  
  
> [!NOTE]
>  ラムダ式を使用すると、関数の式のインラインを定義します。 詳細については、次を参照してください。[関数式](../../../visual-basic/language-reference/operators/function-expression.md)と[ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)します。  
  
## <a name="returning-from-a-function"></a>関数から戻る  
 ときに、`Function`プロシージャを呼び出したステートメントに続くステートメントを使用して、プロシージャ呼び出し元のコードに戻ると、実行が継続します。  
  
 関数から値を返す、関数名に値を割り当てるか、含めることで、`Return`ステートメントです。  
  
 `Return`ステートメントは、同時に戻り値を割り当てるし、次の例のように、関数が終了します。  
  
 [!code-vb[VbVbalrStatements #&24;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_1.vb)]  
  
 次の例では、戻り値を割り当てて、関数名に`myFunction`し、使用して、`Exit Function`を返すステートメントです。  
  
 [!code-vb[VbVbalrStatements 第&23;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_2.vb)]  
  
 `Exit Function`と`Return`ステートメントからすぐに終了が発生する、`Function`プロシージャです。 任意の数の`Exit Function`と`Return`ステートメントが任意の場所で、手順と混在させることが`Exit Function`と`Return`ステートメントです。  
  
 使用する場合`Exit Function`、値を割り当てることがなく`name`で指定されているデータ型の既定値を返し`returntype`します。 場合`returntype`を返し、指定されていない`Nothing`の既定値は`Object`です。  
  
## <a name="calling-a-function"></a>関数を呼び出す  
 呼び出す、`Function`プロシージャ名、式の中で、かっこで囲まれた引数のリストを使用してプロシージャです。 すべての引数を指定していない場合にのみ、かっこを省略することができます。 ただし、コードは常にかっこを含める場合は、読みやすくします。  
  
 呼び出す、`Function`プロシージャなどの任意のライブラリを呼び出すことと同様の関数`Sqrt`、 `Cos`、または`ChrW`です。  
  
 使用して関数を呼び出すことができます、`Call`キーワードです。 その場合は、戻り値は無視されます。 使用、`Call`キーワードは、ほとんどの場合にお勧めしません。 詳細については、次を参照してください。 [Call ステートメント](call-statement.md)します。  
  
 Visual Basic では、算術式内部の効率を向上させることがあります再配置します。 そのため、使用しないでください、`Function`算術式、関数には、同じ式内の変数の値が変更されたときの手順です。  
  
## <a name="async-functions"></a>Async 関数  
 *Async*機能は、明示的なコールバックの使用や複数の関数やラムダ式で、コードを手動で分割を行わず、非同期関数を呼び出すことができます。  
  
 持つ関数をマークした場合、 [Async](../../../visual-basic/language-reference/modifiers/async.md)修飾子は、使用できます、 [Await](../../../visual-basic/language-reference/operators/await-operator.md)関数内の演算子です。 達するとを制御すると、`Await`内の式、`Async`関数は、呼び出し元に制御が戻るし、関数で進展が待機中のタスクが完了するまでです。 タスクが完了すると、関数の実行を再開できます。  
  
> [!NOTE]
>  `Async`がまだ完了していない最初の待機中のオブジェクトを検出するかとプロシージャを呼び出し元に返しますまたはの最後に、`Async`プロシージャか早い方です。  
  
 `Async`関数<xref:System.Threading.Tasks.Task%601>または<xref:System.Threading.Tasks.Task>.</xref:System.Threading.Tasks.Task></xref:System.Threading.Tasks.Task%601>の戻り値の型を設定できます 例、`Async`関数の戻り値の型を持つ<xref:System.Threading.Tasks.Task%601>を次に示します</xref:System.Threading.Tasks.Task%601>。  
  
 `Async`関数は、いずれかを宣言できません[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)パラメーター。  
  
 A [Sub ステートメント](sub-statement.md)でマークできるも、`Async`修飾子です。 これは主に使用、イベント ハンドラーの値が返されることはできません。 `Async``Sub`プロシージャを待機することはできないと、呼び出し元の`Async``Sub`プロシージャによってスローされる例外をキャッチできません、`Sub`プロシージャです。  
  
 詳細については`Async`関数を参照してください[Async および Await を使用した非同期プログラミング](../../../visual-basic/programming-guide/concepts/async/index.md)、[非同期プログラムにおける制御のフロー](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)、および[Async を返す型](../../../visual-basic/programming-guide/concepts/async/async-return-types.md)します。  
  
## <a name="iterator-functions"></a>反復子関数  
 *反復子*関数は、リストや配列などのコレクションに対するカスタムの反復を実行します。 Iterator 関数を使用して、 [Yield](yield-statement.md)ステートメントを一度に&1; つの各要素を返します。 ときに、 [Yield](yield-statement.md)ステートメントに達すると、コード内の現在位置が記憶されます。 次回の反復子関数が呼び出されたとき、その場所から実行が再開されます。  
  
 使用して、クライアント コードから反復子を呼び出す、[ごとにしています.次](for-each-next-statement.md)ステートメントです。  
  
 反復子関数の戻り値の型を指定できます<xref:System.Collections.IEnumerable>、 <xref:System.Collections.Generic.IEnumerable%601>、 <xref:System.Collections.IEnumerator>、または<xref:System.Collections.Generic.IEnumerator%601>.</xref:System.Collections.Generic.IEnumerator%601> </xref:System.Collections.IEnumerator> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable>  
  
 詳細については、「[反復子](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)」をご覧ください。  
  
## <a name="example"></a>例  
 次の例では、`Function`を名前、パラメーター、およびコードの本体を形成する宣言ステートメント、`Function`プロシージャです。 `ParamArray`修飾子により、可変個の引数を受け入れるように機能します。  
  
 [!code-vb[VbVbalrStatements&#25;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_3.vb)]  
  
## <a name="example"></a>例  
 次の例では、前の例で宣言された関数を呼び出します。  
  
 [!code-vb[VbVbalrStatements #&26;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_4.vb)]  
  
## <a name="example"></a>例  
 次の例で`DelayAsync`は、 `Async``Function` <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601>の戻り値の型を持つ `DelayAsync` には、整数を返す `Return` ステートメントがあります。 したがって、関数宣言の`DelayAsync`の戻り値の型を持っている必要がある`Task(Of Integer)`です。 戻り値の型である`Task(Of Integer)`の評価、`Await`式`DoSomethingAsync`整数値を生成します。 これを次のステートメントに示します:`Dim result As Integer = Await delayTask`です。  
  
 `startButton_Click`手順の例は、`Async Sub`プロシージャです。 `DoSomethingAsync`は、`Async`関数への呼び出しのタスク`DoSomethingAsync`、次のステートメントで示すように、待機する必要があります:`Await DoSomethingAsync()`です。 `startButton_Click``Sub`でプロシージャを定義する必要があります、`Async`修飾子があるため、`Await`式です。  
  
 [!code-vb[csAsyncMethod&1;](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/function-statement_5.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Sub ステートメント](sub-statement.md)   
 [Function プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [パラメーター リスト](parameter-list.md)   
 [Dim ステートメント](dim-statement.md)   
 [Call ステートメント](call-statement.md)   
 [Of](of-clause.md)   
 [パラメーター配列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [方法: ジェネリック クラスを使用して](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [トラブルシューティングの手順](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Function 式](../../../visual-basic/language-reference/operators/function-expression.md)


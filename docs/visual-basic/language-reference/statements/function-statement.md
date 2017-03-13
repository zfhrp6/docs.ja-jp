---
title: "Function ステートメント (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Function"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "手順については、作成します。"
  - "Function プロシージャ、関数ステートメントの構文"
  - "関数 [Visual Basic] function プロシージャ"
  - "ParamArray キーワード、関数ステートメント"
  - "Private キーワード、関数ステートメント"
  - "プロシージャの宣言"
  - "手順については、宣言"
  - "Function ステートメントの public キーワード"
  - "ByVal キーワード、関数ステートメント"
  - "手順については、再帰的な"
  - "Implements キーワード、関数ステートメント"
  - "手順については、値を返す"
  - "Function プロシージャの exit ステートメント"
  - "再帰プロシージャ"
  - "Function ステートメントのキーワードとして"
  - "Function ステートメントの省略可能なキーワード"
  - "Function ステートメント"
  - "Visual Basic コード、Function プロシージャ"
  - "プロシージャ、関数"
  - "ByRef キーワード、関数ステートメント"
  - "Friend キーワード、関数ステートメント"
  - "End キーワード Function ステートメント"
  - "Handles キーワード、関数ステートメント"
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
caps.latest.revision: 62
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 62
---
# Function ステートメント (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

名前、パラメーター、および定義するコードを宣言して、 `Function` プロシージャです。  
  
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
  
     省略可能です。 参照してください [属性一覧](../../../visual-basic/language-reference/statements/attribute-list.md)します。  
  
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
  
-   `Iterator`  
  
     省略可能です。 参照してください [反復子](../../../visual-basic/language-reference/modifiers/iterator.md)します。  
  
-   `name`  
  
     必須です。 プロシージャの名前。 「 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。  
  
-   `typeparamlist`  
  
     省略可能です。 手順については、ジェネリック型パラメーターの一覧です。 参照してください [のリストを入力](../../../visual-basic/language-reference/statements/type-list.md)します。  
  
-   `parameterlist`  
  
     省略可能です。 このプロシージャのパラメーターを表すローカル変数名の一覧です。 参照してください [パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)します。  
  
-   `returntype`  
  
     必要な場合 `Option Strict` は `On`です。 このプロシージャによって返される値のデータ型。  
  
-   `Implements`  
  
     省略可能です。 この手順が 1 つまたは複数を実装することを示します `Function` の手順は、この手順を含むクラスまたは構造体によって実装されるインターフェイスで定義されている 1 つずつです。 参照してください [ステートメントを実装します](../../../visual-basic/language-reference/statements/implements-statement.md)します。  
  
-   `implementslist`  
  
     `Implements` を指定する場合は、必ず指定します。 実装される `Function` プロシージャのリストです。  
  
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
  
     省略可能です。 このプロシージャ内で実行されるステートメントのブロックです。  
  
-   `End Function`  
  
     このプロシージャの定義を終了します。  
  
## <a name="remarks"></a>コメント  
 すべての実行可能コードは、プロシージャの中にする必要があります。 さらに、各プロシージャは、クラス、構造体またはクラス、構造体、またはモジュールとして参照されているモジュール内で宣言されます。  
  
 呼び出し元のコードに値を返すには使用、 `Function` プロシージャです。 それ以外の場合、を使用して、 `Sub` プロシージャです。  
  
## <a name="defining-a-function"></a>関数を定義します。  
 定義する、 `Function` 手順をモジュール レベルでのみです。 そのため、関数の宣言コンテキストを使用して、クラス、構造体、モジュールの場合、またはインターフェイスがあります、ソース ファイル、名前空間、プロシージャ、またはブロックすることはできません。 詳細については、次を参照してください。 [宣言コンテキストとアクセス レベルの既定の](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)です。  
  
 `Function` パブリック アクセスを既定値をプロシージャです。 アクセス修飾子を使用してこれらのアクセス レベルを調整できます。  
  
 A `Function` プロシージャがプロシージャが返す値のデータ型を宣言できます。 任意のデータ型または列挙体、構造体、クラスまたはインターフェイスの名前を指定することができます。 指定しない場合、 `returntype` プロシージャは、パラメーターを返します `Object`します。  
  
 この手順で使用する場合、 `Implements` キーワードを含むクラスまたは構造体があります、 `Implements` 直後に続くステートメントの `Class` または `Structure` ステートメントです。  `Implements` ステートメントで指定されている各インターフェイスを含める必要があります `implementslist`します。 ただし、インターフェイスを定義する名前、 `Function` (で `definedname`) このプロシージャの名前と一致する必要はありません (で `name`)。  
  
> [!NOTE]
>  ラムダ式を使用すると、関数の式のインラインを定義します。 詳細については、次を参照してください。 [関数式](../../../visual-basic/language-reference/operators/function-expression.md) と [ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)します。  
  
## <a name="returning-from-a-function"></a>関数から戻る  
 ときに、 `Function` 、プロシージャを呼び出したステートメントに続くステートメントを使用して、プロシージャ呼び出し元のコードに戻ると、実行が継続します。  
  
 関数から値を返す、関数名に値を割り当てるか、含めることで、 `Return` ステートメントです。  
  
  `Return` ステートメントは、同時に戻り値を割り当てるし、次の例のように、関数が終了します。  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_1.vb)]  
  
 次の例では、戻り値を割り当てて、関数名に `myFunction` し、使用して、 `Exit Function` を返すステートメントです。  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_2.vb)]  
  
  `Exit Function` と `Return` ステートメントからすぐに終了が発生する、 `Function` プロシージャです。 任意の数の `Exit Function` と `Return` ステートメントが任意の場所で、手順と混在させることが `Exit Function` と `Return` ステートメントです。  
  
 使用する場合 `Exit Function` 値を割り当てることがなく `name`, で指定されているデータ型の既定値を返し `returntype`します。 場合 `returntype` を返し、指定されていない `Nothing`, の既定値は `Object`です。  
  
## <a name="calling-a-function"></a>関数を呼び出す  
 呼び出す、 `Function` プロシージャ名、式の中で、かっこで囲まれた引数のリストを使用してプロシージャです。 すべての引数を指定していない場合にのみ、かっこを省略することができます。 ただし、コードは常にかっこを含める場合は、読みやすくします。  
  
 呼び出す、 `Function` プロシージャなどの任意のライブラリを呼び出すことと同様の関数 `Sqrt`, 、`Cos`, 、または `ChrW`です。  
  
 使用して関数を呼び出すことができます、 `Call` キーワードです。 その場合は、戻り値は無視されます。 使用、 `Call` キーワードは、ほとんどの場合にお勧めしません。 詳細については、次を参照してください。 [Call ステートメント](../../../visual-basic/language-reference/statements/call-statement.md)します。  
  
 Visual Basic では、算術式内部の効率を向上させることがあります再配置します。 そのため、使用しないでください、 `Function` 算術式、関数には、同じ式内の変数の値が変更されたときの手順です。  
  
## <a name="async-functions"></a>Async 関数  
  *Async* 機能は、明示的なコールバックの使用や複数の関数やラムダ式で、コードを手動で分割を行わず、非同期関数を呼び出すことができます。  
  
 持つ関数をマークした場合、 [Async](../../../visual-basic/language-reference/modifiers/async.md) 修飾子は、使用できます、 [Await](../../../visual-basic/language-reference/operators/await-operator.md) 関数内の演算子です。 達するとを制御すると、 `Await` 内の式、 `Async` 関数は、呼び出し元に制御が戻るし、関数で進展が待機中のタスクが完了するまでです。 タスクが完了すると、関数の実行を再開できます。  
  
> [!NOTE]
>   `Async` がまだ完了していない最初の待機中のオブジェクトを検出するかとプロシージャを呼び出し元に返しますまたはの最後に、 `Async` プロシージャか早い方です。  
  
  `Async` 関数の戻り値の型を設定できます <xref:System.Threading.Tasks.Task%601> または <xref:System.Threading.Tasks.Task>します。 例、 `Async` 関数の戻り値の型を持つ <xref:System.Threading.Tasks.Task%601> を次に示します。  
  
  `Async` 関数は、いずれかを宣言できません [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) パラメーター。  
  
 A [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md) でマークできるも、 `Async` 修飾子です。 これは主に使用、イベント ハンドラーの値が返されることはできません。  `Async``Sub` プロシージャを待機することはできないと、呼び出し元の `Async``Sub` プロシージャによってスローされる例外をキャッチできません、 `Sub` プロシージャです。  
  
 詳細については `Async` 関数を参照してください [Async および Await を使用した非同期プログラミング](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md), 、[非同期プログラムにおける制御のフロー](../Topic/Control%20Flow%20in%20Async%20Programs%20\(C%23%20and%20Visual%20Basic\).md), 、および [Async を返す型](../Topic/Async%20Return%20Types%20\(C%23%20and%20Visual%20Basic\).md)します。  
  
## <a name="iterator-functions"></a>反復子関数  
  *反復子* 関数は、リストや配列などのコレクションに対するカスタムの反復を実行します。 Iterator 関数を使用して、 [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) ステートメントを一度に 1 つの各要素を返します。 ときに、 [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) ステートメントに達すると、コード内の現在位置が記憶されます。 次回の反復子関数が呼び出されたとき、その場所から実行が再開されます。  
  
 使用して、クライアント コードから反復子を呼び出す、 [ごとにしています.次](../../../visual-basic/language-reference/statements/for-each-next-statement.md) ステートメントです。  
  
 反復子関数の戻り値の型を指定できます <xref:System.Collections.IEnumerable>, 、<xref:System.Collections.Generic.IEnumerable%601>, 、<xref:System.Collections.IEnumerator>, 、または <xref:System.Collections.Generic.IEnumerator%601>します。  
  
 詳細については、「 [反復子](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、 `Function` を名前、パラメーター、およびコードの本体を形成する宣言ステートメント、 `Function` プロシージャです。  `ParamArray` 修飾子により、可変個の引数を受け入れるように機能します。  
  
 [!code-vb[VbVbalrStatements#25](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_3.vb)]  
  
## <a name="example"></a>例  
 次の例では、前の例で宣言された関数を呼び出します。  
  
 [!code-vb[VbVbalrStatements#26](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_4.vb)]  
  
## <a name="example"></a>例  
 次の例で `DelayAsync` は、 `Async``Function` の戻り値の型を持つ <xref:System.Threading.Tasks.Task%601>します。 `DelayAsync` には、整数を返す `Return` ステートメントがあります。 したがって、関数宣言の `DelayAsync` の戻り値の型を持っている必要がある `Task(Of Integer)`です。 戻り値の型である `Task(Of Integer)`, の評価、 `Await` 式 `DoSomethingAsync` 整数値を生成します。 これを次のステートメントに示します: `Dim result As Integer = Await delayTask`です。  
  
  `startButton_Click` 手順の例は、 `Async Sub` プロシージャです。  `DoSomethingAsync` は、 `Async` 関数への呼び出しのタスク `DoSomethingAsync` 、次のステートメントで示すように、待機する必要があります: `Await DoSomethingAsync()`です。  `startButton_Click``Sub` でプロシージャを定義する必要があります、 `Async` 修飾子があるため、 `Await` 式です。  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/function-statement_5.vb)]  
  
## <a name="see-also"></a>「  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Function プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)   
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Call ステートメント](../../../visual-basic/language-reference/statements/call-statement.md)   
 [の](../../../visual-basic/language-reference/statements/of-clause.md)   
 [パラメーター配列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [方法: ジェネリック クラスを使用して](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [トラブルシューティングの手順](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [関数式](../../../visual-basic/language-reference/operators/function-expression.md)
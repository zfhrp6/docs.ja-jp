---
title: For Each...Next ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ForEach
- vb.ForEachNext
- vb.Each
- ForEachNext
helpviewer_keywords:
- infinite loops
- Next statement [Visual Basic], For Each...Next
- endless loops
- loop structures [Visual Basic], For Each...Next
- loops, endless
- Each keyword [Visual Basic]
- instructions, repeating
- For Each statement [Visual Basic]
- collections, instruction repetition
- loops, infinite
- For Each...Next statements
- For keyword [Visual Basic], For Each...Next statements
- Exit statement [Visual Basic], For Each...Next statements
- iteration
ms.assetid: ebce3120-95c3-42b1-b70b-fa7da40c75e2
ms.openlocfilehash: ec7e5196bcb939631f4bf426f2e94cddc0c88a9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605382"
---
# <a name="for-eachnext-statement-visual-basic"></a>For Each...Next ステートメント (Visual Basic)
コレクションの各要素に対して、ステートメントのグループを繰り返します。  
  
## <a name="syntax"></a>構文  
  
```  
For Each element [ As datatype ] In group  
    [ statements ]  
    [ Continue For ]  
    [ statements ]  
    [ Exit For ]  
    [ statements ]  
Next [ element ]  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`element`|必要な`For Each`ステートメントです。 省略可能で、`Next`ステートメントです。 変数。 コレクションの要素を反復処理するために使用します。|  
|`datatype`|場合は必須`element`既に宣言されていません。 データ型`element`です。|  
|`group`|必須。 コレクション型またはオブジェクト型を含む変数を指定します。 コレクションを参照する対象で、`statements`繰り返されるはします。|  
|`statements`|任意。 1 つまたは複数のステートメント間`For Each`と`Next`内の各項目で実行される`group`です。|  
|`Continue For`|任意。 先頭に制御を転送、`For Each`ループします。|  
|`Exit For`|任意。 うちの制御を転送、`For Each`ループします。|  
|`Next`|必須。 定義を終了、`For Each`ループします。|  
  
## <a name="simple-example"></a>簡単な例  
 使用して、`For Each`しています.`Next`コレクションまたは配列の各要素の一連のステートメントを繰り返すときループします。  
  
> [!TIP]
>  A[をしています.次のステートメントの](../../../visual-basic/language-reference/statements/for-next-statement.md)うまくループの各反復処理を制御変数に関連付けるし、その変数の最初と最後の値を決定することができます。 ただし、コレクションを扱う場合は、最初と最後の値の概念が意味を持つと、コレクションには、要素の数がわからないとは限りません。 このような場合で、`For Each`しています.`Next`ループは多くの場合があることをお勧めします。  
  
 次の例で、`For Each`しています.`Next` ステートメントは、リスト コレクションのすべての要素を反復処理します。  
  
 [!code-vb[VbVbalrStatements#121](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_1.vb)]  
  
 例については、次を参照してください。[コレクション](../../../standard/collections/index.md)と[配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)です。  
  
## <a name="nested-loops"></a>入れ子になったループ  
 入れ子にすることができます`For Each`別内で 1 つのループを記述することによってループします。  
  
 次の例で入れ子になった`For Each`しています.`Next` 構造体。  
  
 [!code-vb[VbVbalrStatements#122](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_2.vb)]  
  
 ループを入れ子にする場合は、各ループが一意なが必要`element`変数。  
  
 さまざまな種類の他の制御構造を入れ子にすることもできます。 詳細については、次を参照してください。[制御構造の入れ子になった](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)です。  
  
## <a name="exit-for-and-continue-for"></a>終了し、続行  
 [Exit For](../../../visual-basic/language-reference/statements/exit-statement.md)ステートメントは、実行を終了する、`For`しています.`Next` これに続くステートメントにループと転送の制御、`Next`ステートメントです。  
  
 `Continue For`ステートメントに制御を移しますすぐに、ループの次の反復処理します。 詳細については、次を参照してください。 [Continue ステートメント](../../../visual-basic/language-reference/statements/continue-statement.md)です。  
  
 次の例を使用する方法を示しています、`Continue For`と`Exit For`ステートメントです。  
  
 [!code-vb[VbVbalrStatements#123](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_3.vb)]  
  
 任意の数を配置する`Exit For`内のステートメント、`For Each`ループします。 使用すると内で入れ子になった`For Each`ループ、`Exit For`終了して入れ子の上位のレベルに最も内側のループと転送コントロールの実行制御が移ります。  
  
 `Exit For` いくつかの条件の評価後は、よく使用などで、`If`しています.`Then`...`Else`構造体。 使用することができます`Exit For`次の条件。  
  
-   反復処理を続行するは、不要なまたは不可能です。 値が間違っているか、終了要求によってためと考えられます。  
  
-   例外がキャッチされました、`Try`しています.`Catch`...`Finally`.使用する場合があります`Exit For`の最後に、`Finally`ブロックします。  
  
-   これは、大規模なまたは無限も可能回数だけ実行できるループ、無限ループがあります。 このような条件を検出した場合を使用できます`Exit For`ループをエスケープするためにします。 詳細については、次を参照してください[操作を行います...ステートメントをループ](../../../visual-basic/language-reference/statements/do-loop-statement.md)です。  
  
## <a name="iterators"></a>Iterators  
 使用する、*反復子*コレクションに対するカスタム イテレーションを実行します。 関数は、反復子または`Get`アクセサー。 使用して、`Yield`ステートメントを一度にいずれかのコレクションの各要素を返します。  
  
 使用して、反復子を呼び出す、`For Each...Next`ステートメントです。 `For Each` ループの各イテレーションは、反復子を呼び出します。 ときに、`Yield`ステートメントが、反復子の式に到達、`Yield`ステートメントが返され、コードの現在の位置が保持されます。 次回、反復子が呼び出されると、この位置から実行が再開されます。  
  
 次の例では、iterator 関数を使用します。 Iterator 関数が、`Yield`内にあるステートメント、[をしています.[次へ]](../../../visual-basic/language-reference/statements/for-next-statement.md)ループします。 `ListEvenNumbers`メソッドは、の各反復処理、`For Each`ステートメント本体を作成、関数の呼び出しを反復子を次に進みます`Yield`ステートメントです。  
  
 [!code-vb[VbVbalrStatements#127](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_4.vb)]  
  
 詳細については、次を参照してください。[反復子](../../programming-guide/concepts/iterators.md)、 [Yield ステートメント](../../../visual-basic/language-reference/statements/yield-statement.md)、および[反復子](../../../visual-basic/language-reference/modifiers/iterator.md)です。  
  
## <a name="technical-implementation"></a>技術的な実装  
 ときに、`For Each`しています.`Next` ステートメントが実行されて、Visual Basic では、コレクション、ループを開始する前に、1 つだけの時間を評価します。 ステートメント ブロックが変更された場合`element`または`group`、これらの変更には影響しません、ループの反復処理します。  
  
 ときに、コレクション内のすべての要素まで連続的に割り当てられている`element`、`For Each`ループが停止し、次のステートメントのパスを制御、`Next`ステートメントです。  
  
 場合`element`宣言されていないこのループの外側に宣言する必要がありますで、`For Each`ステートメントです。 型を宣言する`element`を使用して明示的に、`As`ステートメント、またはするが、型を割り当てる型の推定に依存できます。 どちらの場合のスコープ`element`ループの本体します。 ただし、宣言することはできません`element`ループの内外両方です。  
  
 必要に応じて指定することができます`element`で、`Next`ステートメントです。 これが読みやすく、プログラムでは、入れ子にしていない場合に特に`For Each`ループします。 対応する、含まれているものと同じ変数を指定する必要があります`For Each`ステートメントです。  
  
 値が変更されないようにすることができます`element`ループ内です。 これを行うことができます難しくを読み取り、コードをデバッグします。 値を変更する`group`コレクションまたはその要素は、ループが最初に入力されたときに決定されたには影響しません。  
  
 場合に、ループがネストしているときに、`Next`する前に外部の入れ子レベルのステートメントが見つかりましたが、`Next`内部レベルでのコンパイラはエラーです。 ただし、コンパイラが検出できるこれを指定する場合にのみ、エラーを重複`element`ですべて`Next`ステートメントです。  
  
 特定の順序でコレクションを走査することで、コードが依存している場合、`For Each`しています.`Next`ループが最適な選択肢はありません、列挙子オブジェクトの特性をわかっていない限り、コレクションを公開します。 走査の順序はの Visual Basic では、によって決定されていない、<xref:System.Collections.IEnumerator.MoveNext%2A>列挙子オブジェクトのメソッドです。 そのため、するできないことがありますのどの要素のコレクションは、最初に返されるを予測する`element`、これは、指定された要素の後に返される次またはします。 など、さまざまなループ構造を使用して信頼性を高めるの結果が得られる可能性があります`For`しています.`Next`または`Do`しています.`Loop`.  
  
 データ型`element`の要素のデータ型になるようにする必要があります`group`に変換することができます。  
  
 データ型`group`列挙可能な配列またはコレクションに参照する参照型である必要があります。 つまり通常`group`を実装するオブジェクトを参照して、<xref:System.Collections.IEnumerable>のインターフェイス、`System.Collections`名前空間または<xref:System.Collections.Generic.IEnumerable%601>のインターフェイス、`System.Collections.Generic`名前空間。 `System.Collections.IEnumerable` 定義、<xref:System.Collections.IEnumerable.GetEnumerator%2A>メソッドで、コレクションの列挙子オブジェクトを返します。 列挙子オブジェクトが実装する、`System.Collections.IEnumerator`のインターフェイス、`System.Collections`名前空間を公開し、<xref:System.Collections.IEnumerator.Current%2A>プロパティおよび<xref:System.Collections.IEnumerator.Reset%2A>と<xref:System.Collections.IEnumerator.MoveNext%2A>メソッドです。 Visual Basic では、これらを使用して、コレクションを走査します。  
  
### <a name="narrowing-conversions"></a>縮小変換  
 ときに`Option Strict`に設定されている`On`、縮小変換に通常はコンパイラ エラーが発生します。 `For Each`ステートメント、ただし、内の要素からの変換`group`に`element`が評価され、実行時に実行し、コンパイラによってエラーが発生縮小変換は抑制されます。  
  
 割り当て、次の例で`m`の初期値として`n`ときにコンパイルされません`Option Strict`ためにはへの変換、`Long`を`Integer`縮小変換です。 `For Each`ステートメント、ただし、コンパイラ エラーがないへの割り当てがいなくても報告`number`から同じ変換が必要`Long`に`Integer`です。 `For Each`大きな数値を含んだステートメントでは、実行時エラーが発生したときに<xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A>は膨大な数に適用します。  
  
 [!code-vb[VbVbalrStatements#89](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_5.vb)]  
  
### <a name="ienumerator-calls"></a>IEnumerator の呼び出し  
 ときの実行、`For Each`しています.`Next`ループが開始、Visual Basic では、あることを確認`group`は有効なコレクション オブジェクトを参照します。 ない場合は、例外をスローします。 それ以外の場合、呼び出し、<xref:System.Collections.IEnumerator.MoveNext%2A>メソッドおよび<xref:System.Collections.IEnumerator.Current%2A>最初の要素を返す列挙子オブジェクトのプロパティです。 場合`MoveNext`が示されるない次の要素は、コレクションが空の場合、`For Each`ループが停止し、次のステートメントのパスを制御、`Next`ステートメントです。 それ以外の場合、Visual Basic 設定`element`を最初の要素と、ステートメント ブロックを実行します。  
  
 Visual Basic が発生するたびに、`Next`にステートメントを返します、`For Each`ステートメントです。 再び呼び出します`MoveNext`と`Current`を返す次の要素と、もう一度するか、ブロックが実行または結果に応じて、ループを終了します。 までこの処理を続けます`MoveNext`次の要素がないことを示しますまたは`Exit For`ステートメントが見つかりました。  
  
 **コレクションを変更します。** によって返される列挙子オブジェクト<xref:System.Collections.IEnumerable.GetEnumerator%2A>通常することは追加、削除、置換、または任意の要素を並べ替えることによりコレクションを変更します。 開始した後にコレクションを変更する場合、`For Each`しています.`Next`ループ、列挙子オブジェクトは、無効になり、[次へ] しようとすると、要素アクセス、<xref:System.InvalidOperationException>例外。  
  
 ただし、この変更のブロックされていない決定 Visual Basic での実装ではなく、<xref:System.Collections.IEnumerable>インターフェイスです。 実装することは`IEnumerable`ことがイテレーション中に変更が可能です。 このような動的な変更を行うを検討している場合は、特性を理解することを確認してください、`IEnumerable`を使用しているコレクションを実装します。  
  
 **コレクションの要素を変更します。** <xref:System.Collections.IEnumerator.Current%2A>列挙子オブジェクトのプロパティが[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)、し、コレクションの各要素のローカル コピーを返します。 つまり、要素自体を変更できないことで、`For Each`しています.`Next`ループします。 対して行った変更の影響からローカルのコピーのみ`Current`し、基になるコレクションに反映されることはありません。 ただし、要素が参照型の場合は、ポイントするインスタンスのメンバーを変更できます。 次の例を変更、`BackColor`のそれぞれに所属`thisControl`要素。 ただし、変更することはできません、`thisControl`自体です。  
  
```vb  
Sub lightBlueBackground(ByVal thisForm As System.Windows.Forms.Form)  
    For Each thisControl As System.Windows.Forms.Control In thisForm.Controls  
        thisControl.BackColor = System.Drawing.Color.LightBlue  
    Next thisControl  
End Sub  
```  
  
 前の例を変更できます、`BackColor`のそれぞれに所属`thisControl`要素、それを変更できませんが`thisControl`自体です。  
  
 **配列の反復処理します。** <xref:System.Array>クラスが実装する、<xref:System.Collections.IEnumerable>インターフェイス、すべての配列を公開、<xref:System.Array.GetEnumerator%2A>メソッドです。 つまり、格納された配列を反復処理できること、`For Each`しています.`Next`ループします。 ただし、配列の要素のみを読み取ることができます。 変更することはできません。  
  
## <a name="example"></a>例  
 次の例を使用して、C:\ ディレクトリ内のすべてのフォルダーを一覧表示、<xref:System.IO.DirectoryInfo>クラスです。  
  
 [!code-vb[VbVbalrStatements#124](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_6.vb)]  
  
## <a name="example"></a>例  
 次の例では、コレクションを並べ替えるための手順を示しています。 例では、インスタンスの並べ替え、`Car`に格納されているクラス、<xref:System.Collections.Generic.List%601>です。 `Car` クラスは、<xref:System.IComparable%601> のメソッドの実装を必要とする <xref:System.IComparable%601.CompareTo%2A> インターフェイスを実装します。  
  
 呼び出しごとに、<xref:System.IComparable%601.CompareTo%2A>メソッドは、並べ替えに使用される単一の比較できます。 `CompareTo` メソッドのユーザーが作成したコードは、現在のオブジェクトと別のオブジェクトとの各比較の値を戻します。 現在のオブジェクトが別のオブジェクトよりも小さい場合はゼロ未満の値を、大きい場合はゼロ以上の値を、等しい場合はゼロを戻します。 これによって、より大きい、より小さい、等しい、の条件をコードに定義することができます。  
  
 `ListCars` のメソッドでは、`cars.Sort()` ステートメントがリストを並べ替えます。 <xref:System.Collections.Generic.List%601.Sort%2A> の <xref:System.Collections.Generic.List%601> メソッドへの呼び出しによって、`CompareTo` メソッドは `Car` 内の `List` オブジェクトに自動的に呼び出されます。  
  
 [!code-vb[VbVbalrStatements#125](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_7.vb)]  
  
## <a name="see-also"></a>関連項目  
 [コレクション](../../../standard/collections/index.md)  
 [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [ループ構造](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [While...End While ステートメント](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [Do...Loop ステートメント](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [オブジェクト初期化子 : 名前付きの型と匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [コレクション初期化子](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)

---
title: "各.次のステートメント (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ForEach
- vb.ForEachNext
- vb.Each
- ForEachNext
dev_langs:
- VB
helpviewer_keywords:
- infinite loops
- Next statement, For Each...Next
- endless loops
- loop structures, For Each...Next
- loops, endless
- Each keyword
- instructions, repeating
- For Each statement
- collections, instruction repetition
- loops, infinite
- For Each...Next statements
- For keyword [Visual Basic], For Each...Next statements
- Exit statement, For Each...Next statements
- iteration
ms.assetid: ebce3120-95c3-42b1-b70b-fa7da40c75e2
caps.latest.revision: 56
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e0173877fa4a57da76fd774d70ce63d2beda23ad
ms.lasthandoff: 03/13/2017

---
# <a name="for-eachnext-statement-visual-basic"></a>For Each...Next ステートメント (Visual Basic)
ステートメントのコレクション内の各要素に対して繰り返します。  
  
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
|`datatype`|必要な場合`element`既に宣言されていません。 データ型`element`します。|  
|`group`|必須です。 コレクション型またはオブジェクトの型を含む変数。 どのコレクションを参照、`statements`られます。|  
|`statements`|省略可能です。 1 つまたは複数のステートメントの間で`For Each`と`Next`内の各項目で実行される`group`します。|  
|`Continue For`|省略可能です。 先頭に制御を転送、`For Each`ループします。|  
|`Exit For`|省略可能です。 制御を転送、`For Each`ループします。|  
|`Next`|必須です。 定義を終了、`For Each`ループします。|  
  
## <a name="simple-example"></a>簡単な例  
 Use a `For Each`...`Next`コレクションまたは配列の各要素の一連のステートメントを繰り返し使用するときにループ処理します。  
  
> [!TIP]
>  A [For...次のステートメントの](../../../visual-basic/language-reference/statements/for-next-statement.md)うまくループの各反復処理を制御変数に関連付けるし、その変数の最初と最後の値を決定することができます。 ただし、コレクションを処理するときは、最初と最後の値の概念は、わかりやすいと、コレクションは、要素の数がわからないとは限りません。 このような場合で、 `For Each`.`Next`ループは、多くの場合、方が適しています。  
  
 次の例では、 `For Each`.`Next` ステートメントは、リスト コレクションのすべての要素を反復処理します。  
  
 [!code-vb[VbVbalrStatements #&121;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_1.vb)]  
  
 例については、次を参照してください。[コレクション](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)と[配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)します。  
  
## <a name="nested-loops"></a>入れ子になったループ  
 入れ子にすることができます`For Each`内に別の&1; つのループを記述することによってループします。  
  
 次の例で入れ子になった`For Each`.`Next` 構造体。  
  
 [!code-vb[VbVbalrStatements #&122;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_2.vb)]  
  
 ループを入れ子にする場合は、各ループが一意が必要`element`変数です。  
  
 さまざまな種類の他の制御構造を入れ子にすることもできます。 詳細については、次を参照してください。[制御構造の入れ子になった](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)します。  
  
## <a name="exit-for-and-continue-for"></a>終了し、継続  
 [Exit For](../../../visual-basic/language-reference/statements/exit-statement.md)ステートメントは、実行を終了する、 `For`.`Next` 次のステートメントをループおよび転送の制御、`Next`ステートメントです。  
  
 `Continue For`に制御を移しますすぐに、ループの次の反復処理します。 詳細については、次を参照してください。 [Continue ステートメント](../../../visual-basic/language-reference/statements/continue-statement.md)します。  
  
 次の例では、使用する方法、`Continue For`と`Exit For`ステートメントです。  
  
 [!code-vb[VbVbalrStatements&#123;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_3.vb)]  
  
 任意の数を配置する`Exit For`内のステートメント、`For Each`ループします。 使用すると内で入れ子になった`For Each`ループ、`Exit For`実行を入れ子の上位のレベルに最も内側のループと転送コントロールを終了します。  
  
 `Exit For`いくつかの条件の評価後は、よく使用など、 `If`.`Then`...`Else`構造体。 使用することができます`Exit For`次の条件。  
  
-   反復処理に進むことは不要なか不可能です。 値が間違っているか、終了要求によってためと考えられます。  
  
-   例外がキャッチされました、 `Try`.`Catch`...`Finally`. 使用する`Exit For`の最後に、`Finally`ブロックします。  
  
-   何度も長時間または無限でも実行できるループ、無限ループがあります。 このような条件を検出した場合を使用できます`Exit For`ループを抜けます。 詳細については、次を参照してください[操作を行います.。ステートメントのループ](../../../visual-basic/language-reference/statements/do-loop-statement.md)します。  
  
## <a name="iterators"></a>反復子  
 使用する、*反復子*コレクションに対するカスタム イテレーションを実行します。 関数は、反復子または`Get`アクセサー。 使用して、`Yield`ステートメントを一度に&1; つのコレクションの各要素を返します。  
  
 使用して、反復子を呼び出す、`For Each...Next`ステートメントです。 `For Each` ループの各イテレーションは、反復子を呼び出します。 ときに、`Yield`ステートメントが反復子の式に到達、`Yield`ステートメントが返され、コードの現在位置が保持されます。 次回、反復子が呼び出されると、この位置から実行が再開されます。  
  
 次の例では、iterator 関数を使用します。 Iterator 関数が、`Yield`ステートメント内にある、[にしています.次](../../../visual-basic/language-reference/statements/for-next-statement.md)ループします。 `ListEvenNumbers`メソッドは、の各反復処理、`For Each`ステートメント本体を次の手順を実行する反復子関数の呼び出しを作成`Yield`ステートメントです。  
  
 [!code-vb[VbVbalrStatements&#127;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_4.vb)]  
  
 詳細については、次を参照してください。[反復子](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)、 [Yield ステートメント](../../../visual-basic/language-reference/statements/yield-statement.md)、および[反復子](../../../visual-basic/language-reference/modifiers/iterator.md)します。  
  
## <a name="technical-implementation"></a>技術的な実装  
 ときに、 `For Each`.`Next` ステートメントが実行されて、Visual Basic では、コレクション、ループの開始前に&1; つだけの時間を評価します。 ステートメント ブロックが変更された場合`element`または`group`、これらの変更、ループの反復処理に影響を与えません。  
  
 ときに、コレクション内のすべての要素が連続的に割り当てられた`element`、`For Each`ループが停止し、次のステートメントのパスを制御、`Next`ステートメントです。  
  
 場合`element`宣言されていないこのループの外側に宣言する必要がありますで、`For Each`ステートメントです。 型を宣言する`element`を使用して明示的に、`As`ステートメント、またはは、型を割り当てる型の推定で利用できます。 いずれの場合、スコープの`element`がループの本体。 ただし、宣言することはできません`element`外側と、ループ内の両方です。  
  
 必要に応じて指定することができます`element`で、`Next`ステートメントです。 入れ子にしていない場合に特にがプログラムを読みやすく`For Each`ループします。 対応する、含まれているものと同じ変数を指定する必要があります`For Each`ステートメントです。  
  
 値を変更しないようにすることができます`element`ループの中。 これを行うできるようになります読み取りやコードのデバッグが困難です。 値を変更する`group`コレクションまたはその要素は、ループが最初に入力されたときに決定されたには影響しません。  
  
 場合に、ループがネストしているとき、`Next`する前に外部の入れ子レベルのステートメントが検出された、 `Next` 、内側のレベルのコンパイラがエラーを通知します。 ただし、コンパイラが検出できるこれを指定する場合にのみ、エラーを重複する`element`ですべて`Next`ステートメントです。  
  
 コードは、特定の順序でコレクションを走査に依存する場合、 `For Each`.`Next`ループ、最適なのだ、列挙子オブジェクトの特性をわかっていない限り、コレクションを公開します。 走査の順序はありませんによって決定される Visual Basic の場合は、<xref:System.Collections.IEnumerator.MoveNext%2A>列挙子オブジェクトのメソッドです</xref:System.Collections.IEnumerator.MoveNext%2A>。 したがって、しないことができますのどの要素のコレクションが、最初に返されるを予測`element`にある指定された要素の後に返されるか。 など、さまざまなループ構造を使用して、信頼性の高い結果を得られるもあります`For`.`Next` or `Do`...`Loop`.  
  
 データ型`element`の要素のデータを入力するようにする必要があります`group`に変換できます。  
  
 データ型`group`コレクションまたは列挙可能なである配列を参照する参照型である必要があります。 このため、最もよく`group`を実装するオブジェクトを指す、<xref:System.Collections.IEnumerable>のインターフェイス、`System.Collections`名前空間または<xref:System.Collections.Generic.IEnumerable%601>のインターフェイス、`System.Collections.Generic`名前空間</xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.IEnumerable>。 `System.Collections.IEnumerable`定義、<xref:System.Collections.IEnumerable.GetEnumerator%2A>メソッドで、コレクションの列挙子オブジェクトを返します</xref:System.Collections.IEnumerable.GetEnumerator%2A>。 列挙子オブジェクトを実装して、`System.Collections.IEnumerator`のインターフェイス、`System.Collections`名前空間を公開し、<xref:System.Collections.IEnumerator.Current%2A>プロパティおよび<xref:System.Collections.IEnumerator.Reset%2A>と<xref:System.Collections.IEnumerator.MoveNext%2A>メソッド</xref:System.Collections.IEnumerator.MoveNext%2A></xref:System.Collections.IEnumerator.Reset%2A></xref:System.Collections.IEnumerator.Current%2A>。 Visual Basic では、これらを使用して、コレクションを走査します。  
  
### <a name="narrowing-conversions"></a>縮小変換  
 `Option Strict`に設定されている`On`、縮小変換に通常はコンパイラ エラーが発生します。 `For Each`ステートメント、ただし、内の要素からの変換`group`に`element`が評価され、実行時に実行される、縮小変換によるコンパイラ エラーを抑制します。  
  
 割り当て、次の例で`m`の初期値として`n`場合はコンパイルされません`Option Strict`ためへの変換、`Long`に、`Integer`縮小変換です。 `For Each`ステートメント、ただし、コンパイラ エラーがないへの代入も報告`number`から同じ変換が必要`Long`に`Integer`します。 `For Each`を膨大な数を含むステートメントでは、実行時エラーが発生したときに<xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A>膨大な数に適用されます</xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A>。  
  
 [!code-vb[VbVbalrStatements #&89;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_5.vb)]  
  
### <a name="ienumerator-calls"></a>IEnumerator 呼び出し  
 時の実行、 `For Each`.`Next`ループの開始、Visual Basic では、あることを確認`group`は有効なコレクション オブジェクトを参照します。 ない場合は、例外がスローされます。 それ以外の場合、それを呼び出す、<xref:System.Collections.IEnumerator.MoveNext%2A>メソッドおよび<xref:System.Collections.IEnumerator.Current%2A>最初の要素を返す列挙子オブジェクトのプロパティ</xref:System.Collections.IEnumerator.Current%2A></xref:System.Collections.IEnumerator.MoveNext%2A>。 場合`MoveNext`ないことを示しますが次の要素は、コレクションが空である場合、`For Each`ループが停止し、次のステートメントのパスを制御、`Next`ステートメントです。 Visual Basic のそれ以外の場合、設定`element`に最初の要素と、ステートメント ブロックを実行します。  
  
 Visual Basic が発生するたびに、`Next`にステートメントを返します、`For Each`ステートメントです。 再び呼び出します`MoveNext`と`Current`次の要素と、もう一度を返す、ブロックが実行か、その結果に応じて、ループを停止します。 このプロセスが到達するまで続行`MoveNext`次の要素がないことを示しますまたは`Exit For`ステートメントが見つかりました。  
  
 **コレクションを変更します。** によって返される列挙子オブジェクト<xref:System.Collections.IEnumerable.GetEnumerator%2A>通常することは、コレクションを変更するには、追加、削除、置換、または任意の要素の順序を変更します</xref:System.Collections.IEnumerable.GetEnumerator%2A>。 開始した後にコレクションを変更する場合、 `For Each`.`Next`ループ、列挙子オブジェクトは、無効になり、要素にアクセスするには、次の試行により、<xref:System.InvalidOperationException>例外</xref:System.InvalidOperationException>。  
  
 ただし、によって決定されていない変更のこのブロック[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]の実装ではなく、<xref:System.Collections.IEnumerable>インターフェイス</xref:System.Collections.IEnumerable>。 実装することは`IEnumerable`イテレーション中に変更を許可するようにします。 このような動的な変更を行うを検討している場合は、特性を理解していることを確認してください、`IEnumerable`を使用しているコレクションを実装します。  
  
 **コレクションの要素を変更します。** <xref:System.Collections.IEnumerator.Current%2A>列挙子オブジェクトのプロパティが[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)コレクションの各要素のローカル コピーを返します</xref:System.Collections.IEnumerator.Current%2A>。 つまり、要素自体を変更できないことで、 `For Each`.`Next` loop. 対して行った変更からのローカル コピーのみに影響を与えます`Current`し、基になるコレクションに反映されることはありません。 ただし、要素が参照型の場合は、ポイントするインスタンスのメンバーを変更できます。 次の例では、変更、`BackColor`のそれぞれに所属`thisControl`要素。 ただし、変更することはできません`thisControl`自体です。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 前の例を変更できます、`BackColor`のそれぞれに所属`thisControl`要素、それを変更できませんが`thisControl`自体です。  
  
 **配列の反復処理します。** <xref:System.Array>クラスが実装する、<xref:System.Collections.IEnumerable>インターフェイス、すべての配列を公開、<xref:System.Array.GetEnumerator%2A>メソッド</xref:System.Array.GetEnumerator%2A></xref:System.Collections.IEnumerable></xref:System.Array>。 つまり、配列を反復処理できること、 `For Each`.`Next` loop. ただし、配列の要素のみを読み取ることができます。 変更することはできません。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.IO.DirectoryInfo>クラス</xref:System.IO.DirectoryInfo>を使用して、C:\ ディレクトリ内のすべてのフォルダーが一覧表示します。  
  
 [!code-vb[VbVbalrStatements #&124;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_6.vb)]  
  
## <a name="example"></a>例  
 次の例では、コレクションを並べ替えるための手順を示しています。 この例のインスタンスの並べ替え、 `Car` <xref:System.Collections.Generic.List%601>.</xref:System.Collections.Generic.List%601>に格納されているクラス `Car`クラスが実装する、<xref:System.IComparable%601>を必要とするインターフェイス、<xref:System.IComparable%601.CompareTo%2A>メソッドを実装する</xref:System.IComparable%601.CompareTo%2A></xref:System.IComparable%601>。  
  
 呼び出すたび、<xref:System.IComparable%601.CompareTo%2A>メソッドは、並べ替えに使用される単一の比較</xref:System.IComparable%601.CompareTo%2A>。 `CompareTo` メソッドのユーザーが作成したコードは、現在のオブジェクトと別のオブジェクトとの各比較の値を戻します。 現在のオブジェクトが別のオブジェクトよりも小さい場合はゼロ未満の値を、大きい場合はゼロ以上の値を、等しい場合はゼロを戻します。 これによって、より大きい、より小さい、等しい、の条件をコードに定義することができます。  
  
 `ListCars` のメソッドでは、`cars.Sort()` ステートメントがリストを並べ替えます。 この呼び出しを<xref:System.Collections.Generic.List%601.Sort%2A>のメソッド、<xref:System.Collections.Generic.List%601>により、`CompareTo`に対して自動的に呼び出されるメソッド、`Car`内のオブジェクト、 `List`</xref:System.Collections.Generic.List%601> </xref:System.Collections.Generic.List%601.Sort%2A> 。  
  
 [!code-vb[VbVbalrStatements #&125;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-each-next-statement_7.vb)]  
  
## <a name="see-also"></a>関連項目  
 [コレクション](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)   
 [.次のステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [ループ構造](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [しばらくしています.While ステートメントの終了](../../../visual-basic/language-reference/statements/while-end-while-statement.md)   
 [操作を実行しています.ループ ステートメント](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [オブジェクト初期化子: 名前付きおよび匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)   
 [コレクション初期化子](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)   
 [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)

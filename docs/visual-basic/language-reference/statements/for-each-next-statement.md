---
title: "For Each...Next ステートメント (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ForEach"
  - "vb.ForEachNext"
  - "vb.Each"
  - "ForEachNext"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "無限ループ"
  - "Next ステートメント、For Each...Next"
  - "無限ループ"
  - "ループ構造、For Each...Next"
  - "ループ、無限"
  - "Each キーワード"
  - "命令、繰り返し"
  - "For Each ステートメント"
  - "コレクション、命令の繰り返し"
  - "ループ、無限"
  - "For Each...Next ステートメント"
  - "For キーワード [Visual Basic]、For Each...Next ステートメント"
  - "Exit ステートメント、For Each...Next ステートメント"
  - "イテレーション"
ms.assetid: ebce3120-95c3-42b1-b70b-fa7da40c75e2
caps.latest.revision: 56
caps.handback.revision: 56
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# For Each...Next ステートメント (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

コレクションの各要素に対して、一連のステートメントを繰り返し実行する一連のステートメントです。  
  
## 構文  
  
```  
For Each element [ As datatype ] In group  
    [ statements ]  
    [ Continue For ]  
    [ statements ]  
    [ Exit For ]  
    [ statements ]  
Next [ element ]  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`element`|`For Each` ステートメントには必ず指定します。  `Next` ステートメントでは省略可能です。  変数を表します。  コレクションの各要素を反復処理するために使用します。|  
|`datatype`|`element` が既に宣言されていない場合  `element` のデータ型を指定します。|  
|`group`|必須です。  コレクション型またはオブジェクトである型の変数。  `statements` で反復処理するコレクションを表します。|  
|`statements`|省略可能です。  `For Each` から `Next` までの間に記述した 1 つ以上のステートメントは、`group` 内の各項目に対して実行されます。|  
|`Continue For`|省略可能です。  プログラムの制御を `For Each` ループの先頭に移します。|  
|`Exit For`|省略可能です。  制御を `For Each` ループの外に移します。|  
|`Next`|必須です。  `For Each` ループの定義を終了します。|  
  
## 簡単な例  
 コレクションまたは配列の各要素に対して一連のステートメントを繰り返し実行するときには、`For Each`...`Next` ループを使用します。  
  
> [!TIP]
>  [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md) は、ループの毎回の反復を制御変数に関連付けることができ、制御変数の初期値と最終値を決定できるときには役立ちます。  ただし、コレクションを扱うときに、初期値と最終値の概念は意味を持ちませんし、の要素がコレクションにある必ずしも判明している。  このようなケースでは、`For Each`…ループの`Next` は、により適しています。  
  
 次の例では、`For Each`\[…\]`Next` のステートメントはリスト コレクションのすべての要素に対して繰り返します。  
  
 [!code-vb[VbVbalrStatements#121](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/for-each-next-statement_1.vb)]  
  
 その他の例については、「[コレクション](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)」および「[配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)」を参照してください。  
  
## 入れ子になったループ  
 `For Each` ループは入れ子構造にできます。つまり、ループの中に別のループを入れることができます。  
  
 次の例は、入れ子になった `For Each`…`Next` 構造体を示しています。  
  
 [!code-vb[VbVbalrStatements#122](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/for-each-next-statement_2.vb)]  
  
 ループを入れ子にする場合は、各ループは `element` の一意の変数を指定する必要があります。  
  
 また、さまざまな種類の制御構造を入れ子にすることもできます。  詳細については、「[Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)」を参照してください。  
  
## の終了、のを続行します。  
 `Next` のステートメントの次のステートメントに `For`\[…\]`Next` のループおよび制御を移しますを終了する [の終了します。](../../../visual-basic/language-reference/statements/exit-statement.md) のステートメントで実行されます。  
  
 `Continue For` ステートメントは、制御をループの次の反復処理に直ちに移します。  詳細については、「[Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md)」を参照してください。  
  
 次の例は、`Continue For` ステートメントおよび `Exit For` ステートメントの使用方法を示しています。  
  
 [!code-vb[VbVbalrStatements#123](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/for-each-next-statement_3.vb)]  
  
 `Exit For` ステートメントは、`For Each` ループで何度でも使用できます。  入れ子構造になっている `For Each`ループの中で使用すると、`Exit For` により、実行で最も内側のループが終了し、入れ子構造の 1 つ外側のレベルに制御が移されます。  
  
 `Exit For` は、`If`...`Then`...`Else` 構造の中などで、なんらかの条件を評価した後によく使用されます。  次のような条件の場合に `Exit For` を使用できます。  
  
-   ループの継続が不要または不可能である。  この原因としては、エラー値または終了要求が考えられます。  
  
-   `Try`...`Catch`...`Finally` で例外が検出される。  `Finally` ブロックの最後で `Exit For` を使用できます。  
  
-   無限ループ \(実行回数が多いか、または無限に繰り返されるループ\) がある。  このような条件を検出した場合は、`Exit For` を使用してループを抜けることができます。  詳細については、「[Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md)」を参照してください。  
  
## 反復子  
 コレクションに対するカスタムのイテレーションを実行するために *反復子を* 使用します。  反復子は、関数または `Get` アクセサーのいずれかです。  これはコレクションの各要素を一つずつ返すために `Yield` のステートメントを使用します。  
  
 `For Each...Next` のステートメントを使用して、反復子を呼び出します。  `For Each` ループの各反復で反復子を呼び出します。  `Yield` のステートメントが反復子に到達すると、`Yield` のステートメントの式は戻り、コードの現在の位置は保持されます。  実装はその位置から反復子が呼び出されると、に再起動されます。  
  
 次の例は、反復子関数を使用します。  反復子の関数に [次に、…](../../../visual-basic/language-reference/statements/for-next-statement.md) のループ内にある `Yield` のステートメントがあります。  `ListEvenNumbers` のメソッドでは、`For Each` ステートメントのメイン フレームの各反復で `Yield` の次のステートメントに進む反復子の関数への呼び出しを作成します。  
  
 [!code-vb[VbVbalrStatements#127](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/for-each-next-statement_4.vb)]  
  
 詳細については、「[反復子](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)」、「[Yield ステートメント](../../../visual-basic/language-reference/statements/yield-statement.md)」、および「[Iterator](../../../visual-basic/language-reference/modifiers/iterator.md)」を参照してください。  
  
## 技術的な実装  
 `For Each`\[…\]`Next` のステートメントの実行、Visual Basic がコレクションを 1 回だけ評価すると、ループの開始前にします。  次のステートメント ブロックが `element` か `group`を変更すると、ループの繰り返しには影響しません。  
  
 コレクションのすべての要素が `element` に代入されると、`For Each` ループは停止し、`Next` ステートメントの次のステートメントに制御が渡されます。  
  
 `element` がこのループの外側でを宣言していない場合は、の `For Each` ステートメント内で宣言する必要があります。  `As` ステートメントを使用して `element` の型を明示的に宣言するか、または型の推論に基づいて型を割り当てることができます。  いずれの場合も、`element` のスコープはループの本体になります。  ただし、ループの外側と内側の両方で `element` を宣言することはできません。  
  
 オプションとして、`Next` ステートメントに `element` を指定することもできます。  こうするとプログラムの読みやすさが向上し、特に `For Each` ループを入れ子にしている場合は効果があります。  その場合には、`For Each` ステートメントで指定したのと同じ変数を指定する必要があります。  
  
 ループ内で `element` の値を変更しないようにすることができます。  値を変更すると、コードの読みやすさが低下してデバッグが難しくなります。  `group` の値を変更すると、最初のループに入る時点に決定されますがその要素は影響を与えません、またはコレクションにします。  
  
 内部のレベルの `Next` が、コンパイラ エラーを通知する前にループの入れ子である場合、外側の入れ子レベルの `Next` のステートメントが検出された場合。  ただし、コンパイラがこのエラーを検出できるのは、すべての `Next` ステートメントに `element` を指定した場合に限られます。  
  
 コードの特定の順序でコレクションを反復処理に依存している場合、`For Each`…ループは`Next` のコレクションを公開する列挙子オブジェクトの特性を理解している場合、最適なオプションではありません。  反復処理の順序は、Visual Basic では、列挙子オブジェクトの <xref:System.Collections.IEnumerator.MoveNext%2A> のメソッドによって決まります。  したがって、コレクションのどの要素が最初に `element` に返されるかや、特定の要素の後にどの要素が返されるかを予測することはできません。  `For`...`Next` ループや `Do`...`Loop` ループなど、別のループ構造を使用した方が、信頼できる結果が得られます。.  
  
 `element` のデータ型は、`group` の要素のデータ型から変換可能なものにする必要があります。  
  
 `group` のデータ型は、列挙可能なコレクションまたは配列を参照する参照型である必要があります。  つまり、通常、`group` は、`System.Collections` 名前空間の <xref:System.Collections.IEnumerable> インターフェイスまたは `System.Collections.Generic` 名前空間の <xref:System.Collections.Generic.IEnumerable%601> インターフェイスを実装するオブジェクトを参照します。  `System.Collections.IEnumerable` は、コレクションの列挙子オブジェクトを返す <xref:System.Collections.IEnumerable.GetEnumerator%2A> メソッドを定義します。  列挙子オブジェクトは `System.Collections` 名前空間の `System.Collections.IEnumerator` インターフェイスを実装し、<xref:System.Collections.IEnumerator.Current%2A> プロパティと <xref:System.Collections.IEnumerator.Reset%2A> メソッドおよび <xref:System.Collections.IEnumerator.MoveNext%2A> メソッドを公開します。  このプロパティとメソッドは、コレクションの反復処理に使用されます。  
  
### 縮小変換  
 `Option Strict` が `On` に設定されている場合、縮小変換は通常はコンパイラ エラーの原因になります。  ただし、`For Each` ステートメントでは、`group` 内の要素から `element` への変換は、実行時に評価されて実行され、縮小変換を原因とするコンパイラ エラーは抑制されます。  
  
 次の例では、`n` の初期値として `m` の割り当ては `Integer` への `Long` の変換が縮小変換であるための `Option Strict` がいつあるかコンパイルされます。  ただし、`For Each` ステートメントでは、`number` への代入で同じ `Long` から `Integer` への変換が必要とされますが、コンパイラ エラーは報告されません。  大きな数値が含まれる `For Each` ステートメントでは、<xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> が大きな数値に適用された場合に実行時エラーが発生します。  
  
 [!code-vb[VbVbalrStatements#89](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/for-each-next-statement_5.vb)]  
  
### IEnumerator の呼び出し  
 `For Each`...`Next` ループの実行を開始するときには、`group` が有効なコレクション オブジェクトを参照しているかどうかが検証されます。  有効なコレクション オブジェクトでない場合は、例外がスローされます。  有効なコレクション オブジェクトである場合は、列挙子オブジェクトの <xref:System.Collections.IEnumerator.MoveNext%2A> メソッドと <xref:System.Collections.IEnumerator.Current%2A> プロパティが呼び出され、1 つ目の要素が返されます。  `MoveNext` が次の要素がないことを示した場合、つまりコレクションが空の場合は、`For Each` ループは停止し、`Next` ステートメントの次のステートメントに制御が渡されます。  それ以外の場合は、`element` が 1 つ目の要素に設定され、ステートメント ブロックが実行されます。  
  
 `Next` ステートメントに達すると、そのたびに `For Each` ステートメントに制御が戻されます。  次の要素を返すために再び `MoveNext` と `Current` が呼び出され、その結果に応じて、ステートメント ブロックが再度実行されるか、ループが停止します。  `MoveNext` メソッドが次の要素がないことを示すまで、または `Exit For` ステートメントに達するまでは、このプロセスが繰り返されます。  
  
 **コレクションの変更** <xref:System.Collections.IEnumerable.GetEnumerator%2A> によって返される列挙子オブジェクトは、通常、要素を追加、削除、置換したり並べ替えたりすることでコレクションを変更することはできません。  `For Each`...`Next` ループの開始後にコレクションを変更すると列挙子オブジェクトが無効になり、次に要素にアクセスしようとしたときに <xref:System.InvalidOperationException> 例外が発生します。  
  
 ただし、この変更のブロックは [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]でなく、<xref:System.Collections.IEnumerable> のインターフェイスの実装によって決まります。  反復処理中の変更を許可するように `IEnumerable` を実装できます。  このような動的な変更を行う場合には、使用するコレクションでの `IEnumerable` 実装の特徴を理解しておくことが必要です。  
  
 **コレクション要素の変更。**列挙子オブジェクトの <xref:System.Collections.IEnumerator.Current%2A> プロパティは [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md) であり、各コレクション要素のローカル コピーを返します。  これは、`For Each`...`Next` ループ内では要素そのものを変更できないということを意味します。  変更 `Current` からローカル コピーだけに影響して、基になるコレクションに反映されません。  ただし、要素が参照型である場合、その要素が指すインスタンスのメンバーを変更することはできます。  次の例では `thisControl` の各要素の `BackColor` のメンバーを変更します。  ただし、`thisControl` 自体を変更できません。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 この例では各 `thisControl` 要素の `BackColor` メンバーを変更していますが、`thisControl` そのものは変更できません。  
  
 **配列の反復処理。** <xref:System.Array> クラスは <xref:System.Collections.IEnumerable> インターフェイスを実装するため、すべての配列は <xref:System.Array.GetEnumerator%2A> メソッドを公開します。  これは、`For Each`...`Next` ループによって配列を反復処理できることを意味します。  ただし、配列要素は読み取ることしかできません。  変更することはできません。  
  
## 使用例  
 次の例では、<xref:System.IO.DirectoryInfo> クラスを使用して、C:\\ ディレクトリ内のすべてのフォルダーを一覧表示します。  
  
 [!code-vb[VbVbalrStatements#124](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/for-each-next-statement_6.vb)]  
  
## 使用例  
 次の例は、コレクションを並べ替えるための手順を示します。  <xref:System.Collections.Generic.List%601>に格納されている `Car` の例の並べ替えのインスタンスを示します。  `Car` のクラスは <xref:System.IComparable%601.CompareTo%2A> のメソッドは、実行する必要のある <xref:System.IComparable%601> のインターフェイスを実装します。  
  
 <xref:System.IComparable%601.CompareTo%2A> のメソッドに対する各呼び出しは、並べ替えに使用される単一の比較を行います。  `CompareTo` のメソッドのユーザー作成コードは別のオブジェクトを使用して現在のオブジェクトの各比較の値を返します。  返される値が等しい場合は、現在のオブジェクトが他のオブジェクトより大きい、およびゼロ。現在のオブジェクトが他のオブジェクトより小さい場合はゼロよりも小さい、非常にはゼロ。  これは、コードに大きなの条件を定義することにより、より小さく、AND できます。  
  
 `ListCars` のメソッドでは、`cars.Sort()` のステートメントは、リストを並べ替えます。  <xref:System.Collections.Generic.List%601> の <xref:System.Collections.Generic.List%601.Sort%2A> のメソッドへの呼び出しは、この `CompareTo` のメソッドを `List`の `Car` のオブジェクトを自動的に呼び出します。  
  
 [!code-vb[VbVbalrStatements#125](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/for-each-next-statement_7.vb)]  
  
## 参照  
 [コレクション](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)   
 [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Loop Structures](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md)   
 [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Collection Initializers](../../../visual-basic/reference/command-line-compiler/index.md)   
 [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
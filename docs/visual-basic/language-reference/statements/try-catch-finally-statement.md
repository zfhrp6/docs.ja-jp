---
title: "Try...Catch...Finally Statement (Visual Basic) | Microsoft Docs"
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
  - "vb.Try...Catch...Finally"
  - "vb.when"
  - "vb.Finally"
  - "vb.Catch"
  - "vb.Try"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Try...Catch...Finally statements"
  - "Try statement"
  - "try-catch exception handling, Try...Catch...Finally statements"
  - "error handling, while running code"
  - "Try statement, Try...Catch...Finally"
  - "Finally keyword [Visual Basic], Try...Catch...Finally"
  - "Catch statement"
  - "When keyword"
  - "Visual Basic code, handling errors while running"
  - "structured exception handling, Try...Catch...Finally statements"
ms.assetid: d6488026-ccb3-42b8-a810-0d97b9d6472b
caps.latest.revision: 69
caps.handback.revision: 69
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Try...Catch...Finally Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

コードの実行中に、コードのブロックで発生する可能性のあるエラーの一部またはすべてを処理する方法を提供します。  
  
## 構文  
  
```  
Try  
    [ tryStatements ]  
    [ Exit Try ]  
[ Catch [ exception [ As type ] ] [ When expression ]  
    [ catchStatements ]  
    [ Exit Try ] ]  
[ Catch ... ]  
[ Finally  
    [ finallyStatements ] ]  
End Try  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`tryStatements`|省略可能。  エラーが発生する可能性のあるステートメント。  複合ステートメントを指定することもできます。|  
|`Catch`|省略可能。  複数の `Catch` ブロックを指定できます。  `Try` ブロックの処理時に例外が発生した場合は、それぞれの `Catch` ステートメントがテキストの順序で評価され、その例外を処理できるかどうかが調べられます。このとき、スローされた例外は `exception` で表されます。|  
|`exception`|省略可能。  任意の変数名を指定します。  `exception` の初期値は、スローされたエラーの値です。  `Catch` と共に使用して、キャッチされたエラーを指定します。  省略した場合、`Catch` ステートメントはどの例外でもキャッチします。|  
|`type`|省略可能。  クラス フィルターの種類を指定します。  `exception` の値が `type` で指定した型、または派生した型の値と一致する場合は、その識別子が例外オブジェクトにバインドされます。|  
|`When`|省略可能。  `Catch` ステートメントに `When` 句が記述されている場合は、`expression` の評価が `True` になるときにのみ例外がキャッチされます。  `When` 句は、例外の型をチェックした後にだけ適用されます。`expression` は、例外を表す識別子を参照することがあります。|  
|`expression`|省略可能。  暗黙的にブール型 \(`Boolean`\) に変換できる必要があります。  汎用フィルターを記述する任意の式。  通常、エラー番号によるフィルター処理に使用されます。  `When` キーワードと共に使用して、エラーがキャッチされる状況を指定します。|  
|`catchStatements`|省略可能。  関連付けられた `Try` ブロックで発生したエラーを処理するステートメントです。  複合ステートメントを指定することもできます。|  
|`Exit Try`|省略可能。  `Try...Catch...Finally` 構造から抜けるためのキーワードです。  `End Try` ステートメントのすぐ下にあるコードから実行が再開されます。  その場合でも、`Finally` ステートメントは実行されます。  `Finally` ブロック内には記述できません。|  
|`Finally`|省略可能。  `Try...Catch` ステートメントから抜けるときには、必ず `Finally` ブロックが実行されます。|  
|`finallyStatements`|省略可能。  他のエラー処理がすべて行われた後に実行されるステートメント。|  
|`End Try`|`Try...Catch...Finally` 構造の終わりを表します。|  
  
## 解説  
 コード内の特定のセクションで特定の例外が発生することが予想される場合、コードを `Try` ブロック内に記述し、`Catch` ブロックを使用してコントロールを保持して、例外が発生した場合にこれを処理するようにします。  
  
 `Try…Catch` ステートメントは、`Try` ブロックと、それに続く 1 つ以上の `Catch` 句で構成されます。この句にはさまざまな例外のハンドラーを指定します。  `Try` ブロックで例外がスローされると、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] は、その例外を処理する `Catch` ステートメントを検索します。  対応する `Catch` ステートメントが見つからない場合、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] は現在のメソッドの呼び出し元メソッドをチェックします \(この方法で、呼び出しスタックの上位をチェックしていきます\)。  `Catch` ブロックが見つからない場合、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] は未処理例外のメッセージをユーザーに表示し、プログラムの実行を停止します。  
  
 `Try…Catch` ステートメントでは、複数の `Catch` ステートメントを使用できます。  この場合、`Catch` 句は順序どおりにチェックされるため、その順序が重要になります。  例外は、特定性の高い順にキャッチしてください。  
  
 次のような `Catch` ステートメントの条件は、特定性が最も低く、<xref:System.Exception> クラスから派生するすべての例外がキャッチされます。  通常は、`Try...Catch...Finally` 構造内で、期待する特定の例外すべてをキャッチした後の最後の `Catch` ブロックとして、これらのバリエーションのいずれかを使用する必要があります。  制御フローは、これらのバリエーションのいずれかより後の `Catch` ブロックに到達できません。  
  
-   `type` が `Exception` である \(例: `Catch ex As Exception`\)。  
  
-   ステートメントに `exception` 変数がない \(例: `Catch`\)。  
  
 `Try…Catch…Finally` ステートメントが別の `Try` ブロック内に入れ子になっている場合、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] は、最初に最も内側の `Try` ブロック内の各 `Catch` ステートメントをチェックします。  対応する `Catch` ステートメントが見つからなかった場合は、外側にある `Try…Catch…Finally` ブロックの `Catch` ステートメントが検索されます。  
  
 `Try` ブロックと `Catch` ブロックは別々のブロックであるため、Try ブロック内のローカル変数を Catch ブロック内で使用することはできません。  変数を複数のブロックで使用するには、その変数を `Try...Catch...Finally` 構造の外で宣言します。  
  
> [!TIP]
>  `Try…Catch…Finally` ステートメントは、IntelliSense コード スニペットとして利用できます。  コード スニペット マネージャーで、**\[コード パターン \- If、For Each、Try Catch、Property、その他\]**、**\[エラー処理 \(例外\)\]** の順に展開します。  詳細については、「[コード スニペット](/visual-studio/ide/code-snippets)」を参照してください。  
  
## Finally ブロック  
 `Try` 構造体を終了する前に実行するステートメントがある場合は、`Finally` ブロックを使用します。  コントロールは `Try…Catch` 構造体に移る直前に `Finally` ブロックに移ります。  これは、`Try` 構造体の中で例外が発生した場合でも同様です。  
  
 `Finally` ブロックは、例外が発生した場合でも実行する必要があるコードを実行するのに便利です。  制御は、`Try...Catch` ブロックがどのように終了したかに関係なく、`Finally` ブロックに移動します。  
  
 `Finally` ブロック内のコードは、コードで `Try` ブロックまたは `Catch` ブロック内に `Return` ステートメントがある場合でも実行されます。  次の場合、コントロールは `Try` または `Catch` ブロックから、対応する `Finally` ブロックに移りません。  
  
-   `Try` または `Catch` ブロック内に [End Statement](../../../visual-basic/language-reference/statements/end-statement.md) がある場合  
  
-   `Try` または `Catch` ブロックで <xref:System.StackOverflowException> がスローされた場合  
  
 これは明示的に無効 `Finally` ブロックに実行を転送することです。  `Finally` ブロックから移動実行は例外の場合を除き、無効です。  
  
 `Try` ステートメント内に `Catch` ブロックが 1 つもない場合は、`Finally` ブロックを含める必要があります。  
  
> [!TIP]
>  特定の例外をキャッチする必要がない場合には、`Using` ステートメントを使用すると `Try…Finally` ブロックと同じように動作し、どのようにブロック内の処理が終了する場合でも確実にリソースを解放できます。  これは、未処理の例外の場合にも該当します。  詳細については、「[Using Statement](../../../visual-basic/language-reference/statements/using-statement.md)」を参照してください。  
  
## 例外の引数  
 `Catch` ブロックの `exception` 引数は、<xref:System.Exception> クラスのインスタンス、または `Exception` クラスから派生したクラスのインスタンスです。  `Exception` クラス インスタンスは、`Try` ブロックで発生したエラーに対応します。  
  
 `Exception` オブジェクトのプロパティは、例外の原因と場所を特定するのに役立ちます。  たとえば、<xref:System.Exception.StackTrace%2A> プロパティでは、例外が発生するまでに呼び出されたメソッドの一覧を確認できるため、コードのどこでエラーが発生したのかを突き止めるのに便利です。  <xref:System.Exception.Message%2A> は、例外を説明するメッセージを返します。  <xref:System.Exception.HelpLink%2A> は、関連付けられたヘルプ ファイルへのリンクを返します。  <xref:System.Exception.InnerException%2A> は、現在の例外の原因になった `Exception` オブジェクトを返します。元の `Exception` がない場合は、`Nothing` を返します。  
  
## Try…Catch ステートメントを使用する場合の考慮事項  
 `Try…Catch` ステートメントは、異常なプログラム イベントまたは予期しないプログラム イベントの発生を伝えるためだけに使用してください。  これには次のような理由があります。  
  
-   実行時に例外をキャッチすると、追加のオーバーヘッドが発生し、多くの場合、事前にチェックして例外を回避する場合よりも処理が遅くなります。  
  
-   `Catch` ブロックが適切に処理されない場合、例外がユーザーに適切に報告されないことがあります。  
  
-   例外処理によってプログラムがより複雑になります。  
  
 発生する可能性が高い条件をチェックするのに、`Try…Catch` ステートメントが常に必要なわけではありません。  ファイルを開く前にファイルの有無をチェックする例を次に示します。  これにより、<xref:System.IO.File.OpenText%2A> メソッドによってスローされる例外をキャッチする必要性が低くなります。  
  
 [!code-vb[VbVbalrStatements#94](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/try-catch-finally-statement_1.vb)]  
  
 `Catch` ブロック内のコードで、スレッド セーフなログまたは適切なメッセージを通じて、例外がユーザーに適切に報告されるようにしてください。  そうでない場合、例外に気付かないままになる可能性があります。  
  
## 単一のメソッド  
 [非同期操作](../../../visual-basic/language-reference/modifiers/async.md) 修飾子のメソッドにマークを付ける場合、メソッドで [待機します。](../../../visual-basic/language-reference/operators/await-operator.md) の演算子を使用できます。  `Await` 演算子とのステートメントが必要なタスクが完了するまでメソッドの実行を中断します。  タスクは、進行中の作業を表します。  `Await` の演算子に関連付けられているタスクが終了すると、実行が同じメソッドで再開します。  詳細については、「[非同期プログラムにおける制御フロー](../Topic/Control%20Flow%20in%20Async%20Programs%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
 単一のメソッドによって返されるタスクはハンドルされない例外が原因で完了したことを示す違反状態で終わる場合があります。  タスクは、予定の式からスローされる `OperationCanceledException` が取り消された状態に終了することがあります。  例外のいずれかの型を、`Try` ブロックのタスクに関連付けられたキャッチし、例外をキャッチするように設定します `Catch` ブロックに `Await` の式が。  例については、このトピックの後半で説明します。  
  
 タスクは、違反状態に複数の例外がエラーの原因となっているためです。  たとえば、タスクは <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>呼び出しの結果である場合があります。  このようなタスクで待機する場合、キャッチされた例外は、1 ビットのみで、どの例外がキャッチされるかは予測できません。  例については、このトピックの後半で説明します。  
  
 `Await` の式は `Catch``Finally` ブロックまたはブロック内に置くことはできません。  
  
## 反復子  
 `Get` の反復子の関数またはアクセサーはコレクションに対するカスタムのイテレーションを実行します。  反復子はコレクションの各要素を一つずつ返すために [yield](../../../visual-basic/language-reference/statements/yield-statement.md) のステートメントを使用します。  [For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)を使用して、反復子の関数を呼び出します。  
  
 `Yield` のステートメントは `Try` ブロックの中にある場合もあります。  `Yield` のステートメントを含む `Try` ブロックは `Catch` ブロックを持ち `Finally` のブロックを指定できます。  例については、「 [反復子](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md) の Visual Basic の try ブロック」を参照してください。  
  
 `Yield` のステートメントは `Catch``Finally` ブロックまたはブロック内に置くことはできません。  
  
 反復子関数 \(外\) `For Each` の本体で例外をスローする場合、反復子関数の `Catch` ブロックは実行されませんが、反復子関数の `Finally` ブロックが実行されます。  反復子関数のブロック `Catch` は、反復子関数内で発生した例外のみをキャッチします。  
  
## 部分的に信頼されている状況  
 ネットワーク共有でホストされているアプリケーションなど、部分的に信頼されている状況では、`Try...Catch...Finally` はその呼び出しを含むメソッドが呼び出される前に発生したセキュリティ例外をキャッチしません。  次のコード例をサーバー共有に配置し、そこから実行すると、"System.Security.SecurityException: 要求が失敗しました。" のエラーが発生します。セキュリティ例外の詳細については、<xref:System.Security.SecurityException> クラスの説明を参照してください。  
  
 [!code-vb[VbVbalrStatements#85](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/try-catch-finally-statement_2.vb)]  
  
 このような部分的に信頼されている状況では、`Process.Start` ステートメントを別の `Sub` に入れる必要があります。  `Sub` の最初の呼び出しは失敗します。  これによって、`Try...Catch` は、`Process.Start` を含んでいる `Sub` が開始されてセキュリティ例外が生成される前に、その失敗をキャッチできます。  
  
## 使用例  
 次の例は、`Try...Catch...Finally` ステートメントの構造を示しています。  
  
 [!code-vb[VbVbalrStatements#86](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/try-catch-finally-statement_3.vb)]  
  
## 使用例  
 次の例では、`CreateException` メソッドにより `NullReferenceException` がスローされます。  `Try` ブロックには、例外を生成するコードはありません。  そのため、`CreateException` メソッドは例外を処理しません。  `RunSample` メソッドが例外を処理します。これは、`CreateException` メソッドの呼び出しが `Try` ブロック内にあるためです。  
  
 例には、最も特殊な例外から最も一般的な例外の順に、いくつかの種類の例外のための `Catch` ステートメントが含まれています。  
  
 [!code-vb[VbVbalrStatements#91](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/try-catch-finally-statement_4.vb)]  
  
## 使用例  
 次の例は、`Catch When` ステートメントを使用して、条件式によってフィルターする方法を示しています。  条件式が `True` と評価された場合に、`Catch` ブロック内のコードが実行されます。  
  
 [!code-vb[VbVbalrStatements#92](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/try-catch-finally-statement_5.vb)]  
  
## 使用例  
 次の例には、`Try` ブロックに含まれている `Try…Catch` ステートメントがあります。  内側の `Catch` ブロックによって、`InnerException` プロパティが元の例外に設定されている例外がスローされます。  外側の `Catch` ブロックによって、それ自体の例外と内側の例外が報告されます。  
  
 [!code-vb[VbVbalrStatements#93](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/try-catch-finally-statement_6.vb)]  
  
## 使用例  
 次の例では、非同期のメソッドの例外処理を示します。  async のタスクに適用する例外をキャッチするには、`Await` の式は、呼び出し元の `Try` ブロックになり、例外は `Catch` ブロックでキャッチされます。  
  
 コメント例外処理を示す例に `Throw New Exception` の行。  例外は `Catch` ブロックでキャッチされますが、タスクの `IsFaulted` のプロパティは `True`に設定され、タスクの `Exception.InnerException` のプロパティは、例外に設定されます。  
  
 非同期処理を取り消すとコメントから外すとどうなるかを示す `Throw New OperationCancelledException` の行。  例外は `Catch` ブロックでキャッチして、タスクの `IsCanceled` のプロパティは `True`に設定されます。  ただし、条件では、この例には適用されません `IsFaulted` は、`True` に設定され、`IsCanceled` は `False`に設定されます。  
  
 [!code-vb[csAsyncExceptions#1](../../../csharp/language-reference/keywords/codesnippet/VisualBasic/try-catch-finally-statement_7.vb)]  
  
## 使用例  
 次の例では、複数のタスクが複数の例外が発生する可能性がある場所で例外処理を示します。  `Try` ブロックに <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> が返したタスクの `Await` の式が含まれています。  タスクは <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> が適用される 3 種類のタスクが完了すると完了します。  
  
 3 個のタスクの原因の各例外。  `Catch` ブロックは `Task.WhenAll` が返したタスクの `Exception.InnerExceptions` のプロパティに、例外を反復処理します。  
  
 [!code-vb[csAsyncExceptions#3](../../../csharp/language-reference/keywords/codesnippet/VisualBasic/try-catch-finally-statement_8.vb)]  
  
## 参照  
 <xref:Microsoft.VisualBasic.Information.Err%2A>   
 <xref:System.Exception>   
 [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [On Error Statement](../../../visual-basic/language-reference/statements/on-error-statement.md)   
 [コード スニペットを使用するためのベスト プラクティス](/visual-studio/ide/best-practices-for-using-code-snippets)   
 [例外処理](../Topic/Exception%20Handling%20\(Task%20Parallel%20Library\).md)   
 [Throw Statement](../../../visual-basic/language-reference/statements/throw-statement.md)
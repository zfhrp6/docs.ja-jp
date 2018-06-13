---
title: Try...Catch...Finally ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Try...Catch...Finally
- vb.when
- vb.Finally
- vb.Catch
- vb.Try
helpviewer_keywords:
- Try...Catch...Finally statements
- Try statement [Visual Basic]
- try-catch exception handling, Try...Catch...Finally statements
- error handling, while running code
- Try statement [Visual Basic], Try...Catch...Finally
- Finally keyword [Visual Basic], Try...Catch...Finally
- Catch statement [Visual Basic]
- When keyword [Visual Basic]
- Visual Basic code, handling errors while running
- structured exception handling, Try...Catch...Finally statements
ms.assetid: d6488026-ccb3-42b8-a810-0d97b9d6472b
ms.openlocfilehash: 5e7037d1f89d56d1c65fe94e7c5fbafc7b3c40f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605486"
---
# <a name="trycatchfinally-statement-visual-basic"></a>Try...Catch...Finally ステートメント (Visual Basic)
コードの実行中に、コードの所定のブロックで発生する可能性があります一部またはすべての可能なエラーを処理する方法を提供します。  
  
## <a name="syntax"></a>構文  
  
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
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`tryStatements`|任意。 ステートメントは、エラーが発生できます。 複合ステートメントにすることもできます。|  
|`Catch`|任意。 複数`Catch`許可されているブロックです。 処理するときに例外が発生した場合、`Try`ブロックする場合に、各`Catch`と、例外を処理するかどうかを決定するテキストの順序でステートメントを調べる`exception`がスローされた例外を表すです。|  
|`exception`|任意。 任意の変数名を指定します。 `exception` の初期値は、スローされたエラーの値です。 と共に使用`Catch`キャッチ、エラーを指定します。 省略した場合は、`Catch`ステートメントはすべての例外をキャッチします。|  
|`type`|任意。 クラスのフィルターの種類を指定します。 場合の値`exception`で指定された型の`type`。 つまり、派生型の識別子が例外オブジェクトをバインドになります。|  
|`When`|任意。 A`Catch`ステートメントを`When`句が例外がキャッチされる場合にのみ`expression`に評価される`True`です。 A`When`句は、例外の種類を確認後にのみ適用されると`expression`が例外を表す識別子を参照してください。|  
|`expression`|任意。 暗黙的に変換する必要があります`Boolean`です。 汎用フィルターを記述する式。 通常、エラー番号によるフィルター処理に使用されます。 と共に使用`When`エラーはキャッチされる状況を指定するキーワードです。|  
|`catchStatements`|任意。 関連する発生したエラーを処理するステートメント`Try`ブロックします。 複合ステートメントにすることもできます。|  
|`Exit Try`|任意。 抜けキーワード、`Try...Catch...Finally`構造体。 すぐに次のコードの実行が再開、`End Try`ステートメントです。 `Finally`ステートメントは実行もします。 は許可されません`Finally`ブロックします。|  
|`Finally`|任意。 A`Finally`ブロックは、実行がの一部を離れると常に実行、`Try...Catch`ステートメントです。|  
|`finallyStatements`|任意。 その他のすべての処理の中にエラーが発生した後に実行されるステートメントです。|  
|`End Try`|終了、`Try...Catch...Finally`構造体。|  
  
## <a name="remarks"></a>コメント  
 特定の例外コードの特定のセクションの中に発生する可能性がある場合は、コードを配置、`Try`をブロックしを使用して、`Catch`コントロールを保持し、発生した場合、例外を処理するブロック。  
  
 A`Try…Catch`ステートメントには、`Try`ブロックとそれに続く 1 つ以上`Catch`句で、さまざまな例外のハンドラーを指定します。 例外がスローされたときに、`Try`ブロック、Visual Basic を検索、`Catch`例外を処理するステートメント。 一致する場合`Catch`ステートメントが見つからない場合は、Visual Basic が呼び出し履歴の上に、現在のメソッドを呼び出す方法を調べます。 ない場合は`Catch`ブロックが見つかると、Visual Basic をユーザーにハンドルされない例外メッセージを表示して、プログラムの実行を停止します。  
  
 1 つ以上を使用することができます`Catch`内のステートメント、`Try…Catch`ステートメントです。 これには、順にした場合、`Catch`句は重要では順序がチェックされるためです。 例外は、特殊性の高い順にキャッチしてください。  
  
 次`Catch`ステートメントの条件が少なくとも固有であり、すべてをキャッチする例外から派生する、<xref:System.Exception>クラスです。 前回通常これらのバリエーションの 1 つ使用する必要があります`Catch`のブロック、`Try...Catch...Finally`期待するすべての特定の例外をキャッチした後、構造体。 制御フローに到達できることはありません、`Catch`これらのバリエーションのいずれかに依存してブロックします。  
  
-   `type`は`Exception`、例を示します。 `Catch ex As Exception`  
  
-   ステートメントが no`exception`例については、変数。 `Catch`  
  
 ときに、`Try…Catch…Finally`ステートメントが別の入れ子になった`Try`ブロック、Visual Basic が最初に各検証`Catch`最も内側のステートメント`Try`ブロックします。 一致する場合`Catch`ステートメントが見つかりましたに、 `Catch` 、外側のステートメントの`Try…Catch…Finally`ブロックします。  
  
 ローカル変数、`Try`ブロックでは使用できない、`Catch`独立したブロックであるためにをブロックします。 複数のブロックで変数を使用する場合は、外部変数を宣言、`Try...Catch...Finally`構造体。  
  
> [!TIP]
>  `Try…Catch…Finally`ステートメントは IntelliSense コード スニペットとして使用できます。 コード スニペット マネージャーで **コード パターン - If、For Each、Try Catch、プロパティなど**、し**エラー処理 (例外)** です。 詳細については、「[Code Snippets](/visualstudio/ide/code-snippets)」を参照してください。  
  
## <a name="finally-block"></a>Finally ブロックします。  
 1 つまたは複数のステートメントを終了する前に実行する必要がある場合、`Try`構造体を使用して、`Finally`ブロックします。 制御が渡されます、`Finally`ブロックだけの out を渡す前に、`Try…Catch`構造体。 これは内で例外が発生した場合でも、`Try`構造体。  
  
 A`Finally`ブロックが役に任意のコードを実行している場合でも、例外が発生しましたに実行する必要があります。 制御が渡されます、`Finally`に関係なく、どのブロック`Try...Catch`ブロックが終了します。  
  
 内のコード、`Finally`ブロックが実行されますが、コードが発生した場合でも、`Return`内のステートメント、`Try`または`Catch`ブロックします。 コントロールを渡しません、`Try`または`Catch`、対応するブロック`Finally`次の場合にブロックします。  
  
-   [End ステートメント](../../../visual-basic/language-reference/statements/end-statement.md)で見つかりましたが、`Try`または`Catch`ブロックします。  
  
-   A<xref:System.StackOverflowException>でスローされた、`Try`または`Catch`ブロックします。  
  
 実行を明示的に転送することはできません、`Finally`ブロックします。 Out の実行を転送する、`Finally`ブロックが正しくないを除く、例外を通じてします。  
  
 場合、`Try`ステートメントが 1 つ以上含まれていない`Catch`ブロックを含めることは、`Finally`ブロックします。  
  
> [!TIP]
>  場合は、特定の例外をキャッチする必要はありません、`Using`ステートメントの動作と同様に、`Try…Finally`ブロックおよびブロックを終了する方法に関係なく、リソースの破棄を保証します。 これは、未処理の例外にも該当します。 詳細については、「[Using ステートメント](../../../visual-basic/language-reference/statements/using-statement.md)」を参照してください。  
  
## <a name="exception-argument"></a>例外の引数  
 `Catch`ブロック`exception`引数がのインスタンスでは、<xref:System.Exception>クラスまたはクラスから派生した、`Exception`クラスです。 `Exception`クラスのインスタンスで発生したエラーに対応して、`Try`ブロックします。  
  
 プロパティ、`Exception`オブジェクトのヘルプを原因と、例外の場所を指定します。 たとえば、<xref:System.Exception.StackTrace%2A>プロパティに、コード内のエラーの発生場所を確認できるため、例外を引き起こした呼び出されたメソッドの一覧です。 <xref:System.Exception.Message%2A> 例外を説明するメッセージが返されます。 <xref:System.Exception.HelpLink%2A> 関連付けられているヘルプ ファイルへのリンクを返します。 <xref:System.Exception.InnerException%2A> 返します、`Exception`または現在の例外の原因となったオブジェクトを返します`Nothing`元が存在しない場合`Exception`です。  
  
## <a name="considerations-when-using-a-trycatch-statement"></a>使用に関する注意点、試してみてください.Catch ステートメント  
 使用して、`Try…Catch`ステートメントのみにプログラムの異常なまたは予期しないイベントの発生を通知します。 この理由から、次のとおりです。  
  
-   実行時に例外をキャッチ、追加のオーバーヘッドを作成し、例外を回避する事前に確認するよりも遅くする可能性があります。  
  
-   場合、`Catch`ブロックが正しく処理されないが、例外が正しく表示されないことをユーザーにします。  
  
-   例外処理より複雑なプログラムをによりします。  
  
 常に必要としない、`Try…Catch`条件で発生する可能性がある条件をチェックするステートメント。 次の例では、それを開く前にファイルが存在するかどうかを確認します。 これは、必要が減り、によってスローされる例外をキャッチするため、<xref:System.IO.File.OpenText%2A>メソッドです。  
  
 [!code-vb[VbVbalrStatements#94](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_1.vb)]  
  
 必要なコードを確認してください`Catch`ブロックがまたは適切なメッセージのログ記録をスレッド セーフであるかどうかをユーザーに例外を正しく報告できます。 それ以外の場合、例外は、不明な残る可能性があります。  
  
## <a name="async-methods"></a>非同期メソッド  
 持つメソッドをマークする場合、 [Async](../../../visual-basic/language-reference/modifiers/async.md)修飾子、行うこともできます、 [Await](../../../visual-basic/language-reference/operators/await-operator.md)メソッド内の演算子。 ステートメントを`Await`演算子は、待機中のタスクが完了するまでに、メソッドの実行を中断します。 このタスクは、進行中の作業を表します。 ときに、タスクに関連付けられている、`Await`演算子が終了すると、同じメソッド内で実行が再開されます。 詳細については、次を参照してください。[非同期プログラムにおける制御フロー](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)です。  
  
 非同期のメソッドによって返されるタスクは、未処理の例外によって終了したことを示す違反状態になる可能性があります。 タスクがその結果、取り消された状態で終了するも、 `OperationCanceledException` await 式からスローされています。 どちらの種類の例外をキャッチするには、配置、`Await`内のタスクに関連付けられている式、`Try`で例外をキャッチして、ブロック、`Catch`ブロックします。 このトピックで後述する例を示します。  
  
 複数の例外がそのエラーの前に行うために、タスクは faulted 状態にできます。 たとえば、タスクは <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> の呼び出しの結果になることがあります。 このようなタスクを待機して例外をキャッチしましたが、例外の 1 つだけどの例外がキャッチされるかを予測することはできません。 このトピックで後述する例を示します。  
  
 `Await`内の式で使用できない、`Catch`ブロックまたは`Finally`ブロックします。  
  
## <a name="iterators"></a>Iterators  
 Iterator 関数または`Get`アクセサーは、コレクションに対するカスタム イテレーションを実行します。 反復子を使用して、 [Yield](../../../visual-basic/language-reference/statements/yield-statement.md)ステートメントを一度にいずれかのコレクションの各要素を返します。 使用して反復子関数を呼び出す、[ごとにしています.次のステートメントの](../../../visual-basic/language-reference/statements/for-each-next-statement.md)します。  
  
 A`Yield`内のステートメントに含めることができます、`Try`ブロックします。 A`Try`を含むブロック、`Yield`ステートメントが持つことができます`Catch`をブロックしてができます、`Finally`ブロックします。 "再試行ブロック Visual Basic で"を参照してください[反復子](../../programming-guide/concepts/iterators.md)例についてはします。  
  
 A`Yield`ステートメント内で使用できない、`Catch`ブロックまたは`Finally`ブロックします。  
  
 場合、`For Each`本体 (関数の外側で、反復子)、例外がスロー、 `Catch` iterator 関数内のブロックが実行されていないが、 `Finally` iterator 関数内のブロックを実行します。 A`Catch`反復子関数の内側のブロックは、iterator 関数内で発生する例外のみをキャッチします。  
  
## <a name="partial-trust-situations"></a>部分的に信頼された状況  
 ネットワーク共有でホストされているアプリケーションなど、部分的に信頼された状況で`Try...Catch...Finally`呼び出しを含むメソッドが呼び出される前に発生したセキュリティ例外をキャッチしません。 サーバーの共有および実行にそこから、配置するときに、次の例は、エラーを生成します"System.Security.SecurityException: 要求が失敗しました。"。 セキュリティ例外の詳細については、次を参照してください。、<xref:System.Security.SecurityException>クラスです。  
  
 [!code-vb[VbVbalrStatements#85](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_2.vb)]  
  
 このような部分的に信頼された状況で、配置する必要がある、`Process.Start`別個のステートメント`Sub`です。 最初の呼び出し、`Sub`は失敗します。 これにより、`Try...Catch`する前にそれをキャッチする、`Sub`を格納している`Process.Start`が開始されており、セキュリティ例外が生成します。  
  
## <a name="example"></a>例  
 次の例の構造を示しています、`Try...Catch...Finally`ステートメントです。  
  
 [!code-vb[VbVbalrStatements#86](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_3.vb)]  
  
## <a name="example"></a>例  
 次の例で、`CreateException`メソッドがスローされます、`NullReferenceException`です。 例外を生成するコードに含まれていない、`Try`ブロックします。 したがって、`CreateException`メソッドが例外を処理できません。 `RunSample`ために、メソッドは例外を処理はへの呼び出し、`CreateException`にメソッドが、`Try`ブロックします。  
  
 例が含まれています`Catch`から複数の種類、例外のためのステートメントの順序、一般的に最も固有の仕様です。  
  
 [!code-vb[VbVbalrStatements#91](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_4.vb)]  
  
## <a name="example"></a>例  
 次の例を使用する方法を示しています、`Catch When`条件付きの式をフィルター処理ステートメント。 条件式の評価が場合`True`、内のコード、`Catch`ブロックが実行されます。  
  
 [!code-vb[VbVbalrStatements#92](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_5.vb)]  
  
## <a name="example"></a>例  
 次の例は、`Try…Catch`ステートメントに含まれている、`Try`ブロックします。 内部`Catch`ブロックが例外をスローする、`InnerException`プロパティを元の例外に設定します。 外側`Catch`ブロックは、独自の例外と内部例外を報告します。  
  
 [!code-vb[VbVbalrStatements#93](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_6.vb)]  
  
## <a name="example"></a>例  
 次の例では、非同期メソッドの例外処理を示します。 非同期タスクに適用される例外をキャッチする、`Await`式には、`Try`でブロック、呼び出し元とは、例外がキャッチされました、`Catch`ブロックします。  
  
 例外処理を示すために、この例の `Throw New Exception` 行のコメントを解除します。 例外がキャッチされました、`Catch`ブロック、タスクの`IsFaulted`プロパティに設定されている`True`、およびタスクの`Exception.InnerException`プロパティが例外に設定します。  
  
 `Throw New OperationCancelledException` 行のコメントを解除して、非同期処理を取り消したときに何が起こるかを示します。 例外がキャッチされました、`Catch`ブロック、およびタスクの`IsCanceled`プロパティに設定されている`True`です。 ただし、この例に該当しない一部の条件下で`IsFaulted`に設定されている`True`と`IsCanceled`に設定されている`False`です。  
  
 [!code-vb[csAsyncExceptions#1](../../../csharp/language-reference/keywords/codesnippet/VisualBasic/try-catch-finally-statement_7.vb)]  
  
## <a name="example"></a>例  
 次の例では、複数のタスクで複数の例外が発生する可能性がある例外処理について説明します。 `Try`ブロックには、`Await`タスクの式を<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>が返されます。 3 つのタスクとタスクが完了<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>適用が完了します。  
  
 3 つのタスクでそれぞれ例外が発生します。 `Catch`は、例外を反復処理ブロック、`Exception.InnerExceptions`タスクのプロパティを`Task.WhenAll`が返されます。  
  
 [!code-vb[csAsyncExceptions#3](../../../csharp/language-reference/keywords/codesnippet/VisualBasic/try-catch-finally-statement_8.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:System.Exception>  
 [Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [On Error ステートメント](../../../visual-basic/language-reference/statements/on-error-statement.md)  
 [コード スニペットを使用するためのベスト プラクティス](/visualstudio/ide/best-practices-for-using-code-snippets)  
 [例外処理](../../../standard/parallel-programming/exception-handling-task-parallel-library.md)  
 [Throw ステートメント](../../../visual-basic/language-reference/statements/throw-statement.md)

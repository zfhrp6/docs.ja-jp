---
title: "しようとしてください.キャッチしてください.Finally ステートメント (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Try...Catch...Finally
- vb.when
- vb.Finally
- vb.Catch
- vb.Try
dev_langs:
- VB
helpviewer_keywords:
- Try...Catch...Finally statements
- Try statement
- try-catch exception handling, Try...Catch...Finally statements
- error handling, while running code
- Try statement, Try...Catch...Finally
- Finally keyword [Visual Basic], Try...Catch...Finally
- Catch statement
- When keyword
- Visual Basic code, handling errors while running
- structured exception handling, Try...Catch...Finally statements
ms.assetid: d6488026-ccb3-42b8-a810-0d97b9d6472b
caps.latest.revision: 69
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 379359e3a338746ccd440dbe1ad58c483e562dbe
ms.lasthandoff: 03/13/2017

---
# <a name="trycatchfinally-statement-visual-basic"></a>Try...Catch...Finally ステートメント (Visual Basic)
コードを実行しながら、コードの所定のブロックで発生する可能性一部またはすべての可能なエラーを処理する方法を提供します。  
  
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
|`tryStatements`|省略可能です。 ステートメントは、エラーが発生することができます。 複合ステートメントにすることもできます。|  
|`Catch`|省略可能です。 複数`Catch`許可されているブロックです。 処理するときに例外が発生した場合、`Try`ブロックする場合に、各`Catch`ステートメントが記述されていると、例外を処理するかどうかを判断する順で調べられ`exception`がスローされた例外を表します。|  
|`exception`|省略可能です。 任意の変数名を指定します。 `exception` の初期値は、スローされたエラーの値です。 併用`Catch`キャッチ、エラーを指定します。 省略した場合は、`Catch`ステートメントは、例外をキャッチします。|  
|`type`|省略可能です。 クラスのフィルターの種類を指定します。 場合の値`exception`で指定された型の`type`または派生型の識別子は、例外オブジェクトにバインドになります。|  
|`When`|省略可能です。 A`Catch`ステートメントを`When`句が例外がキャッチされる場合にのみ`expression`に評価`True`します。 A`When`句は、例外の種類を確認後にのみ適用されると`expression`が例外を表す識別子を参照してください。|  
|`expression`|省略可能です。 暗黙的に変換する必要があります`Boolean`します。 汎用フィルターを記述する式です。 通常、エラー番号でフィルター処理に使用されます。 併用`When`エラーがキャッチされる状況を指定するキーワードです。|  
|`catchStatements`|省略可能です。 関連する発生したエラーを処理するステートメント`Try`ブロックします。 複合ステートメントにすることもできます。|  
|`Exit Try`|省略可能です。 抜けキーワード、`Try...Catch...Finally`構造体。 すぐに次のコードから実行が再開、`End Try`ステートメントです。 `Finally`ステートメントは引き続き実行されます。 は許可されません`Finally`ブロックします。|  
|`Finally`|省略可能です。 A`Finally`実行がの任意の部分を離れると、ブロックが常に実行、`Try...Catch`ステートメントです。|  
|`finallyStatements`|省略可能です。 他のすべてのエラー処理が発生した後に実行されるステートメントです。|  
|`End Try`|終了、`Try...Catch...Finally`構造体。|  
  
## <a name="remarks"></a>コメント  
 コードの特定のセクションで特定の例外が発生することを予定の場合にコードを配置、`Try`をブロックし、使用して、`Catch`ブロックを制御し、発生した場合、例外を処理します。  
  
 A`Try…Catch`ステートメントには、`Try`ブロックでは、1 つ以上続く`Catch`句で、さまざまな例外のハンドラーを指定します。 例外がスローされたときに、`Try`ブロック、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]の検索、`Catch`例外を処理するステートメントです。 一致する場合は、`Catch`ステートメントが検出されなければ、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コール スタックの上に、現在のメソッドが呼び出されるメソッドを調べます。 ない場合`Catch`ブロックが見つかると、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]をユーザーにハンドルされない例外メッセージが表示され、プログラムの実行を停止します。  
  
 1 つ以上を使用する`Catch`内のステートメントで、`Try…Catch`ステートメントです。 これにより、注文の場合、`Catch`句は重要では順序がチェックされるためです。 例外は、特殊性の高い順にキャッチしてください。  
  
 次`Catch`ステートメントの条件が少なくとも固有であり、キャッチ オール<xref:System.Exception>クラス</xref:System.Exception>から派生する例外 最後として通常これらのバリエーションの&1; つ使用する必要があります`Catch`内のブロック、`Try...Catch...Finally`期待するすべての特定の例外をキャッチした後、構造体。 制御フローに到達できることはありません、`Catch`これらのバリエーションのいずれかを次のブロックにします。  
  
-   `type`は`Exception`など。`Catch ex As Exception`  
  
-   ステートメントでは、no`exception`例については、変数。`Catch`  
  
 ときに、`Try…Catch…Finally`別のステートメントが入れ子になった`Try`ブロック、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]最初に各検証`Catch`最も内側のステートメント`Try`ブロックします。 一致する場合は、`Catch`ステートメントが見つかると、検索を実行する、`Catch`の外側のステートメント`Try…Catch…Finally`ブロックします。  
  
 ローカル変数、`Try`ブロックでは使用できない、`Catch`これらは独立したブロックをブロックします。 複数のブロックで変数を使用する場合は、外部変数を宣言、`Try...Catch...Finally`構造体。  
  
> [!TIP]
>  `Try…Catch…Finally`ステートメントは IntelliSense コード スニペットとして利用できます。 コード スニペット マネージャーでは、展開**コード パターンの場合は、ごとに、Try Catch プロパティなど**、し**エラー処理 (例外)**します。 詳細については、「[Code Snippets](https://docs.microsoft.com/visualstudio/ide/code-snippets)」を参照してください。  
  
## <a name="finally-block"></a>Finally ブロックします。  
 終了する前に実行する&1; つまたは複数のステートメントがある場合、`Try`構造体を使用して、`Finally`ブロックします。 コントロールに渡して、`Finally`の外部に移るにする前にブロック、`Try…Catch`構造体。 これは内で例外が発生した場合でも、`Try`構造体。  
  
 A`Finally`ブロックは例外がある場合でも任意のコードを実行すると実行する必要があります。 制御が渡される、`Finally`関係なくブロック`Try...Catch`ブロックが終了します。  
  
 内のコード、 `Finally` 、コードが発生した場合でも、ブロックが実行を`Return`内のステートメントで、`Try`または`Catch`ブロックします。 コントロールを渡しません、`Try`または`Catch`、対応するブロック`Finally`ブロックで、次の場合。  
  
-   [End ステートメント](../../../visual-basic/language-reference/statements/end-statement.md)がで検出された、`Try`または`Catch`ブロックします。  
  
-   A<xref:System.StackOverflowException>でスローされた、`Try`または`Catch`ブロック</xref:System.StackOverflowException>。  
  
 実行を明示的に転送することはできません、`Finally`ブロックします。 Out の実行を転送する、`Finally`ブロックが例外を除いて有効ではありません。  
  
 場合、`Try`ステートメントが&1; つ以上含まれていない`Catch`ブロックを含めることは、`Finally`ブロックします。  
  
> [!TIP]
>  場合は、特定の例外をキャッチする必要はありません、`Using`のようにステートメントの動作、`Try…Finally`ブロックおよびブロックを終了する方法に関係なく、リソースの破棄を保証します。 これは、未処理の例外にも当てはまります。 詳細については、次を参照してください。 [Using ステートメント](../../../visual-basic/language-reference/statements/using-statement.md)します。  
  
## <a name="exception-argument"></a>例外の引数  
 `Catch`ブロック`exception`引数は、のインスタンス、<xref:System.Exception>クラスまたはクラスから派生した、`Exception`クラス</xref:System.Exception> `Exception`クラスのインスタンスで発生したエラーに対応して、`Try`ブロックします。  
  
 プロパティ、`Exception`オブジェクトのヘルプを原因と、例外の場所を指定します。 たとえば、<xref:System.Exception.StackTrace%2A>プロパティに、コード内のエラーの発生場所を確認できるため、例外を引き起こしたと呼ばれるメソッドの一覧します</xref:System.Exception.StackTrace%2A>。 <xref:System.Exception.Message%2A>例外を説明するメッセージが返されます。</xref:System.Exception.Message%2A> <xref:System.Exception.HelpLink%2A>関連するヘルプ ファイルにリンクが返されます。</xref:System.Exception.HelpLink%2A> <xref:System.Exception.InnerException%2A>返します、`Exception`または現在の例外の原因となったオブジェクトが返す`Nothing`元が存在しない場合`Exception`します。</xref:System.Exception.InnerException%2A>  
  
## <a name="considerations-when-using-a-trycatch-statement"></a>Try を使用する際の考慮事項は.Catch ステートメント  
 使用して、`Try…Catch`ステートメント プログラムの異常なまたは予期しないイベントの発生を通知するだけです。 この理由から、次のとおりです。  
  
-   実行時に例外をキャッチすると、追加のオーバーヘッドを作成し、例外を回避する前に確認するよりも遅くする可能性があります。  
  
-   場合、`Catch`ブロックが正常に処理されない、例外がユーザーに正しく報告されましていない可能性があります。  
  
-   例外処理では、プログラムをさらに複雑なにします。  
  
 常に必要としない、`Try…Catch`条件で発生する可能性がある条件をチェックするステートメントです。 次の例では、それを開く前に、ファイルが存在するかどうかを確認します。 これによってスローされる例外をキャッチする必要性が軽減、<xref:System.IO.File.OpenText%2A>メソッド</xref:System.IO.File.OpenText%2A>。  
  
 [!code-vb[VbVbalrStatements #&94;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_1.vb)]  
  
 コードのことを確認`Catch`ブロックを通じてスレッド セーフなログ記録、または適切なメッセージにユーザーが例外を報告正しくことができます。 それ以外の場合、例外は、不明な残る可能性があります。  
  
## <a name="async-methods"></a>非同期メソッド  
 持つメソッドをマークした場合、 [Async](../../../visual-basic/language-reference/modifiers/async.md)修飾子は、使用できます、 [Await](../../../visual-basic/language-reference/operators/await-operator.md)メソッド内の演算子です。 指定したステートメント、`Await`演算子は、待機中のタスクが完了するまでに、メソッドの実行を中断します。 このタスクは、進行中の作業を表します。 ときに関連付けられているタスク、`Await`演算子が終了すると、同じメソッド内での実行が再開されます。 詳細については、次を参照してください。[非同期プログラムにおける制御のフロー](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)します。  
  
 非同期のメソッドによって返されるタスクは、未処理の例外によって完了したことを示すエラーが発生した状態になる可能性があります。 タスクがその結果、取り消された状態になる可能性がありますも、 `OperationCanceledException` await 式からスローされます。 どちらの種類の例外をキャッチするには、配置、`Await`式内のタスクに関連付けられている、`Try`で例外をキャッチして、ブロック、`Catch`ブロックします。 例については、このトピックの後半で提供されます。  
  
 複数の例外がそのエラーの前に行うために、タスクは faulted 状態にできます。 タスクが<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>。</xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>への呼び出しの結果になる可能性があります、 このようなタスクを待機するときにキャッチされた例外は、例外を&1; つと、どの例外がキャッチされるを予測することはできません。 例については、このトピックの後半で提供されます。  
  
 `Await`内の式で使用できない、`Catch`ブロックまたは`Finally`ブロックします。  
  
## <a name="iterators"></a>反復子  
 Iterator 関数または`Get`アクセサーは、コレクションに対するカスタム イテレーションを実行します。 反復子を使用して、 [Yield](../../../visual-basic/language-reference/statements/yield-statement.md)ステートメントを一度に&1; つのコレクションの各要素を返します。 使用して反復子関数を呼び出す、[ごとにしています.次のステートメントの](../../../visual-basic/language-reference/statements/for-each-next-statement.md)です。  
  
 A`Yield`ステートメントは、内で使用できます、`Try`ブロックします。 A`Try`を含むブロック、`Yield`ステートメントにはできます`Catch`ブロック、およびことができますが、`Finally`ブロックします。 "再試行ブロックで Visual Basic"を参照してください[反復子](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)例については、です。  
  
 A`Yield`ステートメント内で使用できない、`Catch`ブロックまたは`Finally`ブロックします。  
  
 場合、`For Each`本体 (iterator 関数) の外部で、例外がスロー、 `Catch` iterator 関数内のブロックは実行されませんが、`Finally`反復子関数でのブロックを実行します。 A`Catch`反復子関数の内側のブロックは、反復子関数内で発生する例外だけをキャッチします。  
  
## <a name="partial-trust-situations"></a>部分的に信頼された状況  
 ネットワーク共有にホストされるアプリケーションなど、部分的に信頼された状況で`Try...Catch...Finally`呼び出しが含まれているメソッドが呼び出される前に発生するセキュリティ例外をキャッチしません。 次の例、そこから、サーバーの共有と実行に格納するときにエラーを生成する"System.Security.SecurityException: 失敗を要求します"。 セキュリティ例外の詳細については、<xref:System.Security.SecurityException>クラス</xref:System.Security.SecurityException>を参照してください。  
  
 [!code-vb[VbVbalrStatements #&85;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_2.vb)]  
  
 このような部分的に信頼された場合に、登録する必要が、`Process.Start`別個のステートメント`Sub`します。 最初の呼び出し、`Sub`は失敗します。 これにより、`Try...Catch`する前にそれをキャッチする、`Sub`を含む`Process.Start`が開始し、セキュリティ例外が生成されます。  
  
## <a name="example"></a>例  
 次の例の構造を示しています、`Try...Catch...Finally`ステートメントです。  
  
 [!code-vb[VbVbalrStatements #&86;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_3.vb)]  
  
## <a name="example"></a>例  
 次の例では、`CreateException`メソッドでのスロー、`NullReferenceException`です。 例外を生成するコードに含まれていない、`Try`ブロックします。 したがって、`CreateException`メソッドが例外を処理できません。 `RunSample`ため、例外の処理はメソッドへの呼び出し、`CreateException`にメソッドが、`Try`ブロックします。  
  
 この例では`Catch`からいくつかの種類の例外、ステートメントの順序に最も一般的な特定します。  
  
 [!code-vb[VbVbalrStatements #&91;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_4.vb)]  
  
## <a name="example"></a>例  
 次の例を使用する方法を示しています、`Catch When`ステートメント条件式をフィルター処理します。 条件式と評価された場合`True`、内のコード、`Catch`ブロックが実行されます。  
  
 [!code-vb[VbVbalrStatements #&92;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_5.vb)]  
  
## <a name="example"></a>例  
 次の例は、`Try…Catch`ステートメントに含まれている、`Try`ブロックします。 内部`Catch`ブロックが例外をスローする、`InnerException`プロパティが、元の例外に設定します。 外側`Catch`ブロックは、独自の例外と内部例外を報告します。  
  
 [!code-vb[VbVbalrStatements #&93;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/try-catch-finally-statement_6.vb)]  
  
## <a name="example"></a>例  
 次の例では、非同期メソッドの例外処理を示します。 非同期タスクに適用される例外をキャッチする、`Await`にある式は、`Try`でブロック、呼び出し元と、例外がキャッチされました、`Catch`ブロックします。  
  
 例外処理を示すために、この例の `Throw New Exception` 行のコメントを解除します。 例外がキャッチされました、`Catch`ブロック、タスクの`IsFaulted`にプロパティが設定されている`True`、およびタスクの`Exception.InnerException`プロパティは、例外に設定します。  
  
 コメントを解除、`Throw New OperationCancelledException`行を非同期的な処理をキャンセルすると、動作を示します。 例外がキャッチされました、`Catch`ブロック、およびタスクの`IsCanceled`にプロパティが設定されている`True`します。 ただし、状況によってこの例に適用されない`IsFaulted`に設定されている`True`と`IsCanceled`に設定されている`False`します。  
  
 [!code-vb[csAsyncExceptions&1;](../../../csharp/language-reference/keywords/codesnippet/VisualBasic/try-catch-finally-statement_7.vb)]  
  
## <a name="example"></a>例  
 次の例では、複数のタスクで複数の例外が発生する可能性がある例外処理について説明します。 `Try`ブロックには、`Await`タスクの式を<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>が返されます</xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>。 タスクが完了するタスクの&3; つすると<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>適用が完了します</xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>。  
  
 3 つのタスクでそれぞれ例外が発生します。 `Catch`は、例外を反復処理ブロック、`Exception.InnerExceptions`タスクのプロパティを`Task.WhenAll`が返されます。  
  
 [!code-vb[csAsyncExceptions&3;](../../../csharp/language-reference/keywords/codesnippet/VisualBasic/try-catch-finally-statement_8.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Information.Err%2A></xref:Microsoft.VisualBasic.Information.Err%2A>   
 <xref:System.Exception></xref:System.Exception>   
 [Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [On Error ステートメント](../../../visual-basic/language-reference/statements/on-error-statement.md)   
 [コード スニペットを使用するためのベスト プラクティス](https://docs.microsoft.com/visualstudio/ide/best-practices-for-using-code-snippets)   
 [例外処理](https://msdn.microsoft.com/library/dd997415)   
 [Throw ステートメント](../../../visual-basic/language-reference/statements/throw-statement.md)

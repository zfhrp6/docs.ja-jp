---
redirect_url: /dotnet/articles/csharp/programming-guide/exceptions/
caps.handback.revision: 33
---
# 例外と例外処理 (C# プログラミング ガイド)
C\# 言語の例外処理機能は、プログラムの実行中に発生する不測の状況や例外的な状況への対処に役立ちます。  例外処理では、`try`、`catch`、および `finally` の各キーワードを使用して、成功しない可能性のあるアクションの試行、妥当と判断した場合のエラーの処理、およびリソースの後処理を行います。  例外は、共通言語ランタイム \(CLR: Common Language Runtime\)、.NET Framework やサードパーティ ライブラリ、またはアプリケーション コードによって生成できます。  例外は、`throw` キーワードを使用して作成されます。  
  
 例外は、コードで直接呼び出したメソッドからではなく、呼び出し履歴の深い階層に位置する他のメソッドからスローされることがよくあります。  このような例外が発生すると、CLR は呼び出し履歴をアンワインドして、特定の種類の例外を処理する `catch` ブロックを持つメソッドを探し、最初に見つかった `catch` ブロックを実行します。  呼び出し履歴内のどこにも適切な `catch` ブロックがない場合は、プロセスが終了し、ユーザーにメッセージが表示されます。  
  
 次の例では、メソッドでゼロ除算をテストしてエラーをキャッチします。  例外処理がなければ、このプログラムは、**"DivideByZeroException はハンドルされませんでした。"** エラーによって終了します。  
  
 [!code-cs[csProgGuideExceptions#18](../../../csharp/programming-guide/exceptions/codesnippet/csharp/exceptions-and-exception_1.cs)]  
  
## 例外の概要  
 例外には、次のような特徴があります。  
  
-   例外は、最終的にはすべて `System.Exception` から派生する型です。  
  
-   例外をスローする可能性のあるステートメントの周囲に `try` ブロックを使用します。  
  
-   `try` ブロックで例外が発生すると、制御フローは呼び出し履歴内の任意の場所に存在する最初の関連する例外ハンドラーにジャンプします。  C\# では、`catch` キーワードを使用して例外ハンドラーを定義します。  
  
-   特定の例外用の例外ハンドラーがない場合、プログラムはエラー メッセージを表示して実行を停止します。  
  
-   例外を処理し、アプリケーションを既知の状態にしておくことができない場合は、例外をキャッチしないでください。  `System.Exception` をキャッチした場合は、`catch` ブロックの最後で `throw` キーワードを使用して再スローします。  
  
-   `catch` ブロックに例外変数が定義されている場合は、これを使用して、発生した例外の種類についての詳細な情報を取得できます。  
  
-   `throw` キーワードを使用すると、例外をプログラムで明示的に生成することができます。  
  
-   例外オブジェクトには、呼び出し履歴の状態やエラーのテキスト説明など、エラーに関する詳細情報が含まれています。  
  
-   例外がスローされた場合でも、`finally` ブロック内のコードが実行されます。  `finally` ブロックを使用して、たとえば、`try` ブロックで開いたストリームまたはファイルを閉じるために、リソースを解放します。  
  
-   .NET Framework のマネージ例外は、Win32 構造化例外処理機構上に実装されます。  詳細については、「[構造化例外処理](/visual-cpp/cpp/structured-exception-handling-c-cpp)」と「[A Crash Course on the Depths of Win32 Structured Exception Handling](http://go.microsoft.com/fwlink/?LinkId=119654)」を参照してください。  
  
## 関連項目  
 例外と例外処理の詳細については、以下のトピックを参照してください。  
  
-   [例外の使用](../../../csharp/programming-guide/exceptions/using-exceptions.md)  
  
-   [例外処理](../../../csharp/programming-guide/exceptions/exception-handling.md)  
  
-   [例外の作成とスロー](../../../csharp/programming-guide/exceptions/creating-and-throwing-exceptions.md)  
  
-   [コンパイラにより生成された例外](../../../csharp/programming-guide/exceptions/compiler-generated-exceptions.md)  
  
-   [方法: try\/catch を使用して例外を処理する](../../../csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md)  
  
-   [方法: finally を使用してクリーンアップ コードを実行する](../../../csharp/programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md)  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 <xref:System.SystemException>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [throw](../../../csharp/language-reference/keywords/throw.md)   
 [try\-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [try\-finally](../../../csharp/language-reference/keywords/try-finally.md)   
 [try\-catch\-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)   
 [例外](../Topic/Handling%20and%20Throwing%20Exceptions.md)   
 [例外階層](../Topic/Exception%20Hierarchy.md)   
 [信頼できる.NETコードを記述できます。](http://go.microsoft.com/fwlink/?LinkId=112400)   
 [特定の例外のミニダンプ](http://go.microsoft.com/fwlink/?LinkId=112408)
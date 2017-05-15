---
title: "try-catch (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- try
- try_CSharpKeyword
- catch
- catch_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- catch keyword [C#]
- try-catch statement [C#]
ms.assetid: cb5503c7-bfa1-4610-8fc2-ddcd2e84c438
caps.latest.revision: 45
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 13684c7e32c52765f4d45d6a5bd2c6f8194efefe
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="try-catch-c-reference"></a>try-catch (C# リファレンス)
try-catch ステートメントは、`try` ブロックと、それに続く 1 つ以上の `catch` 句で構成されます。この句にはさまざまな例外のハンドラーを指定します。  
  
## <a name="remarks"></a>コメント  
 例外がスローされると、共通言語ランタイム (CLR) によって、この例外を処理する `catch` ステートメントが検索されます。 現在実行されているメソッドにそのような `catch` ブロックが含まれていない場合、CLR は現在のメソッドを呼び出したメソッドを検索し、呼び出し履歴の上位を検索していきます。 `catch` ブロックが見つからない場合、CLR はハンドルされていない例外のメッセージをユーザーに表示し、プログラムの実行を停止します。  
  
 `try` ブロックには、例外を発生させる可能性がある保護されたコードが含まれます。 このブロックは、例外がスローされるか、ブロックが正常に終了するまで実行されます。 たとえば、次の例では `null` オブジェクトをキャストしようとすると、<xref:System.NullReferenceException> 例外が発生します。  
  
```csharp  
object o2 = null;  
try  
{  
    int i2 = (int)o2;   // Error  
}  
```  
  
 `catch` 句は、引数なしで使用してすべての種類の例外をキャッチできますが、この使用方法はお勧めできません。 通常は、回復方法が判明している例外のみキャッチします。 そのため、常に <xref:System.Exception?displayProperty=fullName> から派生したオブジェクト引数を指定してください。以下に例を示します。  
  
```csharp  
catch (InvalidCastException e)   
{  
}  
```  
  
 同一の try-catch ステートメントで、特定の `catch` 句を複数回使用することもできます。 この場合、`catch` 句は順序どおりにチェックされるため、`catch` 句の順序が重要になります。 例外は、特殊性の高い順にキャッチしてください。 後のブロックに到達しないような順序で catch ブロックを並べた場合、コンパイラでエラーが発生します。  
  
 処理対象の例外をフィルター処理する方法の 1 つに、`catch` 引数の使用があります。  また、述語式を使用して例外を確認し、それを処理するかどうかを決定することもできます。  述語式が false を返す場合、ハンドラーの検索が続行されます。  
  
```csharp  
catch (ArgumentException e) when (e.ParamName == "…")  
{  
}  
```  
  
 スタックはフィルターの影響を受けないため、キャッチと再スロー (以下で説明します) には例外フィルターが適しています。  後のハンドラーでスタックをダンプすると、再スローされた最後の場所だけではなく、例外が最初に発生した場所がわかります。  例外のフィルター式の一般的な用途の 1 つにログの記録があります。  常に false を返しログも出力する述語関数を作成すれば、処理や再スローの必要なしにそのままの状態で例外をログに記録することができます。  
  
 `catch` ステートメントでキャッチされた例外を再びスローするには、`catch` ブロックで [throw](../../../csharp/language-reference/keywords/throw.md) ステートメントを使用できます。 次の例では、<xref:System.IO.IOException> 例外からソース情報を抽出した後、親メソッドに例外をスローします。  
  
```csharp  
catch (FileNotFoundException e)  
{  
    // FileNotFoundExceptions are handled here.  
}  
catch (IOException e)  
{  
    // Extract some information from this exception, and then   
    // throw it to the parent method.  
    if (e.Source != null)  
        Console.WriteLine("IOException source: {0}", e.Source);  
    throw;  
}  
```  
  
 例外をキャッチして、別の例外をスローできます。 これを行うには、次の例に示すように、キャッチする例外を内部例外として指定します。  
  
```csharp  
catch (InvalidCastException e)   
{  
    // Perform some action here, and then throw a new exception.  
    throw new YourCustomException("Put your error message here.", e);  
}  
```  
  
 次の例に示すように、指定した条件が true の場合に例外を再スローすることもできます。  
  
```csharp  
catch (InvalidCastException e)  
{  
    if (e.Data == null)  
    {  
        throw;  
    }  
    else  
    {  
        // Take some action.  
    }  
 }  
```  
  
 `try` ブロック内では、そのブロックで宣言されている変数のみを初期化します。 そうしないと、ブロックの実行が完了する前に例外が発生する可能性があります。 たとえば、次のコードでは、変数 `n` が `try` ブロック内で初期化されています。 この変数を `try` ブロックの外側にある `Write(n)` ステートメントで使おうとすると、コンパイラ エラーが発生します。  
  
```csharp  
static void Main()   
{  
    int n;  
    try   
    {  
        // Do not initialize this variable here.  
        n = 123;  
    }  
    catch  
    {  
    }  
    // Error: Use of unassigned local variable 'n'.  
    Console.Write(n);  
}  
```  
  
 catch の詳細については、「[try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)」を参照してください。  
  
## <a name="exceptions-in-async-methods"></a>非同期メソッドの例外  
 非同期メソッドは [async](../../../csharp/language-reference/keywords/async.md) 修飾子でマークされ、通常は 1 つ以上の await 式またはステートメントが含まれます。 await 式では、[await](../../../csharp/language-reference/keywords/await.md) 演算子が <xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> に適用されます。  
  
 コントロールが非同期メソッドの `await` に到達すると、メソッドの進行状況は、待機中のタスクが完了するまで中断されます。 タスクが完了すると、メソッドで実行を再開できます。 詳細については、「[Async および Await を使用した非同期プログラミング](../../../csharp/programming-guide/concepts/async/index.md)」と「[非同期プログラムにおける制御フロー](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)」を参照してください。  
  
 `await` が適用される完了したタスクは、タスクを返すメソッドでハンドルされない例外が発生したことが原因で、違反状態になる場合があります。 タスクを待機すると例外がスローされます。 タスクを返す非同期処理が取り消された場合に、取り消された状態でタスクを終了することもできます。 取り消されたタスクを待機すると、`OperationCanceledException` がスローされます。 非同期処理を取り消す方法の詳細については、「[非同期アプリケーションの微調整](http://msdn.microsoft.com/library/daaa32ea-c84c-4761-8230-c8292ffebd74)」を参照してください。  
  
 例外をキャッチするには、`try` ブロックでタスクを待機し、関連付けられている `catch` ブロックで例外をキャッチします。 例については、「使用例」のセクションを参照してください。  
  
 待機中の非同期メソッドで複数の例外が発生したことが原因で、タスクが違反状態になることがあります。 たとえば、タスクが <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> の呼び出しの結果である場合があります。 このようなタスクを待機すると、1 つの例外のみがキャッチされます。どの例外がキャッチされるかは予測できません。 例については、「使用例」のセクションを参照してください。  
  
## <a name="example"></a>例  
 例外が発生する可能性がある `ProcessString` メソッドへの呼び出しを含む `try` ブロックの例を次に示します。 `catch` 句には、メッセージを画面に表示するだけの例外ハンドラーがあります。 `throw` ステートメントが `MyMethod` の内側から呼び出されると、システムによって `catch` ステートメントが検索され、メッセージ `Exception caught` が表示されます。  
  
 [!code-cs[csrefKeywordsExceptions#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_1.cs)]  
  
## <a name="example"></a>例  
 次の例では、2 種類の catch ブロックが使用され、特殊性が最も高い最初の例外がキャッチされます。  
  
 特殊性が最も低い例外をキャッチするには、`ProcessString` の throw ステートメントを `throw new Exception()` と置き換えることができます。  
  
 この例で特殊性が最も低い catch ブロックを最初に配置すると、"`A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`" というエラー メッセージが表示されます。  
  
 [!code-cs[csrefKeywordsExceptions#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_2.cs)]  
  
## <a name="example"></a>例  
 次の例では、非同期メソッドの例外処理を示します。 非同期タスクからスローされる例外をキャッチするには、`try` ブロックに `await` 式を配置し、`catch` ブロックで例外をキャッチします。  
  
 例外処理を示すために、この例の `throw new Exception` 行のコメントを解除します。 タスクの `IsFaulted` プロパティが `True` に設定され、タスクの `Exception.InnerException` プロパティが例外に設定され、例外が `catch` ブロックでキャッチされます。  
  
 `throw new OperationCancelledException` 行のコメントを解除して、非同期処理を取り消したときに何が起こるかを示します。 タスクの `IsCanceled` プロパティが `true` に設定され、例外が `catch` ブロックでキャッチされます。 この例に該当しない一部の条件では、タスクの `IsFaulted` プロパティが `true` に設定され、`IsCanceled` が `false` に設定されます。  
  
 [!code-cs[csAsyncExceptions#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_3.cs)]  
  
## <a name="example"></a>例  
 次の例では、複数のタスクで複数の例外が発生する可能性がある例外処理について説明します。 `try` ブロックは <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> の呼び出しで返されるタスクを待機します。 WhenAll が適用される 3 つのタスクが完了すると、このタスクは完了します。  
  
 3 つのタスクでそれぞれ例外が発生します。 `catch` ブロックは例外を反復処理します。この例外は、<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> で返されたタスクの `Exception.InnerExceptions` プロパティで見つかります。  
  
 [!code-cs[csAsyncExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_4.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [try、throw、catch ステートメント (C++)](https://docs.microsoft.com/cpp/cpp/try-throw-and-catch-statements-cpp)   
 [例外処理ステートメント](../../../csharp/language-reference/keywords/exception-handling-statements.md)   
 [throw](../../../csharp/language-reference/keywords/throw.md)   
 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)   
 [方法: 例外を明示的にスローする](https://msdn.microsoft.com/library/xhcbs8fz)


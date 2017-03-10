---
redirect_url: /dotnet/articles/csharp/linq/handle-exceptions-in-query-expressions
caps.handback.revision: 15
---
# 方法 : クエリ式の例外を処理する (C# プログラミング ガイド)
クエリ式のコンテキストで任意のメソッドを呼び出すことができます。  ただし、データ ソースの内容が変更されたり例外がスローされたりする副作用が発生する可能性のあるメソッドを、クエリ式で呼び出すことは避けることをお勧めします。  ここでは、クエリ式でメソッドを呼び出すときに、例外の処理に関する一般的な [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] のガイドラインに違反することなく、例外の発生を防ぐ方法の例を示します。  これらのガイドラインでは、特定の例外が特定のコンテキストでスローされる理由を把握できている場合は、その例外のキャッチが許可されるものとして説明されています。  詳細については、「[例外の推奨事項](../Topic/Best%20Practices%20for%20Exceptions.md)」を参照してください。  
  
 最後の例は、クエリの実行時に例外をスローする必要がある場合の処理方法を示しています。  
  
## 使用例  
 例外処理コードをクエリ式の外に移動する方法の例を次に示します。  これは、メソッドがクエリのローカル変数に依存しない場合にのみ可能です。  
  
 [!code-cs[csProgGuideLINQ#10](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csrefLINQHowTos.cs#10)]  
  
## 使用例  
 場合によっては、クエリの実行を即座に停止することが、クエリ内からスローされる例外に対する最良の対処方法になります。  クエリ本体の内部からスローされる可能性のある例外の処理方法の例を次に示します。  `SomeMethodThatMightThrow` で、クエリの実行を停止する必要のある例外が発生する可能性があると仮定します。  
  
 `try` ブロックは `foreach` ループを包含しますが、クエリ自体は包含しません。  これは、クエリを実際に実行する場所が `foreach` ループであるためです。  詳細については、「[Introduction to LINQ Queries \(C\#\)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)」を参照してください。  
  
 [!code-cs[csProgGuideLINQ#12](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csrefLINQHowTos.cs#12)]  
  
## コードのコンパイル  
  
-   .NET Framework Version 3.5 を対象とする [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs-current-short-md.md)] プロジェクトを作成します。  既定では、プロジェクトには、System.Core.dll への参照と、System.Linq 名前空間に対する `using` ディレクティブが含まれます。  
  
-   コードをプロジェクト内にコピーします。  
  
-   F5 キーを押して、プログラムをコンパイルおよび実行します。  
  
 任意のキーを押して、コンソール ウィンドウを終了します。  
  
## 参照  
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)
---
redirect_url: /dotnet/articles/csharp/programming-guide/main-and-command-args/
caps.handback.revision: 30
---
# Main() とコマンド ライン引数 (C# プログラミング ガイド)
`Main` メソッドは、C\# コンソール アプリケーションまたは Windows アプリケーションのエントリ ポイントです    \(ライブラリおよびサービスは、エントリ ポイントとして `Main` メソッドを必要としません\)。  `Main` メソッドは、アプリケーション起動時に最初に呼び出されるメソッドです。  
  
 C\# プログラムでは、エントリ ポイントは 1 つだけに限られます。  `Main` メソッドのあるクラスが複数ある場合、どの `Main` メソッドをエントリ ポイントとして使用するか指定するために、**\/main** コンパイラ オプションを使用してプログラムをコンパイルする必要があります。  詳細については、「[\/main \(Specify Location of Main Method\)](../../../csharp/language-reference/compiler-options/main-compiler-option.md)」を参照してください。  
  
 [!code-cs[csProgGuideMain#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-and-command-line-arguments_1.cs)]  
  
## 概要  
  
-   `Main` メソッドは .exe プログラムのエントリ ポイントで、プログラムの制御を開始および終了する場所です。  
  
-   `Main` はクラス内または構造体内で宣言します。  `Main` は [静的](../../../csharp/language-reference/keywords/static.md) にする必要があり、に [パブリック](../../../csharp/language-reference/keywords/public.md)はずではありません。  \(前の例では、既定アクセスである [private](../../../csharp/language-reference/keywords/private.md) を受け取ります\)。外側のクラスまたは構造体を static にする必要はありません。  
  
-   `Main` の戻り値の型は、`void` と `int` のいずれかを使用できます。  
  
-   `Main` メソッドは、コマンド ライン引数を格納する `string[]` パラメーターを指定して宣言、または指定しないで宣言できます。  [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] を使用して Windows フォーム アプリケーションを作成する場合、パラメーターを手動で追加、または <xref:System.Environment> クラスを使用してコマンド ライン引数を取得できます。  パラメーターは、インデックス付きのコマンド ライン引数として読み取られます。C、および C\+\+ とは異なり、プログラムの名前は、最初のコマンド ライン引数として扱われません。  
  
## このセクションの内容  
  
-   [コマンド ライン引数](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)  
  
-   [方法: コマンド ライン引数を表示する](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
  
-   [方法: foreach を使用してコマンド ライン引数にアクセスする](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
  
-   [Main\(\) の戻り値](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [Command\-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [インサイド C\# プログラム](../../../csharp/programming-guide/inside-a-program/index.md)   
 [\<paveover\>C\# Sample Applications](http://msdn.microsoft.com/ja-jp/9a9d7aaa-51d3-4224-b564-95409b0f3e15)
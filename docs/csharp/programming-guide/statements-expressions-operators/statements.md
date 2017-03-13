---
title: "ステートメント (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 言語, ステートメント"
  - "ステートメント [C#], ステートメントの概要"
ms.assetid: 901bcde7-87de-4e15-833c-f9cfd40c8ce3
caps.latest.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 28
---
# ステートメント (C# プログラミング ガイド)
プログラムが実行する処理は、ステートメントとして表されます。  一般的な処理には、変数の宣言、値の代入、メソッドの呼び出し、コレクションに対するループ処理、条件に応じたコード ブロックへの分岐などがあります。  プログラム内でステートメントが実行される順序は、制御フローまたは実行フローと呼ばれます。  制御フローは、実行時に渡された入力に対するプログラムの応答に応じて、プログラムを実行するたびに変わる可能性があります。  
  
 ステートメントは、セミコロンで終わる単一行のコードか、1 つのブロックを形成する一連の単一行ステートメントで構成されます。  ステートメント ブロックは中かっこ {} で囲み、入れ子になったブロックを含めることができます。  次のコードは、2 つの単一行ステートメントの例と、1 つの複数行ステートメント ブロックを示しています。  
  
 [!code-cs[csProgGuideStatements#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_1.cs)]  
  
## ステートメントの種類  
 次の表は、C\# のさまざまな種類のステートメントと、それぞれに関連付けられているキーワードの一覧です。詳細が記載されているトピックへのリンクも示しています。  
  
|カテゴリ|C\# のキーワード\/メモ|  
|----------|--------------------|  
|宣言ステートメント|宣言ステートメントは、新しい変数または定数を定義します。  変数宣言では、必要に応じて変数に値を代入することもできます。  定数宣言では、常に代入が必要です。<br /><br /> [!code-cs[csProgGuideStatements#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_2.cs)]|  
|式ステートメント|値を計算する式ステートメントでは、値を変数に格納する必要があります。<br /><br /> [!code-cs[csProgGuideStatements#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_3.cs)]|  
|[選択ステートメント](../../../csharp/language-reference/keywords/selection-statements.md)|選択ステートメントを使用すると、指定した 1 つ以上の条件に基づいて、異なるコード セクションに分岐できます。  詳細については、次のトピックを参照してください。<br /><br /> [if](../../../csharp/language-reference/keywords/if-else.md)、[else](../../../csharp/language-reference/keywords/if-else.md)、[switch](../../../csharp/language-reference/keywords/switch.md)、[case](../../../csharp/language-reference/keywords/switch.md)|  
|[繰り返しステートメント](../../../csharp/language-reference/keywords/iteration-statements.md)|繰り返しステートメントを使用すると、配列などのコレクションをループ処理したり、指定した条件が満たされるまで同じステートメントのセットを繰り返し実行したりできます。  詳細については、次のトピックを参照してください。<br /><br /> [do](../../../csharp/language-reference/keywords/do.md)、[for](../../../csharp/language-reference/keywords/for.md)、[foreach](../../../csharp/language-reference/keywords/foreach-in.md)、[in](../../../csharp/language-reference/keywords/foreach-in.md)、[while](../../../csharp/language-reference/keywords/while.md)|  
|[ジャンプ ステートメント](../../../csharp/language-reference/keywords/jump-statements.md)|ジャンプ ステートメントは、別のコード セクションに制御を移します。  詳細については、次のトピックを参照してください。<br /><br /> [break](../../../csharp/language-reference/keywords/break.md)、[continue](../../../csharp/language-reference/keywords/continue.md)、[default](../../../csharp/language-reference/keywords/switch.md)、[goto](../../../csharp/language-reference/keywords/goto.md)、[return](../../../csharp/language-reference/keywords/return.md)、[yield \(C\# リファレンス\)](../../../csharp/language-reference/keywords/yield.md)|  
|[例外処理ステートメント](../../../csharp/language-reference/keywords/exception-handling-statements.md)|例外処理ステートメントを使用すると、実行時に発生する例外状態から適切に回復できます。  詳細については、次のトピックを参照してください。<br /><br /> [throw](../../../csharp/language-reference/keywords/throw.md)、[try\-catch](../../../csharp/language-reference/keywords/try-catch.md)、[try\-finally](../../../csharp/language-reference/keywords/try-finally.md)、[try\-catch\-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)|  
|[Checked と Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)|checked ステートメントと unchecked ステートメントを使用すると、結果の値を保持するには小さすぎる変数に結果が格納される場合に、数値演算でオーバーフローが発生するのを許可するかどうかを指定できます。  詳細については、「[checked](../../../csharp/language-reference/keywords/checked.md)」および「[unchecked](../../../csharp/language-reference/keywords/unchecked.md)」を参照してください。|  
|`await` ステートメント|[async](../../../csharp/language-reference/keywords/async.md) 修飾子のメソッドにマークを付ける場合、メソッドで [&#91;await&#93;](../../../csharp/language-reference/keywords/await.md) の演算子を使用できます。  コントロールが非同期のメソッドの `await` の式に到達すると、コントロールは呼び出し元に戻り、予期されるタスクが完了するまでメソッドの進行状況は中断されます。  タスクが完了すると、実行には、メソッドで再開できます。<br /><br /> 簡単な例については、[メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)のメソッド「Async」を参照してください。  詳細については、「[Async および Await を使用した非同期プログラミング](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。|  
|`yield return` ステートメント|反復子は、リストや配列などのコレクションに対するカスタムのイテレーションを実行します。  反復子は、要素を一つずつ返すために [yieldを返します。](../../../csharp/language-reference/keywords/yield.md) のステートメントを使用します。  `yield return` のステートメントに到達すると、コードの現在の位置が保持されます。  実装は、その場所から反復子は、次に呼び出されると再起動されます。<br /><br /> 詳細については、「[反復子](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。|  
|`fixed` ステートメント|fixed ステートメントは、移動可能な変数がガベージ コレクターにより再配置されることを防ぎます。  詳細については、「[fixed](../../../csharp/language-reference/keywords/fixed-statement.md)」を参照してください。|  
|`lock` ステートメント|lock ステートメントを使用すると、一度に 1 つのスレッドしかコード ブロックにアクセスしないように制限できます。  詳細については、「[lock](../../../csharp/language-reference/keywords/lock-statement.md)」を参照してください。|  
|ラベル付きステートメント|ステートメントにラベルを付与し、[goto](../../../csharp/language-reference/keywords/goto.md) キーワードを使用して、そのラベル付きステートメントにジャンプできます。  次の行の例を参照してください。|  
|空のステートメント|空のステートメントは、単一のセミコロンから成ります。  このステートメントは何も実行しませんが、ステートメントが必要な場所で、どのような処理も実行する必要がない場合に使用できます。  空のステートメントの 2 つの使用例を次に示します。<br /><br /> [!code-cs[csProgGuideStatements#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_4.cs)]|  
  
## 埋め込みステートメント  
 [do](../../../csharp/language-reference/keywords/do.md)、[while](../../../csharp/language-reference/keywords/while.md)、[for](../../../csharp/language-reference/keywords/for.md)、[foreach](../../../csharp/language-reference/keywords/foreach-in.md) などの一部のステートメントでは、その後に必ず埋め込みステートメントが続きます。  埋め込みステートメントは、単一のステートメントか、または複数のステートメントを中かっこ {} で囲んだステートメント ブロックです。  単一行の埋め込みステートメントでも、次の例に示すように中かっこ {} で囲むことができます。  
  
 [!code-cs[csProgGuideStatements#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_5.cs)]  
  
 中かっこ {} で囲まれていない埋め込みステートメントは、宣言ステートメントやラベル付きステートメントにはできません。  これを次の例に示します。  
  
 [!code-cs[csProgGuideStatements#27](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_6.cs)]  
  
 エラーを修正するには、埋め込みステートメントをブロックに格納します。  
  
 [!code-cs[csProgGuideStatements#28](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_7.cs)]  
  
## 入れ子になったステートメント ブロック  
 次のコードに示すように、ステートメント ブロックは入れ子にすることができます。  
  
 [!code-cs[csProgGuideStatements#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_8.cs)]  
  
## 到達できないステートメント  
 コンパイラは、どのような状況でも特定のステートメントに制御フローが到達できないことを検出すると、警告 CS0162 を生成します。  
  
 [!code-cs[csProgGuideStatements#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_9.cs)]  
  
## 関連項目  
  
-   [ステートメントのキーワード](../../../csharp/language-reference/keywords/statement-keywords.md)  
  
-   [式](../../../csharp/programming-guide/statements-expressions-operators/expressions.md)  
  
-   [演算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)
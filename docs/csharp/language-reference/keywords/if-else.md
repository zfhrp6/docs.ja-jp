---
title: "if-else (C# リファレンス) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "if_CSharpKeyword"
  - "else"
  - "else_CSharpKeyword"
  - "if"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "else キーワード [C#]"
  - "if キーワード [C#]"
ms.assetid: d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2
caps.latest.revision: 32
caps.handback.revision: 32
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# if-else (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`if` ステートメントは、`Boolean` 式の値に基づいて実行するステートメントを決定します。 次の例では、`Boolean` 変数 `result` を `true` に設定してから、`if` ステートメントにチェックインします。 出力は `The condition is true` になります。  
  
 [!code-cs[csrefKeywordsSelection#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_1.cs)]  
  
 このトピックの例を実行するには、コンソール アプリケーションの `Main` メソッドに例を挿入します。  
  
 C\# の `if` ステートメントは、次の例に示すように 2 つの形式を取ります。  
  
```c#  
  
// if-else statement if (condition) { then-statement; } else { else-statement; } // Next statement in the program. // if statement without an else if (condition) { then-statement; } // Next statement in the program.  
```  
  
 `if-else` ステートメントで、`condition` が true に評価されると、`then-statement` が実行されます。`condition` が false の場合は、`else-statement` が実行されます。`condition` が同時に true と false に評価されることはないため、`if-else` ステートメントの `then-statement` と `else-statement` の両方が実行されることは決してありません。`then-statement` または `else-statement` が実行された後、制御は `if` ステートメントの後のステートメントに移ります。  
  
 `else` ステートメントが含まれない `if` ステートメントで `condition` が true に評価された場合は、`then-statement` が実行されます。`condition` が false の場合、制御は `if` ステートメントの後のステートメントに移ります。  
  
 `then-statement` と `else-statement` はどちらも、中かっこ \(`{}`\) で囲まれた 1 つのステートメントまたは複数のステートメントで構成できます。 ステートメントが 1 つの場合、中かっこは省略可能ですが、使用することが推奨されます。  
  
 `then-statement` および `else-statement` では、任意の種類のステートメントを使用できます。元の `if` ステートメント内に別の `if` ステートメントを入れ子にすることもできます。 入れ子になった `if` ステートメントでは、各 `else` 句が、対応する `else` がない最後の `if` に属します。 次の例では、`m > 10` と `n > 20` の両方が true に評価されると、`Result1` が表示されます。`m > 10` が true で `n > 20` が false の場合は、`Result2` が表示されます。  
  
 [!code-cs[csrefKeywordsSelection#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_2.cs)]  
  
 代わりに `(m > 10)` が false の場合に `Result2` を表示させるには、次の例に示すように、中かっこを使用して入れ子になった `if` の開始と終了を設定することで、その関連付けを指定します。  
  
 [!code-cs[csrefKeywordsSelection#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_3.cs)]  
  
 条件 `(m > 10)` が false に評価されると、`Result2` が表示されます。  
  
## 使用例  
 次の例では、キーボードから文字を入力すると、プログラムが、入れ子になった `if` ステートメントを実行して、入力された文字が英字かどうかを判別します。 入力された文字が英字である場合、プログラムはその文字が小文字と大文字のどちらであるかを判別します。 いずれの場合も、メッセージが表示されます。  
  
 [!code-cs[csrefKeywordsSelection#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_4.cs)]  
  
## 使用例  
 以下の部分的なコードに示すように、`if` ステートメントを else ブロック内に入れ子にすることもできます。 この例では、2 つの else ブロックと 1 つの then ブロックの中で `if` ステートメントを入れ子にしています。 コメントに、各ブロックでどの条件が true または false であるかを示しています。  
  
 [!code-cs[csrefKeywordsSelection#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_5.cs)]  
  
## 使用例  
 この例では、入力された文字が小文字、大文字、または数値のいずれであるかを判別します。 3 つすべての条件が false の場合、文字は英数字ではありません。 この例では、いずれの場合もメッセージが表示されます。  
  
 [!code-cs[csrefKeywordsSelection#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_6.cs)]  
  
 else ブロックまたは then ブロック内のステートメントを任意の有効なステートメントにできるように、条件には任意の有効なブール式を使用できます。[&&](../../../csharp/language-reference/operators/conditional-and-operator.md)、[&](../../../visual-basic/language-reference/operators/and-operator.md)、[&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md)、[&#124;](../../../csharp/language-reference/operators/or-operator.md)、[\!](../../../csharp/language-reference/operators/logical-negation-operator.md) などの論理演算子を使用して複合条件を作成できます。 次のコードに例を示します。  
  
```c#  
// NOT bool result = true; if (!result) { Console.WriteLine("The condition is true (result is false)."); } else { Console.WriteLine("The condition is false (result is true)."); } // Short-circuit AND int m = 9; int n = 7; int p = 5; if (m >= n && m >= p) { Console.WriteLine("Nothing is larger than m."); } // AND and NOT if (m >= n && !(p > m)) { Console.WriteLine("Nothing is larger than m."); } // Short-circuit OR if (m > n || m > p) { Console.WriteLine("m isn't the smallest."); } // NOT and OR m = 4; if (!(m >= n || m >= p)) { Console.WriteLine("Now m is the smallest."); } // Output: // The condition is false (result is true). // Nothing is larger than m. // Nothing is larger than m. // m isn't the smallest. // Now m is the smallest.  
```  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [?: 演算子](../../../csharp/language-reference/operators/conditional-operator.md)   
 [if\-else ステートメント \(C\+\+\)](/visual-cpp/cpp/if-else-statement-cpp)   
 [switch](../../../csharp/language-reference/keywords/switch.md)
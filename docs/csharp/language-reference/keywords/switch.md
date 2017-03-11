---
title: "switch (C# リファレンス) | Microsoft Docs"
ms.date: "2017-03-07"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "switch_CSharpKeyword"
  - "switch"
  - "case"
  - "case_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "switch ステートメント [C#]"
  - "switch キーワード [C#]"
  - "case ステートメント [C#]"
  - "default キーワード [C#]"
ms.assetid: 44bae8b8-8841-4d85-826b-8a94277daecb
caps.latest.revision: 47
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 47
---
# switch (C# リファレンス)
`switch` ステートメントは、候補のリストから実行する *switch セクション*を選択するための制御ステートメントです。  
  
 `switch` ステートメントには、1 つ以上の switch セクションが含まれています。  各 switch セクションには、1 つ以上の *case ラベル*と、そのあとに続く 1 つ以上のステートメントのリストが含まれています。  次の例に、3 つの switch セクションを持つ簡単な `switch` ステートメントを示します。  各 switch セクションには、`case 1` のような case ラベルと、2 つのステートメントが含まれます。  
  
 [!code-cs[csrefKeywordsSelection#7](../../../csharp/language-reference/keywords/codesnippet/csharp/switch_1.cs)]  
  
## 解説  
 各 case ラベルでは、定数値を指定します。  switch ステートメントは、*switch 式*の値に一致する case ラベルを持つ switch セクション \(この例では `caseSwitch`\) に制御を移動します。  一致する値が case ラベルにない場合、制御は `default` セクションに移動します \(default セクションがある場合\)。  `default` セクションがない場合は、何の処理も行われないまま、制御は `switch` ステートメントの外部に移動します。  前の例では、`case 1` が `caseSwitch` の値に一致するため、ステートメント内の最初の switch セクションが実行されます。  
  
 `switch` ステートメントには、任意の数の switch セクションを含めることができ、また \(文字型の case ラベルも使用している以下の例に示すように\) 各セクションに 1 つ以上の case ラベルを含めることができます。  ただし、複数の case ラベルで同じ定数値を使用することはできません。  
  
 選択された switch セクションにおけるステートメント リストの実行は、ステートメント リストに沿って最初のステートメントから順に開始され、通常は、`break`、`goto case`、`return`、`throw` などのジャンプ ステートメントに達するまで続きます。  この時点で、制御は `switch` ステートメントの外側、または他の case ラベルに移動します。  
  
 C\+\+ とは異なり、C\# では 1 つの switch セクションから次のセクションへ実行が連続することが許可されません。  次のコードでは、エラーが発生します。  
  
```c#  
switch (caseSwitch)  
{  
    // The following switch section causes an error.  
    case 1:  
        Console.WriteLine("Case 1...");  
        // Add a break or other jump statement here.  
    case 2:  
        Console.WriteLine("... and/or Case 2");  
        break;  
}  
```  
  
 最終セクションも含め、各 switch セクションの末尾には到達不可能であることが C\# の要件です。つまり、他のいくつかの言語とは異なり、コードが次の switch セクションにフォール スルーすることはできません。通常この要件は、`break` ステートメントを使用することによって満たされますが、ステートメント リストの末尾に到達不可能であるため、次のコードも有効になります。  
  
```c#  
case 4:  
    while (true)  
        Console.WriteLine("Endless looping. . . .");  
```  
  
## 使用例  
 次の例は、`switch` ステートメントの要件と機能について示しています。  
  
 [!code-cs[csrefKeywordsSelection#9](../../../csharp/language-reference/keywords/codesnippet/csharp/switch_2.cs)]  
  
## 使用例  
 最後の例では、文字列変数 `str`と文字列の case ラベルを使用して、実行の流れを制御します。  
  
 [!code-cs[csrefKeywordsSelection#8](../../../csharp/language-reference/keywords/codesnippet/csharp/switch_3.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [switch ステートメント \(C\+\+\)](/visual-cpp/cpp/switch-statement-cpp)   
 [if\-else](../../../csharp/language-reference/keywords/if-else.md)
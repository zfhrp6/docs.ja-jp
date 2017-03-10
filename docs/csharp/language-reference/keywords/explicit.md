---
title: "explicit (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "explicit_CSharpKeyword"
  - "explicit"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "explicit キーワード [C#]"
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# explicit (C# リファレンス)
`explicit` キーワードは、キャストを使って呼び出す必要があるユーザー定義型の変換演算子を宣言します。  たとえば、この演算子は Fahrenheit というクラスを Celsius というクラスに変換します。  
  
 [!code-cs[csrefKeywordsConversion#2](../../../csharp/language-reference/keywords/codesnippet/csharp/explicit_1.cs)]  
  
 この変換演算子は次のように呼び出すことができます。  
  
 [!code-cs[csrefKeywordsConversion#3](../../../csharp/language-reference/keywords/codesnippet/csharp/explicit_2.cs)]  
  
 変換演算子は、変換元の型を変換先の型に変換します。  変換元の型が変換演算子を提供します。  暗黙の型変換の場合とは異なり、明示的な型変換演算子はキャストを使って呼び出す必要があります。  変換の演算によって例外が発生したり情報が失われたりする可能性がある場合、その変換には `explicit` キーワードを使用する必要があります。  これにより、予想外の結果を招く可能性がある変換演算がコンパイラによって暗黙的に呼び出されることがなくなります。  
  
 キャストを省略すると、コンパイル時のエラー CS0266 の原因になります。  
  
 詳細については、「[変換演算子の使用](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)」を参照してください。  
  
## 使用例  
 次の例に示す `Fahrenheit` と `Celsius` の各クラスは、他方のクラスへの変換を行うための明示的な変換演算子を提供します。  
  
 [!code-cs[csrefKeywordsConversion#1](../../../csharp/language-reference/keywords/codesnippet/csharp/explicit_3.cs)]  
  
## 使用例  
 1 桁の 10 進値を表す構造体 `Digit` を定義する例を次に示します。  `byte` 型から `Digit` 型へ変換するための演算子が定義されていますが、すべての `byte` 型を `Digit` 型に変換できるとは限らないため、この変換は明示的に行うように指定されています。  
  
 [!code-cs[csrefKeywordsConversion#4](../../../csharp/language-reference/keywords/codesnippet/csharp/explicit_4.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [implicit](../../../csharp/language-reference/keywords/implicit.md)   
 [operator](../../../csharp/language-reference/keywords/operator.md)   
 [方法 : 構造体間にユーザー定義の変換を実装する](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)   
 [、Cのチェーン ユーザー定義の変換](http://go.microsoft.com/fwlink/?LinkId=112384)
---
title: "out (C# リファレンス) | Microsoft Docs"
ms.date: "2017-03-01"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "out_CSharpKeyword"
  - "out"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "out [C#]"
  - "out キーワード [C#]"
ms.assetid: 7e911a0c-3f98-4536-87be-d539b7536ca8
caps.latest.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 30
---
# out (C# リファレンス)
`out` コンテキスト キーワードは、[パラメーター修飾子](../../../csharp/language-reference/keywords/out-parameter-modifier.md)として使用するか、またはインターフェイスとデリゲートの[ジェネリック型パラメーターの宣言](../../../csharp/language-reference/keywords/out-generic-modifier.md)で使用するという 2 つのコンテキスト \(それぞれは詳細な情報へのリンク\) で使用できます。  このトピックでは、パラメーター修飾子について説明しますが、ジェネリック型パラメーターの宣言の詳細については、[こちらのトピック](../../../csharp/language-reference/keywords/out-generic-modifier.md)を参照してください。  
  
 `out` キーワードによって、参照により引数が渡されます。  これは、[ref](../../../csharp/language-reference/keywords/ref.md) キーワードと同様ですが、`ref` は渡す前に、変数を初期化する必要があります。  `out` パラメーターを使用するには、メソッド定義と呼び出し元のメソッドの両方で `out` キーワードを明示的に使用する必要があります。  次に例を示します。  
  
 [!code-cs[csrefKeywordsMethodParams#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/out_1.cs)]  
  
 `out` 引数として渡された変数を渡す前に初期化する必要はありませんが、呼び出されたメソッドには、メソッドが返す前に値を割り当てる必要があります。  
  
 `ref` キーワードと `out` キーワードは実行時の動作が異なりますが、コンパイル時に、メソッド シグネチャの一部とは見なされません。  したがって、唯一の違いが、1 つのメソッドは `ref` 引数を使用し、もう一方のメソッドは `out` 引数を使用することである場合、メソッドはオーバーロードできません。  たとえば、次のコードはコンパイルされません。  
  
 [!code-cs[csrefKeywordsMethodParams#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/out_2.cs)]  
  
 ただし、次のように 1 つのメソッドが `ref` 引数または `out` 引数を使用し、他のメソッドがいずれも使用しない場合はオーバーロードを実行できます。  
  
 [!code-cs[csrefKeywordsMethodParams#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/out_3.cs)]  
  
 プロパティは変数ではないため、`out` パラメーターとして渡すことはできません。  
  
 配列の引き渡しについては、「[ref と out を使用した配列の引き渡し](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)」を参照してください。  
  
 次の種類のメソッドには、`ref` キーワードと `out` キーワードを使用することはできません。  
  
-   [async](../../../csharp/language-reference/keywords/async.md) 修飾子を使用して定義した Async メソッド  
  
-   [yield return](../../../csharp/language-reference/keywords/yield.md) または `yield break` ステートメントを含む Iterator メソッド  
  
## 使用例  
 `out` メソッドの宣言は、複数の値を返すメソッドが必要な場合に便利です。  次の例では `out` を使用して、1 つのメソッド呼び出しで 3 つの変数を返します。  3 番目の引数が null に割り当てられることに注意してください。  これにより、必要に応じてメソッドが値を返すことができます。  
  
 [!code-cs[csrefKeywordsMethodParams#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/out_4.cs)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)
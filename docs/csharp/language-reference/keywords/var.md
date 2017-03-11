---
title: "var (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "var"
  - "var_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "var キーワード [C#]"
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
caps.latest.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 13
---
# var (C# リファレンス)
Visual C\# 3.0 以降では、メソッドのスコープで宣言される変数が、`var` という暗黙の型を持つことができます。  暗黙的に型指定されたローカル変数は、型を宣言した場合と同様に厳密に型指定されますが、コンパイラが型を決定します。  次に示す 2 つの `i` の宣言は、機能的に同じです。  
  
```  
var i = 10; // implicitly typed  
int i = 10; //explicitly typed  
```  
  
 詳細については、「[暗黙的に型指定されるローカル変数](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)」および「[Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)」を参照してください。  
  
## 使用例  
 次の例では、2 つのクエリ式を示します。  最初の式では、クエリ結果の型が `IEnumerable<string>` として明示的に宣言できるため、`var` は使用できますが、使用する必要はありません。  しかし、2 番目の例では、結果が匿名型のコレクションで、型名にアクセスできるのがコンパイラだけであるため、`var` を使用する必要があります。  例 2 では、`foreach` の反復変数である `item` も、暗黙的に型指定する必要があります。  
  
 [!code-cs[csrefKeywordsTypes#18](../../../csharp/language-reference/keywords/codesnippet/csharp/var_1.cs)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [暗黙的に型指定されるローカル変数](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
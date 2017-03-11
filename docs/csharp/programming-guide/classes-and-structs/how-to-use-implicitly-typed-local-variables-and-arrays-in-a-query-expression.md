---
title: "方法 : クエリ式で暗黙的に型指定されるローカル変数および配列を使用する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "暗黙的に型指定されるローカル変数 [C#], 使い方"
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# 方法 : クエリ式で暗黙的に型指定されるローカル変数および配列を使用する (C# プログラミング ガイド)
コンパイラによってローカル変数の型が決定されるようにする場合は、暗黙的に型指定されたローカル変数を使用できます。  クエリ式でよく使用する匿名型を格納するには、暗黙的に型指定されたローカル変数を使用する必要があります。  以下の例では、クエリで暗黙的に型指定されたローカル変数を省略できる場合と、使用しなければならない場合の両方を示します。  
  
 暗黙的に型指定されたローカル変数は、[var](../../../csharp/language-reference/keywords/var.md) コンテキスト キーワードを使用して宣言します。  詳細については、「[暗黙的に型指定されるローカル変数](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)」および「[暗黙的に型指定される配列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)」を参照してください。  
  
## 使用例  
 次の例は、`var` キーワードが必須である一般的なシナリオ \(匿名型のシーケンスを生成するクエリ式\) を示しています。  このシナリオでは、匿名型の型名にアクセスできないため、`var` を使用して `foreach` ステートメントのクエリ変数と反復変数を暗黙的に型指定する必要があります。  匿名型の詳細については、「[匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)」を参照してください。  
  
 [!code-cs[csProgGuideLINQ#32](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csRef30LangFeatures_2.cs#32)]  
  
## 使用例  
 次の例では、同様の状況で `var` キーワードを使用しています。ただし、この場合、`var` は省略可能です。  `student.LastName` は文字列であるため、クエリを実行すると文字列のシーケンスが返されます。  したがって、`queryID` の型は、`var` ではなく `System.Collections.Generic.IEnumerable<string>` として宣言できます。  `var` キーワードは利便性のために使用されます。  この例では、`foreach` ステートメントの反復変数は文字列として明示的に型指定されていますが、代わりに `var` を使用して宣言することもできます。  反復変数の型は匿名型ではないため、`var` の使用は省略可能であり、必須ではありません。  `var` 自体は型ではなく、型を推論して割り当てるようコンパイラに指示する命令です。  
  
 [!code-cs[csProgGuideLINQ#33](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csRef30LangFeatures_2.cs#33)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [拡張メソッド](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)   
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [var](../../../csharp/language-reference/keywords/var.md)   
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)
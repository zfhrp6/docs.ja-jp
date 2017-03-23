---
title: "暗黙的に型指定されるローカル変数 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "暗黙的に型指定されるローカル変数 [C#]"
  - "var [C#]"
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
caps.latest.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 23
---
# 暗黙的に型指定されるローカル変数 (C# プログラミング ガイド)
ローカル変数には、明示的な型ではなく、推論される "型" `var` を設定できます。  `var` キーワードは、初期化ステートメントの右側の式から変数の型を推測することをコンパイラに指示します。  推論される型は、組み込み型、匿名型、ユーザー定義型、または .NET Framework クラス ライブラリで定義されている型です。  配列を `var` で初期化する方法の詳細については、「[暗黙的に型指定される配列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)」を参照してください。  
  
 `var` を使用してローカル変数を宣言するさまざまな方法を次の例に示します。  
  
 [!code-cs[csProgGuideLINQ#43](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_1.cs)]  
  
 `var` キーワードは "バリアント型" を意味するものではなく、変数の柔軟な型指定や遅延バインディングを示すものでもない点を理解しておくことが重要です。  このキーワードは、最適な型をコンパイラが決定し割り当てることを意味するだけです。  
  
 キーワード `var` は、次のような状況で使用します。  
  
-   前の例に示したようなローカル変数 \(メソッド スコープで宣言された変数\) に対する設定。  
  
-   初期化ステートメント [for](../../../csharp/language-reference/keywords/for.md) 内。  
  
    ```  
    for(var x = 1; x < 10; x++)  
    ```  
  
-   初期化ステートメント [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 内。  
  
    ```  
    foreach(var item in list){...}  
    ```  
  
-   [using](../../../csharp/language-reference/keywords/using-statement.md) ステートメント内。  
  
    ```  
    using (var file = new StreamReader("C:\\myfile.txt")) {...}  
    ```  
  
 詳細については、「[方法 : クエリ式で暗黙的に型指定されるローカル変数および配列を使用する](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)」を参照してください。  
  
## var と匿名型  
 多くの場合、`var` の使用は任意で、構文上便利なだけです。  ただし、変数が匿名型で初期化される場合、後でオブジェクトのプロパティにアクセスできるようにするには、その変数を `var` として宣言する必要があります。  これは、[!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] クエリ式ではよくあることです。  詳細については、「[匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)」を参照してください。  
  
 ソース コードから見た場合、匿名型には名前がありません。  したがって、クエリ変数を `var` で初期化した場合、返されたオブジェクトのシーケンスのプロパティにアクセスする唯一の方法は、`foreach` ステートメント内の反復変数の型として `var` を使用することです。  
  
 [!code-cs[csProgGuideLINQ#44](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_2.cs)]  
  
## 解説  
 暗黙的に型指定された変数の宣言には、次の制約があります。  
  
-   `var` は、ローカル変数を宣言し、宣言と同じステートメントで初期化する場合にのみ使用できます。この変数を、null 値、メソッド グループ、または匿名関数に初期化することはできません。  
  
-   `var` をクラス スコープのフィールドで使用することはできません。  
  
-   `var` を使用して宣言された変数は、初期化式では使用できません。  つまり、式 `int i = (i = 20);` は有効ですが、`var i = (i = 20);` はコンパイル時にエラーになります。  
  
-   複数の暗黙的に型指定された変数を、同じステートメントで初期化することはできません。  
  
-   スコープ内に `var` という名前の型が存在する場合、`var` キーワードはその型名に解決され、暗黙に型指定されたローカル変数宣言の一部とは見なされません。  
  
 `var` は、クエリ式と使用する場合にも便利なことがあります。クエリ変数の構築された型を厳密に判別することが難しい場合です。  この状況はグループ化および順序付けの操作で生じることがあります。  
  
 `var` キーワードは、変数の特定の型をキーボードで入力するのが面倒な場合、型が明白な場合、または型によってコードが読みやすくならない場合にも有用です。  このような理由で `var` が有用な例としては、グループ化操作で使用されるような入れ子にされたジェネリック型があります。  次のクエリでは、クエリ変数の型は `IEnumerable<IGrouping<string, Student>>` です。  コードの記述者とそのコードを保守する担当者がこのことを理解している限り、簡略にするために暗黙的な型指定を使用しても問題はありません。  
  
 [!code-cs[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicitly-typed-local-variables_3.cs)]  
  
 ただし、`var` を使用すると、少なくとも他の開発者がコードを理解しづらくなる潜在的な可能性があります。  このため、C\# のドキュメントでは通常、必要なときにのみ `var` を使用しています。  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [暗黙的に型指定される配列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)   
 [方法 : クエリ式で暗黙的に型指定されるローカル変数および配列を使用する](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)   
 [匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [オブジェクト初期化子とコレクション初期化子](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)   
 [var](../../../csharp/language-reference/keywords/var.md)   
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [for](../../../csharp/language-reference/keywords/for.md)   
 [foreach、in](../../../csharp/language-reference/keywords/foreach-in.md)   
 [using ステートメント](../../../csharp/language-reference/keywords/using-statement.md)
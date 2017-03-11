---
title: "foreach、in (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "foreach"
  - "foreach_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "foreach キーワード [C#]"
  - "foreach ステートメント [C#]"
  - "in キーワード [C#]"
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
caps.latest.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 29
---
# foreach、in (C# リファレンス)
`foreach` ステートメントは、<xref:System.Collections.IEnumerable?displayProperty=fullName> インターフェイスまたは <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> インターフェイスを実装する配列またはオブジェクト コレクションのそれぞれの要素に対して埋め込みステートメントを繰り返します。  `foreach` ステートメントは、コレクションを繰り返し処理して目的の情報を取得するために使用しますが、予期しない副作用を防ぐため、ソース コレクションに対する項目の追加または削除には使用しないでください。  ソース コレクションに対して項目を追加または削除する必要がある場合は、[for](../../../csharp/language-reference/keywords/for.md) ループを使用します。  
  
 埋め込みステートメントは、配列またはコレクション内の各要素に対して繰り返し実行されます。  コレクション内の全要素に対する繰り返しが完了すると、制御は、`foreach` ブロックに続く次のステートメントに移動します。  
  
 `foreach` ブロック内の任意の位置で、[break](../../../csharp/language-reference/keywords/break.md) キーワードを使用してループから抜けることができます。または、[continue](../../../csharp/language-reference/keywords/continue.md) キーワードを使用して、ループ内の次の反復処理にスキップできます。  
  
 [goto](../../../csharp/language-reference/keywords/goto.md) ステートメント、[return](../../../csharp/language-reference/keywords/return.md) ステートメント、または [throw](../../../csharp/language-reference/keywords/throw.md) ステートメントを使用しても、`foreach` ループを抜けることができます。  
  
 `foreach` キーワードとコード例の詳細については、以下のトピックを参照してください。  
  
 [配列での foreach の使用](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
 [方法 : foreach を使用してコレクション クラスにアクセスする](../../../csharp/programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)  
  
## 使用例  
 次のコードは、3 つの例を示しています。  
  
-   整数の配列の内容を表示する一般的な `foreach` ループ  
  
-   同じ処理を行う [for](../../../csharp/language-reference/keywords/for.md) ループ  
  
-   配列内の要素数のカウントを保持する `foreach` ループ  
  
 [!code-cs[csrefKeywordsIteration#4](../../../csharp/language-reference/keywords/codesnippet/csharp/foreach-in_1.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [繰り返しステートメント](../../../csharp/language-reference/keywords/iteration-statements.md)   
 [for](../../../csharp/language-reference/keywords/for.md)
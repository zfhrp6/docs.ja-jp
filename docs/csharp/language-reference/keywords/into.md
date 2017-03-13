---
title: "into (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "into_CSharpKeyword"
  - "into"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "into キーワード [C#]"
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# into (C# リファレンス)
`into` コンテキスト キーワードを使用すると、[group](../../../csharp/language-reference/keywords/group-clause.md)、[join](../../../csharp/language-reference/keywords/join-clause.md)、または [select](../../../csharp/language-reference/keywords/select-clause.md) 句の結果を新しい識別子に格納するための一時識別子を作成できます。  この識別子自体が、追加のクエリ コマンドのジェネレーターになります。  `group` 句または `select` 句で使用する場合、この新しい識別子の用法は、*継続*と呼ばれることがあります。  
  
## 使用例  
 `into` キーワードを使用して、推論された型 `IGrouping` を持つ一時識別子 `fruitGroup` を使用可能にする方法の例を次に示します。  識別子を使用することにより、各グループに対して <xref:System.Linq.Enumerable.Count%2A> メソッドを呼び出し、2 つ以上の単語を含むグループのみを選択できます。  
  
 [!code-cs[cscsrefQueryKeywords#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/into_1.cs)]  
  
 `into` を `group` 句で使用する必要があるのは、各グループに対して追加のクエリ操作を実行する場合だけです。  詳細については、「[group 句](../../../csharp/language-reference/keywords/group-clause.md)」を参照してください。  
  
 `join` 句での `into` の使用例については、「[join 句](../../../csharp/language-reference/keywords/join-clause.md)」を参照してください。  
  
## 参照  
 [クエリ キーワード \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [group 句](../../../csharp/language-reference/keywords/group-clause.md)
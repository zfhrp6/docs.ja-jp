---
title: "let 句 (C# リファレンス) | Microsoft Docs"
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
  - "let_CSharpKeyword"
  - "let"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "let 句 [C#]"
  - "let キーワード [C#]"
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# let 句 (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

クエリ式で、サブ式の結果を格納して後の句で使用すると便利な場合があります。  `let` キーワードを使用すると、これを行うことができます。このキーワードは、新しい範囲変数を作成し、指定した式の結果でその範囲変数を初期化します。  範囲変数は、いったん値で初期化されると、別の値を格納するために使用できなくなります。  ただし、範囲変数がクエリ可能型を格納している場合、そのクエリ可能型を照会できます。  
  
## 使用例  
 次の例では、`let` が 2 つの方法で使用されています。  
  
1.  照会できる列挙型を作成する。  
  
2.  範囲変数 `word` に対して `ToLower` を一度だけクエリで呼び出すことができるようにする。  `let` を使用しない場合、`where` 句の各述語で `ToLower` を呼び出す必要があります。  
  
 [!CODE [cscsrefQueryKeywords#28](../CodeSnippet/VS_Snippets_VBCSharp/CsCsrefQueryKeywords#28)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [クエリ キーワード \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Getting Started with LINQ in C\#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [方法 : クエリ式の例外を処理する](../Topic/How%20to:%20Handle%20Exceptions%20in%20Query%20Expressions%20\(C%23%20Programming%20Guide\).md)
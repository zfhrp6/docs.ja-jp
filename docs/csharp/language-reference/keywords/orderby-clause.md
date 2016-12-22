---
title: "orderby 句 (C# リファレンス) | Microsoft Docs"
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
  - "orderby"
  - "orderby_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "orderby 句 [C#]"
  - "orderby キーワード [C#]"
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# orderby 句 (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

クエリ式では、`orderby` 句により、返されるシーケンスまたはサブシーケンス \(グループ\) が昇順または降順で並べ替えられます。  1 つ以上の 2 次並べ替え操作を実行するために、複数のキーを指定できます。  並べ替えは、要素の型の既定の比較子によって行われます。  既定の並べ替え順序は昇順です。  カスタム比較子を指定することもできます。  ただし、カスタム比較演算子を使用できるのは、メソッドを基準にした構文を使用する場合のみです。  詳細については、「[Sorting Data](../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)」を参照してください。  
  
## 使用例  
 次の例では、最初のクエリは単語を A から始めてアルファベット順に並べ替え、2 番目のクエリは同じ単語を降順に並べ替えます   \(`ascending` キーワードは既定の並べ替え値であるため、省略できます\)。  
  
 [!CODE [cscsrefQueryKeywords#20](../CodeSnippet/VS_Snippets_VBCSharp/CsCsrefQueryKeywords#20)]  
  
## 使用例  
 学生の姓で 1 番目の並べ替えを実行し、学生の名で 2 番目の並べ替えを実行する例を次に示します。  
  
 [!CODE [cscsrefQueryKeywords#22](../CodeSnippet/VS_Snippets_VBCSharp/CsCsrefQueryKeywords#22)]  
  
## 解説  
 コンパイル時に、`orderby` 句は <xref:System.Linq.Enumerable.OrderBy%2A> メソッドの呼び出しに変換されます。  `orderby` 句の複数のキーは、<xref:System.Linq.Enumerable.ThenBy%2A> メソッド呼び出しに変換されます。  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [クエリ キーワード \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [group 句](../../../csharp/language-reference/keywords/group-clause.md)   
 [Getting Started with LINQ in C\#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
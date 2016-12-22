---
title: "do (C# リファレンス) | Microsoft Docs"
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
  - "do_CSharpKeyword"
  - "do"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "do キーワード [C#]"
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
caps.latest.revision: 22
caps.handback.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# do (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`do` ステートメントでは、指定した式が `false` になるまでステートメントまたはステートメントのブロックが繰り返し実行されます。  ループの本体は、単一のステートメントで構成されている場合を除いて、中かっこ \(`{}`\) で囲まれている必要があります。  単一ステートメントで構成されている場合、中かっこはオプションです。  
  
## 使用例  
 次の例では、変数 `x` が 5 未満である限り、`do-while` ループ ステートメントが実行されます。  
  
 [!code-cs[csrefKeywordsIteration#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/do_1.cs)]  
  
 [while](../../../csharp/language-reference/keywords/while.md) ステートメントとは異なり、`do-while` ループは条件式が評価される前に 1 回は実行されます。  
  
 `do-while` ブロック内の任意の位置で、[break](../../../csharp/language-reference/keywords/break.md) ステートメントを使用してループを抜けることができます。  [continue](../../../csharp/language-reference/keywords/continue.md) ステートメントを使用すると、`while` 式の評価ステートメントに直接ステップできます。  `while` 式の評価が true の場合、ループの最初のステートメントから実行が続行されます。  式の評価が false の場合、`do-while` ループの後の最初のステートメントで実行が続行されます。  
  
 [goto](../../../csharp/language-reference/keywords/goto.md) ステートメント、[return](../../../csharp/language-reference/keywords/return.md) ステートメント、または [throw](../../../csharp/language-reference/keywords/throw.md) ステートメントを使用しても、`do-while` ループを抜けることができます。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [do\-while ステートメント \(C\+\+\)](/visual-cpp/cpp/do-while-statement-cpp)   
 [繰り返しステートメント](../../../csharp/language-reference/keywords/iteration-statements.md)
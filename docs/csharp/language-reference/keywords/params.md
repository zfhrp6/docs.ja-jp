---
title: "params (C# リファレンス) | Microsoft Docs"
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
  - "params_CSharpKeyword"
  - "params"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "パラメーター [C#]、params"
  - "params キーワード [C#]"
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# params (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`params` キーワードを使用すると、可変個の引数を受け取る[メソッド パラメーター](../../../csharp/language-reference/keywords/method-parameters.md)を指定できます。  
  
 パラメーター宣言で指定した型の引数のコンマ区切りのリスト、または指定した型の引数の配列を渡すことができます。  また、引数を渡さないこともできます。  引数を渡さない場合、`params` リストの長さはゼロになります。  
  
 1 つのメソッド宣言内では、`params` キーワード以後にパラメーターを追加できないため、1 つの `params` キーワードだけを使用できます。  
  
## 使用例  
 次の例に示すように、さまざまな方法で `params` パラメーターに引数を渡すことができます。  
  
 [!CODE [csrefKeywordsMethodParams#5](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsMethodParams#5)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [メソッドのパラメーター](../../../csharp/language-reference/keywords/method-parameters.md)
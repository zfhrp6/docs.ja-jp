---
title: "partial (メソッド) (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "partialmethod_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "部分メソッド [C#]"
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
caps.latest.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 26
---
# partial (メソッド) (C# リファレンス)
部分メソッドには、部分型の一部に定義されたシグネチャ、および部分型の別の部分に定義された実装があります。  部分メソッドを使用すると、イベント ハンドラーと同じように、開発者が実装するかどうかを決定できるメソッド フックをクラス デザイナーで提供できます。  開発者が実装を指定しない場合、コンパイラはコンパイル時にシグネチャを削除します。  部分メソッドには次の条件が適用されます。  
  
-   部分型の両方の部分のシグネチャが一致する必要がある。  
  
-   メソッドが void を返す必要がある。  
  
-   アクセス修飾子はできない。  部分メソッドは暗黙的にプライベート メソッドになる。  
  
 部分クラスの 2 つの部分に定義された部分メソッドを次の例に示します。  
  
 [!code-cs[csrefKeywordsContextual#9](../../../csharp/language-reference/keywords/codesnippet/csharp/partial-method_1.cs)]  
  
 詳細については、「[部分クラスと部分メソッド](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)」を参照してください。  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [partial \(型\)](../../../csharp/language-reference/keywords/partial-type.md)
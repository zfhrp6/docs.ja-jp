---
title: "-= 演算子 (C# リファレンス) | Microsoft Docs"
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
  - "-=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-= 演算子 (減算代入) [C#]"
  - "減算代入演算子 (-=) [C#]"
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# -= 演算子 (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

減算代入演算子です。  
  
## 解説  
 次のような `-=` 代入演算子を使用する式があるとします。  
  
```  
x -= y  
```  
  
 上記のコードは、次のコードと同じです。  
  
```  
x = x - y  
```  
  
 ただし、`x` が評価されるのは 1 回だけです。  [\- 演算子](../../../csharp/language-reference/operators/subtraction-operator.md)の意味は、`x` および `y` の型に依存します。たとえば、数値オペランドの場合は減算、デリゲート オペランドの場合はデリゲートの削除になります。  
  
 `-=` 演算子は直接オーバーロードできませんが、[\- 演算子](../../../csharp/language-reference/operators/subtraction-operator.md)はユーザー定義型でオーバーロードできます。詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  
  
 \-\= 演算子は、C\# でイベント サブスクリプションを解除するためにも使用します。  詳細については、「[方法 : イベント サブスクリプションとサブスクリプションの解除](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)」を参照してください。  
  
## 使用例  
 [!CODE [csRefOperators#6](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#6)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)
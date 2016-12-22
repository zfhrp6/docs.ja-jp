---
title: "+= 演算子 (C# リファレンス) | Microsoft Docs"
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
  - "+=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "+= 演算子 [C#]"
  - "加算代入演算子 (+=) [C#]"
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# += 演算子 (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

加算代入演算子です。  
  
## 解説  
 次のような `+=` 代入演算子を使用する式があるとします。  
  
```  
x += y  
```  
  
 上記のコードは、次のコードと同じです。  
  
```  
x = x + y  
```  
  
 ただし、`x` が評価されるのは 1 回だけです。  [\+ 演算子](../../../csharp/language-reference/operators/addition-operator.md)の意味は、`x` および `y` の型に依存します。たとえば、数値オペランドの場合は加算、文字列オペランドの場合は連結になります。  
  
 `+=` 演算子は直接オーバーロードできませんが、[\+ 演算子](../../../csharp/language-reference/operators/addition-operator.md)はユーザー定義型でオーバーロードできます。詳細については、「[operator \(C\# リファレンス\)](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  
  
 加算代入演算子 `+=` を使用して、イベントに対する応答として呼び出されるメソッドを指定できます。これらのメソッドをイベント ハンドラーと呼びます。  このような `+=` 演算子の使用は、*イベントのサブスクライブ*と呼ばれます。  詳細については、「[方法 : イベント サブスクリプションとサブスクリプションの解除](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)」を参照してください。   および [デリゲート](../../../csharp/programming-guide/delegates/index.md) を参照してください。  
  
## 使用例  
 [!CODE [csRefOperators#35](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#35)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)
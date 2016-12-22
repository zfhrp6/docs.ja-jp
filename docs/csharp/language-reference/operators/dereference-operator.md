---
title: "-&gt; 演算子 (C# リファレンス) | Microsoft Docs"
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
  - "->_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-> 演算子 [C#]"
  - "メンバー アクセス演算子 (->) [C#]"
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# -&gt; 演算子 (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`->` 演算子は、ポインターの逆参照とメンバー アクセスを組み合わせます。  
  
## 解説  
 次のような形式の式があるとします。  
  
```  
x->y  
```  
  
 この式は次の式と同じです `x` は `T*` 型のポインター、`y` は `T` のメンバー\)。  
  
```  
(*x).y  
```  
  
 `->` 演算子は、[unsafe](../../../csharp/language-reference/keywords/unsafe.md) とマークされているコードでのみ使用できます。  
  
 `->` 演算子はオーバーロードできません。  
  
## 使用例  
 [!CODE [csRefOperators#15](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#15)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)
---
title: "&lt;&lt;= 演算子 (C# リファレンス) | Microsoft Docs"
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
  - "<<=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<<= 演算子 (左シフト代入) [C#]"
  - "左シフト代入演算子 (<<=) [C#]"
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;&lt;= 演算子 (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

左シフト代入演算子です。  
  
## 解説  
 次のような形式の式があるとします。  
  
```  
x <<= y  
```  
  
 この式は、次のように評価されます。  
  
```  
x = x << y  
```  
  
 ただし、`x` が評価されるのは 1 回だけです。  [\<\< 演算子](../../../csharp/language-reference/operators/left-shift-operator.md)では、`y` で指定されたビット数だけ `x` が左にシフトされます。  
  
 `<<=` 演算子は直接オーバーロードできませんが、[\<\< 演算子](../../../csharp/language-reference/operators/left-shift-operator.md)はユーザー定義型でオーバーロードできます。詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  
  
## 使用例  
 [!CODE [csRefOperators#12](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#12)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)
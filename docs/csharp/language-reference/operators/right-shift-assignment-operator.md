---
title: "&gt;&gt;= 演算子 (C# リファレンス) | Microsoft Docs"
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
  - ">>=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - ">>= 演算子 (右シフト代入) [C#]"
  - "右シフト代入演算子 (>>=) [C#]"
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &gt;&gt;= 演算子 (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

右シフト代入演算子です。  
  
## 解説  
 次のような形式の式があるとします。  
  
```  
x >>= y  
```  
  
 この式は、次のように評価されます。  
  
```  
x = x >> y  
```  
  
 ただし、`x` が評価されるのは 1 回だけです。  [\>\> 演算子](../Topic/%3E%3E%20Operator%20\(C%23%20Reference\).md)では、`y` で指定された分だけ `x` が右にシフトされます。  
  
 \>\>\= 演算子は直接オーバーロードできませんが、[\>\> 演算子](../Topic/%3E%3E%20Operator%20\(C%23%20Reference\).md)はユーザー定義型でオーバーロードできます。詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  
  
## 使用例  
 [!CODE [csRefOperators#11](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#11)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)
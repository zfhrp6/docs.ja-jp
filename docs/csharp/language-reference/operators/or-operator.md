---
title: "| 演算子 (C# リファレンス) | Microsoft Docs"
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
  - "|_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "| 演算子 [C#]"
  - "二項演算子 (|) [C#]"
  - "ビットごとの OR 演算子 [C#]"
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# | 演算子 (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Binary       `|`  演算子は、整数型と `bool` に対してあらかじめ定義されています。  整数型の場合、  `|`ではオペランドのビットごとの OR が計算されます。  `bool` オペランドの場合は、  `|` オペランドの論理 OR が計算されます。つまり、両方のオペランドが `false` の場合だけ結果が `false` になります。  
  
## 解説  
 ユーザー定義型で         `|` 演算子はオーバーロードできます。詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  
  
## 使用例  
 [!CODE [csRefOperators#31](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#31)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)
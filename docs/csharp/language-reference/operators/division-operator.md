---
title: "/ 演算子 (C# リファレンス) | Microsoft Docs"
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
  - "/_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/ 演算子 [C#]"
  - "除算演算子 [C#]"
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# / 演算子 (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

除算演算子 \(`/`\)、最初のオペランドが 2 番目のオペランドで除算します。  すべての数値型には定義済みの除算演算子があります。  
  
## 解説  
 `/` 演算子はユーザー定義型でオーバーロードできます。詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  `/` 演算子をオーバーロードすると、[\/\= 演算子](../../../csharp/language-reference/operators/subtraction-assignment-operator.md)が暗黙的にオーバーロードされます。  
  
 2 つの整数を除算したときの結果は常に整数になります。  7 の結果は、\/2 は 3 です。  7 の残りの部分を決定するのには\/3、剰余演算子を使用 \([%](../../../csharp/language-reference/operators/modulus-operator.md)\)。  商を有理数または小数として得るには、非除数または除数を `float` 型または `double` 型にします。  次の例のように、小数点の右側にある数字を入れて配当金または除数としては、10 進数を表す場合は、暗黙的に型を割り当てることができます。  
  
## 使用例  
 [!CODE [csRefOperators#42](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#42)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)
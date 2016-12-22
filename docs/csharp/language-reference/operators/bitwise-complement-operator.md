---
title: "~ 演算子 (C# リファレンス) | Microsoft Docs"
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
  - "~_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "~ [C#], ビットごとの補数演算子"
  - "~ 演算子 [C#]"
  - "ビットごとの補数演算子 [C#]"
  - "ティルダ (~) 1 の補数演算子 [C#]"
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# ~ 演算子 (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`~` 演算子は、そのオペランドにビットごとの補数演算を実行し、各ビットを反転させます。  ビットごとの補数演算子は、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、および [ulong](../../../csharp/language-reference/keywords/ulong.md) に対して組み込まれています。  
  
> [!NOTE]
>  `~` 記号は、デストラクターの宣言にも使用されます。  詳細については、「[デストラクター](../../../csharp/programming-guide/classes-and-structs/destructors.md)」を参照してください。  
  
## 解説  
 `~`  演算子はユーザー定義型でオーバーロードできます。  詳細については、「[operator \(C\# リファレンス\)](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  通常、整数型に対する演算は、列挙に対して適用されます。  
  
## 使用例  
 [!CODE [csRefOperators#25](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#25)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)   
 [デストラクター](../../../csharp/programming-guide/classes-and-structs/destructors.md)
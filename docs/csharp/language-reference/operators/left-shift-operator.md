---
title: "&lt;&lt; 演算子 (C# リファレンス) | Microsoft Docs"
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
  - "<<_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<< 演算子 [C#]"
  - "左シフト演算子 (<<) [C#]"
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;&lt; 演算子 (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

左シフト演算子 \(`<<`\) では、2 番目のオペランドで指定されたビット数だけ最初のオペランドが左にシフトされます。  2 番目のオペランドの型は [int](../../../csharp/language-reference/keywords/int.md) であるか、`int` への暗黙の数値変換が定義されている型である必要があります。  
  
## 解説  
 1 番目のオペランドが [int](../../../csharp/language-reference/keywords/int.md) または [uint](../../../csharp/language-reference/keywords/uint.md) \(32 ビット値\) の場合、シフト数は 2 番目のオペランドの下位 5 ビットで指定されます。  つまり、実際のシフト数は 0 ～ 31 ビットです。  
  
 1 番目のオペランドが [long](../../../csharp/language-reference/keywords/long.md) または [ulong](../../../csharp/language-reference/keywords/ulong.md) \(64 ビット値\) の場合、シフト数は 2 番目のオペランドの下位 6 ビットで指定されます。  つまり、実際のシフト数は 0 ～ 63 ビットです。  
  
 シフトの結果、1 番目のオペランドの型の範囲内にない上位ビットは破棄され、空になる下位ビットには 0 が入ります。  シフト演算では、オーバーフローは発生しません。  
  
 `<<` 演算子はユーザー定義型でオーバーロードできます。詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。オーバーロードでは、最初のオペランドの型はユーザー定義型、2 番目のオペランドの型は `int` である必要があります。  二項演算子をオーバーロードすると、対応する代入演算子がある場合には、この演算子も暗黙でオーバーロードされます。  
  
## 使用例  
 [!CODE [csRefOperators#14](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#14)]  
  
## コメント  
 1 と 33 では下位 5 ビットが同じであるため、`i<<1` と `i<<33`  の結果は同じになります。  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)
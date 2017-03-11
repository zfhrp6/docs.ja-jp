---
title: "&gt;&gt; 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - ">>_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - ">> 演算子 [C#]"
  - "右シフト演算子 (>>) [C#]"
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# &gt;&gt; 演算子 (C# リファレンス)
右シフト演算子 \(`>>`\) では、2 番目のオペランドで指定されたビット数だけ最初のオペランドが右にシフトされます。  
  
## 解説  
 最初のオペランドが [int](../../../csharp/language-reference/keywords/int.md) または [uint](../../../csharp/language-reference/keywords/uint.md) \(32 ビット値\) の場合、シフト数は 2 番目のオペランドの下位 5 ビット \(2 番目のオペランド & 0x1f\) で指定されます。  
  
 最初のオペランドが [long](../../../csharp/language-reference/keywords/long.md) または [ulong](../../../csharp/language-reference/keywords/ulong.md) \(64 ビット値\) の場合、シフト数は 2 番目のオペランドの下位 6 ビット \(2 番目のオペランド & 0x3f\) で指定されます。  
  
 最初のオペランドが [int](../../../csharp/language-reference/keywords/int.md) または [long](../../../csharp/language-reference/keywords/long.md) の場合、右シフトは算術シフトです。つまり、シフトの結果空になる上位ビットに符号ビットが設定されます。  最初のオペランドが [uint](../../../csharp/language-reference/keywords/uint.md) 型または [ulong](../../../csharp/language-reference/keywords/ulong.md) 型の場合、右シフトは論理シフトです。つまり、上位ビットには 0 が入ります。  
  
 `>>` 演算子はユーザー定義型でオーバーロードできます。オーバーロードでは、最初のオペランドの型はユーザー定義型、2 番目のオペランドの型は [int](../../../csharp/language-reference/keywords/int.md) である必要があります。  詳細については、「[operator \(C\# リファレンス\)](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  二項演算子をオーバーロードすると、対応する代入演算子がある場合には、この演算子も暗黙でオーバーロードされます。  
  
## 使用例  
 [!code-cs[csRefOperators#26](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#26)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)
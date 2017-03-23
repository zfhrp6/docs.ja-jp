---
title: "方法 : ポインター変数の値を取得する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ポインター式 [C#], 間接"
  - "ポインター [C#], * 演算子"
  - "ポインター [C#], 間接"
  - "変数 [C#], ポインター"
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# 方法 : ポインター変数の値を取得する (C# プログラミング ガイド)
ポインターが指している位置にある変数を取得するには、ポインター間接演算子を使用します。  この式は、次の形式になります。 `p` はポインター型を表します。  
  
```  
*p;  
```  
  
 単項間接演算子は、ポインター型以外の型の式では使用できません。  また、[void](../../../csharp/language-reference/keywords/void.md) ポインターに適用することもできません。  
  
 間接演算子を [null](../../../csharp/language-reference/keywords/null.md) ポインターに適用したときの結果は、実装によって異なります。  
  
## 使用例  
 次の例では、異なる型のポインターを使用して `char` 型の変数にアクセスしています。  変数に割り当てられる物理アドレスは一定ではないので、`theChar` のアドレスは、実行するたびに変化することに注意してください。  
  
 [!code-cs[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]  
  
 [!code-cs[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]  
  
  **Value of theChar \= Z**  
**Address of theChar \= 12F718**  
**Value of pChar \= Z**  
**Value of pInt \= 90**   
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ポインター式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [型](../../../csharp/language-reference/keywords/types.md)   
 [安全でない](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
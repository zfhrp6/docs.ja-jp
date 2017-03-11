---
title: "方法: 変数のアドレスを取得する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ポインター式 [C#], address-of 演算子"
  - "ポインター [C#], & 演算子"
  - "変数 [C#], アドレス"
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# 方法: 変数のアドレスを取得する (C# プログラミング ガイド)
固定変数に評価される単項式のアドレスを取得するには、アドレス演算子を使用します。  
  
```  
int number;  
int* p = &number; //address-of operator &  
```  
  
 アドレス演算子は、変数にのみ適用できます。  変数が可変変数である場合は、[固定ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)を使用して、アドレスを取得する前に一時的に変数を固定します。  
  
 変数は、確実に初期化してください。  変数が初期化されていない場合、コンパイラはエラー メッセージを発行しません。  
  
 定数や値のアドレスは取得できません。  
  
## 使用例  
 次の例では、`int` へのポインター `p` を宣言し、整数の変数 `number` のアドレスを代入します。  \*p に代入することによって変数 `number` が初期化されます。  この代入ステートメントをコメントにすると、変数 `number` の初期化が削除されますが、コンパイル時のエラーは発行されません。  [メンバー アクセス](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md)演算子 `->` を使用して、ポインターに格納されているアドレスを取得し、表示することに注意してください。  
  
 [!code-cs[csProgGuidePointers#7](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/csharp/Pointers/Pointers2.cs#7)]  
  
 [!code-cs[csProgGuidePointers#8](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/csharp/Pointers/Pointers.cs#8)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ポインター式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [型](../../../csharp/language-reference/keywords/types.md)   
 [安全でない](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
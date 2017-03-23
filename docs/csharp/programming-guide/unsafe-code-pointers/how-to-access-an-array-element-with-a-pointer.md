---
title: "方法 : ポインターを使用して配列要素にアクセスする (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ポインター [C#], 配列アクセス"
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# 方法 : ポインターを使用して配列要素にアクセスする (C# プログラミング ガイド)
unsafe コンテキストでは、次の例のようにポインター要素アクセスを使用して、メモリ内の要素にアクセスできます。  
  
```  
 char* charPointer = stackalloc char[123];  
for (int i = 65; i < 123; i++)  
{  
    charPointer[i] = (char)i; //access array elements  
}  
```  
  
 角かっこ内の式は、暗黙的に `int`、`uint`、`long`、または `ulong` に変換できる必要があります。  演算 p\[e\] は \*\(p\+e\) と等価です。  C や C\+\+ の場合と同様に、ポインター要素アクセスでは、範囲外のエラーをチェックしません。  
  
## 使用例  
 次の例では、123 のメモリ位置を文字配列 `charPointer` に割り当てます。  この配列を使用して、2 つの [for](../../../csharp/language-reference/keywords/for.md) ループ中の小文字と大文字を表示します。  
  
 式 `charPointer[i]` と式 `*(charPointer + i)` は等価であり、どちらの式を使用しても同じ結果が得られます。  
  
 [!code-cs[csProgGuidePointers#11](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_1.cs)]  
  
 [!code-cs[csProgGuidePointers#12](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_2.cs)]  
  
  **Uppercase letters:**  
**ABCDEFGHIJKLMNOPQRSTUVWXYZ**  
**Lowercase letters:**  
**abcdefghijklmnopqrstuvwxyz**   
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ポインター式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [型](../../../csharp/language-reference/keywords/types.md)   
 [安全でない](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
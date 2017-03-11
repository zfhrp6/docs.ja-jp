---
title: "ref と out を使用した配列の引き渡し (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "配列 [C#], 受け渡し (ref と out を使用)"
ms.assetid: 6a2b261e-a1cc-49a6-b4f0-6cacae385a1e
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# ref と out を使用した配列の引き渡し (C# プログラミング ガイド)
すべての [out](../../../csharp/language-reference/keywords/out.md) パラメーターと同じように、配列型の `out` パラメーターも使用する前に代入される必要があります。つまり、呼び出される側で代入する必要があります。  次に例を示します。  
  
 [!code-cs[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/csharp/passing-arrays-using-ref_1.cs)]  
  
 すべての [ref](../../../csharp/language-reference/keywords/ref.md) パラメーターと同じように、配列型の `ref` パラメーターも、呼び出し側で明示的に代入する必要があります。  したがって、呼び出される側で明示的に代入する必要はありません。  配列型の `ref` パラメーターは、呼び出しの結果として変更される場合があります。  たとえば、配列に [null](../../../csharp/language-reference/keywords/null.md) 値が代入されたり、別の配列で初期化されたりする場合があります。  次に例を示します。  
  
 [!code-cs[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/csharp/passing-arrays-using-ref_2.cs)]  
  
 次の 2 つの例は、メソッドに配列を渡すときに使われる `out` と `ref` の違いを示しています。  
  
## 使用例  
 この例では、配列 `theArray` は呼び出し元 \(`Main` メソッド\) で宣言されて、`FillArray` メソッドで初期化されます。  その後、配列要素は呼び出し元に返されて表示されます。  
  
 [!code-cs[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/csharp/passing-arrays-using-ref_3.cs)]  
  
## 使用例  
 この例では、配列 `theArray` は呼び出し元 \(`Main` メソッド\) で初期化された後、`ref` パラメーターを使って `FillArray` メソッドに渡されます。  一部の配列要素は、`FillArray` メソッドの中で変更されます。  その後、配列要素は呼び出し元に返されて表示されます。  
  
 [!code-cs[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/csharp/passing-arrays-using-ref_4.cs)]  
  
## 参照  
 [ref](../../../csharp/language-reference/keywords/ref.md)   
 [out パラメーター修飾子](../../../csharp/language-reference/keywords/out-parameter-modifier.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [配列](../../../csharp/programming-guide/arrays/index.md)   
 [1 次元配列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)   
 [多次元配列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)   
 [ジャグ配列](../../../csharp/programming-guide/arrays/jagged-arrays.md)
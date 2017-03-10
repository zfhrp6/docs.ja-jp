---
title: "1 次元配列 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "配列 [C#], 1 次元"
  - "1 次元配列 [C#]"
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# 1 次元配列 (C# プログラミング ガイド)
5 個の整数値を含む 1 次元配列は、次の例のように宣言できます。  
  
 [!code-cs[csProgGuideArrays#4](../../../csharp/programming-guide/arrays/codesnippet/csharp/single-dimensional-arrays_1.cs)]  
  
 この配列には、`array[0]` から `array[4]` までの要素が含まれています。  [new](../../../csharp/language-reference/keywords/new.md) 演算子を使って配列を作成すると、配列の要素は、既定値で初期化されます。  この例では、配列要素はすべて 0 に初期化されます。  
  
 文字列を格納する配列も、同様の方法で宣言できます。  次に例を示します。  
  
 [!code-cs[csProgGuideArrays#5](../../../csharp/programming-guide/arrays/codesnippet/csharp/single-dimensional-arrays_2.cs)]  
  
## 配列の初期化  
 宣言時に配列を初期化できます。その場合、ランク指定子は、初期化リスト内の要素数で既に与えられているので必要ありません。  次に例を示します。  
  
 [!code-cs[csProgGuideArrays#6](../../../csharp/programming-guide/arrays/codesnippet/csharp/single-dimensional-arrays_3.cs)]  
  
 文字列配列も、同じ方法で初期化できます。  次に示す文字列配列の宣言では、各配列要素を曜日の名前で初期化しています。  
  
 [!code-cs[csProgGuideArrays#7](../../../csharp/programming-guide/arrays/codesnippet/csharp/single-dimensional-arrays_4.cs)]  
  
 宣言時に配列を初期化するときは、次の短縮形を使用できます。  
  
 [!code-cs[csProgGuideArrays#8](../../../csharp/programming-guide/arrays/codesnippet/csharp/single-dimensional-arrays_5.cs)]  
  
 初期化せずに配列変数を宣言することはできますが、そのような変数に配列を代入するときは、`new` 演算子を使用する必要があります。  次に例を示します。  
  
 [!code-cs[csProgGuideArrays#9](../../../csharp/programming-guide/arrays/codesnippet/csharp/single-dimensional-arrays_6.cs)]  
  
 C\# 3.0 では、暗黙的に型指定される配列が導入されています。  詳細については、「[暗黙的に型指定される配列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)」を参照してください。  
  
## 値型と参照型の配列  
 配列宣言の例を次に示します。  
  
 [!code-cs[csProgGuideArrays#10](../../../csharp/programming-guide/arrays/codesnippet/csharp/single-dimensional-arrays_7.cs)]  
  
 このステートメントの結果は、`SomeType` が値型か参照型かによって異なります。  値型の場合は、各要素が `SomeType` 型である 10 個の要素から成る配列が作成されます。  `SomeType` が参照型の場合は、10 個の要素から成る配列が作成されて、各要素は null 参照で初期化されます。  
  
 値型と参照型の詳細については、「[型](../../../csharp/language-reference/keywords/types.md)」を参照してください。  
  
## 参照  
 <xref:System.Array>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [配列](../../../csharp/programming-guide/arrays/index.md)   
 [多次元配列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)   
 [ジャグ配列](../../../csharp/programming-guide/arrays/jagged-arrays.md)
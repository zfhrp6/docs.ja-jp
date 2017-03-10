---
title: "多次元配列 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "配列 [C#], 多次元"
  - "多次元配列 [C#]"
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# 多次元配列 (C# プログラミング ガイド)
複数の次元で構成される配列を作成できます。  たとえば、次の宣言では、4 つの行と 2 つの列から成る 2 次元配列が作成されます。  
  
 [!code-cs[csProgGuideArrays#11](../../../csharp/programming-guide/arrays/codesnippet/csharp/multidimensional-arrays_1.cs)]  
  
 次の宣言では、大きさが 4、2、3 の 3 つの次元を持つ配列が作成されます。  
  
 [!code-cs[csProgGuideArrays#12](../../../csharp/programming-guide/arrays/codesnippet/csharp/multidimensional-arrays_2.cs)]  
  
## 配列の初期化  
 次の例に示すように、宣言時に配列を初期化できます。  
  
 [!code-cs[csProgGuideArrays#13](../../../csharp/programming-guide/arrays/codesnippet/csharp/multidimensional-arrays_3.cs)]  
  
 ランクを指定せずに配列を初期化することもできます。  
  
 [!code-cs[csProgGuideArrays#14](../../../csharp/programming-guide/arrays/codesnippet/csharp/multidimensional-arrays_4.cs)]  
  
 初期化せずに配列変数を宣言する場合は、`new` 演算子を使用して配列を変数に割り当てます。  `new` を使用する例を次に示します。  
  
 [!code-cs[csProgGuideArrays#15](../../../csharp/programming-guide/arrays/codesnippet/csharp/multidimensional-arrays_5.cs)]  
  
 次の例では、特定の配列要素に値を割り当てます。  
  
 [!code-cs[csProgGuideArrays#16](../../../csharp/programming-guide/arrays/codesnippet/csharp/multidimensional-arrays_6.cs)]  
  
 同様に、次の例では、特定の配列要素の値を取得して、この値を変数 `elementValue` に割り当てます。  
  
 [!code-cs[csProgGuideArrays#42](../../../csharp/programming-guide/arrays/codesnippet/csharp/multidimensional-arrays_7.cs)]  
  
 配列要素を既定値に初期化するコード例を次に示します \(ジャグ配列の場合を除きます\)。  
  
 [!code-cs[csProgGuideArrays#17](../../../csharp/programming-guide/arrays/codesnippet/csharp/multidimensional-arrays_8.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [配列](../../../csharp/programming-guide/arrays/index.md)   
 [1 次元配列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)   
 [ジャグ配列](../../../csharp/programming-guide/arrays/jagged-arrays.md)
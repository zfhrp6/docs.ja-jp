---
title: "ジャグ配列 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "配列 [C#], ジャグ"
  - "ジャグ配列 [C#]"
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# ジャグ配列 (C# プログラミング ガイド)
ジャグ配列とは、その要素も配列である配列です。  ジャグ配列の要素は、次元やサイズが異なっていてもかまいません。  ジャグ配列は、"配列の配列" と呼ばれることもあります。次の例で、ジャグ配列の宣言、初期化、アクセスの各方法について説明します。  
  
 次に示すのは、3 つの要素を持つ 1 次元配列の宣言で、各要素は整数の 1 次元配列です。  
  
 [!code-cs[csProgGuideArrays#19](../../../csharp/programming-guide/arrays/codesnippet/csharp/jagged-arrays_1.cs)]  
  
 `jaggedArray` を使用するには、先に要素を初期化する必要があります。  要素の初期化は、次の方法で行うことができます。  
  
 [!code-cs[csProgGuideArrays#20](../../../csharp/programming-guide/arrays/codesnippet/csharp/jagged-arrays_2.cs)]  
  
 各要素は、整数の 1 次元配列です。  1 番目の要素は 5 個の整数値の配列、2 番目の要素は 4 個の整数値の配列、そして 3 番目の要素は 2 個の整数値の配列です。  
  
 初期化子を使って配列要素に値を格納することもできます。この場合、配列のサイズは必要ありません。  次に例を示します。  
  
 [!code-cs[csProgGuideArrays#21](../../../csharp/programming-guide/arrays/codesnippet/csharp/jagged-arrays_3.cs)]  
  
 次に示すように、宣言時に配列を初期化することもできます。  
  
 [!code-cs[csProgGuideArrays#22](../../../csharp/programming-guide/arrays/codesnippet/csharp/jagged-arrays_4.cs)]  
  
 次の簡単な形式を使用できます。  要素の初期化では `new` 演算子を省略できないことに注意してください。これは、要素に既定の初期化はないためです。  
  
 [!code-cs[csProgGuideArrays#23](../../../csharp/programming-guide/arrays/codesnippet/csharp/jagged-arrays_5.cs)]  
  
 ジャグ配列は配列の配列です。そのため、配列要素は参照型で、`null` に初期化されます。  
  
 各配列要素は、次の例に示す方法で参照できます。  
  
 [!code-cs[csProgGuideArrays#24](../../../csharp/programming-guide/arrays/codesnippet/csharp/jagged-arrays_6.cs)]  
  
 ジャグ配列と多次元配列を併用できます。  次に示すのは、サイズが異なる 3 つの 2 次元配列要素を含む 1 次元のジャグ配列を宣言および初期化する例です。  2 次元配列の詳細については、「[多次元配列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)」を参照してください。  
  
 [!code-cs[csProgGuideArrays#25](../../../csharp/programming-guide/arrays/codesnippet/csharp/jagged-arrays_7.cs)]  
  
 各要素には、次の例に示す方法でアクセスできます。この例では、最初の配列の要素 `[1,0]` の値 \(`5`\) を表示しています。  
  
 [!code-cs[csProgGuideArrays#26](../../../csharp/programming-guide/arrays/codesnippet/csharp/jagged-arrays_8.cs)]  
  
 メソッド `Length` は、ジャグ配列に含まれる配列数を返します。  たとえば、前の配列を宣言した状態で、次の行を指定したとします。  
  
 [!code-cs[csProgGuideArrays#27](../../../csharp/programming-guide/arrays/codesnippet/csharp/jagged-arrays_9.cs)]  
  
 値 3 を返します。  
  
## 使用例  
 次の例では、配列を要素とする配列を作成します。  各配列要素のサイズは同じではありません。  
  
 [!code-cs[csProgGuideArrays#18](../../../csharp/programming-guide/arrays/codesnippet/csharp/jagged-arrays_10.cs)]  
  
## 参照  
 <xref:System.Array>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [配列](../../../csharp/programming-guide/arrays/index.md)   
 [1 次元配列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)   
 [多次元配列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
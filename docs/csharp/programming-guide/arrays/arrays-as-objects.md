---
title: "オブジェクトとしての配列 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "配列 [C#], オブジェクトとしての"
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# オブジェクトとしての配列 (C# プログラミング ガイド)
C\# の配列はオブジェクトそのものであり、C や C\+\+ の場合のように、単なるアドレス指定可能な連続メモリ領域ではありません。  <xref:System.Array> は、すべての配列型の抽象基本型です。  <xref:System.Array> のプロパティとその他のクラス メンバーを使用できます。  この例としては、<xref:System.Array.Length%2A> プロパティを使用して配列の長さを取得する場合などがあります。  `numbers` 配列の長さ `5` を `lengthOfNumbers` という変数に代入するコードは、次のようになります。  
  
 [!code-cs[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/csharp/arrays-as-objects_1.cs)]  
  
 <xref:System.Array> クラスには、配列の並べ替え、検索、コピーを行うための、多くの便利なメソッドやプロパティが他にも用意されています。  
  
## 使用例  
 次の例では、<xref:System.Array.Rank%2A> プロパティを使用して、配列の次元数を表示します。  
  
 [!code-cs[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/csharp/arrays-as-objects_2.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [配列](../../../csharp/programming-guide/arrays/index.md)   
 [1 次元配列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)   
 [多次元配列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)   
 [ジャグ配列](../../../csharp/programming-guide/arrays/jagged-arrays.md)
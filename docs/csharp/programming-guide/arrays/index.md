---
title: "配列 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "配列 [C#]"
  - "C# 言語, 配列"
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
caps.latest.revision: 33
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 33
---
# 配列 (C# プログラミング ガイド)
配列データ構造体には、同じ型の複数の変数を格納できます。  配列は、要素の型を指定することで宣言します。  
  
 `type[] arrayName;`  
  
 次の例では、1 次元配列、多次元配列、およびジャグ配列を作成しています。  
  
 [!code-cs[csProgGuideArrays#1](../../../csharp/programming-guide/arrays/codesnippet/csharp/index_1.cs)]  
  
## 配列の概要  
 配列には、次の特徴があります。  
  
-   配列は、[1 次元配列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)、[多次元配列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)、または[ジャグ配列](../../../csharp/programming-guide/arrays/jagged-arrays.md)のいずれかになります。  
  
-   次元数と各次元の長さは、配列インスタンスの作成時に設定されます。  インスタンスの有効期間中にこれらの値を変更することはできません。  
  
-   数値配列要素の既定値はゼロに設定され、参照要素は null に設定されます。  
  
-   ジャグ配列は配列の配列です。そのため、配列要素は参照型で、`null` に初期化されます。  
  
-   配列には、ゼロから始まるインデックスが付けられます。`n` 個の要素を含む配列には、`0` から `n-1` までのインデックスが付けられます。  
  
-   配列の要素および配列型は、どのような型でもかまいません。  
  
-   配列型は、抽象基本型 <xref:System.Array> から派生した[参照型](../../../csharp/language-reference/keywords/reference-types.md)です。  この型は <xref:System.Collections.IEnumerable> と <xref:System.Collections.Generic.IEnumerable%601> を実装するので、C\# のすべての配列で [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 反復処理を使用できます。  
  
## 関連項目  
  
-   [オブジェクトとしての配列](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
-   [配列での foreach の使用](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
-   [引数としての配列の受け渡し](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
-   [ref と out を使用した配列の引き渡し](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)  
  
-   『[Beginning Visual C\# 2010 \(Visual C\# 2010 の開始\)](http://go.microsoft.com/fwlink/?LinkId=221214)』の「[More About Variables \(変数の詳細\)](http://go.microsoft.com/fwlink/?LinkId=221230)」  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [コレクション](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)   
 [Array Collection Type](http://msdn.microsoft.com/ja-jp/8a9964de-8941-47b1-a3cf-a01bc88db9e8)
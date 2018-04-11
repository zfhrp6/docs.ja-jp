---
title: 配列 (C# プログラミング ガイド)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
caps.latest.revision: 33
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8d395bcb179650fe29ab0918e7f91f3c8b6197b5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="arrays-c-programming-guide"></a>配列 (C# プログラミング ガイド)
配列データ構造体には、同じ型の複数の変数を格納できます。 配列は、要素の型を指定することで宣言します。  
  
 `type[] arrayName;`  
  
 次の例では、1 次元配列、多次元配列、およびジャグ配列を作成しています。  
  
 [!code-csharp[csProgGuideArrays#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/index_1.cs)]  
  
## <a name="array-overview"></a>配列の概要  
 配列には、次の特徴があります。  
  
-   配列は、[1 次元配列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)、[多次元配列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)、または[ジャグ配列](../../../csharp/programming-guide/arrays/jagged-arrays.md)のいずれかになります。  
  
-   次元数と各次元の長さは、配列インスタンスの作成時に設定されます。 インスタンスの有効期間中にこれらの値を変更することはできません。  
  
-   数値配列要素の既定値はゼロに設定され、参照要素は null に設定されます。  
  
-   ジャグ配列は配列の配列です。そのため、配列要素は参照型で、`null` に初期化されます。  
  
-   配列には、ゼロから始まるインデックスが付けられます。`n` 個の要素を含む配列には、`0` から `n-1` までのインデックスが付けられます。  
  
-   配列の要素および配列型は、どのような型でもかまいません。  
  
-   配列型は、抽象基本型 <xref:System.Array> から派生した[参照型](../../../csharp/language-reference/keywords/reference-types.md)です。 この型は <xref:System.Collections.IEnumerable> と <xref:System.Collections.Generic.IEnumerable%601> を実装するので、C# のすべての配列で [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 反復処理を使用できます。  
  
## <a name="related-sections"></a>関連項目  
  
-   [オブジェクトとしての配列](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
-   [配列での foreach の使用](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
-   [引数としての配列の受け渡し](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
-   [ref と out を使用した配列の引き渡し](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)   
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>参照  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [コレクション](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)  
 [Array コレクション型](http://msdn.microsoft.com/library/8a9964de-8941-47b1-a3cf-a01bc88db9e8)

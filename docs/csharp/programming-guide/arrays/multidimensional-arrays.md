---
title: 多次元配列 (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: 12cc7ff4f0a688145f2dee130e66dbe9a05ec7e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33313850"
---
# <a name="multidimensional-arrays-c-programming-guide"></a>多次元配列 (C# プログラミング ガイド)
配列は 1 つ以上の配列を持つことができます。 たとえば、次の宣言は、4 行と 2 列の 2 次元の配列を作成します。  
  
 [!code-csharp[csProgGuideArrays#11](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_1.cs)]  
  
 次の宣言は、4、2、3 の 3 次元配列を作成します。  
  
 [!code-csharp[csProgGuideArrays#12](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_2.cs)]  
  
## <a name="array-initialization"></a>配列の初期化  
 次の例に示すように、宣言時に配列を初期化することができます。  
  
 [!code-csharp[csProgGuideArrays#13](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_3.cs)]  
  
 また、順位を指定せずに配列を初期化することもできます。  
  
 [!code-csharp[csProgGuideArrays#14](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_4.cs)]  
  
 初期化せずに配列変数を宣言する場合、`new` 演算子を使用して配列を変数に代入する必要があります。 `new` の使用を次の例に示します。  
  
 [!code-csharp[csProgGuideArrays#15](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_5.cs)]  
  
 次の例では、特定の配列要素に値を代入します。  
  
 [!code-csharp[csProgGuideArrays#16](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_6.cs)]  
  
 同様に、次の例では、特定の配列要素の値を取得して、それを変数 `elementValue` に代入します。  
  
 [!code-csharp[csProgGuideArrays#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_7.cs)]  
  
 次のコード例では、配列要素を既定値に初期化します (ジャグ配列を除く)。  
  
 [!code-csharp[csProgGuideArrays#17](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_8.cs)]  
  
## <a name="see-also"></a>参照  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [配列](../../../csharp/programming-guide/arrays/index.md)  
 [1 次元配列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [ジャグ配列](../../../csharp/programming-guide/arrays/jagged-arrays.md)

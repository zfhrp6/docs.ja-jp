---
title: 1 次元配列 (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: 2f5dcb032c5dea764cdd212bbcd02e1640089d96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33313954"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>1 次元配列 (C# プログラミング ガイド)
次の例のように、5 つの整数の 1 次元配列を宣言することができます。  
  
 [!code-csharp[csProgGuideArrays#4](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_1.cs)]  
  
 この配列は、`array[0]` から `array[4]` の要素を含んでいます。 [new](../../../csharp/language-reference/keywords/new.md) 演算子を使用して、配列を作成し、配列要素を既定値に初期化します。 この例では、すべての配列要素はゼロに初期化されます。  
  
 同じ方法では、文字列要素を格納する配列を宣言できます。 例:  
  
 [!code-csharp[csProgGuideArrays#5](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_2.cs)]  
  
## <a name="array-initialization"></a>配列の初期化  
 宣言時に配列を初期化することができます。この場合、初期化リスト内の要素の数によって次元が既に提供されているので、次元指定子は必要ありません。 例:  
  
 [!code-csharp[csProgGuideArrays#6](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_3.cs)]  
  
 文字列の配列は、同じ方法で初期化できます。 配列の各要素が曜日の名前で初期化される文字列配列の宣言を次に示します。  
  
 [!code-csharp[csProgGuideArrays#7](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_4.cs)]  
  
 宣言時に配列を初期化する場合は、次のショートカットを使用できます。  
  
 [!code-csharp[csProgGuideArrays#8](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_5.cs)]  
  
 初期化せずに配列変数を宣言できますが、配列をこの変数に割り当てるときに、`new` 演算子を使用する必要があります。 例:  
  
 [!code-csharp[csProgGuideArrays#9](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_6.cs)]  
  
 C# 3.0 で暗黙的に型指定される配列が導入されます。 詳細については、「[暗黙的に型指定される配列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)」を参照してください。  
  
## <a name="value-type-and-reference-type-arrays"></a>値の型と参照型の配列  
 次の配列の宣言を検討してみます。  
  
 [!code-csharp[csProgGuideArrays#10](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_7.cs)]  
  
 このステートメントの結果は、`SomeType` が値型か参照型かによって決まります。 値型の場合、ステートメントはそれそれが型 `SomeType` である 10 個の要素の配列を作成します。 `SomeType` が参照型の場合、ステートメントは、それぞれが null 参照に初期化される 10 個の要素の配列を作成します。  
  
 値型と参照型の詳細については、「[型](../../../csharp/language-reference/keywords/types.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 <xref:System.Array>  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [配列](../../../csharp/programming-guide/arrays/index.md)  
 [多次元配列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [ジャグ配列](../../../csharp/programming-guide/arrays/jagged-arrays.md)

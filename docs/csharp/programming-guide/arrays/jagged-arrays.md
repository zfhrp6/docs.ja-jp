---
title: ジャグ配列 (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: c1825e1a731c40a5945060f8085bd612b5d62008
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297369"
---
# <a name="jagged-arrays-c-programming-guide"></a>ジャグ配列 (C# プログラミング ガイド)
ジャグ配列とは、その要素も配列である配列です。 ジャグ配列の要素には、異なるディメンションとサイズを指定できます。 ジャグ配列は、"配列の配列" と呼ばれることがあります。 次の例では、ジャグ配列の宣言、初期化、およびアクセスの方法について説明します。  
  
 次の 3 つの要素を持つ 1 次元配列の宣言では、それぞれが整数の 1 次元配列になっています。  
  
 [!code-csharp[csProgGuideArrays#19](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_1.cs)]  
  
 `jaggedArray` を使用する前に、その要素を初期化する必要があります。 次のように要素を初期化することができます。  
  
 [!code-csharp[csProgGuideArrays#20](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_2.cs)]  
  
 各要素は、整数の 1 次元配列です。 最初の要素は 5 つの整数の配列で、2 番目の要素は 4 つの整数の配列であり、3 番目の要素は 2 つの整数の配列です。  
  
 初期化子を使って配列の要素に値を格納することもできます。この場合、配列のサイズは不要です。 例:  
  
 [!code-csharp[csProgGuideArrays#21](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_3.cs)]  
  
 次のように宣言時に配列を初期化することもできます。  
  
 [!code-csharp[csProgGuideArrays#22](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_4.cs)]  
  
 次の短い形式を使用できます。 要素の既定の初期化はないので、`new` 演算子を要素の初期化から省略することはできません。  
  
 [!code-csharp[csProgGuideArrays#23](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_5.cs)]  
  
 ジャグ配列は配列の配列です。そのため、配列要素は参照型で、`null` に初期化されます。  
  
 これらの例のように配列の各要素にアクセスできます。  
  
 [!code-csharp[csProgGuideArrays#24](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_6.cs)]  
  
 ジャグ配列と多次元配列を混在させることができます。 異なるサイズの 3 つの 2 次元の配列要素を含む 1 次元のジャグ配列の宣言と初期化を次に示します。 2 次元配列の詳細については、「[多次元配列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)」を参照してください。  
  
 [!code-csharp[csProgGuideArrays#25](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_7.cs)]  
  
 この例に示すように個々の要素にアクセスすることができます。この場合、最初の配列の要素 `[1,0]` の値 (値 `5`) が表示されます。  
  
 [!code-csharp[csProgGuideArrays#26](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_8.cs)]  
  
 メソッド `Length` は、ジャグ配列に含まれる配列の数を返します。 たとえば、前の配列を宣言し、次のコマンド ラインを実行したとします。  
  
 [!code-csharp[csProgGuideArrays#27](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_9.cs)]  
  
 この場合は値 3 が返されます。  
  
## <a name="example"></a>例  
 この例では、要素自体が配列である配列を構築します。 配列の要素のそれぞれのサイズが異なります。  
  
 [!code-csharp[csProgGuideArrays#18](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_10.cs)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Array>  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [配列](../../../csharp/programming-guide/arrays/index.md)  
 [1 次元配列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [多次元配列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)

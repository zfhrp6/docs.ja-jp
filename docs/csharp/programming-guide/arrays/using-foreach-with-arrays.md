---
title: 配列での foreach の使用 (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: 8511d9dd3b7155d2f6bca229f264071b54ed173b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>配列での foreach の使用 (C# プログラミング ガイド)
C# には、[foreach](../../../csharp/language-reference/keywords/foreach-in.md) ステートメントも用意されています。 このステートメントでは、配列または任意の列挙可能なコレクションの要素の反復処理を簡単に、また安全に行うことができます。 `foreach` ステートメントは、配列またはコレクション型の列挙子から返される順序で要素を処理します。これは通常、ゼロ番目の要素から最後の要素までです。 たとえば、次のコードは `numbers` という配列を作成し、`foreach` ステートメントで配列内の反復処理を行います。  
  
 [!code-csharp[csProgGuideArrays#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_1.cs)]  
  
 多次元配列を使用する場合は、同じメソッドを使用して配列要素を反復処理できます。次に例を示します。  
  
 [!code-csharp[csProgGuideArrays#29](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_2.cs)]  
  
 ただし、多次元配列では、入れ子になった [for](../../../csharp/language-reference/keywords/for.md) ループを使用した方が配列要素をより厳密に制御できます。  
  
## <a name="see-also"></a>参照  
 <xref:System.Array>  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [配列](../../../csharp/programming-guide/arrays/index.md)  
 [1 次元配列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [多次元配列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [ジャグ配列](../../../csharp/programming-guide/arrays/jagged-arrays.md)

---
title: 引数としての配列の受け渡し (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: d863cdc33a8a1a844aabbea9ba5876614e6e8dba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a>引数としての配列の受け渡し (C# プログラミング ガイド)
配列は、引数としてメソッド パラメーターに渡すことができます。 配列は参照型であるため、メソッドは要素の値を変更できます。  
  
## <a name="passing-single-dimensional-arrays-as-arguments"></a>1 次元配列を引数として渡す  
 初期化された 1 次元配列をメソッドに渡すことができます。 たとえば、次のステートメントは、配列を print メソッドに送信します。  
  
 [!code-csharp[csProgGuideArrays#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_1.cs)]  
  
 次のコードは、print メソッドの実装の一部を示しています。  
  
 [!code-csharp[csProgGuideArrays#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_2.cs)]  
  
 次の例に示すように、一度に新しい配列を初期化して渡すことができます。  
  
 [!code-csharp[CsProgGuideArrays#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_3.cs)]  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例では、文字列の配列が初期化され、引数として文字列の `PrintArray` メソッドに渡されます。 このメソッドは、配列の要素を表示します。 次に、値渡しで配列引数を送信することで配列要素の変更が妨げられないことを示すため、メソッド `ChangeArray` と `ChangeArrayElement` が呼び出されます。  
  
### <a name="code"></a>コード  
 [!code-csharp[csProgGuideArrays#30](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_4.cs)]  
  
## <a name="passing-multidimensional-arrays-as-arguments"></a>多次元配列を引数として渡す  
 1 次元配列を渡すのと同じ方法で、初期化された多次元配列をメソッドに渡します。  
  
 [!code-csharp[csProgGuideArrays#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_5.cs)]  
  
 次のコードに、2 次元配列を引数として受け取る print メソッドの宣言の一部を示します。  
  
 [!code-csharp[csProgGuideArrays#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_6.cs)]  
  
 次の例に示すように、一度に新しい配列を初期化して渡すことができます。  
  
 [!code-csharp[csProgGuideArrays#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_7.cs)]  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例では、整数の 2 次元配列が初期化され、`Print2DArray` メソッドに渡されます。 このメソッドは、配列の要素を表示します。  
  
### <a name="code"></a>コード  
 [!code-csharp[csProgGuideArrays#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_8.cs)]  
  
## <a name="see-also"></a>参照  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [配列](../../../csharp/programming-guide/arrays/index.md)  
 [1 次元配列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [多次元配列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [ジャグ配列](../../../csharp/programming-guide/arrays/jagged-arrays.md)

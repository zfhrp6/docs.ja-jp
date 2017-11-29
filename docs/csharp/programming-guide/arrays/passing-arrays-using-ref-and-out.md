---
title: "ref と out を使用した配列の引き渡し (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: arrays [C#], passing using ref and out
ms.assetid: 6a2b261e-a1cc-49a6-b4f0-6cacae385a1e
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7f2d4e613491b26e82523d230398af3ec34b4d0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arrays-using-ref-and-out-c-programming-guide"></a>ref と out を使用した配列の引き渡し (C# プログラミング ガイド)
すべての [out](../../../csharp/language-reference/keywords/out.md) パラメーターと同じように、配列型の `out` パラメーターも使用する前に代入される必要があります。つまり、呼び出される側で代入する必要があります。 例:  
  
 [!code-csharp[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]  
  
 すべての [ref](../../../csharp/language-reference/keywords/ref.md) パラメーターと同じように、配列型の `ref` パラメーターも、呼び出し側で明示的に代入する必要があります。 したがって、呼び出される側で明示的に代入する必要はありません。 配列型の `ref` パラメーターは、呼び出しの結果として変更される場合があります。 たとえば、配列に [null](../../../csharp/language-reference/keywords/null.md) 値が代入されたり、別の配列で初期化されたりする場合があります。 例:  
  
 [!code-csharp[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]  
  
 次の 2 つの例は、メソッドに配列を渡すときに使われる `out` と `ref` の違いを示しています。  
  
## <a name="example"></a>例  
 この例では、配列 `theArray` は呼び出し元 (`Main` メソッド) で宣言されて、`FillArray` メソッドで初期化されます。 その後、配列要素は呼び出し元に返されて表示されます。  
  
 [!code-csharp[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]  
  
## <a name="example"></a>例  
 この例では、配列 `theArray` は呼び出し元 (`Main` メソッド) で初期化された後、`FillArray` パラメーターを使って `ref` メソッドに渡されます。 一部の配列要素は、`FillArray` メソッドの中で変更されます。 その後、配列要素は呼び出し元に返されて表示されます。  
  
 [!code-csharp[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]  
  
## <a name="see-also"></a>関連項目  
 [ref](../../../csharp/language-reference/keywords/ref.md)  
 [out パラメーター修飾子](../../../csharp/language-reference/keywords/out-parameter-modifier.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [配列](../../../csharp/programming-guide/arrays/index.md)  
 [1 次元配列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [多次元配列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [ジャグ配列](../../../csharp/programming-guide/arrays/jagged-arrays.md)

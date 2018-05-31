---
title: 配列での foreach の使用 (C# プログラミング ガイド)
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: b858f35167e24390a729769487ce98908a3d349f
ms.sourcegitcommit: 54231aa56fca059e9297888a96fbca1d4cf3746c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/25/2018
ms.locfileid: "34549456"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>配列での foreach の使用 (C# プログラミング ガイド)

[foreach](../../language-reference/keywords/foreach-in.md) ステートメントでは、配列の要素の反復処理を、簡単かつ安全に行うことができます。

1 次元配列の場合、`foreach` ステートメントは、インデックス 0 から始まりインデックス `Length - 1` で終わるインデックスの昇順で要素を処理します。

[!code-csharp[csProgGuideArrays#28](./codesnippet/CSharp/using-foreach-with-arrays_1.cs)]

多次元配列の場合、右端の次元のインデックスが最初に加算されていき、次にその左の次元、またその左、というような方法で各要素がトラバースされます。

[!code-csharp[csProgGuideArrays#29](./codesnippet/CSharp/using-foreach-with-arrays_2.cs)]

ただし、多次元配列では、入れ子になった [for](../../language-reference/keywords/for.md) ループを使用した方が、配列要素を処理する順序をより厳密に制御できます。

## <a name="see-also"></a>関連項目  
 <xref:System.Array>  
 [C# プログラミング ガイド](../index.md)  
 [配列](index.md)  
 [1 次元配列](single-dimensional-arrays.md)  
 [多次元配列](multidimensional-arrays.md)  
 [ジャグ配列](jagged-arrays.md)

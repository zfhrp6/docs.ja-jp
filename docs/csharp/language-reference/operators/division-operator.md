---
title: / 演算子 (C# リファレンス)
ms.date: 04/04/2018
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
ms.openlocfilehash: 9d0bbff1fd9f4ab3c93c879d12ccd5fde1187b44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272572"
---
# <a name="-operator-c-reference"></a>/ 演算子 (C# リファレンス)
除算演算子 (`/`) は、1 つ目のオペランドを 2 つ目のオペランドで除算します。 すべての数値型には定義済みの除算演算子があります。
  
## <a name="remarks"></a>コメント  
 ユーザー定義型は `/` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。 `/` 演算子のオーバーロードは、[/= 演算子](division-assignment-operator.md)を暗黙的にオーバーロードします。  
  
 2 つの整数を除算した場合、結果は常に整数になります。 たとえば、7 / 3 の結果は 2 となります。 これを切り捨て除算と混同しないでください。`/` 演算子では 0 方向に丸められます。-7/3 は-2 になります。  
  
 有理数として商を取得するには、`float`、`double`、または `decimal` 型を使います。 [組み込み数値型](../../../csharp/language-reference/keywords/reference-tables-for-types.md)の間で変換を行う方法はたくさんあります。  
  
 余りを計算するには、[剰余演算子](../../../csharp/language-reference/operators/remainder-operator.md) `%` を使います。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)

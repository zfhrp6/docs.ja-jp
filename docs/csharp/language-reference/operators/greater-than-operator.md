---
title: '&gt; 演算子 (C# リファレンス)'
ms.date: 07/20/2015
f1_keywords:
- '>_CSharpKeyword'
helpviewer_keywords:
- '> operator [C#]'
- greater than operator (>) [C#]
ms.assetid: 26d3cb69-9c0b-4cc5-858b-5be1abd6659d
ms.openlocfilehash: 1589c5e785b33db6106a0ef0a58202e771db9fa0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273499"
---
# <a name="gt-operator-c-reference"></a>&gt; 演算子 (C# リファレンス)
すべての数値型と列挙型で "より大きい" 関係演算子 (`>`) が定義されます。これは、最初のオペランドが 2 番目のオペランドより大きい場合に `true` を返し、それ以外の場合、`false` を返します。  
  
## <a name="remarks"></a>コメント  
 ユーザー定義型は `>` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。 `>` をオーバーロードする場合は、[<](../../../csharp/language-reference/operators/less-than-operator.md) もオーバーロードする必要があります。 二項演算子をオーバーロードすると、対応する代入演算子がある場合、これも暗黙的にオーバーロードされます。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#29](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-operator_1.cs)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)  
 [explicit](../../../csharp/language-reference/keywords/explicit.md)

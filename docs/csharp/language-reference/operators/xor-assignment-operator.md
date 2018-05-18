---
title: ^= 演算子 (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: 0315cab66729d8169527c4b0ba7e00ab3b5ad5da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>^= 演算子 (C# リファレンス)
排他的 OR 代入演算子。  
  
## <a name="remarks"></a>コメント  
 次のような形式の式があります。  
  
```  
x ^= y  
```  
  
 これが次のように評価されます。  
  
```  
x = x ^ y  
```  
  
 ただし、`x` が評価されるのは 1 回だけです。 [^ 演算子](../../../csharp/language-reference/operators/xor-operator.md)は整数オペランドにビット演算排他的 OR 操作を実行し、[ブール](../../../csharp/language-reference/keywords/bool.md) オペランドに論理的 OR 操作を実行します。  
  
 ^= 演算子は直接オーバーロードできませんが、ユーザー定義型は [^ 演算子](../../../csharp/language-reference/operators/xor-operator.md)をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」参照)。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)

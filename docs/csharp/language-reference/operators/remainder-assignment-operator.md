---
title: '%= 演算子 (C# リファレンス)'
ms.date: 04/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: aadcb5ef969ff408cc1e738fc0f5b67152fdc78b
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171968"
---
# <a name="-operator-c-reference"></a>%= 演算子 (C# リファレンス)
剰余代入演算子です。  
  
## <a name="remarks"></a>コメント  
 次のような `%=` 代入演算子を使用する式があるとします  
  
```csharp  
x %= y  
```  
  
 上記の式は、次の式と同じです。  
  
```csharp  
x = x % y  
```  
  
 ただし、`x` が評価されるのは 1 回だけです。 [% 演算子](../../../csharp/language-reference/operators/remainder-operator.md)は、数値型の除算後の剰余を計算するために事前定義されています。  
  
 `%=` 演算子は直接オーバーロードできませんが、ユーザー定義型は [% 演算子](../../../csharp/language-reference/operators/remainder-operator.md)をオーバーロードできます (「[operator (C# リファレンス)](../../../csharp/language-reference/keywords/operator.md)」参照)。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)

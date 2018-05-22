---
title: '|= 演算子 (C# リファレンス)'
ms.date: 07/20/2015
f1_keywords:
- '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
ms.openlocfilehash: 18246d013275c8d6c8ad7e05409387457afc3442
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
---
# <a name="-operator-c-reference"></a>|= 演算子 (C# リファレンス)
OR 代入演算子です。  
  
## <a name="remarks"></a>コメント  
 次のような `|=` 代入演算子を使用する式があるとします  
  
```csharp  
x |= y  
```  
  
 上記の式は、次の式と同じです。  
  
```csharp  
x = x | y  
```  
  
 ただし、`x` が評価されるのは 1 回だけです。 [&#124; 演算子](../../../csharp/language-reference/operators/or-operator.md)では、整数のオペランドではビットごとの論理 OR 演算、ブール オペランドでは論理 OR 演算が実行されます。  
  
 `|=` 演算子は直接オーバーロードできませんが、ユーザー定義型は [&#124; 演算子](../../../csharp/language-reference/operators/or-operator.md)をオーバーロードできます (「[operator](../../../csharp/language-reference/keywords/operator.md)」参照)。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)

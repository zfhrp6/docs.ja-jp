---
title: -= 演算子 (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: 2f37bfa303fb523840b15e896ee3b4a967eb5b2b
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
---
# <a name="--operator-c-reference"></a>-= 演算子 (C# リファレンス)
減算代入演算子です。  
  
## <a name="remarks"></a>コメント  
 次のような `-=` 代入演算子を使用する式があるとします  
  
```csharp  
x -= y  
```  
  
 上記の式は、次の式と同じです。  
  
```csharp  
x = x - y  
```  
  
 ただし、`x` が評価されるのは 1 回だけです。 [- 演算子](../../../csharp/language-reference/operators/subtraction-operator.md)の意味は、`x` および `y` の型によって異なります (数値オペランドの場合は減算、デリゲート オペランドの場合はデリゲートの削除、など)。  
  
 `-=` 演算子は直接オーバーロードできませんが、ユーザー定義型は [- 演算子](../../../csharp/language-reference/operators/subtraction-operator.md)をオーバーロードできます (「[operator](../../../csharp/language-reference/keywords/operator.md)」参照)。  
  
 -= 演算子は、C# でイベント サブスクリプションを解除するときにも使用されます。 詳細については、「[方法: イベント サブスクリプションとサブスクリプションの解除](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)」を参照してください。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)

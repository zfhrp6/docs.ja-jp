---
title: "-= 演算子 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 443f0d717288a491838d23eaa63218150bd346d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="--operator-c-reference"></a>-= 演算子 (C# リファレンス)
減算代入演算子です。  
  
## <a name="remarks"></a>コメント  
 次のような `-=` 代入演算子を使用する式があるとします  
  
```  
x -= y  
```  
  
 上記の式は、次の式と同じです。  
  
```  
x = x - y  
```  
  
 ただし、`x` が評価されるのは 1 回だけです。 [- 演算子](../../../csharp/language-reference/operators/subtraction-operator.md)の意味は、`x` および `y` の型によって異なります (数値オペランドの場合は減算、デリゲート オペランドの場合はデリゲートの削除、など)。  
  
 `-=` 演算子は直接オーバーロードできませんが、ユーザー定義型は [- 演算子](../../../csharp/language-reference/operators/subtraction-operator.md)をオーバーロードできます (「[operator](../../../csharp/language-reference/keywords/operator.md)」参照)。  
  
 -= 演算子は、C# でイベント サブスクリプションを解除するときにも使用されます。 詳細については、「[方法: イベント サブスクリプションとサブスクリプションの解除](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)」を参照してください。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)

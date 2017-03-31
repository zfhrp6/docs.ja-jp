---
title: "-= 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- -=_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d9ffcfe9b42f7ca65801a58338c8e40a37c90316
ms.lasthandoff: 03/13/2017

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
 [!code-cs[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# 演算子](../../../csharp/language-reference/operators/index.md)


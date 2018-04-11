---
title: += 演算子 (C# リファレンス)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: de83f48fc644d8b232d9ef9e1698272f20a27d65
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="-operator-c-reference"></a>+= 演算子 (C# リファレンス)
加算代入演算子です。  
  
## <a name="remarks"></a>コメント  
 次のような `+=` 代入演算子を使用する式があるとします  
  
```  
x += y  
```  
  
 上記の式は、次の式と同じです。  
  
```  
x = x + y  
```  
  
 ただし、`x` が評価されるのは 1 回だけです。 [+ 演算子](../../../csharp/language-reference/operators/addition-operator.md)の意味は、`x` および `y` の型によって異なります (たとえば、数値オペランドの場合は加算、文字列オペランドの場合は連結になります)。  
  
 `+=` 演算子は直接オーバーロードできませんが、ユーザー定義型は [+ 演算子](../../../csharp/language-reference/operators/addition-operator.md)をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」参照)。  
  
 `+=` 演算子は、イベントに対する応答として呼び出されるメソッドを指定するときにも使用されます。こうしたメソッドは、イベント ハンドラーと呼ばれます。 このコンテキストでの `+=` 演算子の使用は、"*イベントのサブスクライブ*" と呼ばれます。 詳細については、「[方法: イベント サブスクリプションとサブスクリプションの解除](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)」と「[デリゲート](../../../csharp/programming-guide/delegates/index.md)」を参照してください。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)

---
title: "&gt;&gt;= 演算子 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6bd0a61860c35a485d61585a90ba297f75d8cf1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt;= 演算子 (C# リファレンス)
右シフト代入演算子。  
  
## <a name="remarks"></a>コメント  
 次のような形式の式があります。  
  
```  
x >>= y  
```  
  
 これが次のように評価されます。  
  
```  
x = x >> y  
```  
  
 ただし、`x` が評価されるのは 1 回だけです。 [>> 演算子](../../../csharp/language-reference/operators/right-shift-operator.md)は、`y` で指定された量だけ `x` を右にシフトします。  
  
 >>= 演算子は直接オーバーロードできませんが、ユーザー定義型は [>> 演算子](../../../csharp/language-reference/operators/right-shift-operator.md)をオーバーロードできます (「[operator](../../../csharp/language-reference/keywords/operator.md)」参照)。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)

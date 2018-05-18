---
title: '&gt;&gt;= 演算子 (C# リファレンス)'
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: 41203f6e7c9929bb349d29c40cf7cc6c24550c36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
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
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)

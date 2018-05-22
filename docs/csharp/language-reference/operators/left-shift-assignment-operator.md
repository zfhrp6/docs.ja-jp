---
title: '&lt;&lt;= 演算子 (C# リファレンス)'
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: e5f3886670baa34b0360501ee15280b93fac36bc
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
---
# <a name="ltlt-operator-c-reference"></a>&lt;&lt;= 演算子 (C# リファレンス)
左シフト代入演算子。  
  
## <a name="remarks"></a>コメント  
 次のような形式の式があります。  
  
```csharp  
x <<= y  
```  
  
 これが次のように評価されます。  
  
```csharp  
x = x << y  
```  
  
 ただし、`x` が評価されるのは 1 回だけです。 [<< 演算子](../../../csharp/language-reference/operators/left-shift-operator.md) は、`y` で指定されたビット数だけ `x` を左にシフトします。  
  
 `<<=` 演算子は直接オーバーロードできませんが、ユーザー定義型は [<< 演算子](../../../csharp/language-reference/operators/left-shift-operator.md) をオーバーロードできます (「[operator](../../../csharp/language-reference/keywords/operator.md)」参照)。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)

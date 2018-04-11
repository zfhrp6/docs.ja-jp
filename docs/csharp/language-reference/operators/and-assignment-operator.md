---
title: '&amp;= 演算子 (C# リファレンス)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bea90651faaafe7b754ce1cf16bddbab997d5f5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-c-reference"></a>&amp;= 演算子 (C# リファレンス)
AND 代入演算子です。  
  
## <a name="remarks"></a>コメント  
 次のような `&=` 代入演算子を使用する式があるとします  
  
```  
x &= y  
```  
  
 上記の式は、次の式と同じです。  
  
```  
x = x & y  
```  
  
 ただし、`x` が評価されるのは 1 回だけです。 [& 演算子](../../../csharp/language-reference/operators/and-operator.md)では、整数のオペランドではビットごとの論理 AND 演算、`bool` オペランドでは論理 AND 演算が実行されます。  
  
 `&=` 演算子は直接オーバーロードできませんが、[& 演算子](../../../csharp/language-reference/operators/and-operator.md)はユーザー定義型でオーバーロードできます (「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照)。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)

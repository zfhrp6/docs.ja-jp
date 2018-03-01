---
title: "%= 演算子 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- modulus assignment operator (=%) [C#]
- '%= assignment operator (modulus assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9bafd0078153e29fbf923948d9b380d4795c3d35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>%= 演算子 (C# リファレンス)
剰余代入演算子です。  
  
## <a name="remarks"></a>コメント  
 次のような `%=` 代入演算子を使用する式があるとします  
  
```  
x %= y  
```  
  
 上記の式は、次の式と同じです。  
  
```  
x = x % y  
```  
  
 ただし、`x` が評価されるのは 1 回だけです。 [% 演算子](../../../csharp/language-reference/operators/modulus-operator.md)は、数値型の除算後の剰余を計算するために事前定義されています。  
  
 `%=` 演算子は直接オーバーロードできませんが、ユーザー定義型は [% 演算子](../../../csharp/language-reference/operators/modulus-operator.md)をオーバーロードできます (「[operator (C# リファレンス)](../../../csharp/language-reference/keywords/operator.md)」参照)。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)

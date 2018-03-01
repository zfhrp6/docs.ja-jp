---
title: "/= 演算子 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 26096d9b5dfc565c9933f1ed8ffb241dc900d9ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>/= 演算子 (C# リファレンス)
除算代入演算子です。  
  
## <a name="remarks"></a>コメント  
 次のような `/=` 代入演算子を使用する式があるとします  
  
```  
x /= y  
```  
  
 上記の式は、次の式と同じです。  
  
```  
x = x / y  
```  
  
 ただし、`x` が評価されるのは 1 回だけです。 [/ 演算子](../../../csharp/language-reference/operators/division-operator.md)は、数値型の除算のために事前定義されています。  
  
 `/=` 演算子は直接オーバーロードできませんが、ユーザー定義型では [/ 演算子](../../../csharp/language-reference/operators/division-operator.md)をオーバーロードできます。(「[演算子](../../../csharp/language-reference/keywords/operator.md)」参照)。 すべての複合代入演算子において、二項演算子をオーバーロードすると、同等の複合代入が暗黙的にオーバーロードされます。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)

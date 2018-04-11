---
title: '|| 演算子 (C# リファレンス)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
caps.latest.revision: 25
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7b95fd162c9a89789e1970b32473c8acf16ba5cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>|| 演算子 (C# リファレンス)
条件付き OR 演算子 (`||`) では、`bool` オペランドの論理 OR が実行されます。 最初のオペランドが `true` と評価されると、2 番目のオペランドは評価されません。 最初のオペランドが `false` と評価されると、2 番目の演算子は、OR 式を、全体として、`true` または `false` に評価するかどうかを判断します。  
  
## <a name="remarks"></a>コメント  
 次の演算は、  
  
```  
x || y  
```  
  
 次の演算に対応しています。  
  
```  
x | y  
```  
  
 ただし `x` が `true` の場合、OR 演算は `y` の値に関係なく `true` となるため、`y` は評価されません。 この概念は、"ショートサーキット" 評価と呼ばれます。  
  
 条件付き OR 演算子はオーバーロードできませんが、通常の論理演算子、[true](../../../csharp/language-reference/keywords/true.md) 演算子、[false](../../../csharp/language-reference/keywords/false.md) 演算子のオーバーロードは、一定の制約内で、条件付き論理演算子のオーバーロードとも見なされます。  
  
## <a name="example"></a>例  
 次の例では、`||` が使用されている式は、最初のオペランドだけを評価します。 `|` が使用されている式は、両方のオペランドを評価します。 2 番目の例では、両方のオペランドが評価されると、実行時例外が発生します。  
  
 [!code-csharp[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-or-operator_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)

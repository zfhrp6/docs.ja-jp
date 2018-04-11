---
title: '&lt;= 演算子 (C# リファレンス)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <=_CSharpKeyword
helpviewer_keywords:
- less than or equal to operator (<=) [C#]
- <= operator [C#]
ms.assetid: bb0caec9-d253-4105-b8bc-5252233251e4
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a74af852451a193aaee70fea2a68ca8ff29cc215
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="lt-operator-c-reference"></a>&lt;= 演算子 (C# リファレンス)
すべての数値型と列挙型で "以下" 関係演算子 (`<=`) が定義されます。これは、最初のオペランドが 2 番目のオペランドと等しいか、それより小さい場合に `true` を返し、それ以外の場合、`false` を返します。  
  
## <a name="remarks"></a>コメント  
 ユーザー定義型は `<=` 演算子をオーバーロードできます。 詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。 `<=` をオーバーロードする場合は、[>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) もオーバーロードする必要があります。 整数型に対する演算は、通常、列挙型で使用できます。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#32](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-equal-operator_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)  
 [explicit](../../../csharp/language-reference/keywords/explicit.md)

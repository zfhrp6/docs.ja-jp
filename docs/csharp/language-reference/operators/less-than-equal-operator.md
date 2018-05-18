---
title: '&lt;= 演算子 (C# リファレンス)'
ms.date: 07/20/2015
f1_keywords:
- <=_CSharpKeyword
helpviewer_keywords:
- less than or equal to operator (<=) [C#]
- <= operator [C#]
ms.assetid: bb0caec9-d253-4105-b8bc-5252233251e4
ms.openlocfilehash: 24bf274bfcb0a8e19a79aafb3bd7920054044be0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="lt-operator-c-reference"></a>&lt;= 演算子 (C# リファレンス)
すべての数値型と列挙型で "以下" 関係演算子 (`<=`) が定義されます。これは、最初のオペランドが 2 番目のオペランドと等しいか、それより小さい場合に `true` を返し、それ以外の場合、`false` を返します。  
  
## <a name="remarks"></a>コメント  
 ユーザー定義型は `<=` 演算子をオーバーロードできます。 詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。 `<=` をオーバーロードする場合は、[>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) もオーバーロードする必要があります。 整数型に対する演算は、通常、列挙型で使用できます。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#32](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-equal-operator_1.cs)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)  
 [explicit](../../../csharp/language-reference/keywords/explicit.md)

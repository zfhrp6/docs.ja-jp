---
title: '!= 演算子 (C# リファレンス)'
ms.date: 07/20/2015
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: e409e2a80886fd5f7f4cdbeaa9b4e3325f8a967b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>!= 演算子 (C# リファレンス)
非等値演算子 (`!=`) は、そのオペランドが等しい場合には false を返し、それ以外の場合は true を返します。 非等値演算子は、文字列とオブジェクトを含むすべての型に対して事前に定義されています。 ユーザー定義型は `!=` 演算子をオーバーロードできます。  
  
## <a name="remarks"></a>コメント  
 組み込みの値型の場合、非等値演算子 (`!=`) ではオペランドの値が異なる場合に true が返され、それ以外の場合は false が返されます。 `string` 以外の参照型の場合、`!=` では 2 つのオペランドが異なるオブジェクトを参照する場合に true が返されます。 `string` 型の場合は、`!=` は文字列の値を比較します。  
  
 ユーザー定義の値の型は `!=` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。 ユーザー定義参照型もオーバーロードはできますが、既定では、組み込み参照型とユーザー定義参照型のいずれに対しても `!=` は前述のとおりに機能します。 `!=` をオーバーロードする場合は、[==](../../../csharp/language-reference/operators/equality-comparison-operator.md) もオーバーロードする必要があります。 整数型に対する演算は、通常、列挙型で使用できます。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)

---
title: '&amp; 演算子 (C# リファレンス)'
ms.date: 04/04/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: 59813b4bc5781776c9f9741c3e49e660c684bff9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267881"
---
# <a name="amp-operator-c-reference"></a>&amp; 演算子 (C# リファレンス)
`&` 演算子には、単項演算子としての働きと 2 項演算子としての働きとがあります。  
  
## <a name="remarks"></a>コメント  
 単項 `&` 演算子では、オペランドのアドレスが返されます ([unsafe](../../../csharp/language-reference/keywords/unsafe.md) コンテキストが必要)。  
  
 整数型と `bool` には、2 項 `&` 演算子が事前定義されています。 整数型の場合、& はオペランドのビットごとの論理 AND を計算します。 `bool` オペランドの場合、& は、そのオペランドの論理 AND を計算します。つまり、結果は、両方のオペランドが `true` の場合にのみ `true` になります。  
  
 バイナリ `&` 演算子は、[条件 AND 演算子](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&` とは対照的に、最初の演算子の値に関係なく、両方の演算子を評価します。 例:  
  
 [!code-csharp[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 ユーザー定義型は二項 `&` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。 整数型に対する演算は、通常、列挙型で使用できます。 二項演算子をオーバーロードすると、対応する代入演算子がある場合、これも暗黙的にオーバーロードされます。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)

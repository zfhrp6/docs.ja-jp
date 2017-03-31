---
title: "+ 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- +_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3c6ef1acc69fed1c43f0a249287ca8819c8f091c
ms.lasthandoff: 03/13/2017

---
# <a name="-operator-c-reference"></a>+ 演算子 (C# リファレンス)
`+` 演算子には、単項演算子としての働きと 2 項演算子としての働きとがあります。  
  
## <a name="remarks"></a>コメント  
 すべての数値型には、単項 `+` 演算子が事前定義されています。 数値型に対する単項 `+` 演算の結果は、単にそのオペランドの値になります。  
  
 数値型と文字列型には、2 項 `+` 演算子が事前定義されています。 数値型の場合、+ の 2 つのオペランドの合計が計算されます。 一方または両方のオペランドが文字列型である場合、+ は、そのオペランドの文字列表現を連結します。  
  
 2 項 `+` 演算子はデリゲート型にも備わっており、その場合、デリゲートの連結が実行されます。  
  
 単項 `+` 演算子と 2 項 `+` 演算子は、ユーザー定義型でオーバーロードすることができます。 整数型に対する演算は、通常、列挙型で使用できます。 詳細については、「[operator (C# Reference) (operator (C# リファレンス))](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  
  
## <a name="example"></a>例  
 [!code-cs[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# 演算子](../../../csharp/language-reference/operators/index.md)   
 [演算子 (C# リファレンス)](../../../csharp/language-reference/keywords/operator.md)

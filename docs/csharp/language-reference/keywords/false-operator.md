---
title: "false 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
caps.latest.revision: 21
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 22aaef73efc1d3327774336bf5b2c5475950ce25
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="false-operator-c-reference"></a>false 演算子 (C# リファレンス)
オペランドが `false` であることを示す[ブール](../../../csharp/language-reference/keywords/bool.md)値 `true` を返します。それ以外の場合は `false` を返します。  
  
 C# 2.0 より前のバージョンでは、`true` および `false` 演算子は、`SqlBool` などの型と互換性のあるユーザー定義の null 非許容の値型を作成するために使用されていました。 ただし、現在の言語には、null 許容の値型が組み込まれているので、可能な限り、`true` および `false` 演算子のオーバーロードではなく、Null 許容の値型を使用することをお勧めします。 詳細については、「[null 許容型](../../../csharp/programming-guide/nullable-types/index.md)」を参照してください。  
  
 null 許容のブール値では、必ずしも式 `a != b` が `!(a == b)` にならないことがあります。これは、いずれかの値が null の場合があるためです。 式内の null 値を適切に処理するには、`true` および `false` 演算子の両方を別にオーバーロードする必要があります。 次の例は、`true` および `false` 演算子をオーバーロードして使用する方法を示しています。  
  
 [!code-cs[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/false-operator_1.cs)]  
  
 `true` および `false` 演算子のオーバーロードする型は、[if](../../../csharp/language-reference/keywords/if-else.md)、[do](../../../csharp/language-reference/keywords/do.md)、[while](../../../csharp/language-reference/keywords/while.md)、[for](../../../csharp/language-reference/keywords/for.md) ステートメント内の制御式と、[条件式](../../../csharp/language-reference/operators/conditional-operator.md)で使用できます。  
  
 型で演算子 `false` を定義する場合は、演算子の [true](../../../csharp/language-reference/keywords/true.md) も定義する必要があります。  
  
 型では、条件付き論理演算子 [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) と [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) を直接オーバーロードできませんが、通常の論理演算子と演算子 `true` および `false` をオーバーロードすることで同等の効果を実現できます。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [C# 演算子](../../../csharp/language-reference/operators/index.md)   
 [true](../../../csharp/language-reference/keywords/true.md)

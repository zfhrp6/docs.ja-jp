---
title: true 演算子 (C# リファレンス)
ms.date: 07/20/2015
helpviewer_keywords:
- true operator [C#]
ms.assetid: acaba817-5da5-4364-b3b2-2e5c75ec1839
ms.openlocfilehash: 71f522b3860f7461f5c52dd77bb424f7ba0f9bf5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275081"
---
# <a name="true-operator-c-reference"></a>true 演算子 (C# リファレンス)
オペランドが true である場合は [ブール](../../../csharp/language-reference/keywords/bool.md)値 `true` を返します。それ以外の場合は `false` を返します。  
  
 C# 2.0 より前のバージョンでは、`true` 演算子と `false` 演算子は、`SqlBool` などの型と互換性のあるユーザー定義の null 非許容の値型を作成するために使用されていました。 ただし、現在は null 許容の値型が組み込まれているため、可能な場合には、`true` 演算子と `false` 演算子のオーバーロードではなく、null 許容の値型を使用してください。 詳細については、「[null 許容型](../../../csharp/programming-guide/nullable-types/index.md)」を参照してください。  
  
 null 許容のブール値では、必ずしも式 `a != b` と `!(a == b)` は同じではありません。これは、一方または両方の値が null になる可能性があるためです。 式内の null 値を正しく識別するには、`true` 演算子と `false` 演算子の両方を個別にオーバーロードする必要があります。 次の例は、`true` 演算子と `false` 演算子をオーバーロードして使用する方法を示しています。  
  
 [!code-csharp[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/true-operator_1.cs)]  
  
 `true` 演算子と `false` 演算子をオーバーロードする型は、[if](../../../csharp/language-reference/keywords/if-else.md)、[do](../../../csharp/language-reference/keywords/do.md)、[while](../../../csharp/language-reference/keywords/while.md)、[for](../../../csharp/language-reference/keywords/for.md) ステートメント内の制御式と、[条件式](../../../csharp/language-reference/operators/conditional-operator.md)で使用できます。  
  
 型で `true` 演算子を定義する場合は [false](../../../csharp/language-reference/keywords/false.md) 演算子も定義する必要があります。  
  
 型では、条件付き論理演算子 ([&&](../../../csharp/language-reference/operators/conditional-and-operator.md) と [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md)) を直接オーバーロードすることはできませんが、通常の論理演算子と演算子 `true` および `false` をオーバーロードすることで同等の効果を実現できます。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)  
 [false](../../../csharp/language-reference/keywords/false.md)

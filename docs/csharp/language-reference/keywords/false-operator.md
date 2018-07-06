---
title: false 演算子 (C# リファレンス)
ms.date: 07/20/2015
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: e1c6da604f35031dd9d712125356243e1735f452
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027838"
---
# <a name="false-operator-c-reference"></a>false 演算子 (C# リファレンス)

オペランドが `false` であることを示す[ブール](bool.md)値 `true` を返します。それ以外の場合は `false` を返します。

C# 2.0 より前のバージョンでは、`true` および `false` 演算子は、`SqlBool` などの型と互換性のあるユーザー定義の null 非許容の値型を作成するために使用されていました。 ただし、現在は null 許容の値型が組み込まれているため、可能な場合には、`true` 演算子と `false` 演算子のオーバーロードではなく、null 許容の値型を使用してください。 詳細については、「[null 許容型](../../programming-guide/nullable-types/index.md)」を参照してください。

null 許容のブール値では、必ずしも式 `a != b` が `!(a == b)` にならないことがあります。これは、いずれかの値が null の場合があるためです。 式内の null 値を適切に処理するには、`true` および `false` 演算子の両方を別にオーバーロードする必要があります。 次の例は、`true` 演算子と `false` 演算子をオーバーロードして使用する方法を示しています。

[!code-csharp[csrefKeywordsOperator#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#16)]

`true` 演算子と `false` 演算子をオーバーロードする型は、[if](if-else.md)、[do](do.md)、[while](while.md)、[for](for.md) ステートメント内の制御式と、[条件式](../operators/conditional-operator.md)で使用できます。

型で演算子 `false` を定義する場合は、演算子の [true](true.md) も定義する必要があります。

型では、条件付き論理演算子 [&&](../operators/conditional-and-operator.md) と [&#124;&#124;](../operators/conditional-or-operator.md) を直接オーバーロードできませんが、通常の論理演算子と演算子 `true` および `false` をオーバーロードすることで同等の効果を実現できます。

## <a name="c-language-specification"></a>C# 言語仕様

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>関連項目

[C# リファレンス](../index.md)  
[C# プログラミング ガイド](../../programming-guide/index.md)  
[C# のキーワード](index.md)  
[C# 演算子](../operators/index.md)  
[true](true.md)  
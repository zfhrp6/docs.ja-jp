---
title: "Null 許容型の使用 (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c8a42392bbcd2e53c54ff4c13bf98c048262ae4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="using-nullable-types-c-programming-guide"></a>Null 許容型の使用 (C# プログラミング ガイド)
Null 許容型は、基底の型のすべての値と、追加の [null](../../../csharp/language-reference/keywords/null.md) 値を表すことができます。 Null 許容型は、次のいずれかの形式で宣言します。  
  
 `System.Nullable<T> variable`  
  
 または  
  
 `T? variable`  
  
 `T` は、Null 許容型の基底の型です。 `T` には、`struct` を含む任意の値型を指定できますが、参照型は指定できません。  
  
 Null 許容型を使用するときの例として、通常のブール値変数が、true と false の 2 つの値をどのように持つことができるかを考えてみましょう。 この変数には、"未定義" を示す値はありません。 多くのプログラミング アプリケーションの中でも特にデータベース操作では、変数が未定義の状態で現れることがあります。 たとえば、データベース フィールドには、true や false の値が入力されている場合がありますが、値がまったく入力されていない場合もあります。 また、参照型に `null` を設定すると、その型が初期化されていないことを示すことができます。  
  
 このような違いから、状態情報を格納する変数を追加したり、特別な値を使用したりするような余分なプログラミング作業が生じることがあります。 C# では、Null 許容型修飾子により、未定義の値を示す値型変数を作成できます。  
  
## <a name="examples-of-nullable-types"></a>Null 許容型の例  
 Null 許容型の基底の型には、任意の値型を使用できます。 例:  
  
 [!code-csharp[csProgGuideTypes#4](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_1.cs)]  
  
## <a name="the-members-of-nullable-types"></a>Null 許容型のメンバー  
 Null 許容型の各インスタンスには、次のような 2 つのパブリックな読み取り専用プロパティがあります。  
  
-   `HasValue`  
  
     `HasValue` は `bool` 型です。 変数が null 以外の値を格納している場合、このプロパティには `true` が設定されます。  
  
-   `Value`  
  
     `Value` は、基になっている型と同じ型です。 `HasValue` が `true` の場合、`Value` には意味のある値が含まれています。 `HasValue` が `false` の場合、`Value` にアクセスすると、<xref:System.InvalidOperationException> がスローされます。  
  
 次の例では、`HasValue` メンバーを使用して、値を表示する前に、変数に値が格納されているかどうかをテストします。  
  
 [!code-csharp[csProgGuideTypes#5](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_2.cs)]  
  
 値のテストは、次の例のように行うこともできます。  
  
 [!code-csharp[csProgGuideTypes#6](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_3.cs)]  
  
## <a name="explicit-conversions"></a>明示的変換  
 Null 許容型は、キャストを明示的に使用するか、または `Value` プロパティを使用して通常の型にキャストできます。 例:  
  
 [!code-csharp[csProgGuideTypes#7](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_4.cs)]  
  
 2 つのデータ型の間でユーザー定義の変換を定義している場合は、これらのデータ型の Null 許容バージョンを使用して、同じユーザー定義変換を実行することもできます。  
  
## <a name="implicit-conversions"></a>暗黙の型変換  
 Null 許容型の変数には、次の例のように `null` キーワードを使用して null に設定できます。  
  
 [!code-csharp[csProgGuideTypes#8](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_5.cs)]  
  
 通常の型から null 許容型への変換は暗黙的です。  
  
 [!code-csharp[csProgGuideTypes#9](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_6.cs)]  
  
## <a name="operators"></a>演算子  
 値型向けに存在している定義済みの単項演算子、2 項演算子およびすべてのユーザー定義演算子は、Null 許容型でも使用できます。 これらの演算子は、オペランドが null の場合は null 値を生成し、null 以外の場合は、含まれている値に基づいて結果を算出します。 例:  
  
 [!code-csharp[csProgGuideTypes#10](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_7.cs)]  
  
 2 つの null 許容型を比較したときに、一方の null 許容型の値が null でもう一方がそれ以外の場合は、`!=` (等しくない) を除くすべての比較が `false` と評価されます。 ある比較から返される結果が `false` であっても、逆のケースから返される結果が `true` とは限らない点が重要です。 次の例では、10 は null より大きくも小さくも等しくもありません。 `num1 != num2` のみが `true` と評価されます。  
  
 [!code-csharp[csProgGuideTypes#11](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_8.cs)]  
  
 どちらも null である 2 つの null 許容型を等価比較すると、結果は `true` と評価されます。  
  
## <a name="the--operator"></a>?? 演算子  
 `??` 演算子は、Null 許容型が Null 許容型以外の型に割り当てられているときに返す既定値を定義します。  
  
 [!code-csharp[csProgGuideTypes#12](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_9.cs)]  
  
 この演算子は、複数の Null 許容型で使用することもできます。 例:  
  
 [!code-csharp[csProgGuideTypes#13](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_10.cs)]  
  
## <a name="the-bool-type"></a>bool? 型  
 Null 許容 `bool?` 型は、[true](../../../csharp/language-reference/keywords/true.md)、[false](../../../csharp/language-reference/keywords/false.md)、[null](../../../csharp/language-reference/keywords/null.md) の 3 つの異なる値を格納できます。 bool? から bool にキャストする方法については、「[方法: bool? から bool に安全にキャストする](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md)」を参照してください。  
  
 Null 許容ブール値は、SQL で使用するブール値変数型と似ています。 `&` 演算子と `|` 演算子によって生成される結果が SQL の 3 値のブール型と一致するようにするには、次の定義済みの演算子を指定します。  
  
 `bool? operator &(bool? x, bool? y)`  
  
 `bool? operator |(bool? x, bool? y)`  
  
 これらの演算子の結果を以下の表に示します。  
  
|X|y|x&y|x&#124;y|  
|-------|-------|---------|--------------|  
|true|TRUE|TRUE|TRUE|  
|TRUE|false|false|TRUE|  
|TRUE|null|null|TRUE|  
|false|TRUE|false|TRUE|  
|false|false|false|false|  
|false|null|false|null|  
|null|TRUE|null|TRUE|  
|null|false|false|null|  
|null|null|null|null|  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [Null 許容型](../../../csharp/programming-guide/nullable-types/index.md)  
 [Null 許容型のボックス化](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
 [null 許容値型](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)

---
title: "Null 許容型の使用 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "null 許容型 [C#], null 許容型の概要"
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
caps.latest.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 31
---
# Null 許容型の使用 (C# プログラミング ガイド)
Null 許容型は、基底の型のすべての値に加えて、[null](../../../csharp/language-reference/keywords/null.md) 値を表すことができます。  Null 許容型は、次のいずれかの形式で宣言します。  
  
 `System.Nullable<T> variable`  
  
 または  
  
 `T?  variable`  
  
 `T` は、Null 許容型の基底の型です。  `T` には、`struct` を含む任意の値型を指定できますが、参照型は指定できません。  
  
 Null 許容型を使用するときの例として、通常のブール型変数が、true と false の 2 つの値をどのように持つことができるかを考えてみましょう。  この変数には、"未定義" を示す値はありません。  多くのプログラミング アプリケーションの中でも特にデータベース操作では、変数が未定義の状態で現れることがあります。  たとえば、データベース フィールドには、true や false の値が入力されている場合がありますが、値が入力されていない場合もあります。  また、参照型に `null` を設定すると、その型が初期化されていないことを示すことができます。  
  
 このような違いから、ステータス情報を格納する変数を追加したり、特別な値を使用したりするような余分なプログラミング作業が生じることがあります。  C\# では、Null 許容型修飾子により、未定義の値を示す値型変数を作成できます。  
  
## Null 許容型の例  
 Null 許容型の基底の型には、任意の値型を使用できます。  次に例を示します。  
  
 [!code-cs[csProgGuideTypes#4](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_1.cs)]  
  
## Null 許容型のメンバー  
 Null 許容型の各インスタンスには、次のような読み取り専用の 2 つのパブリック プロパティがあります。  
  
-   `HasValue`  
  
     `HasValue` は `bool` 型です。  変数が null 以外の値を格納している場合、このプロパティには `true` が設定されます。  
  
-   `Value`  
  
     `Value` は、基底の型と同じ型です。  `HasValue` が `true` の場合、`Value` は、有意な値を格納しています。  `HasValue` が `false` の場合、`Value` にアクセスすると、<xref:System.InvalidOperationException> がスローされます。  
  
 次の例では、`HasValue` メンバーを使用して、値を表示する前に、変数に値が格納されているかどうかをテストします。  
  
 [!code-cs[csProgGuideTypes#5](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_2.cs)]  
  
 値のテストは、次の例のように行うこともできます。  
  
 [!code-cs[csProgGuideTypes#6](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_3.cs)]  
  
## 明示的な変換  
 Null 許容型は、キャストを明示的に使用するか、または `Value` プロパティを使用して通常の型にキャストできます。  次に例を示します。  
  
 [!code-cs[csProgGuideTypes#7](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_4.cs)]  
  
 2 つのデータ型の間でユーザー定義変換を定義している場合は、これらのデータ型の Null 許容バージョンを使用して、同じユーザー定義変換を実行することもできます。  
  
## 暗黙の型変換  
 Null 許容型の変数には、次の例のように `null` キーワードを使用して null に設定できます。  
  
 [!code-cs[csProgGuideTypes#8](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_5.cs)]  
  
 通常の型から Null 許容型への変換は暗黙的です。  
  
 [!code-cs[csProgGuideTypes#9](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_6.cs)]  
  
## 演算子  
 定義済みの単項演算子と二項演算子およびユーザー定義演算子は、いずれも値型を対象にしていますが、Null 許容型でも使用できます。  これらの演算子は、オペランドが null の場合は null 値を生成し、null 以外の場合は、包含されている値に基づいて結果を算出します。  次に例を示します。  
  
 [!code-cs[csProgGuideTypes#10](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_7.cs)]  
  
 2 つの null 許容型を比較したときに、一方の null 許容型の値が null でもう一方がそれ以外の場合は、`!=` \(等しくない\) を除くすべての比較が `false` と評価されます。  ある比較から返される結果が `false` であっても、逆のケースから返される結果が `true` とは限りません。  次の例では、10 は null より大きくも小さくも等しくもありません。  `num1 != num2` のみが `true` です。  
  
 [!code-cs[csProgGuideTypes#11](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_8.cs)]  
  
 どちらも null である 2 つの null 許容型を等価比較すると、結果は `true` になります。  
  
## ?? \[演算子\]  
 `??` 演算子は、Null 許容型が Null 許容型以外の型に割り当てられているときに返す既定値を定義します。  
  
 [!code-cs[csProgGuideTypes#12](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_9.cs)]  
  
 この演算子は、複数の Null 許容型で使用することもできます。  次に例を示します。  
  
 [!code-cs[csProgGuideTypes#13](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_10.cs)]  
  
## bool?type  
 Null 許容 `bool?` 型は、[true](../../../csharp/language-reference/keywords/true.md)、[false](../../../csharp/language-reference/keywords/false.md)、[null](../../../csharp/language-reference/keywords/null.md) の 3 つの異なる値を格納できます。  bool? から bool にキャストする方法については、  「[方法: bool? から bool に安全にキャストする](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md)」を参照してください。  
  
 Null 許容ブール型は、SQL で使用するブール変数型と同じです。  `&` 演算子によって生成される結果が SQL の 3 値のブール型と一致するようにするには、  `|` 次の定義済みの演算子を指定します。  
  
 `bool?  operator &(bool?  x, bool?  y)`  
  
 `bool?  operator |(bool?  x, bool?  y)`  
  
 これらの演算子の結果を以下の表に示します。  
  
|x|y|x&y|x&#124;y|  
|-------|-------|---------|--------------|  
|true|true|true|true|  
|true|false|false|true|  
|true|null|null|true|  
|false|true|false|true|  
|false|false|false|false|  
|false|null|false|null|  
|null|true|null|true|  
|null|false|false|null|  
|null|null|null|null|  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [null 許容型](../../../csharp/programming-guide/nullable-types/index.md)   
 [Null 許容型のボックス化](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)   
 [Nullable Value Types](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
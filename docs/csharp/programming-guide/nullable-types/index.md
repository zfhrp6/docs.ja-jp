---
title: Null 許容型 (C# プログラミング ガイド)
ms.date: 05/15/2017
helpviewer_keywords:
- nullable types [C#]
- C# language, nullable types
- types [C#], nullable
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
ms.openlocfilehash: 64b326b82cd022ed6590a232546690e2ec2a5c78
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105489"
---
# <a name="nullable-types-c-programming-guide"></a>Null 許容型 (C# プログラミング ガイド)
Null 許容型は、<xref:System.Nullable%601?displayProperty=nameWithType> 構造体のインスタンスです。 Null 許容型は、基になる値型の適切な範囲の値だけでなく、`null` 値も表すことができます。 たとえば、`Nullable<Int32>` ("Null 許容の Int32" と読みます) には、-2147483648 ～ 2147483647 の範囲の任意の値または `null` 値を割り当てることができます。 `Nullable<bool>` には、[true](../../../csharp/language-reference/keywords/true.md)、[false](../../../csharp/language-reference/keywords/false.md)、または [null](../../../csharp/language-reference/keywords/null.md) の値を割り当てることができます。 数値型と Boolean 型に `null` を割り当てる機能は、値が割り当てられていない可能性がある要素を含むデータベースとその他のデータ型を処理するときに特に役に立ちます。 たとえば、データベースの Boolean フィールドには、値 `true` または `false` が格納されている可能性がありますが、未定義である可能性もあります。 
  
[!code-csharp[nullable-types](../../../../samples/snippets/csharp/programming-guide/nullable-types/nullable-ex1.cs)]  
  
その他の例については、「[Null 許容型の使用](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)」を参照してください  
  
## <a name="nullable-types-overview"></a>Null 許容型の概要  
 Null 許容型には次の特性があります。  
  
-   Null 許容型は、`null`値を割り当てることができる、値型の変数を表します。 参照型に基づいた Null 許容型は作成できません  (参照型は既に `null` 値をサポートしています)。  
  
-   構文 `T?` は、<xref:System.Nullable%601> の省略表現です。ここで、`T` は値型です。 この 2 つの形式は同義であり、どちらでも使用できます。  
  
-   Null 許容型に値を割り当てる方法は、通常の値型の場合と同じです。たとえば、`int? x = 10;` や `double? d = 4.108;` と指定します。 Null 許容型には、値 `null` も割り当てることができます。たとえば、`int? x = null;` と指定します。  
  
-   割り当てられた値、または値が `null` の場合に基になる型の既定値を返すには、<xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=nameWithType> メソッドを使用します。たとえば、`int j = x.GetValueOrDefault();` と指定します。  
  
-   null かどうかを確認して値を取得するには、<xref:System.Nullable%601.HasValue%2A> と <xref:System.Nullable%601.Value%2A> の読み取り専用プロパティを使用します。たとえば、`if(x.HasValue) j = x.Value;` と指定します。  
  
    -   `HasValue` プロパティは、変数に値が含まれる場合は `true` を返し、`null` の場合は `false` を返します。  
  
    -   `Value` プロパティは、値が割り当てられていれば、その値を返します。 それ以外の場合は、<xref:System.InvalidOperationException?displayProperty=nameWithType> がスローされます。  
  
    -   `HasValue` の既定値は `false` です。 `Value`プロパティには既定値はありません。  
  
    -   Null 許容型では `==` 演算子と `!=` 演算子も使用できます。たとえば、`if (x != null) y = x;` のように指定します。  
  
-   現在の値が `null` である Null 許容型が Null 許容型以外の型に割り当てられるときに適用される既定値を割り当てるには、`??` 演算子を使用します。たとえば、`int? x = null; int y = x ?? -1;` と指定します。  
  
-   入れ子になった Null 許容型は許可されません。 次の行はコンパイルされません。`Nullable<Nullable<int>> n;`  
  
## <a name="related-sections"></a>関連項目  
 詳細情報  
  
-   [Null 許容型の使用](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
-   [Null 許容型のボックス化](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
  
-   [??演算子](../../../csharp/language-reference/operators/null-coalescing-operator.md)  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Nullable>  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C#](../../../csharp/index.md)  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [What Exactly Does 'Lifted' mean? ('Lifted' の正確な意味)](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)

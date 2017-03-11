---
title: "null 許容型 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 言語, null 許容型"
  - "null 許容型 [C#]"
  - "型 [C#], null 許容"
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
caps.latest.revision: 44
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 44
---
# null 許容型 (C# プログラミング ガイド)
null 許容型は、<xref:System.Nullable%601?displayProperty=fullName> 構造体のインスタンスです。  null 許容型は、基礎となる値型の正しい範囲の値だけでなく、`null` 値も表すことができます。  たとえば、`Nullable<Int32>` \("Int32 の Nullable" と読みます\) には、\-2147483648 から 2147483647 の任意の値、または `null` 値を割り当てることができます。  `Nullable<bool>` には、[true](../../../csharp/language-reference/keywords/true.md)、[false](../../../csharp/language-reference/keywords/false.md)、または [null](../../../csharp/language-reference/keywords/null.md) の値を割り当てることができます。  数値型と Boolean 型に `null` を割り当てる機能が便利なのは、値を割り当てられていない可能性がある要素を含むデータベースや他のデータ型を処理するときです。  たとえば、データベースの Boolean フィールドには、値 `true` または `false` を格納するか、未定義にすることが可能です。  
  
 [!code-cs[csProgGuideTypes#3](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/index_1.cs)]  
  
 この例は次の出力を表示します。  
  
 `num = Null`  
  
 `Nullable object must have a value.`  
  
 その他の例については、「[Null 許容型の使用](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)」を参照してください。  
  
## null 許容型の概要  
 null 許容型には次の特性があります。  
  
-   null 許容型は、`null` の値を割り当てることができる、値型の変数を表します。  参照型に基づいた null 許容型は作成できません   \(参照型では `null` 値が既にサポートされています\)。  
  
-   構文 `T?` は、<xref:System.Nullable%601> の省略表現です。ここで、`T` は値型です。  この 2 つの形式はどちらでも使用できます。  
  
-   null 許容型に値を割り当てる方法は、`int? x = 10;`  や  `double? d = 4.108` など、通常の値型の場合と同様です。  null 許容型には、`int? x = null` のように、`null` 値も割り当てることができます。  
  
-   値が `null` である場合、割り当てられた値または基礎となる型の既定値を返すには、<xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=fullName> メソッドを使用します。たとえば、 `int j = x.GetValueOrDefault();` と指定します。  
  
-   null をテストし値を取得するには、次の例に示すように、<xref:System.Nullable%601.HasValue%2A> と <xref:System.Nullable%601.Value%2A> の読み取り専用プロパティを使用します。たとえば、`if(x.HasValue) j = x.Value;` と指定します。  
  
    -   `HasValue` プロパティは、変数に値が含まれる場合は `true` を返し、`null` の場合は `false` を返します。  
  
    -   `Value` プロパティは、値が割り当てられている場合はその値を返します。  それ以外の場合は、<xref:System.InvalidOperationException?displayProperty=fullName> がスローされます。  
  
    -   `HasValue` の既定値は `false` です。  `Value` プロパティには既定値がありません。  
  
    -   null 許容型では、`if (x != null) y = x;` のように、`==` 演算子と `!=` 演算子を使用することもできます。  
  
-   現在の値が `null` である null 許容型を、null 非許容型に割り当てる場合、適用される既定値を割り当てるには、`??` 演算子を使用します。たとえば、`int? x = null; int y = x ?? -1;` と指定します。  
  
-   入れ子になった null 許容型は許可されていません。  `Nullable<Nullable<int>> n;` の行はコンパイルされません。  
  
## 関連項目  
 詳細情報  
  
-   [Null 許容型の使用](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
-   [Null 許容型のボックス化](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
  
-   [?? 演算子](../../../csharp/language-reference/operators/null-conditional-operator.md)  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 <xref:System.Nullable>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\#](../../../csharp/csharp.md)   
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [数が正確に「」持ち上げられた平均か。](http://go.microsoft.com/fwlink/?LinkId=112382)
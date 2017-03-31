---
title: "データ型の変換 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 922e2f26c5f8ded260644e8effa043b03b721020
ms.lasthandoff: 03/13/2017

---
# <a name="converting-data-types-c"></a>データ型の変換 (C#)
変換メソッドは、入力オブジェクトの型を変更します。  
  
 LINQ クエリの変換操作は、さまざまなアプリケーションで役に立ちます。 次にいくつかの例を示します。  
  
-   <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName> メソッドは、標準クエリ演算子の型のカスタム実装を隠すために使用できます。  
  
-   <xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName> メソッドは、LINQ クエリのパラメーター化されていないコレクションを有効にするために使用できます。  
  
-   <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName> メソッド、<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName> メソッド、<xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName> メソッド、<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName> メソッドは、クエリが列挙されるまで延期することなく、即時クエリ実行を強制するために使用できます。  
  
## <a name="methods"></a>メソッド  
 次の表には、データ型の変換を実行する標準クエリ演算子メソッドの一覧が示されています。  
  
 名前が "As" で始まるこの表の変換メソッドは、ソース コレクションの静的型を変更しますが、ソース コレクションを列挙しません。 名前が "To" で始まるメソッドは、ソース コレクションを列挙し、各項目を対応するコレクション型に変換します。  
  
|メソッド名|説明|C# のクエリ式の構文|説明|  
|-----------------|-----------------|---------------------------------|----------------------|  
|AsEnumerable|<xref:System.Collections.Generic.IEnumerable%601> として型指定された入力を返します。|該当なし。|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName>|  
|AsQueryable|(ジェネリック) <xref:System.Collections.IEnumerable> を (ジェネリック) <xref:System.Linq.IQueryable> に変換します。|該当なし。|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName>|  
|Cast|コレクションの要素を指定した型にキャストします。|明示的に型指定された範囲変数を使用します。 例:<br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName>|  
|OfType|指定した型にキャストできるかどうかに応じて値をフィルター処理します。|該当なし。|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName>|  
|ToArray|コレクションを配列に変換します。 このメソッドはクエリの実行を強制します。|該当なし。|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>|  
|ToDictionary|キー セレクター関数に基づいて、<xref:System.Collections.Generic.Dictionary%602> に要素を変換します。 このメソッドはクエリの実行を強制します。|該当なし。|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>|  
|ToList|コレクションを <xref:System.Collections.Generic.List%601> に変換します。 このメソッドはクエリの実行を強制します。|該当なし。|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>|  
|ToLookup|キー セレクター関数に基づいて、<xref:System.Linq.Lookup%602> (一対多の辞書) に要素を変換します。 このメソッドはクエリの実行を強制します。|該当なし。|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-example"></a>クエリ式の構文例  
 次のコード例では、サブタイプでのみ使用できるメンバーにアクセスする前に、明示的に型指定された範囲変数を使用して、型をそのサブタイプにキャストしています。  
  
```csharp  
class Plant  
{  
    public string Name { get; set; }  
}  
  
class CarnivorousPlant : Plant  
{  
    public string TrapType { get; set; }  
}  
  
static void Cast()  
{  
    Plant[] plants = new Plant[] {  
        new CarnivorousPlant { Name = "Venus Fly Trap", TrapType = "Snap Trap" },  
        new CarnivorousPlant { Name = "Pitcher Plant", TrapType = "Pitfall Trap" },  
        new CarnivorousPlant { Name = "Sundew", TrapType = "Flypaper Trap" },  
        new CarnivorousPlant { Name = "Waterwheel Plant", TrapType = "Snap Trap" }  
    };  
  
    var query = from CarnivorousPlant cPlant in plants  
                where cPlant.TrapType == "Snap Trap"  
                select cPlant;  
  
    foreach (Plant plant in query)  
        Console.WriteLine(plant.Name);  
  
    /* This code produces the following output:  
  
        Venus Fly Trap  
        Waterwheel Plant  
    */  
}  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq>   
 [標準クエリ演算子の概要 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [from 句](../../../../csharp/language-reference/keywords/from-clause.md)   
 [LINQ クエリ式](../../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [方法: LINQ を使用して ArrayList を照会する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)

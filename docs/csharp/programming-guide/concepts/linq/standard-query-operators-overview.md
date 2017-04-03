---
title: "標準クエリ演算子の概要 (C#) | Microsoft Docs"
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
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
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
ms.openlocfilehash: 5b03c85a298b3864a91a7052ca80cf3714ba98fe
ms.lasthandoff: 03/13/2017

---
# <a name="standard-query-operators-overview-c"></a>標準クエリ演算子の概要 (C#)
"*標準クエリ演算子*" は、LINQ パターンを形成するメソッドです。 ほとんどの場合、そのメソッドの操作の対象はシーケンスです。シーケンスとは、型が <xref:System.Collections.Generic.IEnumerable%601> インターフェイスまたは <xref:System.Linq.IQueryable%601> インターフェイスを実装しているオブジェクトのことです。 標準クエリ演算子には、フィルター処理、プロジェクション、集計、並べ替えなどのクエリ機能が用意されています。  
  
 LINQ 標準クエリ演算子には 2 つのセットがあります。1 つは <xref:System.Collections.Generic.IEnumerable%601> 型のオブジェクトを操作する演算子、もう 1 つは <xref:System.Linq.IQueryable%601> 型のオブジェクトを操作する演算子です。 各セットを構成するメソッドは、それぞれ <xref:System.Linq.Enumerable> クラスと <xref:System.Linq.Queryable> クラスの静的メンバーで、 そのメソッドの操作対象である型の "*拡張メソッド*" として定義されています。 つまり、静的メソッド構文またはインスタンス メソッド構文のいずれかを使用して呼び出すことができます。  
  
 また、標準クエリ演算子には、<xref:System.Collections.Generic.IEnumerable%601> または <xref:System.Linq.IQueryable%601> をベースにした型以外の型を操作するメソッドがいくつかあります。 <xref:System.Linq.Enumerable> 型ではこのようなメソッドが 2 つ定義されており、両メソッドとも <xref:System.Collections.IEnumerable> 型のオブジェクトを操作します。 その 1 つは <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> メソッドで、もう 1 つは <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29> メソッドです。これらのメソッドを使用すると、パラメーター付きでない (非ジェネリック) コレクションに対して、LINQ パターンでクエリを実行できます。 これを行うには、厳密に型指定されたオブジェクトのコレクションを作成します。 <xref:System.Linq.Queryable> クラスでも、同様のメソッドが 2 つ定義されています。1 つは <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> メソッド、もう 1 つは <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29> メソッドで、両方とも <xref:System.Linq.Queryable> 型のオブジェクトを操作します。  
  
 標準クエリ演算子の実行のタイミングは、シングルトン値を返すか、値のシーケンスを返すかで異なります。 シングルトン値を返すメソッド (<xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Sum%2A> など) は、直ちに実行されます。 シーケンスを返すメソッドは、クエリの実行を遅延させ、列挙可能なオブジェクトを返します。  
  
 メモリ内コレクションを操作するメソッド、つまり <xref:System.Collections.Generic.IEnumerable%601> を拡張するメソッドの場合、返される列挙可能なオブジェクトは、メソッドに渡された引数をキャプチャします。 オブジェクトが列挙されると、クエリ演算子のロジックが使用され、クエリ結果が返されます。  
  
 一方、<xref:System.Linq.IQueryable%601> を拡張するメソッドはクエリ動作を実装しませんが、実行されるクエリを表す式ツリーを作成します。 クエリ処理は、ソース <xref:System.Linq.IQueryable%601> オブジェクトによって行われます。  
  
 クエリ メソッドの呼び出しは 1 回のクエリにまとめてチェーン化できるため、クエリが複雑になることがあります。  
  
 次のコード例は、標準クエリ演算子を使用してシーケンスに関する情報を取得する方法を示しています。  
  
```csharp  
string sentence = "the quick brown fox jumps over the lazy dog";  
// Split the string into individual words to create a collection.  
string[] words = sentence.Split(' ');  
  
// Using query expression syntax.  
var query = from word in words  
            group word.ToUpper() by word.Length into gr  
            orderby gr.Key  
            select new { Length = gr.Key, Words = gr };  
  
// Using method-based query syntax.  
var query2 = words.  
    GroupBy(w => w.Length, w => w.ToUpper()).  
    Select(g => new { Length = g.Key, Words = g }).  
    OrderBy(o => o.Length);  
  
foreach (var obj in query)  
{  
    Console.WriteLine("Words of length {0}:", obj.Length);  
    foreach (string word in obj.Words)  
        Console.WriteLine(word);  
}  
  
// This code example produces the following output:  
//  
// Words of length 3:  
// THE  
// FOX  
// THE  
// DOG  
// Words of length 4:  
// OVER  
// LAZY  
// Words of length 5:  
// QUICK  
// BROWN  
// JUMPS   
```  
  
## <a name="query-expression-syntax"></a>クエリ式の構文  
 頻繁に使用される標準クエリ演算子の中には、C# および Visual Basic 言語専用のキーワード構文が使用されているものがあります。こうした構文では、標準クエリ演算子を、"*クエリ**式*" の一部として呼び出すことができます。 専用キーワードおよびそれに対応する構文が使用されている標準クエリ演算子の詳細については、「[標準クエリ演算子のクエリ式構文 (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)」を参照してください。  
  
## <a name="extending-the-standard-query-operators"></a>標準クエリ演算子の拡張  
 標準クエリ演算子のセットを拡張するには、対象のドメインまたはテクノロジに適したドメイン固有のメソッドを作成します。 また、標準クエリ演算子を、リモート評価、クエリ変換、最適化などの追加サービスが用意されている独自の実装で置き換えることもできます。 例については、「<xref:System.Linq.Enumerable.AsEnumerable%2A>」を参照してください。  
  
## <a name="related-sections"></a>関連項目  
 次のリンクをクリックすると、さまざまな標準クエリ演算子に関する追加情報を機能別に確認することができます。  
  
 [データの並べ替え (C#)](../../../../csharp/programming-guide/concepts/linq/sorting-data.md)  
  
 [セット操作 (C#)](../../../../csharp/programming-guide/concepts/linq/set-operations.md)  
  
 [データのフィルター処理 (C#)](../../../../csharp/programming-guide/concepts/linq/filtering-data.md)  
  
 [量指定子操作 (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [射影操作 (C#)](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)  
  
 [データのパーティション分割](../../../../csharp/programming-guide/concepts/linq/partitioning-data.md)  
  
 [結合演算 (C#)](../../../../csharp/programming-guide/concepts/linq/join-operations.md)  
  
 [データのグループ化 (C#)](../../../../csharp/programming-guide/concepts/linq/grouping-data.md)  
  
 [生成操作 (C#)](../../../../csharp/programming-guide/concepts/linq/generation-operations.md)  
  
 [等価演算 (C#)](../../../../csharp/programming-guide/concepts/linq/equality-operations.md)  
  
 [要素操作 (C#)](../../../../csharp/programming-guide/concepts/linq/element-operations.md)  
  
 [データ型の変換 (C#)](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md)  
  
 [連結演算 (C#)](../../../../csharp/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [集計操作 (C#)](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq.Enumerable>   
 <xref:System.Linq.Queryable>   
 [LINQ クエリの概要 (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)   
 [標準クエリ演算子のクエリ式構文 (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)   
 [実行方法による標準クエリ演算子の分類 (C#)](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)   
 [拡張メソッド](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)

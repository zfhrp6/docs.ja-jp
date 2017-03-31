---
title: "データのフィルター処理 (C#) | Microsoft Docs"
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
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1d0efd313a670348a65870c348dd2ef5e079e5d0
ms.lasthandoff: 03/13/2017

---
# <a name="filtering-data-c"></a>データのフィルター処理 (C#)
フィルター処理とは、特定の条件を満たす要素のみが含まれるように結果セットを限定する操作のことです。 選択とも呼ばれます。  
  
 次の図は、文字のシーケンスをフィルター処理した結果を示したものです。 フィルター処理操作の述語では、文字が "A" でなければならないことが指定されています。  
  
 ![LINQ フィルター処理操作](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")  
  
 次のセクションでは、選択を実行する標準クエリ演算子メソッドの一覧を示します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド名|説明|C# のクエリ式の構文|説明|  
|-----------------|-----------------|---------------------------------|----------------------|  
|OfType|指定した型にキャストできるかどうかにより、値を選択します。|該当なし。|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName>|  
|Where|述語関数に基づいて値を選択します。|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-example"></a>クエリ式の構文例  
 次の例では、`where` 句を使って、配列から特定の長さを持つ文字列をフィルター処理します。  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            where word.Length == 3  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
*/  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq>   
 [標準クエリ演算子の概要 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [where 句](../../../../csharp/language-reference/keywords/where-clause.md)   
 [方法: 実行時に述語フィルターを動的に指定する](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)   
 [方法: リフレクションを使用してアセンブリのメタデータを照会する (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)   
 [方法: 指定された属性または名前のファイルを照会する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)   
 [方法: 任意の単語またはフィールドを基準にテキスト データの並べ替えまたはフィルター処理を実行する (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

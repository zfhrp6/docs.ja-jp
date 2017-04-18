---
title: "クエリ式の null 値の処理"
description: "クエリ式の null 値を処理する方法。"
keywords: ".NET、.NET Core、C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 14b64bf8d3590f4f7dc3d1b00cb50d0bc421d9bc
ms.lasthandoff: 03/13/2017

---
# <a name="handle-null-values-in-query-expressions"></a>クエリ式の null 値の処理

この例では、ソース コレクション内の可能な null 値を処理する方法を示します。 <xref:System.Collections.Generic.IEnumerable%601> などのオブジェクト コレクションには、値が [null](../language-reference/keywords/null.md) である要素を格納できます。 ソース コレクションが null であるか null の値を持つ要素を含み、クエリで null 値を処理しない場合、クエリを実行すると <xref:System.NullReferenceException> がスローされます。  
  
## <a name="example"></a>例

 次の例に示すように、null 参照の例外を回避する防御的なコーディングをすることができます。  
  
 [!code-cs[csProgGuideLINQ#82](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]  
  
 前の例では、`where` 句によって、カテゴリ シーケンス内のすべての null 要素が除外されます。 この手法は、join 句での null チェックに依存しません。 この例の null 条件式が機能する理由は、`Products.CategoryID` が `int?` 型 (`Nullable<int>` の短縮形) であるためです。  
  
## <a name="example"></a>例

 join 句で、比較キーの一方だけが null 許容値型である場合、クエリ式でもう一方のキーを null 許容型にキャストできます。 次の例では、`EmployeeID` は `int?` 型の値を含む列であるとします。  
  
 [!code-cs[csProgGuideLINQ#83](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Nullable%601>   
 [LINQ クエリ式](index.md)   
 [Null 許容型](../programming-guide/nullable-types/index.md)

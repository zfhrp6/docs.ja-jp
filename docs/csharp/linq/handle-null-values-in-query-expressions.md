---
title: クエリ式の null 値の処理
description: クエリ式の null 値を処理する方法。
ms.date: 12/1/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: ecd174462ef51a6dd7b7696abb9e111fc32d9ec7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="handle-null-values-in-query-expressions"></a>クエリ式の null 値の処理

この例では、ソース コレクション内の可能な null 値を処理する方法を示します。 <xref:System.Collections.Generic.IEnumerable%601> のようなオブジェクト コレクションには、値が [null](../language-reference/keywords/null.md) の要素を含めることができます。 ソース コレクションが null であるか null の値を持つ要素を含み、クエリで null 値を処理しない場合、クエリを実行すると <xref:System.NullReferenceException> がスローされます。  
  
## <a name="example"></a>例

 次の例に示すように、null 参照の例外を回避する防御的なコーディングをすることができます。  
  
 [!code-csharp[csProgGuideLINQ#82](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]  
  
 前の例では、`where` 句によって、カテゴリ シーケンス内のすべての null 要素が除外されます。 この手法は、join 句での null チェックに依存しません。 この例の null 条件式が機能する理由は、`Products.CategoryID` が `int?` 型 (`Nullable<int>` の短縮形) であるためです。  
  
## <a name="example"></a>例

 join 句で、比較キーの一方だけが null 許容値型である場合、クエリ式でもう一方のキーを null 許容型にキャストできます。 次の例では、`EmployeeID` は `int?` 型の値を含む列であるとします。  
  
 [!code-csharp[csProgGuideLINQ#83](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Nullable%601>  
 [LINQ クエリ式](index.md)  
 [Null 許容型](../programming-guide/nullable-types/index.md)

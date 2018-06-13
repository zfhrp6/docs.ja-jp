---
title: where 句 (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: bc040e17f5c612b9fc43a9ef24fb6f15f0942b8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284304"
---
# <a name="where-clause-c-reference"></a>where 句 (C# リファレンス)
`where` 句をクエリ式で使用して、クエリ式で返されるデータ ソースの要素を指定します。 ブール条件 (*述語*) を (範囲変数で参照される) 各ソース要素に適用し、指定した条件に該当するものを返します。 単一のクエリ式に複数の `where` 句を含めることができ、単一の句に複数の述語部分式を含めることができます。  
  
## <a name="example"></a>例  
 次の例では、`where` 句で、5 未満の数値を除くすべての数値を除外します。 `where` 句を削除すると、データ ソースのすべての数値が返されます。 式 `num < 5` は、各要素に適用される述語です。  
  
 [!code-csharp[cscsrefQueryKeywords#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_1.cs)]  
  
## <a name="example"></a>例  
 単一の `where` 句内には、[&&](../../../csharp/language-reference/operators/conditional-and-operator.md) および [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) 演算子を使用して、必要な数の述語を指定できます。 次の例のクエリでは、5 未満の偶数のみを選択するために 2 つの述語を指定します。  
  
 [!code-csharp[cscsrefQueryKeywords#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_2.cs)]  
  
## <a name="example"></a>例  
 `where` 句には、ブール値を返す 1 つ以上のメソッドを含めることができます。 次の例の `where` 句では、範囲変数の現在の値が偶数であるか、奇数であるかを判断するためのメソッドを使用します。  
  
 [!code-csharp[cscsrefQueryKeywords#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_3.cs)]  
  
## <a name="remarks"></a>コメント  
 `where` 句はフィルター メカニズムです。 クエリ式のほぼどこにでも指定できますが、最初の句や最後の句にすることはできません。 `where` 句は、ソース要素のフィルター処理をグループ化の前に行うか後に行うかによって、[group](../../../csharp/language-reference/keywords/group-clause.md) 句の前または後に指定できます。  
  
 指定した述語がデータ ソース内の要素に対して有効でない場合は、コンパイル時エラーが発生します。 これは、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] で提供される厳密な型チェックの 1 つの利点です。  
  
 コンパイル時に、`where` キーワードは <xref:System.Linq.Enumerable.Where%2A> 標準クエリ演算子メソッドの呼び出しに変換されます。  
  
## <a name="see-also"></a>参照  
 [クエリ キーワード (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [from 句](../../../csharp/language-reference/keywords/from-clause.md)  
 [select 句](../../../csharp/language-reference/keywords/select-clause.md)  
 [データのフィルター処理](../../programming-guide/concepts/linq/filtering-data.md)  
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [C# の LINQ の概要](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)

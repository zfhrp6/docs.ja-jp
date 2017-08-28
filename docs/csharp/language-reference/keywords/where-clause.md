---
title: "where 句 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- whereclause_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 97d7c16d6bf8048e621141fff52a47907881fd2f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="where-clause-c-reference"></a>where 句 (C# リファレンス)
`where` 句をクエリ式で使用して、クエリ式で返されるデータ ソースの要素を指定します。 ブール条件 (*述語*) を (範囲変数で参照される) 各ソース要素に適用し、指定した条件に該当するものを返します。 単一のクエリ式に複数の `where` 句を含めることができ、単一の句に複数の述語部分式を含めることができます。  
  
## <a name="example"></a>例  
 次の例では、`where` 句で、5 未満の数値を除くすべての数値を除外します。 `where` 句を削除すると、データ ソースのすべての数値が返されます。 式 `num < 5` は、各要素に適用される述語です。  
  
 [!code-cs[cscsrefQueryKeywords#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_1.cs)]  
  
## <a name="example"></a>例  
 単一の `where` 句内には、[&&](../../../csharp/language-reference/operators/conditional-and-operator.md) および [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) 演算子を使用して、必要な数の述語を指定できます。 次の例のクエリでは、5 未満の偶数のみを選択するために 2 つの述語を指定します。  
  
 [!code-cs[cscsrefQueryKeywords#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_2.cs)]  
  
## <a name="example"></a>例  
 `where` 句には、ブール値を返す 1 つ以上のメソッドを含めることができます。 次の例の `where` 句では、範囲変数の現在の値が偶数であるか、奇数であるかを判断するためのメソッドを使用します。  
  
 [!code-cs[cscsrefQueryKeywords#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_3.cs)]  
  
## <a name="remarks"></a>コメント  
 `where` 句はフィルター メカニズムです。 クエリ式のほぼどこにでも指定できますが、最初の句や最後の句にすることはできません。 `where` 句は、ソース要素のフィルター処理をグループ化の前に行うか後に行うかによって、[group](../../../csharp/language-reference/keywords/group-clause.md) 句の前または後に指定できます。  
  
 指定した述語がデータ ソース内の要素に対して有効でない場合は、コンパイル時エラーが発生します。 これは、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] で提供される厳密な型チェックの 1 つの利点です。  
  
 コンパイル時に、`where` キーワードは <xref:System.Linq.Enumerable.Where%2A> 標準クエリ演算子メソッドの呼び出しに変換されます。  
  
## <a name="see-also"></a>関連項目  
 [クエリ キーワード (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [from 句](../../../csharp/language-reference/keywords/from-clause.md)   
 [select 句](../../../csharp/language-reference/keywords/select-clause.md)   
 [データのフィルター処理](http://msdn.microsoft.com/library/cee88d0f-31aa-4c60-9452-cc122ed0057d)   
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [C# の LINQ の概要](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)


---
title: "select 句 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- select_CSharpKeyword
- select
dev_langs:
- CSharp
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
caps.latest.revision: 19
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
ms.openlocfilehash: a505399eb79cbecbefcc53953329279a4abd92f6
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="select-clause-c-reference"></a>select 句 (C# リファレンス)
クエリ式で、`select` 句は、クエリが実行されたときに生成される値の型を指定します。 結果は、以前のすべての句の評価と `select` 句自体の式に基づいています。 クエリ式は、`select` 句または [group](../../../csharp/language-reference/keywords/group-clause.md) 句のいずれかで終了する必要があります。  
  
 次の例は、クエリ式での単純な `select` 句を示したものです。  
  
 [!code-cs[cscsrefQueryKeywords#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_1.cs)]  
  
 `select` 句によって生成されるシーケンスの型は、クエリ変数 `queryHighScores` の型を決定します。 最も簡単なケースでは、`select` 句は、範囲変数だけを指定します。 これにより、返されるシーケンスにデータ ソースと同じ型の要素が含まれます。 詳細については、「[LINQ クエリ操作での型の関係](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)」を参照してください。 ただし、`select` 句は、ソース データを新しい型に変換する (または*投影*する) ための強力なメカニズムも提供します。 詳細については、「[LINQ によるデータ変換 (C#)](../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例は、`select` 句のすべての異なる形式を示しています。 各クエリで、`select` 句と *クエリ変数* (`studentQuery1`、`studentQuery2`など) の型の関係に注意してください。  
  
 [!code-cs[cscsrefQueryKeywords#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_2.cs)]  
  
 前の例の `studentQuery8` に示すように、返されるシーケンスの要素にソース要素のプロパティのサブセットのみを含めることもできます。 返されるシーケンスをできるだけ小さく維持することで、メモリ要件を減らし、クエリの実行の速度を向上させることができます。 これを行うには、`select` 句で匿名型を作成し、オブジェクト初期化子を使用して、ソース要素からの適切なプロパティで初期化します。 これを行う方法の例については、「[オブジェクト初期化子とコレクション初期化子](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)」を参照してください。  
  
## <a name="remarks"></a>コメント  
 コンパイル時に、`select` 句は、<xref:System.Linq.Enumerable.Select%2A> 標準クエリ演算子へのメソッドの呼び出しに変換されます。  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [クエリ キーワード (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [from 句](../../../csharp/language-reference/keywords/from-clause.md)   
 [partial (メソッド) (C# リファレンス)](../../../csharp/language-reference/keywords/partial-method.md)   
 [匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [C# の LINQ の概要](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)


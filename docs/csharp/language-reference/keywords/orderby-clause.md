---
title: orderby 句 (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: 1fd0036e8bd3c838fe92ca27635cd7638d59ef1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="orderby-clause-c-reference"></a>orderby 句 (C# リファレンス)
クエリ式では、`orderby` 句によって返されるシーケンスまたはサブシーケンス (グループ) が昇順または降順で並べ替えられます。 2 番目の並べ替え操作を 1 つ以上実行するために、複数のキーを指定できます。 並べ替えは、要素の型の既定の比較演算子によって実行されます。 既定の並べ替え順序は昇順です。 カスタムの比較演算子を指定することもできます。 ただしこれは、メソッド ベースの構文を使用する場合にのみ使用できます。 詳細については、「[Sorting Data](../../programming-guide/concepts/linq/sorting-data.md)」(データの並べ替え) を参照してください。  
  
## <a name="example"></a>例  
 次の例では、最初のクエリが A から始まるアルファベット順で単語を並べ替え、2 番目のクエリが同じ単語を降順で並べ替えます  (`ascending` キーワードは、既定の並べ替え値で、省略可能です)。  
  
 [!code-csharp[cscsrefQueryKeywords#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_1.cs)]  
  
## <a name="example"></a>例  
 次の例では、学生の姓で最初の並べ替えを実行し、学生の名で 2 番目の並べ替えを実行します。  
  
 [!code-csharp[cscsrefQueryKeywords#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_2.cs)]  
  
## <a name="remarks"></a>コメント  
 コンパイル時に、`orderby` 句は <xref:System.Linq.Enumerable.OrderBy%2A> メソッドの呼び出しに変換されます。 `orderby` 句内の複数のキーは、<xref:System.Linq.Enumerable.ThenBy%2A> メソッドの呼び出しに変換されます。  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [クエリ キーワード (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [group 句](../../../csharp/language-reference/keywords/group-clause.md)  
 [C# の LINQ の概要](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)

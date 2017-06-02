---
title: "group 句 (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- group
- group_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
caps.latest.revision: 24
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 17edc1598b806f073ad93e470dc8764cfeb1e4eb
ms.openlocfilehash: d054a0824e9f072d38c01c2894606c5c492a2481
ms.contentlocale: ja-jp
ms.lasthandoff: 05/22/2017

---
# <a name="group-clause-c-reference"></a>group 句 (C# リファレンス)
`group` 句は、グループのキー値に一致する 0 個以上の項目を含む <xref:System.Linq.IGrouping%602> オブジェクトのシーケンスを返します。 たとえば、各文字列の最初の文字に基づいて文字列のシーケンスをグループ化することができます。 この場合、最初の文字がキーで、型は [char](../../../csharp/language-reference/keywords/char.md) であり、各 <xref:System.Linq.IGrouping%602> オブジェクトの `Key` プロパティに格納されています。 コンパイラは、キーの型を推論します。  
  
 次の例で示すように、クエリ式は `group` 句で終了できます。  
  
 [!code-cs[cscsrefQueryKeywords#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_1.cs)]  
  
 各グループで追加のクエリ操作を実行する場合、[into](../../../csharp/language-reference/keywords/into.md) コンテキスト キーワードを使用して一時的な識別子を指定できます。 `into` を使用する場合、次の抜粋に示すように、クエリを続行し、最終的には `select` ステートメントまたは別の `group` 句でそれを終了する必要があります。  
  
 [!code-cs[cscsrefQueryKeywords#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_2.cs)]  
  
 このトピックの「例」のセクションでは、`into` を含む場合と含まない場合の `group` の使用方法の完全な例があります。  
  
## <a name="enumerating-the-results-of-a-group-query"></a>グループ クエリの結果を列挙する  
 `group` クエリによって生成される <xref:System.Linq.IGrouping%602> オブジェクトは基本的には、リストのリストであるため、各グループのアイテムにアクセスするには、入れ子になった [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ループを使用する必要があります。 外側のループがグループ キーを反復処理し、内側のループがグループ自体の各項目を反復処理します。 グループには、キーがある場合はありますが、要素はありません。 次に、前のコード例でクエリを実行する `foreach` ループを示します。  
  
 [!code-cs[cscsrefQueryKeywords#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_3.cs)]  
  
## <a name="key-types"></a>キーの種類  
 グループ キーは、文字列、組み込みの数値型、またはユーザー定義の名前付きの型または匿名型など、任意の型にすることができます。  
  
### <a name="grouping-by-string"></a>文字列でグループ化する  
 前のコード例では、`char` を使用していました。 姓を完全に指定するなど、簡単に代わりに文字列のキーを指定できます。  
  
 [!code-cs[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_4.cs)]  
  
### <a name="grouping-by-bool"></a>ブールでグループ化する  
 次の例では、結果を 2 つのグループに分割するためのキー用のブール値の用途を示します。 値は `group` 句のサブ式で生成されることに注意してください。  
  
 [!code-cs[cscsrefQueryKeywords#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_5.cs)]  
  
### <a name="grouping-by-numeric-range"></a>数値の範囲でグループ化する  
 次の例では、パーセンタイルの範囲を示す数値のグループ キーを作成する式を使用しています。 `group` 句でメソッドを 2 度呼び出さなくて済むように、メソッド呼び出しの結果を格納する便利な場所として [let](../../../csharp/language-reference/keywords/let-clause.md) を使用できます。 また、0 除算の例外を避けるために、受講者の平均が 0 でないことがコードの `group` 句で確認されています。 クエリ式でメソッドを安全に使用する方法の詳細については、「[方法: クエリ式の例外を処理する](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md)」を参照してください。  
  
 [!code-cs[cscsrefQueryKeywords#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_6.cs)]  
  
### <a name="grouping-by-composite-keys"></a>複合キーでグループ化する  
 1 つ以上のキーを使用して要素をグループ化するには、複合キーを使用します。 複合キーは、キー要素を保持する、匿名型または名前付きの型を使用して作成できます。 次の例では、クラス `Person` が、`surname` と `city` という名前のメンバーで宣言されていると想定しています。 `group` 句により、同じ名前と同じ市の人物のセットごとに、別のグループが作成されます。  
  
```csharp  
group person by new {name = person.surname, city = person.city};  
```  
  
 クエリ変数を別のメソッドに渡す場合には、名前付きの型を使用します。 キーの自動実装プロパティを使用して特殊クラスを作成し、<xref:System.Object.Equals%2A> メソッドと <xref:System.Object.GetHashCode%2A> メソッドをオーバーライドします。 これらのメソッドを厳密にオーバーライドする必要がない構造体を使用することも可能です。 詳細については、「[方法 : 自動実装するプロパティを使用して簡易クラスを実装する](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)」と「[Query for Duplicate Files in a Directory Tree](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)」 (方法: ディレクトリ ツリーで重複するファイルを問い合わせる) を参照してください。 後述のトピックには、名前付きの型を複合キーで使用する方法のコード例があります。  
  
## <a name="example"></a>例  
 次の例では、グループにその他のクエリ ロジックが適用されていない場合、ソース データをグループに並べる標準的なパターンを示します。 これは連結なしのグループ化と呼ばれます。 文字列の配列の要素は、最初の文字でグループ化されます。 クエリの結果は、型 `char` のパブリック `Key` プロパティを含む <xref:System.Linq.IGrouping%602> 型とグループに各項目を含む <xref:System.Collections.Generic.IEnumerable%601> コレクションです。  
  
 `group` 句の結果は、シーケンスのシーケンスです。 そのため、返される各グループ内の各要素にアクセスするには、次の例のように、グループ キーを反復処理するループ内で入れ子になった `foreach` ループを使用します。  
  
 [!code-cs[cscsrefQueryKeywords#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_7.cs)]  
  
## <a name="example"></a>例  
 この例では、作成後に、`into` と共に *continuation* を使用し、グループに追加のロジックを実行する方法を示します。 詳しくは、「[into](../../../csharp/language-reference/keywords/into.md)」をご覧ください。 次の例では、キー値が母音であるものだけを選択するために各グループに問い合せを行います。  
  
 [!code-cs[cscsrefQueryKeywords#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_8.cs)]  
  
## <a name="remarks"></a>コメント  
 コンパイル時に `group` 句が <xref:System.Linq.Enumerable.GroupBy%2A> メソッドの呼び出しに変換されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq.IGrouping%602>   
 <xref:System.Linq.Enumerable.GroupBy%2A>   
 <xref:System.Linq.Enumerable.ThenBy%2A>   
 <xref:System.Linq.Enumerable.ThenByDescending%2A>   
 [クエリ キーワード (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [方法: 入れ子になったグループを作成する](../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md)   
 [方法: クエリ結果をグループ化する](../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md)   
 [方法: グループ化操作でサブクエリを実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)


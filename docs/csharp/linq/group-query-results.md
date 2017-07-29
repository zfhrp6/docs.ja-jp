---
title: "クエリ結果のグループ化"
description: "結果をグループ化する方法です。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1c1639651699afbe5fb768db26b98a9b2d734315
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="group-query-results"></a>クエリ結果のグループ化

グループ化は、LINQ の最も強力な機能の 1 つです。 次の例では、さまざまな方法でデータをグループ化する方法を示します。  
  
-   1 つのプロパティで。  
  
-   文字列プロパティの最初の文字で。  
  
-   計算された数値の範囲で。  
  
-   ブール述語またはその他の式で。  
  
-   複合キーで。  
  
 さらに、最後の 2 つのクエリは、学生の名と姓だけを含む新しい匿名型に結果を射影します。 詳しくは、「[group 句](../language-reference/keywords/group-clause.md)」をご覧ください。  
  
## <a name="example"></a>例  
 このトピックのすべての例では、次のヘルパー クラスとデータ ソースを使います。  
  
 [!code-cs[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]  
  
## <a name="example"></a>例  
 次の例では、要素の 1 つのプロパティをグループ化キーとして使って、ソース要素をグループ化する方法を示します。 この場合、キーは学生の姓である `string` です。 また、キーの部分文字列を使うこともできます。 グループ化操作では、型の既定の等値比較子を使います。  
  
 次のメソッドを `StudentClass` クラスに貼り付けます。 `Main` メソッドの呼び出しステートメントを `sc.GroupBySingleProperty()` に変更します。  
  
 [!code-cs[csProgGuideLINQ#17](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]  
  
## <a name="example"></a>例  
 次の例では、オブジェクトのプロパティ以外の何かをグループ化キーとして使って、ソース要素をグループ化する方法を示します。 この例では、キーは学生の姓の最初の文字です。  
  
 次のメソッドを `StudentClass` クラスに貼り付けます。 `Main` メソッドの呼び出しステートメントを `sc.GroupBySubstring()` に変更します。  
  
 [!code-cs[csProgGuideLINQ#18](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]  
  
## <a name="example"></a>例  
 次の例では、数値範囲をグループ化キーとして使って、ソース要素をグループ化する方法を示します。 クエリは、名と姓および学生が属しているパーセンタイル範囲のみを含む匿名型に、結果を投影します。 匿名型を使っているのは、結果を表示するために完全な `Student` オブジェクトを使う必要がないためです。 `GetPercentile` は、学生の平均スコアに基づいてパーセンタイルを計算するヘルパー関数です。 メソッドは、0 から 10 の間の整数を返します。  
  
 [!code-cs[csProgGuideLINQ#50](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]  
  
 次のメソッドを `StudentClass` クラスに貼り付けます。 `Main` メソッドの呼び出しステートメントを `sc.GroupByRange()` に変更します。  
  
 [!code-cs[csProgGuideLINQ#19](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]  
  
## <a name="example"></a>例  
 次の例では、ブール比較式を使って、ソース要素をグループ化する方法を示します。 この例のブール式は、学生の平均試験スコアが 75 より大きいかどうかをテストします。 前の例と同じように、完全なソース要素が必要ないため、結果を匿名型に投影します。 匿名型のプロパティは `Key` メンバーのプロパティになり、クエリ実行時に名前でアクセスできることに注意してください。  
  
 次のメソッドを `StudentClass` クラスに貼り付けます。 `Main` メソッドの呼び出しステートメントを `sc.GroupByBoolean()` に変更します。  
  
 [!code-cs[csProgGuideLINQ#20](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]  
  
## <a name="example"></a>例  
 次の例では、匿名型を使って、複数の値を含むキーをカプセル化する方法を示します。 この例では、最初のキーの値は学生の姓の最初の文字です。 2 番目のキーの値は、最初の試験での学生のスコアが 85 より高いかどうかを示すブール値です。 キーの任意のプロパティでグループを並べ替えることができます。  
  
 次のメソッドを `StudentClass` クラスに貼り付けます。 `Main` メソッドの呼び出しステートメントを `sc.GroupByCompositeKey()` に変更します。  
  
 [!code-cs[csProgGuideLINQ#21](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq.Enumerable.GroupBy%2A>   
 <xref:System.Linq.IGrouping%602>   
 [LINQ クエリ式](index.md)   
 [group 句](../language-reference/keywords/group-clause.md)   
 [匿名型](../programming-guide/classes-and-structs/anonymous-types.md)   
 [グループ化操作でのサブクエリの実行](perform-a-subquery-on-a-grouping-operation.md)   
 [入れ子になったグループの作成](create-a-nested-group.md)   
 [データのグループ化](../programming-guide/concepts/linq/grouping-data.md)


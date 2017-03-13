---
title: "group 句 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "group"
  - "group_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "group 句 [C#]"
  - "group キーワード [C#]"
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# group 句 (C# リファレンス)
`group` 句は、グループのキー値に一致するゼロ以上のアイテムを含む <xref:System.Linq.IGrouping%602> オブジェクトを返します。  たとえば、各文字列の最初の文字に従って文字列のシーケンスをグループ化できます。  この場合、最初の文字が [char](../../../csharp/language-reference/keywords/char.md) 型のキーで、各 <xref:System.Linq.IGrouping%602> オブジェクトの `Key` プロパティに格納されます。  キーの型はコンパイラによって推論されます。  
  
 次の例に示すように、クエリ式の末尾に `group` 句を使用できます。  
  
 [!code-cs[cscsrefQueryKeywords#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_1.cs)]  
  
 各グループに対して追加のクエリ操作を実行する場合、[into](../../../csharp/language-reference/keywords/into.md) コンテキスト キーワードを使用して一時的な識別子を指定できます。  `into` を使用するときは、次のコードの抜粋に示すように、クエリを継続し、最後は `select` ステートメントまたは別の `group` 句にする必要があります。  
  
 [!code-cs[cscsrefQueryKeywords#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_2.cs)]  
  
 `into` を指定した場合と指定しない場合の `group` の完成度の高い使用例については、このトピックの「使用例」を参照してください。  
  
## グループ クエリの結果を列挙する  
 `group` クエリによって生成される <xref:System.Linq.IGrouping%602> オブジェクトは、基本的にリストのリストであるため、各グループのアイテムをアクセスするには、入れ子にされた [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ループを使用する必要があります。  外側のループがグループ キーを反復処理し、内側のループがグループ自体の各アイテムを反復処理します。  グループにはキーがある場合がありますが、要素はありません。  前のコード例でクエリを実行する `foreach` ループは次のようになります。  
  
 [!code-cs[cscsrefQueryKeywords#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_3.cs)]  
  
## キーの型  
 グループ キーは、文字列、組み込み数値型、ユーザー定義の名前付き型などの任意の型、または匿名型です。  
  
### 文字列でグループ化  
 前のコード例では `char` を使用しました。  代わりに、完全な姓などの文字列のキーも簡単に指定できます。  
  
 [!code-cs[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_4.cs)]  
  
### ブールでグループ化  
 キーにブール値を使用して、結果を 2 つのグループに分ける方法を次の例に示します。  値は、`group` 句内のサブ式によって生成されます。  
  
 [!code-cs[cscsrefQueryKeywords#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_5.cs)]  
  
### 数値の範囲でグループ化  
 次の例では、式を使用して、パーセンタイルの範囲を表す数値のグループ キーを作成します。  `group` 句でメソッドを 2 回呼び出す必要がないように、メソッド呼び出しの結果を格納する便利な場所として [let](../../../csharp/language-reference/keywords/let-clause.md) を使用しています。  また、"0 で除算" 例外を回避するために、`group` 句内のコードで、学生の平均がゼロでないことを確認しています。  クエリ式でメソッドを安全に使用する方法の詳細については、「[方法 : クエリ式の例外を処理する](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md)」を参照してください。  
  
 [!code-cs[cscsrefQueryKeywords#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_6.cs)]  
  
### 複合キーでグループ化  
 複数のキーに従って要素をグループ化するには、複合キーを使用します。  複合キーは、キー要素の保持に匿名型または名前付き型を使用して作成します。  次の例では、`surname` という名前のメンバーおよび `city` という名前のメンバーと共にクラス `Person` が宣言されていることを想定しています。  `group` 句によって、同じ姓で同じ都市の人物のセットごとに個別のグループが作成されます。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 別のメソッドにクエリ変数を渡す必要がある場合、名前付き型を使用します。  キーに自動実装プロパティを使用して特別なクラスを作成し、<xref:System.Object.Equals%2A> メソッドおよび <xref:System.Object.GetHashCode%2A> メソッドをオーバーライドします。  構造体を使用することもできます。この場合、これらのメソッドのオーバーライドは必ずしも必要ではありません。  詳細については、「[方法 : 自動実装するプロパティを使用して簡易クラスを実装する](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)」および「[How to: Query for Duplicate Files in a Directory Tree \(LINQ\)](../Topic/How%20to:%20Query%20for%20Duplicate%20Files%20in%20a%20Directory%20Tree%20\(LINQ\).md)」を参照してください。  後者のトピックには、名前付き型と共に複合キーを使用する方法を示すコード例があります。  
  
## 使用例  
 グループに追加のクエリ ロジックが適用されない場合の、グループごとにソース データを並べる標準的なパターンを次の例に示します。  これは、継続なしのグループ化と呼ばれます。  それぞれの最初の文字に従って、文字列の配列内の要素がグループ化されます。  クエリの結果は、`char` 型の `Key` パブリック プロパティを格納する <xref:System.Linq.IGrouping%602> 型、およびグループ内の各アイテムを格納する <xref:System.Collections.Generic.IEnumerable%601> コレクションです。  
  
 `group` 句の結果は、シーケンスのシーケンスです。  このため、返された各グループ内の個々の要素にアクセスするには、次の例に示すように、グループ キーを反復処理するループ内で、入れ子にされた `foreach` ループを使用します。  
  
 [!code-cs[cscsrefQueryKeywords#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_7.cs)]  
  
## 使用例  
 グループの作成後に、*継続*と `into` を使用して、グループに対して追加ロジックを実行する方法を次の例に示します。  詳細については、「[into](../../../csharp/language-reference/keywords/into.md)」を参照してください。  次の例では、各グループを照会し、キー値が母音であるものだけを選択します。  
  
 [!code-cs[cscsrefQueryKeywords#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/group-clause_8.cs)]  
  
## 解説  
 コンパイル時に、`group` 句は <xref:System.Linq.Enumerable.GroupBy%2A> メソッドの呼び出しに変換されます。  
  
## 参照  
 <xref:System.Linq.IGrouping%602>   
 <xref:System.Linq.Enumerable.GroupBy%2A>   
 <xref:System.Linq.Enumerable.ThenBy%2A>   
 <xref:System.Linq.Enumerable.ThenByDescending%2A>   
 [クエリ キーワード \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [方法: 入れ子になったグループを作成する](../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md)   
 [方法: クエリ結果をグループ化する](../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md)   
 [方法: グループ化操作でサブクエリを実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)
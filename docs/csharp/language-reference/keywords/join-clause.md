---
title: "join 句 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "join"
  - "join_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "join 句 [C#]"
  - "join キーワード [C#]"
ms.assetid: 76e9df84-092c-41a6-9537-c3f1cbd7f0fb
caps.latest.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 29
---
# join 句 (C# リファレンス)
オブジェクト モデル内で直接的な関係を持たない、異なるソース シーケンスの要素どうしを関連付けるには、`join` 句を使用すると便利です。  唯一の要件は、各ソースの要素が、等価比較できるような値を共有していることです。  たとえば、食品販売業者が、特定の商品についての仕入先一覧とバイヤー一覧を持っているとします。  `join` 句を使用すると、その商品に関して、指定した同じ地域の仕入先とバイヤーの一覧を作成できます。  
  
 `join` 句は、入力として 2 つのソース シーケンスを受け取ります。  各シーケンス内の要素は、対応するもう一方のシーケンスのプロパティと比較できるプロパティであるか、このプロパティを含んでいる必要があります。  `join` 句は、特別な `equals` キーワードを使用して、指定したキーが等しいかどうかを比較します。  `join` 句によって実行される結合は、すべて等結合です。  `join` 句の出力結果は、実行する結合の種類によって異なります。  最も一般的な結合の種類は、次の 3 つです。  
  
-   内部結合  
  
-   グループ化結合  
  
-   左外部結合  
  
## 内部結合  
 簡単な内部等結合の例を次に示します。  このクエリでは、"商品名\/カテゴリ" ペアのフラットなシーケンスが生成されます。  同じカテゴリ文字列が、複数の要素に表示されます。  `categories` の要素に一致する要素が `products` 内にない場合、そのカテゴリは結果に表示されません。  
  
 [!code-cs[cscsrefQueryKeywords#24](../../../csharp/language-reference/keywords/codesnippet/csharp/csquerykeywords/Join.cs#24)]  
  
 詳細については、「[方法 : 内部結合を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)」を参照してください。  
  
## グループ化結合  
 `into` 式と組み合わせた `join` 句は、グループ化結合と呼ばれます。  
  
 [!code-cs[cscsrefQueryKeywords#25](../../../csharp/language-reference/keywords/codesnippet/csharp/csquerykeywords/Join.cs#25)]  
  
 グループ化結合では、階層構造の結果シーケンスが生成され、左側のソース シーケンスの要素が、右側のソース シーケンスに含まれる 1 つ以上の一致する要素に関連付けられます。  グループ化結合は基本的にオブジェクト配列のシーケンスであり、リレーショナル データベースの用語には、これに相当するものがありません。  
  
 右側のソース シーケンスに左側のソースの要素と一致する要素がない場合、`join` 句はその項目について空の配列を生成します。  このため、結果のシーケンスがグループ別に編成される点を除き、グループ化結合は基本的に内部等結合です。  
  
 グループ化結合の結果を単に選択した場合、項目にアクセスすることはできますが、一致の基準となるキーを特定することはできません。  したがって、一般に、前の例に示すように、グループ化結合の結果を選択し、キー名を持つ新しい型に格納した方が便利です。  
  
 グループ化結合の結果を、別のサブクエリのジェネレーターとして使用することもできます。  
  
 [!code-cs[cscsrefQueryKeywords#26](../../../csharp/language-reference/keywords/codesnippet/csharp/csquerykeywords/Join.cs#26)]  
  
 詳細については、「[方法 : グループ化結合を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)」を参照してください。  
  
## 左外部結合  
 左外部結合では、右側のシーケンスに一致する要素がない場合でも、左側のソース シーケンスに含まれるすべての要素が返されます。  [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] で左外部結合を実行するには、`DefaultIfEmpty` メソッドをグループ化結合と組み合わせて使用して、左側の要素に一致する要素がなかった場合に生成する、既定の右側の要素を指定します。  `null` は、任意の参照型の既定値として使用できます。また、ユーザー定義の既定の型を指定することもできます。  次の例では、ユーザー定義の既定の型を示しています。  
  
 [!code-cs[cscsrefQueryKeywords#27](../../../csharp/language-reference/keywords/codesnippet/csharp/csquerykeywords/Join.cs#27)]  
  
 詳細については、「[方法 : 左外部結合を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)」を参照してください。  
  
## 等値演算子  
 `join` 句は、等結合を実行します。  つまり、2 つのキーが等しい場合のみ、一致が結合されます。  他の種類の比較 \("より大きい"、"等しくない" など\) はサポートされません。  すべての結合が等結合であることを明確にするため、`join` 句では、`==` 演算子の代わりに `equals` キーワードが使用されます。  `join` 句では `equals` キーワードのみ使用できます。このキーワードと `==` 演算子には、重要な違いが 1 つあります。  `equals` の場合、左辺のキーは外部のソース シーケンスを使用し、右辺のキーは内部のソースを使用します。  外部のソースは `equals` の左辺のスコープにしかなく、内部のソース シーケンスは右辺のスコープにしかありません。  
  
## 非等結合  
 複数の `from` 句を使用して新しいシーケンスをクエリに個別に導入すると、非等結合、クロス結合、および他のカスタム結合操作を実行できます。  詳細については、「[方法 : カスタム結合操作を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md)」を参照してください。  
  
## オブジェクト コレクションの結合とリレーショナル テーブルの結合  
 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] クエリ式では、結合操作はオブジェクト コレクションに対して実行されます。  オブジェクト コレクションは、2 つのリレーショナル テーブルを結合するのとまったく同じ方法で "結合" することはできません。  [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] では、2 つのソース シーケンスの間に何の関連付けもない場合のみ、明示的な `join` 句が必要です。  [!INCLUDE[vbtecdlinq](../../../csharp/includes/vbtecdlinq-md.md)] を使用する場合、オブジェクト モデルの外部キー テーブルは、主テーブルのプロパティとして表されます。  たとえば、Northwind データベースの Customer テーブルと Orders テーブルとの間には、外部キー リレーションシップがあります。  この 2 つのテーブルをオブジェクト モデルにマップすると、Customer クラスは Orders プロパティを持っていて、Orders プロパティにはその Customer に関連付けられた Orders のコレクションが格納されていることになります。  つまり、結合は既に自動的に行われています。  
  
 [!INCLUDE[vbtecdlinq](../../../csharp/includes/vbtecdlinq-md.md)] のコンテキストで複数の関連テーブルを照会する方法の詳細については、「[How to: Map Database Relationships](../Topic/How%20to:%20Map%20Database%20Relationships.md)」を参照してください。  
  
## 複合キー  
 複合キーを使用すると、複数の値が等しいかどうかをテストできます。  詳細については、「[方法 : 複合キーを使用して結合する](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md)」を参照してください。  複合キーは、`group` 句でも使用できます。  
  
## 使用例  
 同じデータ ソースに対して同じ一致するキーを使用して内部結合、グループ化結合、および左外部結合を実行した結果の比較を次の例に示します。  これらの例には、コンソールでの表示結果をわかりやすくするために、余分なコードが追加されています。  
  
 [!code-cs[cscsrefQueryKeywords#23](../../../csharp/language-reference/keywords/codesnippet/csharp/csquerykeywords/Join.cs#23)]  
  
## 解説  
 `join` 句の後に `into` がない場合は、<xref:System.Linq.Enumerable.Join%2A> メソッドの呼び出しに変換されます。  `join` 句の後に `into` がある場合は、<xref:System.Linq.Enumerable.GroupJoin%2A> メソッドの呼び出しに変換されます。  
  
## 参照  
 [クエリ キーワード \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Join Operations](../../../visual-basic/programming-guide/concepts/linq/join-operations.md)   
 [group 句](../../../csharp/language-reference/keywords/group-clause.md)   
 [方法 : 左外部結合を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)   
 [方法 : 内部結合を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)   
 [方法 : グループ化結合を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)   
 [方法 : join 句の結果の順序を指定する](../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)   
 [方法 : 複合キーを使用して結合する](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md)   
 [方法 : サンプル データベースをインストールする](../Topic/How%20to:%20Install%20Sample%20Databases.md)
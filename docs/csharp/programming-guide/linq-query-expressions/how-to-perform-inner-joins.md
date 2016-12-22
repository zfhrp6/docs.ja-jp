---
title: "方法 : 内部結合を実行する (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "内部結合 [C# での LINQ]"
  - "結合 [C#], 内部"
  - "クエリ [C# での LINQ], 結合"
  - "クエリ式 [C# での LINQ], 結合"
ms.assetid: d9edb404-8314-413e-ae51-83bb86c7a4b5
caps.latest.revision: 25
caps.handback.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法 : 内部結合を実行する (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

リレーショナル データベース用語の*内部結合*では、2 番目のコレクション内の一致するすべての要素に対して、最初のコレクションの各要素が一度に表示される結果セットが生成されます。  2 番目のコレクションと一致する要素が最初のコレクションにない場合、その要素は結果セットに表示されません。  <xref:System.Linq.Enumerable.Join%2A> メソッドは、C\# の `join` 句で呼び出され、内部結合を実装します。  
  
 このトピックでは、次の 4 種類の内部結合を実行する方法を示します。  
  
-   簡単なキーに基づいて、2 つのデータ ソースの要素を関連付ける単純な内部結合。  
  
-   *複合*キーに基づいて、2 つのデータ ソースの要素を関連付ける内部結合。  複合キーは複数の値で構成され、複数のプロパティに基づいて要素を関連付けることができます。  
  
-   一連の結合操作が相互に連結された*複数の結合*。  
  
-   グループ結合を使用して実装された内部結合。  
  
## 使用例  
  
## 簡単なキーの結合の例  
 次の例は、2 つのユーザー定義型 `Person` と `Pet` のオブジェクトが含まれた 2 つのコレクションを作成します。  クエリでは、C\# の `join` 句を使用して、`Person` オブジェクトを `Owner` がその `Person` である `Pet` オブジェクトと一致させます。  C\# の `select` 句では、クエリ結果のオブジェクトの表示内容を定義します。  この例では、クエリ結果のオブジェクトは、飼い主の姓とペットの名前で構成された匿名型です。  
  
 [!CODE [CsLINQProgJoining#1](../CodeSnippet/VS_Snippets_VBCSharp/CsLINQProgJoining#1)]  
  
 `LastName` が "Huff" の `Person` オブジェクトは、`Pet.Owner` がその `Person` に等しい `Pet` オブジェクトがないため、結果セットに表示されません。  
  
## 使用例  
  
## 複合キーの結合の例  
 1 つのプロパティだけに基づいて要素を関連付ける代わりに、複合キーを使用して、複数のプロパティに基づいて要素を比較できます。  これを行うには、各コレクションに対してキー セレクター関数を指定し、比較するプロパティで構成された匿名型を返します。  プロパティにラベルを付ける場合は、各キーの匿名型に同じラベルを付ける必要があります。  また、プロパティは、同じ順序で表示する必要があります。  
  
 次の例は、`Employee` オブジェクトのリストと `Student` オブジェクトのリストを使用して、学生でもある社員を調べます。  これらの型の両方に、<xref:System.String> 型の `FirstName` プロパティと `LastName` プロパティがあります。  それぞれのリストの要素から結合キーを作成する関数が、各要素の `FirstName` プロパティと `LastName` プロパティで構成された匿名型を返します。  結合操作で、これらの複合キーが等しいかどうか比較され、それぞれのリストの氏名が一致するオブジェクトのペアが返されます。  
  
 [!CODE [CsLINQProgJoining#2](../CodeSnippet/VS_Snippets_VBCSharp/CsLINQProgJoining#2)]  
  
## 使用例  
  
## 複数の結合の例  
 任意の数の結合操作を相互に連結して、複数の結合を実行できます。  C\# の各 `join` 句は、指定されたデータ ソースを前の結合の結果に関連付けます。  
  
 次の例は、`Person` オブジェクトのリスト、`Cat` オブジェクトのリスト、および `Dog` オブジェクトのリストの 3 つのコレクションを作成します。  
  
 C\# の最初の `join` 句では、`Person` オブジェクトと `Cat.Owner` の照合に基づいて飼い主と猫を一致させます。  この操作で、`Person` オブジェクトと `Cat.Name` が含まれた匿名型のシーケンスが返されます。  
  
 C\# の 2 番目の `join` 句では、`Person` 型の `Owner` プロパティと動物の名前の最初の文字で構成される複合キーに基づいて、最初の結合で返された匿名型を、指定された犬のリストの `Dog` オブジェクトに関連付けます。  この操作で、一致するそれぞれのペアの `Cat.Name` プロパティと `Dog.Name` プロパティが含まれた匿名型のシーケンスが返されます。  これは内部結合であるため、2 番目のデータ ソースと一致する、最初のデータ ソースのオブジェクトのみが返されます。  
  
 [!CODE [CsLINQProgJoining#3](../CodeSnippet/VS_Snippets_VBCSharp/CsLINQProgJoining#3)]  
  
## 使用例  
  
## グループ結合を使用した内部結合の例  
 グループ結合を使用して内部結合を実装する方法を次の例に示します。  
  
 `query1` で、`Person` オブジェクトのリストは、`Pet.Owner` プロパティと一致する `Person` に基づいて、`Pet` オブジェクトのリストにグループ結合されます。  グループ結合によって、それぞれのグループが `Person` オブジェクトおよび一致する `Pet` オブジェクトのシーケンスで構成された、中間グループのコレクションが作成されます。  
  
 2 つ目の `from` 句をクエリに追加すると、シーケンスのこのシーケンスが 1 つの長いシーケンスに結合 \(または平坦化\) されます。  最後のシーケンスの要素の型は、`select` 句で指定されます。  この例では、この型は、一致する各ペアの `Person.FirstName` プロパティと `Pet.Name` プロパティで構成された匿名型です。  
  
 `query1` の結果は、`into` 句のない `join` 句を使用して内部結合を実行することで得られた結果セットと同じです。  `query2` 変数は、これと同等のクエリを示しています。  
  
 [!CODE [CsLINQProgJoining#4](../CodeSnippet/VS_Snippets_VBCSharp/CsLINQProgJoining#4)]  
  
## コードのコンパイル  
  
-   [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)] で新しいコンソール アプリケーション プロジェクトを作成します。  
  
-   System.Core.dll がまだ参照されていない場合は、System.Core.dll への参照を追加します。  
  
-   <xref:System.Linq> 名前空間を含めます。  
  
-   例からコードをコピーし、program.cs ファイルの `Main` メソッドの下に貼り付けます。  貼り付けたメソッドを呼び出すコード行を `Main` メソッドに追加します。  
  
-   プログラムを実行します。  
  
## 参照  
 <xref:System.Linq.Enumerable.Join%2A>   
 <xref:System.Linq.Enumerable.GroupJoin%2A>   
 [Join Operations](../../../visual-basic/programming-guide/concepts/linq/join-operations.md)   
 [方法 : グループ化結合を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)   
 [方法 : 左外部結合を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)   
 [How to: Join Two Collections](../Topic/How%20to:%20Join%20Two%20Collections%20\(C%23\)%20\(LINQ%20to%20XML\).md)   
 [匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
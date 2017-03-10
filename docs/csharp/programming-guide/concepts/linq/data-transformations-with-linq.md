---
title: "LINQ によるデータ変換 (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "[C# での LINQ]、データ変換"
  - "ソース要素 [C# での LINQ]"
  - "結合 (複数の入力を) [C# での LINQ]"
  - "複数の出力を 1 つの出力シーケンスに [C# での LINQ]"
  - "ソース要素のサブセット [C# での LINQ]"
  - "データ ソース [C# での LINQ]、データ変換"
  - "データ変換 [C# での LINQ]"
ms.assetid: 674eae9e-bc72-4a88-aed3-802b45b25811
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# LINQ によるデータ変換 (C#)
[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext-md.md)] で行うことができるのは、データの取得だけではありません。  データ変換のための強力なツールとしても使用できます。  [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] クエリを使用することにより、ソース シーケンスを入力として使用し、さまざまな方法で加工して新しい出力シーケンスを作成できます。  要素自体を変更せずに、並べ替えやグループ化してシーケンス自体を変更できます。しかし、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] のクエリの最も強力な機能は、新しい型を作成する機能があります。  これは [select](../../../../csharp/language-reference/keywords/select-clause.md) 句によって実現されます。  たとえば、次のタスクを実行できます。  
  
-   複数の入力シーケンスを結合して、新しい型の単一の出力シーケンスを作成する。  
  
-   ソース シーケンス内の各要素のプロパティの 1 つまたは一部だけで構成される要素から出力シーケンスを作成する。  
  
-   ソース データに対して操作を実行し、その結果で構成される要素から出力シーケンスを作成する。  
  
-   別の形式で出力シーケンスを作成する。  たとえば、SQL の行またはテキスト ファイルのデータを XML に変換できます。  
  
 これらはほんの一例です。  これらの変換を、同じクエリ内でさまざまな方法で組み合わせて使用することもできます。  また、あるクエリの出力シーケンスを別のクエリの入力シーケンスとして使用することもできます。  
  
## 複数の入力を 1 つの出力シーケンスに結合する  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] クエリを使用して、複数の入力シーケンスの要素を含む 1 つの出力シーケンスを作成できます。  次の例は、2 つのインメモリ データ構造を結合する方法を示していますが、ソースが XML、SQL、または DataSet のデータを結合する場合も、同じ基本原則を適用できます。  次の 2 つのクラス型があるとします。  
  
 [!code-cs[CsLINQGettingStarted#7](../../../../csharp/programming-guide/concepts/linq/codesnippet/csharp/GettingStarted/Class1.cs#7)]  
  
 クエリの例を次に示します。  
  
 [!code-cs[CSLinqGettingStarted#8](../../../../csharp/programming-guide/concepts/linq/codesnippet/csharp/GettingStarted/Class1.cs#8)]  
  
 詳細については、「[join 句](../../../../csharp/language-reference/keywords/join-clause.md)」および「[select 句](../../../../csharp/language-reference/keywords/select-clause.md)」を参照してください。  
  
## 各ソース要素のサブセットを選択する  
 ソース シーケンスの各要素のサブセットを選択するには、主に次の 2 つの方法があります。  
  
1.  ソース要素の 1 つのメンバーのみを選択するには、ドット演算を使用します。  次の例で、`Customer` オブジェクトには、`City` という名前の文字列を含むいくつかのパブリック プロパティが含まれているとします。  このクエリを実行すると、文字列の出力シーケンスが生成されます。  
  
    ```  
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2.  1 つのソース要素からの複数のプロパティを持つ要素を作成するには、名前付きオブジェクトまたは匿名型を指定したオブジェクト初期化子を使用します。  次の例は、匿名型を使用して、各 `Customer` 要素の 2 つのプロパティをカプセル化する方法を示しています。  
  
    ```  
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 詳細については、「[オブジェクト初期化子とコレクション初期化子](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)」および「[匿名型](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)」を参照してください。  
  
## インメモリ オブジェクトを XML に変換する  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] クエリを使用すると、インメモリ データ構造、SQL データベース、[!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado-md.md)] データセット、XML ストリーム、および XML ドキュメントの間でデータ変換を簡単に行うことができます。  インメモリ データ構造のオブジェクトを XML 要素に変換する例を次に示します。  
  
 [!code-cs[CsLINQGettingStarted#9](../../../../csharp/programming-guide/concepts/linq/codesnippet/csharp/GettingStarted/Class1.cs#9)]  
  
 このコードを実行すると、次の XML 出力が生成されます。  
  
```  
< Root>  
  <student>  
    <First>Svetlana</First>  
    <Last>Omelchenko</Last>  
    <Scores>97,92,81,60</Scores>  
  </student>  
  <student>  
    <First>Claire</First>  
    <Last>O'Donnell</Last>  
    <Scores>75,84,91,39</Scores>  
  </student>  
  <student>  
    <First>Sven</First>  
    <Last>Mortensen</Last>  
    <Scores>88,94,65,91</Scores>  
  </student>  
</Root>  
```  
  
 詳細については、「[Creating XML Trees in C\#](../Topic/Creating%20XML%20Trees%20in%20C%23%20\(LINQ%20to%20XML\)1.md)」を参照してください。  
  
## ソース要素に対して操作を実行する  
 出力シーケンスには、ソース シーケンスの要素または要素のプロパティが 1 つも含まれない場合があります。  代わりに、ソース要素を入力引数として使用することで得られた値のシーケンスを出力として生成できます。  次の簡単なクエリを実行すると、`double` 型の要素のソース シーケンスに基づいて計算された値を表す文字列のシーケンスが出力されます。  
  
> [!NOTE]
>  クエリが他のドメインに変換される場合、クエリ式でのメソッド呼び出しはサポートされません。  たとえば、[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq-md.md)] で C\# の通常のメソッドを呼び出すことはできません。これは、C\# のメソッドのコンテキストが SQL Server にないためです。  ただし、ストアド プロシージャをメソッドにマップして呼び出すことは可能です。  詳細については、「[Stored Procedures](../Topic/Stored%20Procedures.md)」を参照してください。  
  
 [!code-cs[CsLINQGettingStarted#10](../../../../csharp/programming-guide/concepts/linq/codesnippet/csharp/GettingStarted/Class1.cs#10)]  
  
## 参照  
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md)   
 [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)   
 [LINQ クエリ式](../../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [select 句](../../../../csharp/language-reference/keywords/select-clause.md)   
 [How to: Combine Data with Joins](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)
---
title: "Basic LINQ Query Operations (C#) | Microsoft Docs"
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
  - "orderby clause [LINQ in C#]"
  - "ordering data [LINQ in C#]"
  - "selecting data [LINQ in C#]"
  - "queries [LINQ in C#], basic operations"
  - "grouping data [LINQ in C#]"
  - "data sources [LINQ in C#]"
  - "sorting data [LINQ in C#]"
  - "projections [LINQ in C#]"
  - "filtering data [LINQ in C#]"
  - "joining data [LINQ in C#]"
  - "select clause [LINQ in C#]"
  - "LINQ [C#], basic query operations"
  - "join clause [LINQ in C#]"
  - "group clause [LINQ in C#]"
ms.assetid: a7ea3421-1cf4-4df7-832a-aa22fe6379e9
caps.latest.revision: 39
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 37
---
# Basic LINQ Query Operations (C#)
ここでは、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] のクエリ式およびクエリで実行する一般的な操作について簡単に紹介します。  詳細については、次のトピックを参照してください。  
  
 [LINQ クエリ式](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
  
 [Standard Query Operators Overview](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
  
 [Walkthrough: Writing Queries in C\#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
>  SQL や XQuery などのクエリ言語に既に精通している場合は、このトピックの大部分をスキップできます。  [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] のクエリ式における句の順序について理解するには、次のセクションの `from` 句に関するトピックを参照してください。  
  
## データ ソースの取得  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] クエリに必要な最初の手順は、データ ソースを指定することです。  ほとんどのプログラミング言語と同様に、C\# でも、変数は使用する前に宣言しておく必要があります。  [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] クエリでは、データ ソース \(`customers`\) と*範囲変数* \(`cust`\) を定義するために `from` 句が最初に使用されます。  
  
 [!code-cs[csLINQGettingStarted#23](../../../../csharp/programming-guide/concepts/linq/codesnippet/csharp/GettingStarted/Class1.cs#23)]  
  
 範囲変数は `foreach` ループの反復変数に似ていますが、クエリ式で実際の反復が発生しない点が異なります。  クエリが実行されると、範囲変数は `customers` の連続する各要素への参照として機能します。  `cust` の型はコンパイラで推論できるので、明示的に指定する必要はありません。  追加の範囲変数は `let` 句で定義できます。  詳細については、「[let 句](../../../../csharp/language-reference/keywords/let-clause.md)」を参照してください。  
  
> [!NOTE]
>  <xref:System.Collections.ArrayList> などの非ジェネリック データ ソースの場合は、範囲変数を明示的に型指定する必要があります。  詳細については、「[How to: Query an ArrayList with LINQ](../Topic/How%20to:%20Query%20an%20ArrayList%20with%20LINQ.md)」および「[from 句](../../../../csharp/language-reference/keywords/from-clause.md)」を参照してください。  
  
## フィルター処理  
 おそらく、最も一般的なクエリ操作は、ブール式の形式でフィルターを適用することです。  フィルターにより、式が true になる要素だけがクエリから返されます。  結果は `where` 句を使用して生成されます。  フィルターは、基本的に、ソース シーケンスから除外する要素を指定します。  次の例では、住所がロンドンにある `customers` だけが返されます。  
  
 [!code-cs[csLINQGettingStarted#24](../../../../csharp/programming-guide/concepts/linq/codesnippet/csharp/GettingStarted/Class1.cs#24)]  
  
 使い慣れた C\# の論理 `AND` 演算子と論理 `OR` 演算子を使用すると、必要に応じていくつでも `where` 句にフィルター式を適用できます。  たとえば、住所が "ロンドン" にあり、かつ \(`AND`\) 名前が "Devon" の顧客だけを返すには、次のコードを記述します。  
  
 [!code-cs[csLINQGettingStarted#25](../../../../csharp/programming-guide/concepts/linq/codesnippet/csharp/GettingStarted/Class1.cs#25)]  
  
 住所がロンドンまたはパリにある顧客を返すには、次のコードを記述します。  
  
 [!code-cs[csLINQGettingStarted#26](../../../../csharp/programming-guide/concepts/linq/codesnippet/csharp/GettingStarted/Class1.cs#26)]  
  
 詳細については、「[where 句](../../../../csharp/language-reference/keywords/where-clause.md)」を参照してください。  
  
## 順序付け  
 返されるデータを並べ替えると便利な場合がよくあります。  `orderby` 句は、返されるシーケンス内の要素を、並べ替える型の既定の比較子に従って並べ替えます。  たとえば、次のクエリは、`Name` プロパティに基づいて結果を並べ替えるように拡張できます。  `Name` は文字列なので、既定の比較子によってアルファベット順 \(A ～ Z\) に並べ替えられます。  
  
 [!code-cs[csLINQGettingStarted#27](../../../../csharp/programming-guide/concepts/linq/codesnippet/csharp/GettingStarted/Class1.cs#27)]  
  
 結果を逆の順序 \(Z ～ A\) で並べ替えるには、`orderby…descending` 句を使用します。  
  
 詳細については、「[orderby 句](../../../../csharp/language-reference/keywords/orderby-clause.md)」を参照してください。  
  
## グループ化  
 `group` 句を使用すると、指定したキーに基づいて結果をグループ化できます。  たとえば、結果を `City` 別にグループ化して、住所がロンドンまたはパリにあるすべての顧客を別々のグループに分けることができます。  この場合のキーは `cust.City` です。  
  
 [!code-cs[csLINQGettingStarted#28](../../../../csharp/programming-guide/concepts/linq/codesnippet/csharp/GettingStarted/Class1.cs#28)]  
  
 `group` 句でクエリを終了すると、結果はリストのリストという形式になります。  リストの各要素はオブジェクトであり、このオブジェクトには、`Key` メンバーと、そのキーに基づいてグループ化された要素のリストが含まれます。  グループのシーケンスを生成するクエリを反復処理する場合は、入れ子になった `foreach` ループを使用する必要があります。  外側のループで各グループを反復処理し、内側のループで各グループのメンバーを反復処理します。  
  
 グループ操作の結果を参照する必要がある場合は、`into` キーワードを使用して、さらに照会が可能な識別子を作成できます。  次のクエリでは、顧客が 2 人よりも多いグループだけが返されます。  
  
 [!code-cs[csLINQGettingStarted#29](../../../../csharp/programming-guide/concepts/linq/codesnippet/csharp/GettingStarted/Class1.cs#29)]  
  
 詳細については、「[group 句](../../../../csharp/language-reference/keywords/group-clause.md)」を参照してください。  
  
## 結合  
 結合操作は、データ ソースで明示的にモデル化されていないシーケンス間に関連付けを作成します。  たとえば、場所が同じであるすべての顧客と販売業者を検索するには、結合を実行できます。  [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] では、`join` 句はデータベース テーブルを直接操作するのではなく、常にオブジェクト コレクションに対して動作します。  
  
 [!code-cs[csLINQGettingStarted#36](../../../../csharp/programming-guide/concepts/linq/codesnippet/csharp/GettingStarted/Class1.cs#36)]  
  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] では、SQL ほど頻繁に `join` を使う必要はありません。これは、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] の外部キーが、オブジェクト モデルでは項目のコレクションを保持するプロパティとして表されるためです。  たとえば、`Customer` オブジェクトには `Order` オブジェクトのコレクションが含まれます。  結合を実行しなくても、ドット表記を使用して注文にアクセスできます。  
  
```  
from order in Customer.Orders...  
```  
  
 詳細については、「[join 句](../../../../csharp/language-reference/keywords/join-clause.md)」を参照してください。  
  
## 選択 \(投影\)  
 `select` 句は、クエリの結果を生成し、返された各要素の "シェイプ" つまり型を指定します。  たとえば、完全な `Customer` オブジェクト、1 つのメンバーのみ、メンバーのサブセット、計算や新しいオブジェクトの作成に基づいたまったく異なる結果の種類のいずれから結果が構成されるかを指定できます。  `select` 句がソース要素のコピー以外を生成する場合、その操作は*投影*と呼ばれます。  投影を使用したデータの変換は、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] のクエリ式の強力な機能です。  詳細については、「[LINQ によるデータ変換 \(C\#\)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)」および「[select 句](../../../../csharp/language-reference/keywords/select-clause.md)」を参照してください。  
  
## 参照  
 [Getting Started with LINQ in C\#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [LINQ クエリ式](../../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Walkthrough: Writing Queries in C\#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)   
 [クエリ キーワード \(LINQ\)](../../../../csharp/language-reference/keywords/query-keywords.md)   
 [匿名型](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [基本的なクエリ操作 \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)
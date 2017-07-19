---
title: "LINQ to Entities でのクエリ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: c015a609-29eb-4e95-abb1-2ca721c6e2ad
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# LINQ to Entities でのクエリ
クエリは、データ ソースからデータを取得する式です。  一般に、クエリは専用のクエリ言語で表現されます。たとえば、リレーショナル データベースであれば SQL、XML であれば XQuery が使用されます。  そのため、開発者はクエリの対象となるデータ ソースやデータ形式ごとに新しいクエリ言語を習得する必要があります。  統合言語クエリ \(LINQ\) は、データ ソースや形式の違いを意識することなくデータを扱うことのできる、より簡素化された一貫したモデルを提供します。  LINQ クエリでは、常にプログラミング オブジェクトを操作することになります。  
  
 LINQ のクエリ操作は、データ ソースを取得し、クエリを作成して、クエリを実行するという 3 つのアクションから成ります。  
  
 LINQ を介したクエリは、<xref:System.Collections.Generic.IEnumerable%601> ジェネリック インターフェイスまたは <xref:System.Linq.IQueryable%601> ジェネリック インターフェイスを実装するデータ ソースに対して行うことができます。  ジェネリック <xref:System.Data.Objects.ObjectQuery%601> インターフェイスを実装するジェネリック <xref:System.Linq.IQueryable%601> クラスのインスタンスは、[!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] クエリのデータ ソースとして動作します。  <xref:System.Data.Objects.ObjectQuery%601> ジェネリック クラスは、0 個以上の型指定されたオブジェクトのコレクションを返すクエリを表します。  C\# キーワード `var` \(Visual Basic の場合は Dim\) を使用して、コンパイラでエンティティの型を推論することもできます。  
  
 クエリでは、データ ソースから取得する情報を正確に指定できます。  また、並べ替え、グループ化、整形方法を指定して情報を取得することもできます。  LINQ では、クエリが変数に格納されます。  クエリが一連の値を返す場合、クエリ変数そのものがクエリ可能な型であることが必要です。  このクエリ変数は、クエリの情報を保存するだけで、なんらかのアクションを実行したり、データを返したりすることはありません。  クエリを作成した後、データを取得するには、そのクエリを実行する必要があります。  
  
## クエリ構文  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] クエリは、クエリ式の構文とメソッド ベースのクエリ構文という 2 とおりの構文を使って作成できます。  クエリ式の構文は、C\# 3.0 および Visual Basic 9.0 で新たに導入され、Transact\-SQL や XQuery などと同様な宣言型の構文で記述された一連の句で構成されます。  ただし、[!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] の共通言語ランタイム \(CLR\) は、クエリ式の構文そのものを理解することはできません。  そのため、クエリ式はコンパイル時に、CLR が理解できる形式 \(メソッド呼び出し\) へと変換されます。  これらのメソッドは*標準クエリ演算子*として知られています。  開発者は、クエリ構文を使う代わりに、メソッド構文を使ってそれらを直接呼び出すこともできます。詳細については、「[Query Syntax and Method Syntax in LINQ](../Topic/Query%20Syntax%20and%20Method%20Syntax%20in%20LINQ%20\(C%23\).md)」を参照してください。  
  
### クエリ式の構文  
 クエリ式は宣言型のクエリ構文です。  開発者は、Transact\-SQL に似た形式の高級言語でクエリを記述できます。  クエリ式の構文を使用することにより、フィルター、並べ替え、グループ化など、データ ソースに対するきわめて複雑な処理を最小限のコードで実行できます。  詳細については、「[基本的なクエリ操作 \(Visual Basic\)](../Topic/Basic%20Query%20Operations%20\(Visual%20Basic\).md)」を参照してください。  クエリ式構文の使用方法を示す例については、次のトピックを参照してください。  
  
-   [クエリ式の構文例 : 射影](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-projection.md)  
  
-   [クエリ式の構文例: フィルター処理](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-filtering.md)  
  
-   [クエリ式の構文例 : 並べ替え](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-ordering.md)  
  
-   [クエリ式の構文例 : 集計演算子](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-aggregate-operators.md)  
  
-   [クエリ式の構文例 : パーティション分割](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-partitioning.md)  
  
-   [クエリ式の構文例 : 結合演算子](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-join-operators.md)  
  
-   [クエリ式の構文例 : 要素演算子](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-element-operators.md)  
  
-   [クエリ式の構文例 : グループ化](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-grouping.md)  
  
-   [クエリ式の構文例 : リレーションシップのナビゲーション](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-navigating-relationships.md)  
  
### メソッド ベースのクエリ構文  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] クエリを作成するもう 1 つの方法として、メソッド ベースのクエリがあります。  メソッド ベースのクエリ構文は、LINQ の演算子メソッドを、ラムダ式をパラメーターとして直接順次呼び出すものです。  詳細については、「[ラムダ式](../Topic/Lambda%20Expressions%20\(C%23%20Programming%20Guide\).md)」を参照してください。  メソッドベースの構文の使用方法を示す例については、次のトピックを参照してください。  
  
-   [メソッド ベースのクエリ構文例 : 射影](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-projection.md)  
  
-   [メソッドベースのクエリ構文例: フィルター処理](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-filtering.md)  
  
-   [メソッド ベースのクエリ構文例 : 並べ替え](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-ordering.md)  
  
-   [メソッド ベースのクエリ構文例 : 集計演算子](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-aggregate-operators.md)  
  
-   [メソッド ベースのクエリ構文例 : パーティション分割](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-partitioning.md)  
  
-   [メソッド ベースのクエリ構文例 : 変換](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-conversion.md)  
  
-   [メソッド ベースのクエリ構文例 : 結合演算子](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-join-operators.md)  
  
-   [メソッド ベースのクエリ構文例 : 要素演算子](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-element-operators.md)  
  
-   [メソッド ベースのクエリ構文例 : グループ化](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-grouping.md)  
  
-   [メソッド ベースのクエリ構文例 : リレーションシップのナビゲーション](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-navigating-relationships.md)  
  
## 参照  
 [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)   
 [Getting Started with LINQ in C\#](../Topic/Getting%20Started%20with%20LINQ%20in%20C%23.md)   
 [Getting Started with LINQ in Visual Basic](../Topic/Getting%20Started%20with%20LINQ%20in%20Visual%20Basic.md)   
 [Entity Framework マージ オプションおよびコンパイル済みクエリ](http://go.microsoft.com/fwlink/?LinkId=199591)
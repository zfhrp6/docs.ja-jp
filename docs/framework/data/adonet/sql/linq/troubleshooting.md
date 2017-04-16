---
title: "Troubleshooting | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8cd4401c-b12c-4116-a421-f3dcffa65670
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Troubleshooting
ここでは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アプリケーションで発生する可能性のある問題をいくつか示し、そうした問題を回避または影響を軽減するための提案を示します。  
  
 その他の問題については、「[Frequently Asked Questions](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)」を参照してください。  
  
## サポートされない標準クエリ演算子  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、すべての標準クエリ演算子メソッド \(たとえば <xref:System.Linq.Enumerable.ElementAt%2A>\) をサポートするわけではありません。  このため、コンパイルできたプロジェクトでも、ランタイム エラーが発生する可能性があります。  詳細については、「[Standard Query Operator Translation](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)」を参照してください。  
  
## メモリの問題  
 クエリにメモリ内コレクションと [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の <xref:System.Data.Linq.Table%601> が含まれる場合、2 つのコレクションの指定順序に応じて、メモリ内でクエリが実行される可能性があります。  クエリをメモリ内で実行する必要がある場合、データベース テーブルのデータを取得する必要があります。  
  
 この手法は非効率的で、メモリとプロセッサの消費量が非常に大きくなる可能性があります。  このような複数ドメインのクエリはできる限り使用しないでください。  
  
## ファイル名と SQLMetal  
 入力ファイル名を指定するには、その名前をコマンド ラインに入力ファイルとして追加します。  **\/conn** オプションを使用して接続文字列にファイル名を含める方法はサポートされていません。  詳細については、「[SqlMetal.exe \(コード生成ツール\)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)」を参照してください。  
  
## クラス ライブラリ プロジェクト  
 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]は、プロジェクトの `app.config` ファイルの中に接続文字列を作成します。  クラス ライブラリ プロジェクトでは `app.config` ファイルが使用されません。  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、デザイン時のファイルで提供される接続文字列を使用します。  `app.config` 内の値を変更しても、アプリケーションの接続先データベースは変更されません。  
  
## 連鎖削除  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は連鎖削除操作をサポートせず、認識もしません。  制約を持つテーブルの行を削除するには、次のいずれかを行う必要があります。  
  
-   データベース内の外部キー制約で `ON DELETE CASCADE` 規則を設定する。  
  
-   独自のコードを使用して、親オブジェクトの削除を妨げる子オブジェクトを最初に削除する。  
  
 このような操作を行わない場合、<xref:System.Data.SqlClient.SqlException> 例外がスローされます。  
  
 詳細については、「[How to: Delete Rows From the Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)」を参照してください。  
  
## クエリ可能でない式  
 「'型' の式はクエリ不可能です。LINQ プロバイダーに対してアセンブリ参照や名前空間インポートが不足していないことを確認してください」というエラーが発生した場合、次の点を確認してください。  
  
-   アプリケーションが [!INCLUDE[compact_v35_short](../../../../../../includes/compact-v35-short-md.md)] を対象としている。  
  
-   `System.Core.dll` および `System.Data.Linq.dll` への参照が存在する。  
  
-   <xref:System.Linq> および <xref:System.Data.Linq> のための `Imports` \([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]\) または `using` \(C\#\) ディレクティブが存在する。  
  
## DuplicateKeyException  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] プロジェクトのデバッグ時に、エンティティのリレーションシップを走査する場合があります。  その際、これらの項目はキャッシュに入り、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] はこれらの存在を認識します。  その後、同じキーの複数の行を生成する <xref:System.Data.Linq.Table%601.Attach%2A> や <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> などのメソッドを実行しようとした場合、<xref:System.Data.Linq.DuplicateKeyException> がスローされます。  
  
## 文字列連結の例外  
 `[n]text` と他の `[n][var]char` にマップされる複数のオペランドを連結する操作はサポートされません。  異なる 2 つの型のセットにマップされる文字列を連結しようとすると、例外がスローされます。  詳細については、「[System.String Methods](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)」を参照してください。  
  
## SQL Server 2000 の Skip 例外と Take 例外  
 SQL Server 2000 データベースに対して <xref:System.Linq.Queryable.Take%2A> または <xref:System.Linq.Queryable.Skip%2A> を使用する際には、ID メンバー \(<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>\) を使用する必要があります。  クエリは、\(結合ではなく\) 1 つのテーブルに対して実行されるか、<xref:System.Linq.Queryable.Distinct%2A>、<xref:System.Linq.Queryable.Except%2A>、<xref:System.Linq.Queryable.Intersect%2A>、または <xref:System.Linq.Queryable.Union%2A> 操作である必要があります。さらに、クエリに <xref:System.Linq.Queryable.Concat%2A> 操作を含めることはできません。  詳細については、「[Standard Query Operator Translation](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)」の「SQL Server 2000 のサポート」を参照してください。  
  
 この要件は [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)] には適用されません。  
  
## GroupBy InvalidOperationException  
 この例外は、たとえば `group x by (Phone==@phone)` のように、`boolean` 式でグループ分けする <xref:System.Linq.Enumerable.GroupBy%2A> クエリ内の列値が null である場合にスローされます。  式が `boolean` であるため、キーは `nullable` `boolean` ではなく、`boolean` と推論されます。  変換された比較で null が生成される場合、`nullable` `boolean` を `boolean` に割り当てようとして、例外がスローされます。  
  
 この状態を回避する \(null を false と扱う\) には、次のような手法を使用してください。  
  
 `GroupBy="(Phone != null) && (Phone=@Phone)"`  
  
## OnCreated\(\) 部分メソッド  
 オブジェクト コンストラクターが呼び出されるたびに、生成されたメソッド `OnCreated()` が呼び出されます。これは、元の値をコピーするために [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] がコンストラクターを呼び出す場合にも当てはまります。  独自の部分クラスに `OnCreated()` メソッドを実装する場合には、この動作を考慮に入れてください。  
  
## 参照  
 [Debugging Support](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)   
 [Frequently Asked Questions](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)
---
title: "トラブルシューティング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cd4401c-b12c-4116-a421-f3dcffa65670
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 56d06fa7adf2690a2cb9194342071c7814a4ec4a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="troubleshooting"></a>トラブルシューティング
ここでは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アプリケーションで発生する可能性のある問題をいくつか示し、そうした問題を回避または影響を軽減するための提案を示します。  
  
 その他の問題はで対処する[に関してよく寄せられる質問](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)です。  
  
## <a name="unsupported-standard-query-operators"></a>サポートされない標準クエリ演算子  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、すべての標準クエリ演算子メソッド (たとえば <xref:System.Linq.Enumerable.ElementAt%2A>) をサポートするわけではありません。 このため、コンパイルできたプロジェクトでも、ランタイム エラーが発生する可能性があります。 詳細については、次を参照してください。[標準クエリ演算子変換](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)です。  
  
## <a name="memory-issues"></a>メモリの問題  
 クエリには、メモリ内コレクションが含まれている場合と[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601>、2 つのコレクションが指定された順序に応じて、メモリ内のクエリを実行する可能性があります。 クエリをメモリ内で実行する必要がある場合、データベース テーブルのデータを取得する必要があります。  
  
 この手法は非効率的で、メモリとプロセッサの消費量が非常に大きくなる可能性があります。 このような複数ドメインのクエリはできる限り使用しないでください。  
  
## <a name="file-names-and-sqlmetal"></a>ファイル名と SQLMetal  
 入力ファイル名を指定するには、その名前をコマンド ラインに入力ファイルとして追加します。 ( **/conn** オプションを使用して) 接続文字列にファイル名を含める操作は、サポートされていません。 詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。  
  
## <a name="class-library-projects"></a>クラス ライブラリ プロジェクト  
 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]は、プロジェクトの `app.config` ファイルの中に接続文字列を作成します。 クラス ライブラリ プロジェクトでは `app.config` ファイルが使用されません。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、デザイン時のファイルで提供される接続文字列を使用します。 `app.config` 内の値を変更しても、アプリケーションの接続先データベースは変更されません。  
  
## <a name="cascade-delete"></a>連鎖削除  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は連鎖削除操作をサポートせず、認識もしません。 制約を持つテーブルの行を削除するには、次のいずれかを行う必要があります。  
  
-   データベース内の外部キー制約で `ON DELETE CASCADE` 規則を設定する。  
  
-   独自のコードを使用して、親オブジェクトの削除を妨げる子オブジェクトを最初に削除する。  
  
 このような操作を行わない場合、<xref:System.Data.SqlClient.SqlException> 例外がスローされます。  
  
 詳細については、次を参照してください。[する方法: 行をデータベースから削除](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)です。  
  
## <a name="expression-not-queryable"></a>クエリ可能でない式  
 場合、"式 [式] はクエリ不可能です。参照が存在するアセンブリですか?" エラー、次のことを確認します。  
  
-   アプリケーションが [!INCLUDE[compact_v35_short](../../../../../../includes/compact-v35-short-md.md)] を対象としている。  
  
-   `System.Core.dll` および `System.Data.Linq.dll` への参照が存在する。  
  
-   `Imports` および [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] のための `using` (<xref:System.Linq>) または <xref:System.Data.Linq> (C#) ディレクティブが存在する。  
  
## <a name="duplicatekeyexception"></a>DuplicateKeyException  
 デバッグ中、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]プロジェクト、エンティティのリレーションシップを走査する可能性があります。 キャッシュ内にこれらの項目は、これにより、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]プレゼンスの対応になります。 その後、同じキーの複数の行を生成する <xref:System.Data.Linq.Table%601.Attach%2A> や <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> などのメソッドを実行しようとした場合、<xref:System.Data.Linq.DuplicateKeyException> がスローされます。  
  
## <a name="string-concatenation-exceptions"></a>文字列連結の例外  
 `[n]text` と他の `[n][var]char` にマップされる複数のオペランドを連結する操作はサポートされません。 異なる 2 つの型のセットにマップされる文字列を連結しようとすると、例外がスローされます。 詳細については、次を参照してください。 [System.String メソッド](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)です。  
  
## <a name="skip-and-take-exceptions-in-sql-server-2000"></a>SQL Server 2000 の Skip 例外と Take 例外  
 SQL Server 2000 データベースに対して <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> または <xref:System.Linq.Queryable.Take%2A> を使用する際には、ID メンバー (<xref:System.Linq.Queryable.Skip%2A>) を使用する必要があります。 クエリは、(結合ではなく) 1 つのテーブルに対して実行されるか、<xref:System.Linq.Queryable.Distinct%2A>、<xref:System.Linq.Queryable.Except%2A>、<xref:System.Linq.Queryable.Intersect%2A>、または <xref:System.Linq.Queryable.Union%2A> 操作である必要があります。さらに、クエリに <xref:System.Linq.Queryable.Concat%2A> 操作を含めることはできません。 詳細については、「SQL Server 2000 のサポート」セクションを参照してください。[標準クエリ演算子変換](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)です。  
  
 この要件は [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)] には適用されません。  
  
## <a name="groupby-invalidoperationexception"></a>GroupBy InvalidOperationException  
 この例外は、たとえば <xref:System.Linq.Enumerable.GroupBy%2A> のように、`boolean` 式でグループ分けする `group x by (Phone==@phone)` クエリ内の列値が null である場合にスローされます。 式があるため、 `boolean`、キーがある推論`boolean`ではなく、`nullable``boolean`です。 変換された比較では、null 値が生成される、しようとしましたが割り当てる、`nullable``boolean`を`boolean`例外がスローされます。  
  
 この状態を回避する (null を false と扱う) には、次のような手法を使用してください。  
  
 `GroupBy="(Phone != null) && (Phone=@Phone)"`  
  
## <a name="oncreated-partial-method"></a>OnCreated() 部分メソッド  
 オブジェクト コンストラクターが呼び出されるたびに、生成されたメソッド `OnCreated()` が呼び出されます。これは、元の値をコピーするために [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] がコンストラクターを呼び出す場合にも当てはまります。 独自の部分クラスに `OnCreated()` メソッドを実装する場合には、この動作を考慮に入れてください。  
  
## <a name="see-also"></a>参照  
 [デバッグのサポート](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)  
 [よく寄せられる質問](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)

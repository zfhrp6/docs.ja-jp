---
title: "分散トランザクション | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 718b257c-bcb2-408e-b004-a7b0adb1c176
caps.latest.revision: 7
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 7
---
# 分散トランザクション
トランザクションとは、たとえば、1 つの単位として成功 \(コミット\) または失敗 \(アボート\) する関連タスク セットです。  *分散トランザクション*は、複数のリソースに影響するトランザクションです。  分散トランザクションがコミットされるためには、すべての参加要素が、すべてのデータ変更が永久的な変更となることを保証する必要があります。  システム クラッシュその他の予期しない出来事が発生した場合でも、変更は保持されます。  1 つの参加要素がこの保証に失敗しただけでも、トランザクション全体が失敗し、トランザクションのスコープ内のデータに対する変更がロールバックされます。  
  
> [!NOTE]
>  トランザクションがアクティブであるときに `DataReader` が開始された場合、トランザクションをコミットまたはロールバックしようとすると例外がスローされます。  
  
## System.Transactions の操作  
 .NET Framework では、分散トランザクションは <xref:System.Transactions> 名前空間内の API を介して管理されます。  複数の永続的なリソース マネージャーが関係する場合、<xref:System.Transactions> API は分散トランザクション処理を Microsoft Distributed Transaction Coordinator \(MS DTC\) などのトランザクション モニターに委任します。  詳細については、「[Transaction Fundamentals](http://msdn.microsoft.com/ja-jp/2a476b63-b94f-443f-992d-53943fdf4e5d)」を参照してください。  
  
 ADO.NET 2.0 では、`EnlistTransaction` メソッドを使用した分散トランザクションへの参加のサポートが導入されました。これにより、接続を <xref:System.Transactions.Transaction> インスタンスに参加させることができます。  ADO.NET の以前のバージョンでは、分散トランザクションへの明示的な参加は、接続の `EnlistDistributedTransaction` メソッドを使用して実行されていました。これによって <xref:System.EnterpriseServices.ITransaction> インスタンス内の接続を参加させることで、下位互換性を得ることができます。  Enterprise Services トランザクションの詳細については、「[Interoperability with Enterprise Services and COM\+ Transactions](http://msdn.microsoft.com/ja-jp/2e93b3c6-4d48-4b9b-82b2-7d5908a2c970)」を参照してください。  
  
 .NET Framework Provider for SQL Server で SQL Server データベースに対して <xref:System.Transactions> トランザクションを使用する場合は、軽量な <xref:System.Transactions.Transaction> が自動的に使用されます。  トランザクションは、必要に応じて完全な分散トランザクションに昇格させることができます。  詳細については、「[SQL Server と System.Transactions の統合](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)」を参照してください。  
  
> [!NOTE]
>  既定では、1 つの Oracle データベースが一度に参加できる分散トランザクションの最大数は 10 に設定されています。  Oracle データベースに接続している場合、トランザクション数が 10 個を超えると例外がスローされます。  Oracle では、分散トランザクション内での `DDL` はサポートされません。  
  
## 分散トランザクションへの自動参加  
 自動参加は、ADO.NET 接続を `System.Transactions` に統合する場合の既定の \(推奨される\) 方法です。  接続オブジェクトは、トランザクションがアクティブであると判定されると、既存の分散トランザクションに自動的に参加します。トランザクションがアクティブであることは、`System.Transaction` から見ると、`Transaction.Current` が null でないことを意味します。  自動トランザクション参加は、接続が開かれた場合に行われます。  その後は、コマンドがトランザクションのスコープ内で実行された場合でも、自動トランザクション参加は行われません。  <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=fullName> の接続文字列パラメーターとして `Enlist=false` を指定するか、<xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A?displayProperty=fullName> の接続文字パラメーターとして `OLE DB Services=-7` を指定すると、既存のトランザクションへの自動参加を無効にできます。  Oracle および ODBC 接続文字列パラメーターの詳細については、「<xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A?displayProperty=fullName>」および「<xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A?displayProperty=fullName>」を参照してください。  
  
## 手動による分散トランザクションへの参加  
 自動参加が無効になっている場合、または接続が開いた後に開始したトランザクションに参加する必要がある場合は、使用中のプロバイダーの <xref:System.Data.Common.DbConnection> オブジェクトの `EnlistTransaction` メソッドを使用して、既存の分散トランザクションに参加できます。  既存の分散トランザクションに参加すると、トランザクションがコミットまたはロールバックされた場合、データ ソースに対してコードで行った変更もコミットまたはロールバックされます。  
  
 分散トランザクションへの参加は、特にビジネス オブジェクトをプールする場合に適切です。  ビジネス オブジェクトが、開かれている接続と共にプールされている場合は、その接続を開くときだけ、自動トランザクション参加が行われます。  プールされているビジネス オブジェクトを使用して複数のトランザクションが実行される場合、そのオブジェクトの開かれている接続は、新しく開始されるトランザクションには自動参加しません。  この場合には、接続の自動トランザクション参加を無効にし、`EnlistTransaction` を使用して、接続をトランザクションに参加させることができます。  
  
 `EnlistTransaction`  は、既存のトランザクションを参照する <xref:System.Transactions.Transaction> 型の引数を 1 つ受け取ります。  接続の `EnlistTransaction` メソッドを呼び出した後、接続を使用してデータ ソースに対して行ったすべての変更は、トランザクションに組み込まれます。  null 値を渡すことで、現在の分散トランザクションから接続の参加が解除されます。  この接続は、`EnlistTransaction` を呼び出す前に開く必要があることに注意してください。  
  
> [!NOTE]
>  一度接続を明示的にトランザクションに参加させると、最初のトランザクションが終了するまでは、参加を解除したり別のトランザクションに参加させたりすることはできません。  
  
> [!CAUTION]
>  接続の <xref:System.Data.Common.DbConnection.BeginTransaction%2A> メソッドを使用してトランザクションが既に開始していた場合、`EnlistTransaction` は例外をスローします。  ただし、トランザクションがデータ ソースで開始されたローカル トランザクションである場合 \(たとえば <xref:System.Data.SqlClient.SqlCommand> を使用して BEGIN TRANSACTION ステートメントを明示的に実行した場合\)、`EnlistTransaction` はローカル トランザクションをロールバックし、要求されたように既存の分散トランザクションに参加します。  ローカル トランザクションがロールバックされたことは通知されないため、<xref:System.Data.Common.DbConnection.BeginTransaction%2A> を使用して開始したのではないローカル トランザクションについては、自分で管理する必要があります。  .NET Framework Data Provider for SQL Server \(`SqlClient`\) を SQL Server で使用する場合は、参加を試みると例外がスローされます。  その他の場合については検出されません。  
  
## SQL Server の昇格可能なトランザクション  
 SQL Server は、軽量のローカル トランザクションを必要に応じて分散トランザクションに自動的に昇格できる、昇格可能なトランザクションをサポートしています。  昇格可能なトランザクションは、必要な場合以外、分散トランザクションのオーバーヘッドの増加を引き起こすことはありません。  詳細とコード サンプルについては、「[SQL Server と System.Transactions の統合](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)」を参照してください。  
  
## 分散トランザクションの設定  
 分散トランザクションを使用するには、ネットワーク上の MS DTC を有効にする必要があります。  Windows ファイアウォールを有効にしている場合は、MS DTC サービスでネットワークを使用するか MS DTC ポートを開くことができるようにする必要があります。  
  
## 参照  
 [トランザクションと同時実行](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)   
 [SQL Server と System.Transactions の統合](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)
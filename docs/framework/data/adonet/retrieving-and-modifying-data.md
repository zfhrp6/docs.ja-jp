---
title: "ADO.NET でのデータの取得および変更 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# ADO.NET でのデータの取得および変更
データベース アプリケーションの主な機能は、データ ソースとの接続およびデータベースに格納されているデータの取得です。  ADO.NET の .NET Framework データ プロバイダーは、アプリケーションとデータ ソース間の橋渡し役として機能し、**DataReader** または **DataAdapter** を使用してコマンドを実行したり、データを取得できるようにします。  データベースに格納されているデータを更新する機能は、データベース アプリケーションの重要な機能の 1 つです。  ADO.NET でデータを更新するには、**DataAdapter** と <xref:System.Data.DataSet>、および **Command** オブジェクトを使用する必要があります。また、トランザクションを使用する必要がある場合もあります。  
  
## このセクションの内容  
 [データ ソースへの接続](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 データ ソースへの接続を確立する方法、および接続イベントを使用する方法について説明します。  
  
 [接続文字列](../../../../docs/framework/data/adonet/connection-strings.md)  
 接続文字列のキーワード、セキュリティ情報、セキュリティ情報の格納や取得など、接続文字列を使用するうえでのさまざまな側面について説明します。  
  
 [接続プール](../../../../docs/framework/data/adonet/connection-pooling.md)  
 .NET Framework Data Provider の接続プールについて説明します。  
  
 [コマンドとパラメーター](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 コマンドおよびコマンド ビルダーを作成する方法、パラメーターを構成する方法、およびコマンドを実行してデータを取得および変更する方法について説明します。  
  
 [DataAdapter と DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 DataReaders、DataAdapters、パラメーター、DataAdapter イベントの処理、およびバッチ操作の実行について説明します。  
  
 [トランザクションと同時実行](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 ローカル トランザクションや分散トランザクションの実行方法、およびオプティミスティック同時実行の使用方法について説明します。  
  
 [ID 値および Autonumber 値の取得](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] テーブルの **identity** 列または、Microsoft Access テーブルの **Autonumber** フィールド用に生成された値を、テーブルの挿入行の列に割り当てる例を示します。  `DataTable` での ID 値の結合について説明します。  
  
 [バイナリ データの取得](../../../../docs/framework/data/adonet/retrieving-binary-data.md)  
 `CommandBehavior`.`SequentialAccess` を使用するバイナリ データまたは大きなデータ構造を取得して、`DataReader` の既定の動作を変更する方法について説明します。  
  
 [ストアド プロシージャでのデータの変更](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 ストアド プロシージャの入力パラメーターおよび出力パラメーターを使用してデータベースに行を挿入し、新しい ID 値を返す方法について説明します。  
  
 [データベース スキーマ情報の取得](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 データベースまたはカタログ、データベース内のテーブルおよびビュー、テーブルに対して存在する制約、およびその他のスキーマ情報をデータ ソースから取得する方法について説明します。  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 プロバイダー ファクトリ モデルについて説明し、`System.Data.Common` 名前空間の基本クラスの使用方法を示します。  
  
 [ADO.NET でのデータ トレース](../../../../docs/framework/data/adonet/data-tracing.md)  
 ADO.NET が備える組み込みデータ トレース機能のしくみについて説明します。  
  
 [ADO.NET でのパフォーマンス カウンター](../../../../docs/framework/data/adonet/performance-counters.md)  
 `SqlClient` および `OracleClient` で使用できるパフォーマンス カウンターについて説明します。  
  
 [非同期プログラミング](../../../../docs/framework/data/adonet/asynchronous-programming.md)  
 非同期プログラミングに対する [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] サポートについて説明します。  
  
 [SqlClient ストリーミング サポート](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md)  
 完全にメモリに読み込むことなく [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] からデータをストリームするアプリケーションの作成方法について説明します。  
  
## 参照  
 [ADO.NET でのデータ型のマッピング](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)   
 [DataSets、DataTables、および DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET アプリケーションのセキュリティ保護](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)   
 [SQL Server と ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)
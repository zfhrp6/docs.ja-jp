---
title: "ADO.NET の新機能 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3bb65d38-cce2-46f5-b979-e5c505e95e10
caps.latest.revision: 25
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 25
---
# ADO.NET の新機能
[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] の [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] では、次の機能が追加されています。  
  
## SqlClient Data Provider  
 [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] の [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] では、次の機能が追加されています。  
  
-   ConnectRetryCount と ConnectRetryInterval の接続文字列キーワード \(<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>\) を使用すると、アイドル状態の接続の復元機能を制御できます。  
  
-   [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] からアプリケーションへのストリーミング サポートで、サーバー上のデータが構造化されていないシナリオをサポートします。  詳細については、「[SqlClient ストリーミング サポート](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md)」を参照してください。  
  
-   非同期のプログラミングにサポートが追加されています。  詳細については、「[非同期プログラミング](../../../../docs/framework/data/adonet/asynchronous-programming.md)」を参照してください。  
  
-   接続エラーは、拡張イベント ログに記録されるようになりました。  詳細については、「[ADO.NET でのデータ トレース](../../../../docs/framework/data/adonet/data-tracing.md)」を参照してください。  
  
-   SqlClient は、[!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] の高可用性、障害復旧機能である AlwaysOn をサポートするようになりました。  詳細については、「[高可用性障害復旧のための SqlClient サポート](../../../../docs/framework/data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md)」を参照してください。  
  
-   [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] 認証を使用している場合、パスワードは <xref:System.Security.SecureString> として渡すことができます。  詳細については、「<xref:System.Data.SqlClient.SqlCredential>」を参照してください。  
  
-   `TrustServerCertificate` が false であり、`Encrypt` が true の場合は、接続文字列に指定されているサーバー名 \(または IP アドレス\) に [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] SSL 証明書が正確に一致する必要があります。  それ以外の場合、接続試行は失敗します。  詳細については、「<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>」の `Encrypt` 接続オプションの説明を参照してください。  
  
     この変更によって既存のアプリケーションが接続しなくなる場合、次のいずれかを使用してアプリケーションを修正できます。  
  
    -   共通名 \(CN\) またはサブジェクト代替名 \(SAN\) フィールドに短い名前を指定する証明書を発行します。  このソリューションは、データベース ミラーリングをする場合に有効です。  
  
    -   短い名前を完全修飾ドメイン名にマップする別名を追加します。  
  
    -   接続文字列では完全修飾ドメイン名を使用します。  
  
-   SqlClient は拡張保護をサポートしています。  拡張保護の詳細については、「[拡張保護を使用したデータベース エンジンへの接続](http://go.microsoft.com/fwlink/?LinkId=219978)」を参照してください。  
  
-   SqlClient は LocalDB データベースへの接続をサポートします。  詳細については、「[SqlClient による LocalDB のサポート](../../../../docs/framework/data/adonet/sql/sqlclient-support-for-localdb.md)」を参照してください。  
  
-   `Type System Version=SQL Server 2012;` は、`Type System Version` 接続プロパティに渡す新しい値です。  `Type System Version=Latest;` 値は廃止されており、`Type System Version=SQL Server 2008;` と同等になっています。  詳細については、「<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>」を参照してください。  
  
-   SqlClient は、スパース列に追加のサポートを提供します。このサポートは SQL Server 2008 で追加された機能です。  アプリケーションがスパース列を使用するテーブルのデータに既にアクセスしていると、パフォーマンスが向上します。  <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> の IsColumnSet 列は、列が列セットのメンバーであるスパース列であるかどうかを示します。  <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> は、列がスパース列であるかどうかを示します \(詳細については、[SQL Server スキーマ コレクション](../../../../docs/framework/data/adonet/sql-server-schema-collections.md) を参照してください\)。  スパース列の詳細については、「[スパース列の使用](http://go.microsoft.com/fwlink/?LinkId=224244)」を参照してください。  
  
-   空間データ型を含むアセンブリ Microsoft.SqlServer.Types.dll は、Version 10.0 から Version 11.0 にアップグレードされました。  このアセンブリを参照するホスト アプリケーションでは、エラーが発生する可能性があります。  詳細については、「[データベース エンジン機能の重大な変更](http://go.microsoft.com/fwlink/?LinkId=224367)」を参照してください。  
  
## ADO.NET Entity Framework  
 [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] は、Entity Framework 5.0 を操作するときに、新しいシナリオを有効にする API を追加します。  Entity Framework 5.0 に追加された機能および機能強化に関する詳細については、「[新機能](http://go.microsoft.com/fwlink/?LinkID=251106)」と「[Entity Framework リリースおよびバージョン管理](http://go.microsoft.com/fwlink/?LinkId=234899)」を参照してください。  
  
## 参照  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)   
 [ADO.NET の概要](../../../../docs/framework/data/adonet/ado-net-overview.md)   
 [SQL Server と ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)   
 [What's New in WCF Data Services](http://msdn.microsoft.com/ja-jp/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)
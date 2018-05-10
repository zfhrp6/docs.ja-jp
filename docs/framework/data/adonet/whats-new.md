---
title: どのような&#39;ADO.NET の
ms.date: 03/30/2017
ms.assetid: 3bb65d38-cce2-46f5-b979-e5c505e95e10
ms.openlocfilehash: eb06681a55f1bd2abffb2e7169fa3bf892cd7313
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="what39s-new-in-adonet"></a>どのような&#39;ADO.NET の
[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] の [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] では、次の機能が追加されています。  
  
## <a name="sqlclient-data-provider"></a>SqlClient Data Provider  
 次の機能が追加されて、 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for SQL Server で[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]:  
  
-   ConnectRetryCount と ConnectRetryInterval の接続文字列キーワード (<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>) を使用すると、アイドル状態の接続の復元機能を制御できます。  
  
-   SQL Server からアプリケーションへのサポートをストリーミングすると、サーバー上のデータが構造化であるシナリオがサポートしています。  参照してください[SqlClient ストリーミング サポート](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md)詳細についてはします。  
  
-   非同期のプログラミングにサポートが追加されています。  参照してください[非同期プログラミング](../../../../docs/framework/data/adonet/asynchronous-programming.md)詳細についてはします。  
  
-   接続エラーは、拡張イベント ログに記録されるようになりました。 詳細については、「[ADO.NET のデータ追跡](../../../../docs/framework/data/adonet/data-tracing.md)」を参照してください。  
  
-   SqlClient では、SQL Server の高可用性、障害復旧機能で AlwaysOn をサポートできるようになりました。 詳細については、次を参照してください。 [High Availability, Disaster Recovery の SqlClient サポート](../../../../docs/framework/data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md)です。  
  
-   パスワードとして渡すことが、 <xref:System.Security.SecureString> SQL Server 認証を使用する場合。 詳細については、「<xref:System.Data.SqlClient.SqlCredential>」を参照してください。  
  
-   ときに`TrustServerCertificate`が false と`Encrypt`が true の場合、SQL Server の SSL 証明書にサーバー名 (または IP アドレス) が正確に一致、サーバー名 (または IP アドレス)、接続文字列で指定します。 それ以外の場合、接続試行は失敗します。 詳細については、「`Encrypt`」の <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> 接続オプションの説明を参照してください。  
  
     この変更によって既存のアプリケーションが接続しなくなる場合、次のいずれかを使用してアプリケーションを修正できます。  
  
    -   共通名 (CN) またはサブジェクト代替名 (SAN) フィールドに短い名前を指定する証明書を発行します。 このソリューションは、データベース ミラーリングをする場合に有効です。  
  
    -   短い名前を完全修飾ドメイン名にマップする別名を追加します。  
  
    -   接続文字列では完全修飾ドメイン名を使用します。  
  
-   SqlClient は拡張保護をサポートしています。 拡張保護の詳細については、次を参照してください。 [、データベース エンジンを使用して拡張保護に接続する](http://go.microsoft.com/fwlink/?LinkId=219978)です。  
  
-   SqlClient は LocalDB データベースへの接続をサポートします。 詳細については、次を参照してください。 [LocalDB の SqlClient サポート](../../../../docs/framework/data/adonet/sql/sqlclient-support-for-localdb.md)です。  
  
-   `Type System Version=SQL Server 2012;` は、`Type System Version` 接続プロパティに渡す新しい値です。 `Type System Version=Latest;` 値は廃止されており、`Type System Version=SQL Server 2008;` と同等になっています。 詳細については、「<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>」を参照してください。  
  
-   SqlClient は、スパース列に追加のサポートを提供します。このサポートは SQL Server 2008 で追加された機能です。 アプリケーションがスパース列を使用するテーブルのデータに既にアクセスしていると、パフォーマンスが向上します。 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> の IsColumnSet 列は、列が列セットのメンバーであるスパース列であるかどうかを示します。 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> 列がスパース列であることを示します (を参照してください[SQL Server スキーマ コレクション](../../../../docs/framework/data/adonet/sql-server-schema-collections.md)詳細については)。 スパース列の詳細については、次を参照してください。[スパース列の使用](http://go.microsoft.com/fwlink/?LinkId=224244)です。  
  
-   空間データ型を含むアセンブリ Microsoft.SqlServer.Types.dll は、Version 10.0 から Version 11.0 にアップグレードされました。 このアセンブリを参照するホスト アプリケーションでは、エラーが発生する可能性があります。 詳細については、次を参照してください。[データベース エンジン機能の重大な変更](http://go.microsoft.com/fwlink/?LinkId=224367)です。  
  
## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework  
 [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] は、Entity Framework 5.0 を操作するときに、新しいシナリオを有効にする API を追加します。 および Entity Framework 5.0 に追加された機能強化の詳細については、次のトピックを参照してください:[新](http://go.microsoft.com/fwlink/?LinkID=251106)と[Entity Framework リリースおよびバージョン管理](http://go.microsoft.com/fwlink/?LinkId=234899)です。  
  
## <a name="see-also"></a>関連項目  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 [ADO.NET の概要](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [SQL Server と ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 [WCF Data Services の新機能](http://msdn.microsoft.com/library/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)

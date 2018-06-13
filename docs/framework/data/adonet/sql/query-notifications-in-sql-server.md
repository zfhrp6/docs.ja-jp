---
title: SQL Server のクエリ通知
ms.date: 03/30/2017
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.openlocfilehash: 60ab686437f764a006fca5a2043d02288ea46d0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364072"
---
# <a name="query-notifications-in-sql-server"></a>SQL Server のクエリ通知
クエリ通知は Service Broker インフラストラクチャに基づいて構築されており、データが変更されたときにクエリ通知を使用してアプリケーションに通知できます。 この機能は、Web アプリケーションなど、データベースから情報のキャッシュを提供し、ソース データが変更された場合に通知を必要とするアプリケーションに特に役立ちます。  
  
 ADO.NET を使用してクエリ通知機能を実装する方法は 3 つあります。  
  
1.  基本レベルの実装は、`SqlNotificationRequest` クラスによって行われます。これによってサーバー側の機能が公開され、通知要求を伴うコマンドを実行できます。  
  
2.  高レベルの実装は、`SqlDependency` クラスによって行われます。このクラスでは、ソース アプリケーションと SQL Server 間の通知機能が高度に抽象化され、その依存関係を使用してサーバー内の変更を検出することができます。 マネージ クライアント アプリケーションが .NET Framework Data Provider for SQL Server を使用して SQL Server の通知機能を活用するには、ほとんどの場合、これが最も簡単かつ効果的な方法です。  
  
3.  さらに、ASP.NET 2.0 以降を使用して構築された Web アプリケーションでは、`SqlCacheDependency` ヘルパー クラスを使用できます。  
  
 クエリ通知は、基になるデータの変更に応じて表示またはキャッシュを更新する必要があるアプリケーションで使用されます。 Microsoft SQL Server では、最初に取得したものと異なる結果セットが同じコマンドで得られた場合には、.NET Framework アプリケーションから SQL Server にコマンドを送信して通知を要求することができます。 サーバーで生成された通知は、キューを通じて送信された後に処理されます。  
  
 通知は SELECT ステートメントおよび EXECUTE ステートメントに対して設定できます。 EXECUTE ステートメントを使用した場合、SQL Server では、EXECUTE ステートメント自体ではなく、EXECUTE ステートメントで実行されたコマンドに対する通知が登録されます。 コマンドは、SELECT ステートメントの要件と制限を満たしている必要があります。 通知を登録するコマンドに複数のステートメントが含まれている場合、データベース エンジンによりバッチ内のステートメントごとに通知が作成されます。  
  
 を開発しているアプリケーション データが変更されたときに、信頼性の高いの 1 秒未満の通知が必要な場合は、セクションを参照**効率的なクエリ通知戦略の計画**と**クエリ通知に代わる方法**で、[通知の計画](http://go.microsoft.com/fwlink/?LinkId=211984)SQL Server オンライン ブックの「します。 クエリ通知と SQL Server Service Broker の詳細については、次の SQL Server オンライン ブックのトピックへのリンクを参照してください。  
  
 **SQL Server オンライン ブック**  
  
-   [クエリ通知の使用](http://msdn.microsoft.com/library/ms175110.aspx)  
  
-   [クエリ通知の作成](http://msdn.microsoft.com/library/ms181122.aspx)  
  
-   [Service Broker](http://msdn.microsoft.com/library/bb522889.aspx)  
  
-   [Service Broker 開発者向けの情報](http://msdn.microsoft.com/library/ms166100.aspx)  
  
-   [開発 (Service Broker)](http://msdn.microsoft.com/library/bb522908.aspx)  
  
## <a name="in-this-section"></a>このセクションの内容  
 [クエリ通知の有効化](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md)  
 クエリ通知を有効にするための要件を含め、クエリ通知の使用方法について説明します。  
  
 [ASP.NET アプリケーションでの SqlDependency](../../../../../docs/framework/data/adonet/sql/sqldependency-in-an-aspnet-app.md)  
 ASP.NET アプリケーションからクエリ通知を使用する方法について説明します。  
  
 [SqlDependency を使用した変更の検出](../../../../../docs/framework/data/adonet/sql/detecting-changes-with-sqldependency.md)  
 最初に取得された結果と異なるクエリ結果を検出する方法について説明します。  
  
 [SqlCommand の実行と SqlNotificationRequest](../../../../../docs/framework/data/adonet/sql/sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 クエリ通知を使用する <xref:System.Data.SqlClient.SqlCommand> オブジェクトの構成例を示します。  
  
## <a name="reference"></a>参照  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 <xref:System.Data.Sql.SqlNotificationRequest> クラスおよびそのすべてのメンバーについて説明します。  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 <xref:System.Data.SqlClient.SqlDependency> クラスおよびそのすべてのメンバーについて説明します。  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 <xref:System.Web.Caching.SqlCacheDependency> クラスおよびそのすべてのメンバーについて説明します。  
  
## <a name="see-also"></a>関連項目  
 [SQL Server と ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)

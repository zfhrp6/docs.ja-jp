---
title: "クエリ通知の有効化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 473f1ca54d54a1d852edaed424729778e5a7513d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="enabling-query-notifications"></a><span data-ttu-id="5a126-102">クエリ通知の有効化</span><span class="sxs-lookup"><span data-stu-id="5a126-102">Enabling Query Notifications</span></span>
<span data-ttu-id="5a126-103">クエリ通知を使用するアプリケーションには、いくつか共通する要件があります。</span><span class="sxs-lookup"><span data-stu-id="5a126-103">Applications that consume query notifications have a common set of requirements.</span></span> <span data-ttu-id="5a126-104">SQL クエリ通知をサポートするには、データ ソースが正しく設定され、ユーザーがクライアント側およびサーバー側の正しい権限を所有している必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a126-104">Your data source must be correctly configured to support SQL query notifications, and the user must have the correct client-side and server-side permissions.</span></span>  
  
 <span data-ttu-id="5a126-105">クエリ通知を使用するためには、次のことが必要です。</span><span class="sxs-lookup"><span data-stu-id="5a126-105">To use query notifications you must:</span></span>  
  
-   <span data-ttu-id="5a126-106">データベースのクエリ通知を有効にする</span><span class="sxs-lookup"><span data-stu-id="5a126-106">Enable query notifications for your database.</span></span>  
  
-   <span data-ttu-id="5a126-107">データベースへの接続に使用するユーザー ID に対して、必要なアクセス許可を設定する</span><span class="sxs-lookup"><span data-stu-id="5a126-107">Ensure that the user ID used to connect to the database has the necessary permissions.</span></span>  
  
-   <span data-ttu-id="5a126-108"><xref:System.Data.SqlClient.SqlCommand> オブジェクトを使用して、関連する通知オブジェクト (<xref:System.Data.SqlClient.SqlDependency> または <xref:System.Data.Sql.SqlNotificationRequest> のいずれか) を持つ有効な SELECT ステートメントを実行する</span><span class="sxs-lookup"><span data-stu-id="5a126-108">Use a <xref:System.Data.SqlClient.SqlCommand> object to execute a valid SELECT statement with an associated notification object—either <xref:System.Data.SqlClient.SqlDependency> or <xref:System.Data.Sql.SqlNotificationRequest>.</span></span>  
  
-   <span data-ttu-id="5a126-109">監視対象のデータが変更された場合に通知を処理するコードを設定する</span><span class="sxs-lookup"><span data-stu-id="5a126-109">Provide code to process the notification if the data being monitored changes.</span></span>  
  
## <a name="query-notifications-requirements"></a><span data-ttu-id="5a126-110">クエリ通知の要件</span><span class="sxs-lookup"><span data-stu-id="5a126-110">Query Notifications Requirements</span></span>  
 <span data-ttu-id="5a126-111">クエリ通知は、特定の要件を満たす SELECT ステートメントでのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="5a126-111">Query notifications are supported only for SELECT statements that meet a list of specific requirements.</span></span> <span data-ttu-id="5a126-112">次の表に、SQL Server オンライン ブックの Service Broker とクエリ通知に関するドキュメントへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="5a126-112">The following table provides links to the Service Broker and Query Notifications documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="5a126-113">**SQL Server オンライン ブック**</span><span class="sxs-lookup"><span data-stu-id="5a126-113">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="5a126-114">クエリ通知の作成</span><span class="sxs-lookup"><span data-stu-id="5a126-114">Creating a Query for Notification</span></span>](http://msdn.microsoft.com/library/ms181122.aspx)  
  
-   [<span data-ttu-id="5a126-115">Service Broker のセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="5a126-115">Security Considerations for Service Broker</span></span>](http://msdn.microsoft.com/library/ms166059.aspx)  
  
-   [<span data-ttu-id="5a126-116">セキュリティと保護 (Service Broker)</span><span class="sxs-lookup"><span data-stu-id="5a126-116">Security and Protection (Service Broker)</span></span>](http://msdn.microsoft.com/library/bb522911.aspx)  
  
-   [<span data-ttu-id="5a126-117">通知サービスのセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="5a126-117">Security Considerations for Notifications Services</span></span>](http://msdn.microsoft.com/library/ms172604.aspx)  
  
-   [<span data-ttu-id="5a126-118">クエリ通知の権限</span><span class="sxs-lookup"><span data-stu-id="5a126-118">Query Notification Permissions</span></span>](http://msdn.microsoft.com/library/ms188311.aspx)  
  
-   [<span data-ttu-id="5a126-119">Service Broker の国際化に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="5a126-119">International Considerations for Service Broker</span></span>](http://msdn.microsoft.com/library/ms166028.aspx)  
  
-   [<span data-ttu-id="5a126-120">ソリューション設計に関する考慮事項 (Service Broker)</span><span class="sxs-lookup"><span data-stu-id="5a126-120">Solution Design Considerations (Service Broker)</span></span>](http://msdn.microsoft.com/library/bb522899.aspx)  
  
-   [<span data-ttu-id="5a126-121">Service Broker 開発者向けの情報</span><span class="sxs-lookup"><span data-stu-id="5a126-121">Service Broker Developer InfoCenter</span></span>](http://msdn.microsoft.com/library/ms166100.aspx)  
  
-   [<span data-ttu-id="5a126-122">開発者ガイド (Service Broker)</span><span class="sxs-lookup"><span data-stu-id="5a126-122">Developer's Guide (Service Broker)</span></span>](http://msdn.microsoft.com/library/bb522908.aspx)  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a><span data-ttu-id="5a126-123">サンプル コードを実行するためのクエリ通知の有効化</span><span class="sxs-lookup"><span data-stu-id="5a126-123">Enabling Query Notifications to Run Sample Code</span></span>  
 <span data-ttu-id="5a126-124">Service Broker を有効にする、 **AdventureWorks**データベースの SQL Server Management Studio を使用して、次の TRANSACT-SQL ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="5a126-124">To enable Service Broker on the **AdventureWorks** database by using SQL Server Management Studio, execute the following Transact-SQL statement:</span></span>  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 <span data-ttu-id="5a126-125">クエリ通知のサンプルを正しく実行するには、次の Transact-SQL ステートメントをデータベース サーバー上で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a126-125">For the query notification samples to run correctly, the following Transact-SQL statements must be executed on the database server.</span></span>  
  
```  
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a><span data-ttu-id="5a126-126">クエリ通知のアクセス許可</span><span class="sxs-lookup"><span data-stu-id="5a126-126">Query Notifications Permissions</span></span>  
 <span data-ttu-id="5a126-127">通知を要求するコマンドを実行するユーザーは、特定のサーバーに対する SUBSCRIBE QUERY NOTIFICATIONS データベース アクセス許可を必要とします。</span><span class="sxs-lookup"><span data-stu-id="5a126-127">Users who execute commands requesting notification must have SUBSCRIBE QUERY NOTIFICATIONS database permission on the server.</span></span>  
  
 <span data-ttu-id="5a126-128">部分信頼の状態で実行されるクライアント側のコードには、<xref:System.Data.SqlClient.SqlClientPermission> が必要です。</span><span class="sxs-lookup"><span data-stu-id="5a126-128">Client-side code that runs in a partial trust situation requires the <xref:System.Data.SqlClient.SqlClientPermission>.</span></span>  
  
 <span data-ttu-id="5a126-129">次のコードでは、<xref:System.Data.SqlClient.SqlClientPermission> オブジェクトを作成して、<xref:System.Security.Permissions.PermissionState> を <xref:System.Security.Permissions.PermissionState.Unrestricted> に設定します。</span><span class="sxs-lookup"><span data-stu-id="5a126-129">The following code creates a <xref:System.Data.SqlClient.SqlClientPermission> object, setting the <xref:System.Security.Permissions.PermissionState> to <xref:System.Security.Permissions.PermissionState.Unrestricted>.</span></span> <span data-ttu-id="5a126-130"><xref:System.Security.CodeAccessPermission.Demand%2A> を指定すると、呼び出し履歴の上流に、権限の付与されていない呼び出し元が 1 つでも存在した場合、実行時に強制的に <xref:System.Security.SecurityException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="5a126-130">The <xref:System.Security.CodeAccessPermission.Demand%2A> will force a <xref:System.Security.SecurityException> at run time if all callers higher in the call stack have not been granted the permission.</span></span>  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a><span data-ttu-id="5a126-131">通知オブジェクトの選択</span><span class="sxs-lookup"><span data-stu-id="5a126-131">Choosing a Notification Object</span></span>  
 <span data-ttu-id="5a126-132">クエリ通知 API は、通知を処理するために <xref:System.Data.SqlClient.SqlDependency> と <xref:System.Data.Sql.SqlNotificationRequest> という 2 つのオブジェクトを提供します。</span><span class="sxs-lookup"><span data-stu-id="5a126-132">The query notifications API provides two objects to process notifications: <xref:System.Data.SqlClient.SqlDependency> and <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="5a126-133">通常、ASP.NET 以外のほとんどのアプリケーションでは、<xref:System.Data.SqlClient.SqlDependency> オブジェクトを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a126-133">In general, most non-ASP.NET applications should use the <xref:System.Data.SqlClient.SqlDependency> object.</span></span> <span data-ttu-id="5a126-134">ASP.NET アプリケーションは、高レベルの <xref:System.Web.Caching.SqlCacheDependency> を使用する必要があります。これは <xref:System.Data.SqlClient.SqlDependency> をラップし、通知オブジェクトとキャッシュ オブジェクトを管理するためのフレームワークになります。</span><span class="sxs-lookup"><span data-stu-id="5a126-134">ASP.NET applications should use the higher-level <xref:System.Web.Caching.SqlCacheDependency>, which wraps <xref:System.Data.SqlClient.SqlDependency> and provides a framework for administering the notification and cache objects.</span></span>  
  
### <a name="using-sqldependency"></a><span data-ttu-id="5a126-135">SqlDependency の使用</span><span class="sxs-lookup"><span data-stu-id="5a126-135">Using SqlDependency</span></span>  
 <span data-ttu-id="5a126-136"><xref:System.Data.SqlClient.SqlDependency> を使用するには、使用する SQL Server データベースに対して Service Broker を有効にし、通知を受け取るためのアクセス許可をユーザーに与える必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a126-136">To use <xref:System.Data.SqlClient.SqlDependency>, Service Broker must be enabled for the SQL Server database being used, and users must have permissions to receive notifications.</span></span> <span data-ttu-id="5a126-137">通知キューなどの Service Broker オブジェクトは、あらかじめ定義されています。</span><span class="sxs-lookup"><span data-stu-id="5a126-137">Service Broker objects, such as the notification queue, are predefined.</span></span>  
  
 <span data-ttu-id="5a126-138">さらに、<xref:System.Data.SqlClient.SqlDependency> によってワーカー スレッドが自動的に開始され、キューにポストされた通知を処理すると共に、Service Broker メッセージが解析され、情報がイベント引数データとして公開されます。</span><span class="sxs-lookup"><span data-stu-id="5a126-138">In addition, <xref:System.Data.SqlClient.SqlDependency> automatically launches a worker thread to process notifications as they are posted to the queue; it also parses the Service Broker message, exposing the information as event argument data.</span></span> <span data-ttu-id="5a126-139"><xref:System.Data.SqlClient.SqlDependency> は `Start` メソッドを呼び出し、データベースに対する依存関係を設定して初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a126-139"><xref:System.Data.SqlClient.SqlDependency> must be initialized by calling the `Start` method to establish a dependency to the database.</span></span> <span data-ttu-id="5a126-140">これは、必要となる各データベース接続に対するアプリケーション初期化中に、1 回だけ呼び出す必要がある静的メソッドです。</span><span class="sxs-lookup"><span data-stu-id="5a126-140">This is a static method that needs to be called only once during application initialization for each database connection required.</span></span> <span data-ttu-id="5a126-141">`Stop` メソッドは、作成された依存関係を持つ接続それぞれのアプリケーションの終了時に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a126-141">The `Stop` method should be called at application termination for each dependency connection that was made.</span></span>  
  
### <a name="using-sqlnotificationrequest"></a><span data-ttu-id="5a126-142">SqlNotificationRequest の使用</span><span class="sxs-lookup"><span data-stu-id="5a126-142">Using SqlNotificationRequest</span></span>  
 <span data-ttu-id="5a126-143">これに対し <xref:System.Data.Sql.SqlNotificationRequest> では、待機するインフラストラクチャ全体を自分で実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a126-143">In contrast, <xref:System.Data.Sql.SqlNotificationRequest> requires you to implement the entire listening infrastructure yourself.</span></span> <span data-ttu-id="5a126-144">さらに、キュー、サービス、およびキューによってサポートされるメッセージの種類など、サポート対象となるすべての Service Broker オブジェクトを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a126-144">In addition, all the supporting Service Broker objects such as the queue, service, and message types supported by the queue must be defined.</span></span> <span data-ttu-id="5a126-145">手動によるこの方法は、使用しているアプリケーションで特殊な通知メッセージや通知動作が必要な場合、またはそのアプリケーションが Service Broker アプリケーションの一部である場合に使用すると便利です。</span><span class="sxs-lookup"><span data-stu-id="5a126-145">This manual approach is useful if your application requires special notification messages or notification behaviors, or if your application is part of a larger Service Broker application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a126-146">参照</span><span class="sxs-lookup"><span data-stu-id="5a126-146">See Also</span></span>  
 [<span data-ttu-id="5a126-147">SQL Server のクエリ通知</span><span class="sxs-lookup"><span data-stu-id="5a126-147">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [<span data-ttu-id="5a126-148">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="5a126-148">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)

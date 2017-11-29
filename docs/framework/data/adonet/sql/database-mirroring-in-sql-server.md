---
title: "SQL Server のデータベース ミラーリング"
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
ms.assetid: 89befaff-bb46-4290-8382-e67cdb0e3de9
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0ec0b25976b1b54c91fcdebbc80bc048d2b48823
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="database-mirroring-in-sql-server"></a><span data-ttu-id="f3920-102">SQL Server のデータベース ミラーリング</span><span class="sxs-lookup"><span data-stu-id="f3920-102">Database Mirroring in SQL Server</span></span>
<span data-ttu-id="f3920-103">SQL Server のデータベース ミラーリング機能を使用すると、スタンバイ サーバー上に SQL Server データベースのコピー (ミラー) を保持できます。</span><span class="sxs-lookup"><span data-stu-id="f3920-103">Database mirroring in SQL Server allows you to keep a copy, or mirror, of a SQL Server database on a standby server.</span></span> <span data-ttu-id="f3920-104">ミラーリングは、常にデータのコピーが 2 つ別々に存在することを保証し、高可用性とデータの完全な冗長性をもたらします。</span><span class="sxs-lookup"><span data-stu-id="f3920-104">Mirroring ensures that two separate copies of the data exist at all times, providing high availability and complete data redundancy.</span></span> <span data-ttu-id="f3920-105">.NET Data Provider for SQL Server では、データベース ミラーリングが暗黙的にサポートされているため、SQL Server データベース用に構成されている場合は、開発者が操作を行ったり、コードを作成したりする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f3920-105">The .NET Data Provider for SQL Server provides implicit support for database mirroring, so that the developer does not need to take any action or write any code once it has been configured for a SQL Server database.</span></span> <span data-ttu-id="f3920-106">さらに、<xref:System.Data.SqlClient.SqlConnection> オブジェクトは、<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> 内のフェールオーバー パートナー サーバーの名前を指定できる明示的な接続モードをサポートします。</span><span class="sxs-lookup"><span data-stu-id="f3920-106">In addition, the <xref:System.Data.SqlClient.SqlConnection> object supports an explicit connection mode that allows supplying the name of a failover partner server in the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="f3920-107">次の簡略化された一連のイベントは、ミラーリング用に構成されているデータベースを対象にする <xref:System.Data.SqlClient.SqlConnection> オブジェクトで発生します。</span><span class="sxs-lookup"><span data-stu-id="f3920-107">The following simplified sequence of events occurs for a <xref:System.Data.SqlClient.SqlConnection> object that targets a database configured for mirroring:</span></span>  
  
1.  <span data-ttu-id="f3920-108">クライアント アプリケーションが正常にプリンシパル データベースに接続し、クライアント上でキャッシュされたパートナー サーバーの名前をサーバーが返信します。</span><span class="sxs-lookup"><span data-stu-id="f3920-108">The client application successfully connects to the principal database, and the server sends back the name of the partner server, which is then cached on the client.</span></span>  
  
2.  <span data-ttu-id="f3920-109">プリンシパル データベースが存在するサーバーで障害が発生したか、接続が中断された場合、接続とトランザクションの状態は失われます。</span><span class="sxs-lookup"><span data-stu-id="f3920-109">If the server containing the principal database fails or connectivity is interrupted, connection and transaction state is lost.</span></span> <span data-ttu-id="f3920-110">クライアント アプリケーションは、プリンシパル データベースへの接続を再確立しようとして、失敗します。</span><span class="sxs-lookup"><span data-stu-id="f3920-110">The client application attempts to re-establish a connection to the principal database and fails.</span></span>  
  
3.  <span data-ttu-id="f3920-111">次に、クライアント アプリケーションでは、パートナー サーバー上のミラー データベースへの接続を透過的に確立しようとします。</span><span class="sxs-lookup"><span data-stu-id="f3920-111">The client application then transparently attempts to establish a connection to the mirror database on the partner server.</span></span> <span data-ttu-id="f3920-112">この処理に成功すると、新しいプリンシパル データベースとなるミラー データベースに、接続がリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="f3920-112">If it succeeds, the connection is redirected to the mirror database, which then becomes the new principal database.</span></span>  
  
## <a name="specifying-the-failover-partner-in-the-connection-string"></a><span data-ttu-id="f3920-113">接続文字列でのフェールオーバー パートナーの指定</span><span class="sxs-lookup"><span data-stu-id="f3920-113">Specifying the Failover Partner in the Connection String</span></span>  
 <span data-ttu-id="f3920-114">接続文字列でフェールオーバー パートナー サーバーの名前を指定すると、クライアント アプリケーションが最初に接続するときにプリンシパル データベースを使用できない場合、クライアントはフェールオーバー パートナーへの接続を透過的に試行します。</span><span class="sxs-lookup"><span data-stu-id="f3920-114">If you supply the name of a failover partner server in the connection string, the client will transparently attempt a connection with the failover partner if the principal database is unavailable when the client application first connects.</span></span>  
  
```  
";Failover Partner=PartnerServerName"  
```  
  
 <span data-ttu-id="f3920-115">接続文字列のフェールオーバー パートナー サーバーの名前を省略すると、クライアント アプリケーションが最初に接続するときにプリンシパル データベースが使用できない場合、<xref:System.Data.SqlClient.SqlException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="f3920-115">If you omit the name of the failover partner server and the principal database is unavailable when the client application first connects then a <xref:System.Data.SqlClient.SqlException> is raised.</span></span>  
  
 <span data-ttu-id="f3920-116"><xref:System.Data.SqlClient.SqlConnection> が正常に開かれた場合、サーバーからフェールオーバー パートナーの名前が返され、接続文字列に指定されている値を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="f3920-116">When a <xref:System.Data.SqlClient.SqlConnection> is successfully opened, the failover partner name is returned by the server and supersedes any values supplied in the connection string.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3920-117">データベース ミラーリング シナリオでは、接続文字列で初期カタログやデータベース名を明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3920-117">You must explicitly specify the initial catalog or database name in the connection string for database mirroring scenarios.</span></span> <span data-ttu-id="f3920-118">クライアントが、初期カタログやデータベースが明示的に指定されていない接続に関するフェールオーバー情報を受信する場合は、このフェールオーバー情報はキャッシュされず、アプリケーションはプリンシパル サーバーでの障害発生時にフェールオーバーを試行しません。</span><span class="sxs-lookup"><span data-stu-id="f3920-118">If the client receives failover information on a connection that doesn't have an explicitly specified initial catalog or database, the failover information is not cached and the application does not attempt to fail over if the principal server fails.</span></span> <span data-ttu-id="f3920-119">接続文字列にフェールオーバー パートナーの値が含まれていても、初期カタログまたはデータベースの値が含まれていない場合、`InvalidArgumentException` が発生します。</span><span class="sxs-lookup"><span data-stu-id="f3920-119">If a connection string has a value for the failover partner, but no value for the initial catalog or database, an `InvalidArgumentException` is raised.</span></span>  
  
## <a name="retrieving-the-current-server-name"></a><span data-ttu-id="f3920-120">現在のサーバー名の取得</span><span class="sxs-lookup"><span data-stu-id="f3920-120">Retrieving the Current Server Name</span></span>  
 <span data-ttu-id="f3920-121">フェールオーバーの場合には、<xref:System.Data.SqlClient.SqlConnection.DataSource%2A> オブジェクトの <xref:System.Data.SqlClient.SqlConnection> プロパティを使って、現在の接続が実際に接続されているサーバーの名前を取得できます。</span><span class="sxs-lookup"><span data-stu-id="f3920-121">In the event of a failover, you can retrieve the name of the server to which the current connection is actually connected by using the <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> property of a <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="f3920-122">次のコード フラグメントでは、アクティブなサーバーの名前を取得します。この場合、接続変数は開いている <xref:System.Data.SqlClient.SqlConnection> を参照することを前提としています。</span><span class="sxs-lookup"><span data-stu-id="f3920-122">The following code fragment retrieves the name of the active server, assuming that the connection variable references an open <xref:System.Data.SqlClient.SqlConnection>.</span></span>  
  
 <span data-ttu-id="f3920-123">フェールオーバー イベントが発生し、接続は、ミラー サーバーに切り替えられます、**データソース**ミラー名を反映するようにプロパティを更新します。</span><span class="sxs-lookup"><span data-stu-id="f3920-123">When a failover event occurs and the connection is switched to the mirror server, the **DataSource** property is updated to reflect the mirror name.</span></span>  
  
```vb  
Dim activeServer As String = connection.DataSource  
```  
  
```csharp  
string activeServer = connection.DataSource;  
```  
  
## <a name="sqlclient-mirroring-behavior"></a><span data-ttu-id="f3920-124">SqlClient ミラーリングの動作</span><span class="sxs-lookup"><span data-stu-id="f3920-124">SqlClient Mirroring Behavior</span></span>  
 <span data-ttu-id="f3920-125">クライアントは、常に現在のプリンシパル サーバーに接続しようとします。</span><span class="sxs-lookup"><span data-stu-id="f3920-125">The client always tries to connect to the current principal server.</span></span> <span data-ttu-id="f3920-126">接続に失敗した場合は、フェールオーバー パートナーに接続しようとします。</span><span class="sxs-lookup"><span data-stu-id="f3920-126">If it fails, it tries the failover partner.</span></span> <span data-ttu-id="f3920-127">ミラー データベースが既にパートナー サーバー上でプリンシパル ロールに切り替わっている場合、接続は正常に行われ、新しいプリンシパルとミラー間のマッピングがクライアントに送信されて <xref:System.AppDomain> の呼び出しの有効期間の間キャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="f3920-127">If the mirror database has already been switched to the principal role on the partner server, the connection succeeds and the new principal-mirror mapping is sent to the client and cached for the lifetime of the calling <xref:System.AppDomain>.</span></span> <span data-ttu-id="f3920-128">永続的ストレージに格納されていないとは別の以降の接続では使用できません、 **AppDomain**またはプロセス。</span><span class="sxs-lookup"><span data-stu-id="f3920-128">It is not stored in persistent storage and is not available for subsequent connections in a different **AppDomain** or process.</span></span> <span data-ttu-id="f3920-129">ただし、同じ内の後続の接続に使用できるは**AppDomain**です。</span><span class="sxs-lookup"><span data-stu-id="f3920-129">However, it is available for subsequent connections within the same **AppDomain**.</span></span> <span data-ttu-id="f3920-130">注別**AppDomain**またはプロセスが常に同じまたは別のコンピューターで実行されている接続のプールがあり、それらの接続はリセットされません。</span><span class="sxs-lookup"><span data-stu-id="f3920-130">Note that another **AppDomain** or process running on the same or a different computer always has its pool of connections, and those connections are not reset.</span></span> <span data-ttu-id="f3920-131">その場合は、プライマリ データベースで障害が発生した場合は、各プロセスまたは**AppDomain**に 1 回は失敗し、プールは自動的に消去されます。</span><span class="sxs-lookup"><span data-stu-id="f3920-131">In that case, if the primary database goes down, each process or **AppDomain** fails once, and the pool is automatically cleared.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3920-132">サーバーのミラーリング サポートは、データベースごとに構成されます。</span><span class="sxs-lookup"><span data-stu-id="f3920-132">Mirroring support on the server is configured on a per-database basis.</span></span> <span data-ttu-id="f3920-133">複数部分から成る名前を使用するか、現在のデータベースを変更することにより、プリンシパル/ミラー セットに含まれない他のデータベースに対してデータの操作が実行された場合、これらの他のデータベースへの変更は障害の発生時には反映されません。</span><span class="sxs-lookup"><span data-stu-id="f3920-133">If data manipulation operations are executed against other databases not included in the principal/mirror set, either by using multipart names or by changing the current database, the changes to these other databases do not propagate in the event of failure.</span></span> <span data-ttu-id="f3920-134">ミラー化されていないデータベース内でデータが変更された場合、エラーは発生しません。</span><span class="sxs-lookup"><span data-stu-id="f3920-134">No error is generated when data is modified in a database that is not mirrored.</span></span> <span data-ttu-id="f3920-135">開発者は、このような操作の考えられる影響を評価する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3920-135">The developer must evaluate the possible impact of such operations.</span></span>  
  
## <a name="database-mirroring-resources"></a><span data-ttu-id="f3920-136">データベース ミラーリングに関するリソース</span><span class="sxs-lookup"><span data-stu-id="f3920-136">Database Mirroring Resources</span></span>  
 <span data-ttu-id="f3920-137">ミラーリングの構成、配置、および管理の概念に関するドキュメントや情報については、SQL Server オンライン ブックの次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3920-137">For conceptual documentation and information on configuring, deploying and administering mirroring, see the following resources in SQL Server Books Online.</span></span>  
  
|<span data-ttu-id="f3920-138">リソース</span><span class="sxs-lookup"><span data-stu-id="f3920-138">Resource</span></span>|<span data-ttu-id="f3920-139">説明</span><span class="sxs-lookup"><span data-stu-id="f3920-139">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="f3920-140">[データベース ミラーリング](http://msdn.microsoft.com/library/bb934127.aspx)SQL Server オンライン ブック</span><span class="sxs-lookup"><span data-stu-id="f3920-140">[Database Mirroring](http://msdn.microsoft.com/library/bb934127.aspx) in SQL Server Books Online</span></span>|<span data-ttu-id="f3920-141">SQL Server でのミラーリングの設定と構成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f3920-141">Describes how to set up and configure mirroring in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f3920-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3920-142">See Also</span></span>  
 [<span data-ttu-id="f3920-143">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="f3920-143">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)

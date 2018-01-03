---
title: "SqlCommand の実行と SqlNotificationRequest"
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
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 509c25f5c6d1108b76028af5cfd8f2a090c92137
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a><span data-ttu-id="3d7e2-102">SqlCommand の実行と SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="3d7e2-102">SqlCommand Execution with a SqlNotificationRequest</span></span>
<span data-ttu-id="3d7e2-103">サーバーからフェッチした後で、データが変更される場合があります。当然、もう一度クエリを実行すると、前回とは異なる結果セットが得られます。<xref:System.Data.SqlClient.SqlCommand> を適切に構成することで、このような場合に通知を生成することができます。</span><span class="sxs-lookup"><span data-stu-id="3d7e2-103">A <xref:System.Data.SqlClient.SqlCommand> can be configured to generate a notification when data changes after it has been fetched from the server and the result set would be different if the query were executed again.</span></span> <span data-ttu-id="3d7e2-104">この機能は、サーバー上でカスタムの通知キューを使用する場合や、実際のオブジェクトを保持しない場合に役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="3d7e2-104">This is useful for scenarios where you want to use custom notification queues on the server or when you do not want to maintain live objects.</span></span>  
  
## <a name="creating-the-notification-request"></a><span data-ttu-id="3d7e2-105">通知要求の作成</span><span class="sxs-lookup"><span data-stu-id="3d7e2-105">Creating the Notification Request</span></span>  
 <span data-ttu-id="3d7e2-106"><xref:System.Data.Sql.SqlNotificationRequest> オブジェクトを使用して通知要求を作成し、それを `SqlCommand` オブジェクトにバインドできます。</span><span class="sxs-lookup"><span data-stu-id="3d7e2-106">You can use a <xref:System.Data.Sql.SqlNotificationRequest> object to create the notification request by binding it to a `SqlCommand` object.</span></span> <span data-ttu-id="3d7e2-107">いったん要求が作成されれば、`SqlNotificationRequest` オブジェクトは不要です。</span><span class="sxs-lookup"><span data-stu-id="3d7e2-107">Once the request is created, you no longer need the `SqlNotificationRequest` object.</span></span> <span data-ttu-id="3d7e2-108">通知がないかどうかをキューに照会し、適宜、それに応じた処理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="3d7e2-108">You can query the queue for any notifications and respond appropriately.</span></span> <span data-ttu-id="3d7e2-109">通知は、アプリケーションをシャットダウンしてから再起動した場合でも受けることができます。</span><span class="sxs-lookup"><span data-stu-id="3d7e2-109">Notifications can occur even if the application is shut down and subsequently restarted.</span></span>  
  
 <span data-ttu-id="3d7e2-110">コマンドに通知を関連付けて実行した場合、元の結果セットになんらかの変更が生じると、通知要求で構成した SQL Server キューにメッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="3d7e2-110">When the command with the associated notification is executed, any changes to the original result set trigger sending a message to the SQL Server queue that was configured in the notification request.</span></span>  
  
 <span data-ttu-id="3d7e2-111">SQL Server のキューをポーリングしメッセージを解釈する方法は、アプリケーションごとに固有なものになります。</span><span class="sxs-lookup"><span data-stu-id="3d7e2-111">How you poll the SQL Server queue and interpret the message is specific to your application.</span></span> <span data-ttu-id="3d7e2-112">メッセージの内容に基づくキューのポーリングや処理は、アプリケーションによって異なります。</span><span class="sxs-lookup"><span data-stu-id="3d7e2-112">The application is responsible for polling the queue and reacting based on the contents of the message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d7e2-113"><xref:System.Data.SqlClient.SqlDependency> によって SQL Server 通知要求を使用する場合は、既定のサービス名を使用せずにキュー名を独自に作成します。</span><span class="sxs-lookup"><span data-stu-id="3d7e2-113">When using SQL Server notification requests with <xref:System.Data.SqlClient.SqlDependency>, create your own queue name instead of using the default service name.</span></span>  
  
 <span data-ttu-id="3d7e2-114"><xref:System.Data.Sql.SqlNotificationRequest> についてクライアント側に新しいセキュリティ要素はありません。</span><span class="sxs-lookup"><span data-stu-id="3d7e2-114">There are no new client-side security elements for <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="3d7e2-115">これは主にサーバーの機能であり、サーバーでは通知を要求するために必要となるユーザーの特権を設定します。</span><span class="sxs-lookup"><span data-stu-id="3d7e2-115">This is primarily a server feature, and the server has created special privileges that users must have to request a notification.</span></span>  
  
### <a name="example"></a><span data-ttu-id="3d7e2-116">例</span><span class="sxs-lookup"><span data-stu-id="3d7e2-116">Example</span></span>  
 <span data-ttu-id="3d7e2-117">次のコード フラグメントは、<xref:System.Data.Sql.SqlNotificationRequest> を作成し、それを <xref:System.Data.SqlClient.SqlCommand> に関連付ける方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="3d7e2-117">The following code fragment demonstrates how to create a <xref:System.Data.Sql.SqlNotificationRequest> and associate it with a <xref:System.Data.SqlClient.SqlCommand>.</span></span>  
  
```vb  
' Assume connection is an open SqlConnection.  
' Create a new SqlCommand object.  
Dim command As New SqlCommand( _  
  "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection)  
  
' Create a SqlNotificationRequest object.  
Dim notficationRequest As New SqlNotificationRequest()  
notficationRequest.id = "NotificationID"  
notficationRequest.Service = "mySSBQueue"  
  
' Associate the notification request with the command.  
command.Notification = notficationRequest  
' Execute the command.  
command.ExecuteReader()  
' Process the DataReader.  
' You can use Transact-SQL syntax to periodically poll the   
' SQL Server queue to see if you have a new message.  
```  
  
```csharp  
// Assume connection is an open SqlConnection.  
// Create a new SqlCommand object.  
SqlCommand command=new SqlCommand(  
 "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection);  
  
// Create a SqlNotificationRequest object.  
SqlNotificationRequest notficationRequest=new SqlNotificationRequest();  
notficationRequest.id="NotificationID";  
notficationRequest.Service="mySSBQueue";  
  
// Associate the notification request with the command.  
command.Notification=notficationRequest;  
// Execute the command.  
command.ExecuteReader();  
// Process the DataReader.  
// You can use Transact-SQL syntax to periodically poll the   
// SQL Server queue to see if you have a new message.  
```  
  
## <a name="see-also"></a><span data-ttu-id="3d7e2-118">参照</span><span class="sxs-lookup"><span data-stu-id="3d7e2-118">See Also</span></span>  
 [<span data-ttu-id="3d7e2-119">SQL Server のクエリ通知</span><span class="sxs-lookup"><span data-stu-id="3d7e2-119">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [<span data-ttu-id="3d7e2-120">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="3d7e2-120">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)

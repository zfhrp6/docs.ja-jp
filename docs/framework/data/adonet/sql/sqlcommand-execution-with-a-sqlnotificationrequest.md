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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fee008d0b1f278a48eacd8eae70d75bbbfd93691
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a>SqlCommand の実行と SqlNotificationRequest
サーバーからフェッチした後で、データが変更される場合があります。当然、もう一度クエリを実行すると、前回とは異なる結果セットが得られます。<xref:System.Data.SqlClient.SqlCommand> を適切に構成することで、このような場合に通知を生成することができます。 この機能は、サーバー上でカスタムの通知キューを使用する場合や、実際のオブジェクトを保持しない場合に役に立ちます。  
  
## <a name="creating-the-notification-request"></a>通知要求の作成  
 <xref:System.Data.Sql.SqlNotificationRequest> オブジェクトを使用して通知要求を作成し、それを `SqlCommand` オブジェクトにバインドできます。 いったん要求が作成されれば、`SqlNotificationRequest` オブジェクトは不要です。 通知がないかどうかをキューに照会し、適宜、それに応じた処理を行うことができます。 通知は、アプリケーションをシャットダウンしてから再起動した場合でも受けることができます。  
  
 コマンドに通知を関連付けて実行した場合、元の結果セットになんらかの変更が生じると、通知要求で構成した SQL Server キューにメッセージが送信されます。  
  
 SQL Server のキューをポーリングしメッセージを解釈する方法は、アプリケーションごとに固有なものになります。 メッセージの内容に基づくキューのポーリングや処理は、アプリケーションによって異なります。  
  
> [!NOTE]
>  <xref:System.Data.SqlClient.SqlDependency> によって SQL Server 通知要求を使用する場合は、既定のサービス名を使用せずにキュー名を独自に作成します。  
  
 <xref:System.Data.Sql.SqlNotificationRequest> についてクライアント側に新しいセキュリティ要素はありません。 これは主にサーバーの機能であり、サーバーでは通知を要求するために必要となるユーザーの特権を設定します。  
  
### <a name="example"></a>例  
 次のコード フラグメントは、<xref:System.Data.Sql.SqlNotificationRequest> を作成し、それを <xref:System.Data.SqlClient.SqlCommand> に関連付ける方法を示しています。  
  
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
  
## <a name="see-also"></a>参照  
 [SQL Server のクエリ通知](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)

---
title: "接続イベント"
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
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0e551a09ef6dc778f5dfab9ba8cf263f803556f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="connection-events"></a><span data-ttu-id="f71fb-102">接続イベント</span><span class="sxs-lookup"><span data-stu-id="f71fb-102">Connection Events</span></span>
<span data-ttu-id="f71fb-103">すべての .NET Framework データ プロバイダーが**接続**データ ソースから情報メッセージを取得するかどうかを判断に使用できる 2 つのイベントを持つオブジェクトの状態、**接続**が変更されました。</span><span class="sxs-lookup"><span data-stu-id="f71fb-103">All of the .NET Framework data providers have **Connection** objects with two events that you can use to retrieve informational messages from a data source or to determine if the state of a **Connection** has changed.</span></span> <span data-ttu-id="f71fb-104">次の表に、イベント、**接続**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f71fb-104">The following table describes the events of the **Connection** object.</span></span>  
  
|<span data-ttu-id="f71fb-105">イベント</span><span class="sxs-lookup"><span data-stu-id="f71fb-105">Event</span></span>|<span data-ttu-id="f71fb-106">説明</span><span class="sxs-lookup"><span data-stu-id="f71fb-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f71fb-107">**InfoMessage**</span><span class="sxs-lookup"><span data-stu-id="f71fb-107">**InfoMessage**</span></span>|<span data-ttu-id="f71fb-108">データ ソースから情報メッセージが返されたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="f71fb-108">Occurs when an informational message is returned from a data source.</span></span> <span data-ttu-id="f71fb-109">情報メッセージはデータ ソースからのメッセージであり、例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="f71fb-109">Informational messages are messages from a data source that do not result in an exception being thrown.</span></span>|  
|<span data-ttu-id="f71fb-110">**StateChange**</span><span class="sxs-lookup"><span data-stu-id="f71fb-110">**StateChange**</span></span>|<span data-ttu-id="f71fb-111">発生したときの状態、**接続**変更します。</span><span class="sxs-lookup"><span data-stu-id="f71fb-111">Occurs when the state of the **Connection** changes.</span></span>|  
  
## <a name="working-with-the-infomessage-event"></a><span data-ttu-id="f71fb-112">InfoMessage イベントの使用</span><span class="sxs-lookup"><span data-stu-id="f71fb-112">Working with the InfoMessage Event</span></span>  
 <span data-ttu-id="f71fb-113"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> オブジェクトの <xref:System.Data.SqlClient.SqlConnection> イベントを使用して、SQL Server データ ソースから警告や情報メッセージを取得できます。</span><span class="sxs-lookup"><span data-stu-id="f71fb-113">You can retrieve warnings and informational messages from a SQL Server data source using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="f71fb-114">重大度レベルが 11 から 16 のエラーがデータ ソースから返されると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f71fb-114">Errors returned from the data source with a severity level of 11 through 16 cause an exception to be thrown.</span></span> <span data-ttu-id="f71fb-115"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントを使用して、エラーに関連付けられていないメッセージをデータ ソースから取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="f71fb-115">However, the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event can be used to obtain messages from the data source that are not associated with an error.</span></span> <span data-ttu-id="f71fb-116">Microsoft SQL Server の場合は、重大度レベルが 10 以下のエラーは情報メッセージと見なされ、<xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントでキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="f71fb-116">In the case of Microsoft SQL Server, any error with a severity of 10 or less is considered to be an informational message, and can be captured by using the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span> <span data-ttu-id="f71fb-117">詳細については、SQL Server オンライン ブックの「エラー メッセージ重大度レベル」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f71fb-117">For more information, see the "Error Message Severity Levels" topic in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="f71fb-118"><xref:System.Data.SqlClient.SqlConnection.InfoMessage>イベントを受け取る、<xref:System.Data.SqlClient.SqlInfoMessageEventArgs>オブジェクトを含むでその**エラー**プロパティ、データ ソースからのメッセージのコレクション。</span><span class="sxs-lookup"><span data-stu-id="f71fb-118">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event receives an <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> object containing, in its **Errors** property, a collection of the messages from the data source.</span></span> <span data-ttu-id="f71fb-119">クエリを実行することができます、**エラー**エラー番号およびメッセージ テキストと、エラーの原因には、このコレクション内のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f71fb-119">You can query the **Error** objects in this collection for the error number and message text, as well as the source of the error.</span></span> <span data-ttu-id="f71fb-120">.NET Framework Data Provider for SQL Server には、データベースの詳細情報、ストアド プロシージャ、およびメッセージ送信元の行番号も含まれます。</span><span class="sxs-lookup"><span data-stu-id="f71fb-120">The .NET Framework Data Provider for SQL Server also includes detail about the database, stored procedure, and line number that the message came from.</span></span>  
  
### <a name="example"></a><span data-ttu-id="f71fb-121">例</span><span class="sxs-lookup"><span data-stu-id="f71fb-121">Example</span></span>  
 <span data-ttu-id="f71fb-122"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントのイベント ハンドラーを追加する方法を次のコード サンプルに示します。</span><span class="sxs-lookup"><span data-stu-id="f71fb-122">The following code example shows how to add an event handler for the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
```vb  
' Assumes that connection represents a SqlConnection object.  
  AddHandler connection.InfoMessage, _  
    New SqlInfoMessageEventHandler(AddressOf OnInfoMessage)  
  
Private Shared Sub OnInfoMessage(sender As Object, _  
  args As SqlInfoMessageEventArgs)  
  Dim err As SqlError  
  For Each err In args.Errors  
    Console.WriteLine("The {0} has received a severity {1}, _  
       state {2} error number {3}\n" & _  
      "on line {4} of procedure {5} on server {6}:\n{7}", _  
      err.Source, err.Class, err.State, err.Number, err.LineNumber, _  
    err.Procedure, err.Server, err.Message)  
  Next  
End Sub  
```  
  
```csharp  
// Assumes that connection represents a SqlConnection object.  
  connection.InfoMessage +=   
    new SqlInfoMessageEventHandler(OnInfoMessage);  
  
protected static void OnInfoMessage(  
  object sender, SqlInfoMessageEventArgs args)  
{  
  foreach (SqlError err in args.Errors)  
  {  
    Console.WriteLine(  
  "The {0} has received a severity {1}, state {2} error number {3}\n" +  
  "on line {4} of procedure {5} on server {6}:\n{7}",  
   err.Source, err.Class, err.State, err.Number, err.LineNumber,   
   err.Procedure, err.Server, err.Message);  
  }  
}  
```  
  
## <a name="handling-errors-as-infomessages"></a><span data-ttu-id="f71fb-123">InfoMessages としてのエラー処理</span><span class="sxs-lookup"><span data-stu-id="f71fb-123">Handling Errors as InfoMessages</span></span>  
 <span data-ttu-id="f71fb-124"><xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントは通常、サーバーが情報メッセージまたは警告メッセージを送信した場合に限り発生します。</span><span class="sxs-lookup"><span data-stu-id="f71fb-124">The <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event will normally fire only for informational and warning messages that are sent from the server.</span></span> <span data-ttu-id="f71fb-125">ただし、実際にエラーが発生するの実行、 **ExecuteNonQuery**または**ExecuteReader**サーバーの操作を開始したメソッドは停止され、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f71fb-125">However, when an actual error occurs, the execution of the **ExecuteNonQuery** or **ExecuteReader** method that initiated the server operation is halted and an exception is thrown.</span></span>  
  
 <span data-ttu-id="f71fb-126">サーバーでエラーが発生してもコマンド内の残りのステートメントの処理を続行する場合は、<xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> の <xref:System.Data.SqlClient.SqlConnection> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="f71fb-126">If you want to continue processing the rest of the statements in a command regardless of any errors produced by the server, set the <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> property of the <xref:System.Data.SqlClient.SqlConnection> to `true`.</span></span> <span data-ttu-id="f71fb-127">このように設定すると、エラーが発生したとき、接続は例外をスローして処理を中断する代わりに、<xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="f71fb-127">Doing this causes the connection to fire the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event for errors instead of throwing an exception and interrupting processing.</span></span> <span data-ttu-id="f71fb-128">クライアント アプリケーションは、このイベントを処理し、エラーに応答できます。</span><span class="sxs-lookup"><span data-stu-id="f71fb-128">The client application can then handle this event and respond to error conditions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f71fb-129">重大度レベルが 17 以上のエラーが発生すると、サーバーのコマンド処理が停止します。このエラーは、例外として処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f71fb-129">An error with a severity level of 17 or above that causes the server to stop processing the command must be handled as an exception.</span></span> <span data-ttu-id="f71fb-130">この場合、<xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントによるエラー処理の方法にかかわらず例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f71fb-130">In this case, an exception is thrown regardless of how the error is handled in the <xref:System.Data.SqlClient.SqlConnection.InfoMessage> event.</span></span>  
  
## <a name="working-with-the-statechange-event"></a><span data-ttu-id="f71fb-131">StateChange イベントの使用</span><span class="sxs-lookup"><span data-stu-id="f71fb-131">Working with the StateChange Event</span></span>  
 <span data-ttu-id="f71fb-132">**StateChange**イベントが発生したときの状態、**接続**変更します。</span><span class="sxs-lookup"><span data-stu-id="f71fb-132">The **StateChange** event occurs when the state of a **Connection** changes.</span></span> <span data-ttu-id="f71fb-133">**StateChange**イベントを受け取る<xref:System.Data.StateChangeEventArgs>の状態の変更を決定することができます、**接続**を使用して、**戻します**と**CurrentState**プロパティです。</span><span class="sxs-lookup"><span data-stu-id="f71fb-133">The **StateChange** event receives <xref:System.Data.StateChangeEventArgs> that enable you to determine the change in state of the **Connection** by using the **OriginalState** and **CurrentState** properties.</span></span> <span data-ttu-id="f71fb-134">**戻します**プロパティは、<xref:System.Data.ConnectionState>の状態を示す列挙体、**接続**内容を変更する前にします。</span><span class="sxs-lookup"><span data-stu-id="f71fb-134">The **OriginalState** property is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** before it changed.</span></span> <span data-ttu-id="f71fb-135">**CurrentState**は、<xref:System.Data.ConnectionState>の状態を示す列挙体、**接続**変更された後です。</span><span class="sxs-lookup"><span data-stu-id="f71fb-135">**CurrentState** is a <xref:System.Data.ConnectionState> enumeration that indicates the state of the **Connection** after it changed.</span></span>  
  
 <span data-ttu-id="f71fb-136">次のコード例では、 **StateChange**コンソールにメッセージを書き込むイベントときの状態、**接続**変更します。</span><span class="sxs-lookup"><span data-stu-id="f71fb-136">The following code example uses the **StateChange** event to write a message to the console when the state of the **Connection** changes.</span></span>  
  
```vb  
' Assumes connection represents a SqlConnection object.  
  AddHandler connection.StateChange, _  
    New StateChangeEventHandler(AddressOf OnStateChange)  
  
Protected Shared Sub OnStateChange( _  
  sender As Object, args As StateChangeEventArgs)  
  
  Console.WriteLine( _  
  "The current Connection state has changed from {0} to {1}.", _  
  args.OriginalState, args.CurrentState)  
End Sub  
```  
  
```csharp  
// Assumes connection represents a SqlConnection object.  
  connection.StateChange  += new StateChangeEventHandler(OnStateChange);  
  
protected static void OnStateChange(object sender,   
  StateChangeEventArgs args)  
{  
  Console.WriteLine(  
    "The current Connection state has changed from {0} to {1}.",  
      args.OriginalState, args.CurrentState);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f71fb-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="f71fb-137">See Also</span></span>  
 [<span data-ttu-id="f71fb-138">データ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="f71fb-138">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="f71fb-139">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="f71fb-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)

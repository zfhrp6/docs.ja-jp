---
title: "接続イベント | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 接続イベント
すべての .NET Framework データ プロバイダーには、データ ソースから情報メッセージを取得したり、**Connection** 状態の変化を確認したりするために使用できる 2 つのイベントを持った **Connection** オブジェクトがあります。  **Connection** オブジェクトのイベントを次の表に示します。  
  
|Event|説明|  
|-----------|--------|  
|**InfoMessage**|データ ソースから情報メッセージが返されたときに発生します。  情報メッセージはデータ ソースからのメッセージであり、例外はスローされません。|  
|**StateChange**|**Connection** の状態が変化したときに発生します。|  
  
## InfoMessage イベントの使用  
 <xref:System.Data.SqlClient.SqlConnection> オブジェクトの <xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントを使用して、SQL Server データ ソースから警告や情報メッセージを取得できます。  重大度レベルが 11 から 16 のエラーがデータ ソースから返されると、例外がスローされます。  <xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントを使用して、エラーに関連付けられていないメッセージをデータ ソースから取得することもできます。  Microsoft SQL Server の場合は、重大度レベルが 10 以下のエラーは情報メッセージと見なされ、<xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントでキャプチャされます。  詳細については、SQL Server オンライン ブックの「エラー メッセージ重大度レベル」を参照してください。  
  
 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントは <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> オブジェクトを受け取りますが、その **Errors** プロパティにはデータ ソースからのメッセージのコレクションが格納されています。  このコレクションの中の **Error** オブジェクトにエラー番号、メッセージ テキスト、およびエラーの原因を問い合わせることができます。  .NET Framework Data Provider for SQL Server には、データベースの詳細情報、ストアド プロシージャ、およびメッセージ送信元の行番号も含まれます。  
  
### 例  
 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントのイベント ハンドラーを追加する方法を次のコード サンプルに示します。  
  
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
  
## InfoMessages としてのエラー処理  
 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントは通常、サーバーが情報メッセージまたは警告メッセージを送信した場合に限り発生します。  ただし、実際にエラーが発生した場合は、サーバーの操作を開始した **ExecuteNonQuery** メソッドまたは **ExecuteReader** メソッドの実行は停止され、例外がスローされます。  
  
 サーバーでエラーが発生してもコマンド内の残りのステートメントの処理を続行する場合は、<xref:System.Data.SqlClient.SqlConnection> の <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> プロパティを `true` に設定します。  このように設定すると、エラーが発生したとき、接続は例外をスローして処理を中断する代わりに、<xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントを発生させます。  クライアント アプリケーションは、このイベントを処理し、エラーに応答できます。  
  
> [!NOTE]
>  重大度レベルが 17 以上のエラーが発生すると、サーバーのコマンド処理が停止します。このエラーは、例外として処理する必要があります。  この場合、<xref:System.Data.SqlClient.SqlConnection.InfoMessage> イベントによるエラー処理の方法にかかわらず例外がスローされます。  
  
## StateChange イベントの使用  
 **StateChange** イベントは、**Connection** の状態が変化したときに発生します。  **StateChange** イベントは **OriginalState** プロパティおよび **CurrentState** プロパティを使用して、**Connection** の状態の変化を判別できる <xref:System.Data.StateChangeEventArgs> を受け取ります。  **OriginalState** プロパティは、**Connection** の状態が変更される前の状態を示す <xref:System.Data.ConnectionState> 列挙体です。  **CurrentState** は、**Connection** の状態が変更された後の状態を示す <xref:System.Data.ConnectionState> 列挙体です。  
  
 **StateChange** イベントを使用して **Connection** の状態が変化したときにコンソールにメッセージを出力するコード サンプルを次に示します。  
  
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
  
## 参照  
 [データ ソースへの接続](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)
---
title: "非同期クライアント ソケットの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "アプリケーション プロトコル、ソケット"
  - "送信 (データの)、ソケット"
  - "データ要求、ソケット"
  - "非同期クライアント ソケット"
  - "Socket クラス、非同期クライアント ソケット"
  - "要求 (インターネットからデータを)、ソケット"
  - "ソケット、非同期クライアント ソケット"
  - "受信 (データの)、ソケット"
  - "プロトコル、ソケット"
  - "インターネット、ソケット"
  - "クライアント ソケット"
ms.assetid: fd85bc88-e06c-467d-a30d-9fd7cffcfca1
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# 非同期クライアント ソケットの使用
非同期なクライアントのネットワークはソケット実行するアクションを待つ間アプリケーションを中断されなくなります。  代わりに、アプリケーションが元のスレッドで実行される作業のスレッド間、1 種類のネットワーク接続を処理するには、標準 .NET Framework 非同期のプログラミング モデルを使用します。  非同期なソケットは、大量を使用するか、ネットワークの進む前に実行する工程ネットワークを待つことができないアプリケーション用に適切です。  
  
 <xref:System.Net.Sockets.Socket> クラスは非同期な方法の .NET Framework のパターンに示す;。たとえば、同期の <xref:System.Net.Sockets.Socket.Receive%2A> 方法は <xref:System.Net.Sockets.Socket.EndReceive%2A> の非同期な <xref:System.Net.Sockets.Socket.BeginReceive%2A> および方法に対応します。  
  
 非同期処理はコールバック方法は、工程の結果が返される必要があります。  自分のアプリケーションで結果を知る必要がなければ、コールバック方法は必要ではありません。  このセクションのコードの例は、方法を完了するには、ネットワークのデバイスがコールバック方法データおよびデータとコールバック方法を受け取ることを開始するために送信を完了するためのコールバック方法の送信を開始する接続を完了する方法、およびメソッドに接続を開始するにはなく、データが表示されます。  
  
 非同期なソケットは、ネットワーク接続を処理するためにシステムのスレッド プールから複数のスレッドを使用します。  1 種類のスレッドは、データの送受信を開始する責任があります; そのほかすべてのネットワーク デバイスと送信への接続に通すまたはデータが表示されます。  次の例では、メイン スレッドの実行を中断し、実行をいつ続行するかを通知に、<xref:System.Threading.ManualResetEvent?displayProperty=fullName> クラスのインスタンスが使用されます。  
  
 次の例では、非同期なソケットをネットワークのデバイスに接続するには、`Connect`方法は **\[ソケット\]** を初期化し、ネットワーク デバイス、接続のコールバック方法と非同期通話中のステータス情報を渡すために使用される、ステータス **\[ソケット\]**オブジェクト \(クライアント\) を表す、エンドポイントを渡す [BeginConnect](frlrfsystemnetsocketssocketclassconnecttopic) 方法を追加します。  例は、指定されたエンドポイントに指定 **\[ソケット\]** を関連付ける場合は、`Connect` 方法を実行します。  これは `connectDone`というグローバルな **\[ManualResetEvent\]** とします。  
  
```vb  
Public Shared Sub Connect(remoteEP As EndPoint, client As Socket)  
    client.BeginConnect(remoteEP, _  
       AddressOf ConnectCallback, client)  
  
    connectDone.WaitOne()  
End Sub 'Connect  
```  
  
```csharp  
public static void Connect(EndPoint remoteEP, Socket client) {  
    client.BeginConnect(remoteEP,   
        new AsyncCallback(ConnectCallback), client );  
  
   connectDone.WaitOne();  
}  
```  
  
 接続のコールバック方法 `ConnectCallback` は <xref:System.AsyncCallback> の委任を実行します。  これは、リモート接続が **\[ManualResetEvent\]** デバイスに `connectDone`の配置に完全であることリモート デバイスが使用可能な接続し、アプリケーションのスレッドに信号を求める場合。  次のコードは `ConnectCallback` 方法を実行します。  
  
```vb  
Private Shared Sub ConnectCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the socket from the state object.  
        Dim client As Socket = CType(ar.AsyncState, Socket)  
  
        ' Complete the connection.  
        client.EndConnect(ar)  
  
        Console.WriteLine("Socket connected to {0}", _  
            client.RemoteEndPoint.ToString())  
  
        ' Signal that the connection has been made.  
        connectDone.Set()  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'ConnectCallback  
  
```  
  
```csharp  
private static void ConnectCallback(IAsyncResult ar) {  
    try {  
        // Retrieve the socket from the state object.  
        Socket client = (Socket) ar.AsyncState;  
  
        // Complete the connection.  
        client.EndConnect(ar);  
  
        Console.WriteLine("Socket connected to {0}",  
            client.RemoteEndPoint.ToString());  
  
        // Signal that the connection has been made.  
        connectDone.Set();  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 例 `Send` 指定方法はソケットで表されるネットワークのデバイスに ASCII 形式と送信の特定の文字列のデータを、非同期的にエンコードします。  次の例では、`Send` 方法を実行します。  
  
```vb  
Private Shared Sub Send(client As Socket, data As [String])  
    ' Convert the string data to byte data using ASCII encoding.  
    Dim byteData As Byte() = Encoding.ASCII.GetBytes(data)  
  
    ' Begin sending the data to the remote device.  
    client.BeginSend(byteData, 0, byteData.Length, SocketFlags.None, _  
        AddressOf SendCallback, client)  
End Sub 'Send  
  
```  
  
```csharp  
private static void Send(Socket client, String data) {  
    // Convert the string data to byte data using ASCII encoding.  
    byte[] byteData = Encoding.ASCII.GetBytes(data);  
  
    // Begin sending the data to the remote device.  
    client.BeginSend(byteData, 0, byteData.Length, SocketFlags.None,  
        new AsyncCallback(SendCallback), client);  
}  
```  
  
 コールバック送信方法 `SendCallback` は <xref:System.AsyncCallback> の委任を実行します。  これは、ネットワークのデバイスが受信する準備が整ったら、データを送信します。  次の例では、`SendCallback` 方法の手順を示します。  これは `sendDone`というグローバルな **\[ManualResetEvent\]** とします。  
  
```vb  
Private Shared Sub SendCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the socket from the state object.  
        Dim client As Socket = CType(ar.AsyncState, Socket)  
  
        ' Complete sending the data to the remote device.  
        Dim bytesSent As Integer = client.EndSend(ar)  
        Console.WriteLine("Sent {0} bytes to server.", bytesSent)  
  
        ' Signal that all bytes have been sent.  
        sendDone.Set()  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'SendCallback  
  
```  
  
```csharp  
private static void SendCallback(IAsyncResult ar) {  
    try {  
        // Retrieve the socket from the state object.  
        Socket client = (Socket) ar.AsyncState;  
  
        // Complete sending the data to the remote device.  
        int bytesSent = client.EndSend(ar);  
        Console.WriteLine("Sent {0} bytes to server.", bytesSent);  
  
        // Signal that all bytes have been sent.  
        sendDone.Set();  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 クライアントのソケットからのデータの読み取りと、非同期の呼び出しの間での値に合格ステータス オブジェクトが必要です。  次のクラスはソケットのクライアントからデータを取得するための例のステータス オブジェクトです。  これは、設定データの文字列を保留に表示されるデータのクライアントのソケット、バッファ、<xref:System.Text.StringBuilder> のフィールドが含まれます。  ステータス オブジェクトにこれらのフィールドの設定はソケット値でクライアントからデータを読み取る際に複数の呼び出しに管理されます。  
  
```vb  
Public Class StateObject  
    ' Client socket.  
    Public workSocket As Socket = Nothing   
    ' Size of receive buffer.  
    Public BufferSize As Integer = 256  
    ' Receive buffer.  
    Public buffer(256) As Byte   
    ' Received data string.  
    Public sb As New StringBuilder()  
End Class 'StateObject  
  
```  
  
```csharp  
public class StateObject {  
    // Client socket.  
    public Socket workSocket = null;  
    // Size of receive buffer.  
    public const int BufferSize = 256;  
    // Receive buffer.  
    public byte[] buffer = new byte[BufferSize];  
    // Received data string.  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 例 `Receive` の方法は、ステータス対象を設定し、クライアントのソケットからデータを非同期的に読み取る場合に **BeginReceive** 方法を追加します。  次の例では、`Receive` 方法を実行します。  
  
```vb  
Private Shared Sub Receive(client As Socket)  
    Try  
        ' Create the state object.  
        Dim state As New StateObject()  
        state.workSocket = client  
  
        ' Begin receiving the data from the remote device.  
        client.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf ReceiveCallback, state)  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'Receive  
  
```  
  
```csharp  
private static void Receive(Socket client) {  
    try {  
        // Create the state object.  
        StateObject state = new StateObject();  
        state.workSocket = client;  
  
        // Begin receiving the data from the remote device.  
        client.BeginReceive( state.buffer, 0, StateObject.BufferSize, 0,  
            new AsyncCallback(ReceiveCallback), state);  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 入庫のコールバック方法 `ReceiveCallback` は **AsyncCallback** の委任を実行します。  これは、ネットワークのデバイスからデータを取得し、メッセージの文字列を基づきます。  これは、バッファ データにクライアントが送信するデータが完了するまでネットワーク上のデータのバイトを読込み、を **BeginReceive** 方法をもう一度呼び出すします。  すべてのデータがクライアントから読まれれば、`ReceiveCallback`、データを **\[ManualResetEvent\]** `sendDone`の配置に完全であることアプリケーションのスレッドに信号を送信します。  
  
 次のコードの例は、`ReceiveCallback`方法を実行します。  これは `response` という `receiveDone`受信したという文字列とグローバルな **\[ManualResetEvent\]** を保持するグローバルな文字列とします。  サーバーは、ネットワークのセッションを終了ためのクライアントのソケットを優雅に締めなければ必要があります。  
  
```vb  
Private Shared Sub ReceiveCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the state object and the client socket   
        ' from the asynchronous state object.  
        Dim state As StateObject = CType(ar.AsyncState, StateObject)  
        Dim client As Socket = state.workSocket  
  
        ' Read data from the remote device.  
        Dim bytesRead As Integer = client.EndReceive(ar)  
  
        If bytesRead > 0 Then  
            ' There might be more data, so store the data received so far.  
            state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, _  
                bytesRead))  
  
            '  Get the rest of the data.  
            client.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
                AddressOf ReceiveCallback, state)  
        Else  
            ' All the data has arrived; put it in response.  
            If state.sb.Length > 1 Then  
                response = state.sb.ToString()  
            End If  
            ' Signal that all bytes have been received.  
            receiveDone.Set()  
        End If  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'ReceiveCallback  
  
```  
  
```csharp  
private static void ReceiveCallback( IAsyncResult ar ) {  
    try {  
        // Retrieve the state object and the client socket   
        // from the asynchronous state object.  
        StateObject state = (StateObject) ar.AsyncState;  
        Socket client = state.workSocket;  
        // Read data from the remote device.  
        int bytesRead = client.EndReceive(ar);  
        if (bytesRead > 0) {  
            // There might be more data, so store the data received so far.  
            state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,bytesRead));  
                //  Get the rest of the data.  
            client.BeginReceive(state.buffer,0,StateObject.BufferSize,0,  
                new AsyncCallback(ReceiveCallback), state);  
        } else {  
            // All the data has arrived; put it in response.  
            if (state.sb.Length > 1) {  
                response = state.sb.ToString();  
            }  
            // Signal that all bytes have been received.  
            receiveDone.Set();  
        }  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
## 参照  
 [同期クライアント ソケットの使用](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)   
 [リッスン \(ソケットで\)](../../../docs/framework/network-programming/listening-with-sockets.md)   
 [非同期クライアント ソケットの例](../../../docs/framework/network-programming/asynchronous-client-socket-example.md)
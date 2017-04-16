---
title: "非同期サーバー ソケットの使用 | Microsoft Docs"
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
  - "ソケット クラス、非同期サーバー ソケット"
  - "データ要求、ソケット"
  - "ソケット、非同期サーバー ソケット"
  - "要求 (インターネットからデータを)、ソケット"
  - "サーバー ソケット"
  - "受信 (データの)、ソケット"
  - "非同期サーバー ソケット"
  - "プロトコル、ソケット"
  - "インターネット、ソケット"
ms.assetid: 813489a9-3efd-41b6-a33f-371d55397676
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# 非同期サーバー ソケットの使用
非同期なサーバーはソケットのネットワーク サービス要求の処理に .NET Framework 非同期のプログラミング モデルを使用します。  <xref:System.Net.Sockets.Socket> のクラスが標準の .NET Framework 非同期示すなパターンに従います; たとえば、同期の <xref:System.Net.Sockets.Socket.Accept%2A> 方法は <xref:System.Net.Sockets.Socket.EndAccept%2A> の非同期な <xref:System.Net.Sockets.Socket.BeginAccept%2A> および方法に対応します。  
  
 非同期なサーバーはソケット終了する方法がネットワーク、コールバック方法接続要求して、ネットワークからデータを取得し始めるとコールバック方法から接続要求を承認する際に要求します。データが表示されます。  これらの方法はすべてこのセクションでさらに説明します。  
  
 次の例では、ネットワークから接続要求を承認を開始するには **\[ソケット\]** 方法 `StartListening` を初期化し、新しい接続を受け入れることを開始するに **BeginAccept** 方法を使用します。  承認のコールバック方法が新しい接続要求がソケットに入庫すると呼ばれます。  これは要求を処理するにそのスレッド接続 **\[ソケット\]** を渡すことが処理 **\[ソケット\]** のインスタンスを取得するために行う必要があります。  承認のコールバック方法は <xref:System.AsyncCallback> の委任を実行して; これは無効を返品した <xref:System.IAsyncResult>型の一つのパラメータを取ります。  次の例では、承認のコールバック方法のシェルです。  
  
```vb  
Sub acceptCallback(ar As IAsyncResult)  
    ' Add the callback code here.  
End Sub 'acceptCallback  
```  
  
```csharp  
void acceptCallback( IAsyncResult ar) {  
    // Add the callback code here.  
}  
```  
  
 **BeginAccept** 方法は、2 種類のパラメータ、承認のコールバック方法とコールバック方法のステータス情報を渡すために使用されるオブジェクトを表す **AsyncCallback** の委任を取ります。  次の例では、リッスン **\[ソケット\]** は、*州の* パラメータでコールバック方法に渡されます。  この例では、**AsyncCallback** の委任を作成し、ネットワークから接続を受け入れることを開始します。  
  
```vb  
listener.BeginAccept( _  
    New AsyncCallback(SocketListener.acceptCallback),_  
    listener)  
```  
  
```csharp  
listener.BeginAccept(  
    new AsyncCallback(SocketListener.acceptCallback),   
    listener);  
```  
  
 非同期な設定はソケット接続を処理するためにシステムのスレッド プールからスレッドを使用します。  1 種類のスレッドは、接続を承認する責任があります。個々の接続を処理するために、別のスレッドが使用され、他のスレッドは、接続からデータを取得する責任があります。  これらはスレッドをスレッド プールに割り当てられている同じスレッドにすることができます。  次の例では、<xref:System.Threading.ManualResetEvent?displayProperty=fullName> のクラスが実装を続行すると、メイン スレッド信号の実行を中断します。  
  
 次の例では、ローカル コンピュータの非同期の TCP\/IP ソケットを作成し、接続を受け付けるを開始する非同期な方法を示します。  方法が `SocketListener`というクラスのメンバであると、`acceptCallback` というコールバック方法が定義されると `allDone`というグローバルな **\[ManualResetEvent\]** があるとします。  
  
```vb  
Public Sub StartListening()  
    Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
    Dim localEP = New IPEndPoint(ipHostInfo.AddressList(0), 11000)  
  
    Console.WriteLine("Local address and port : {0}", localEP.ToString())  
  
    Dim listener As New Socket(localEP.Address.AddressFamily, _  
       SocketType.Stream, ProtocolType.Tcp)  
  
    Try  
        listener.Bind(localEP)  
        listener.Listen(10)  
  
        While True  
            allDone.Reset()  
  
            Console.WriteLine("Waiting for a connection...")  
            listener.BeginAccept(New _  
                AsyncCallback(SocketListener.acceptCallback), _  
                listener)  
  
            allDone.WaitOne()  
        End While  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
    Console.WriteLine("Closing the listener...")  
End Sub 'StartListening  
  
```  
  
```csharp  
public void StartListening() {  
    IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
    IPEndPoint localEP = new IPEndPoint(ipHostInfo.AddressList[0],11000);  
  
    Console.WriteLine("Local address and port : {0}",localEP.ToString());  
  
    Socket listener = new Socket( localEP.Address.AddressFamily,  
        SocketType.Stream, ProtocolType.Tcp );  
  
    try {  
        listener.Bind(localEP);  
        listener.Listen(10);  
  
        while (true) {  
            allDone.Reset();  
  
            Console.WriteLine("Waiting for a connection...");  
            listener.BeginAccept(  
                new AsyncCallback(SocketListener.acceptCallback),   
                listener );  
  
            allDone.WaitOne();  
        }  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
  
    Console.WriteLine( "Closing the listener...");  
}  
```  
  
 承認のコールバック方法 \(前の例で`acceptCallback`\)、クライアントからのデータの処理し、クライアントを使用して接続を確立し、非同期を開始することがメイン アプリケーション スレッドを通知するために行う必要があります読みました。  次の例では、`acceptCallback` のメソッドの実装の最初の部分です。  このセクションの方法で処理することがメイン アプリケーション スレッドに信号を送信し、クライアントへの接続を設定します。  これは `allDone`というグローバルな **\[ManualResetEvent\]** とします。  
  
```vb  
Public Sub acceptCallback(ar As IAsyncResult)  
    allDone.Set()  
  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Additional code to read data goes here.  
End Sub 'acceptCallback  
```  
  
```csharp  
public void acceptCallback(IAsyncResult ar) {  
    allDone.Set();  
  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Additional code to read data goes here.    
}  
```  
  
 クライアントのソケットからのデータの読み取りと、非同期の呼び出しの間での値に合格ステータス オブジェクトが必要です。  次の例では、リモート クライアントの文字列を表示する対象のステータスを実行します。  これは、データの入荷クライアントのバッファ ソケット、データ、およびクライアントが送信するデータの文字列の作成の <xref:System.Text.StringBuilder> のフィールドが含まれます。  ステータス オブジェクトにこれらのフィールドの設定はソケット値でクライアントからデータを読み取る際に複数の呼び出しに管理されます。  
  
```vb  
Public Class StateObject  
    Public workSocket As Socket = Nothing  
    Public BufferSize As Integer = 1024  
    Public buffer(BufferSize) As Byte  
    Public sb As New StringBuilder()  
End Class 'StateObject  
```  
  
```csharp  
public class StateObject {  
    public Socket workSocket = null;  
    public const int BufferSize = 1024;  
    public byte[] buffer = new byte[BufferSize];  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 クライアントのソケットからのデータの最初に入庫を開始する `acceptCallback` 方法のセクションでは、`StateObject` クラスのインスタンスを初期化して、クライアントのソケットからデータを非同期的に読み取ることを開始するに <xref:System.Net.Sockets.Socket.BeginReceive%2A> 方法を追加します。  
  
 次の例では、`acceptCallback` の完了原価方法を示します。  `StateObject` クラスが定義されている `readCallback` 方法がクラスで定義されている `SocketListener`を指定された `allDone,` というグローバルな **\[ManualResetEvent\]** があるとします。  
  
```vb  
Public Shared Sub acceptCallback(ar As IAsyncResult)  
    ' Get the socket that handles the client request.  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Signal the main thread to continue.  
    allDone.Set()  
  
    ' Create the state object.  
    Dim state As New StateObject()  
    state.workSocket = handler  
    handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
        AddressOf AsynchronousSocketListener.readCallback, state)  
End Sub 'acceptCallback  
  
```  
  
```csharp  
public static void acceptCallback(IAsyncResult ar) {  
    // Get the socket that handles the client request.  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Signal the main thread to continue.  
    allDone.Set();  
  
    // Create the state object.  
    StateObject state = new StateObject();  
    state.workSocket = handler;  
    handler.BeginReceive( state.buffer, 0, StateObject.BufferSize, 0,  
        new AsyncCallback(AsynchronousSocketListener.readCallback), state);  
}  
```  
  
 非同期なソケット サーバーの実行する必要がある最終方法は、クライアントが送信するデータを返す読み取りコールバック方法です。  承認のコールバック方法と同様に、読み取りコールバック方法は **AsyncCallback** の必須です。  この方法はバッファ データにクライアントが送信するデータが完了するまでソケットのクライアントから一つ以上のバイトを読込み、を **BeginReceive** 方法をもう一度呼び出すします。  メッセージ全体がクライアントから読まれたらコンソールで、文字列が表示され、クライアントへの接続をサーバーの処理はソケット閉じられます。  
  
 次のオプションが `readCallback` 方法を実行します。  `StateObject` クラスが定義されています。  
  
```vb  
Public Shared Sub readCallback(ar As IAsyncResult)  
    Dim state As StateObject = CType(ar.AsyncState, StateObject)  
    Dim handler As Socket = state.workSocket  
  
    ' Read data from the client socket.   
    Dim read As Integer = handler.EndReceive(ar)  
  
    ' Data was read from the client socket.  
    If read > 0 Then  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, read))  
        handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf readCallback, state)  
    Else  
        If state.sb.Length > 1 Then  
            ' All the data has been read from the client;  
            ' display it on the console.  
            Dim content As String = state.sb.ToString()  
            Console.WriteLine("Read {0} bytes from socket." + _  
                ControlChars.Cr + " Data : {1}", content.Length, content)  
        End If  
    End If  
End Sub 'readCallback  
  
```  
  
```csharp  
public static void readCallback(IAsyncResult ar) {  
    StateObject state = (StateObject) ar.AsyncState;  
    Socket handler = state.WorkSocket;  
  
    // Read data from the client socket.  
    int read = handler.EndReceive(ar);  
  
    // Data was read from the client socket.  
    if (read > 0) {  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,read));  
        handler.BeginReceive(state.buffer,0,StateObject.BufferSize, 0,  
            new AsyncCallback(readCallback), state);  
    } else {  
        if (state.sb.Length > 1) {  
            // All the data has been read from the client;  
            // display it on the console.  
            string content = state.sb.ToString();  
            Console.WriteLine("Read {0} bytes from socket.\n Data : {1}",  
               content.Length, content);  
        }  
        handler.Close();  
    }  
}  
```  
  
## 参照  
 [同期サーバー ソケットの使用](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)   
 [非同期サーバー ソケットの例](../../../docs/framework/network-programming/asynchronous-server-socket-example.md)   
 [Threading](../../../docs/standard/threading/index.md)   
 [リッスン \(ソケットで\)](../../../docs/framework/network-programming/listening-with-sockets.md)
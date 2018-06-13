---
title: 非同期サーバー ソケットの使用
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- Socket class, asynchronous server sockets
- data requests, sockets
- sockets, asynchronous server sockets
- requesting data from Internet, sockets
- server sockets
- receiving data, sockets
- asynchronous server sockets
- protocols, sockets
- Internet, sockets
ms.assetid: 813489a9-3efd-41b6-a33f-371d55397676
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ad52291f5f5f40a65d2f9ec1c07bfb3a3f39fc01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396608"
---
# <a name="using-an-asynchronous-server-socket"></a><span data-ttu-id="26615-102">非同期サーバー ソケットの使用</span><span class="sxs-lookup"><span data-stu-id="26615-102">Using an Asynchronous Server Socket</span></span>
<span data-ttu-id="26615-103">非同期サーバー ソケットは、.NET Framework の非同期プログラミング モデルを使用してネットワーク サービス要求を処理します。</span><span class="sxs-lookup"><span data-stu-id="26615-103">Asynchronous server sockets use the .NET Framework asynchronous programming model to process network service requests.</span></span> <span data-ttu-id="26615-104"><xref:System.Net.Sockets.Socket> クラスは、標準の .NET Framework の非同期名前付けパターンに従います。たとえば、同期の <xref:System.Net.Sockets.Socket.Accept%2A> メソッドは非同期の <xref:System.Net.Sockets.Socket.BeginAccept%2A> メソッドと <xref:System.Net.Sockets.Socket.EndAccept%2A> メソッドに対応します。</span><span class="sxs-lookup"><span data-stu-id="26615-104">The <xref:System.Net.Sockets.Socket> class follows the standard .NET Framework asynchronous naming pattern; for example, the synchronous <xref:System.Net.Sockets.Socket.Accept%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginAccept%2A> and <xref:System.Net.Sockets.Socket.EndAccept%2A> methods.</span></span>  
  
 <span data-ttu-id="26615-105">非同期サーバー ソケットには、ネットワークからの接続要求の受け入れを開始するメソッド、接続要求を処理してネットワークからデータの受信を開始するコールバック メソッド、データの受信を終了するコールバック メソッドが必要です。</span><span class="sxs-lookup"><span data-stu-id="26615-105">An asynchronous server socket requires a method to begin accepting connection requests from the network, a callback method to handle the connection requests and begin receiving data from the network, and a callback method to end receiving the data.</span></span> <span data-ttu-id="26615-106">このセクションでは、このそれぞれについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="26615-106">All these methods are discussed further in this section.</span></span>  
  
 <span data-ttu-id="26615-107">次の例では、ネットワークから接続要求の受け入れを開始するために、メソッド `StartListening` で **Socket** を初期化してから、**BeginAccept** メソッドを使用して新しい接続の受け入れを開始します。</span><span class="sxs-lookup"><span data-stu-id="26615-107">In the following example, to begin accepting connection requests from the network, the method `StartListening` initializes the **Socket** and then uses the **BeginAccept** method to start accepting new connections.</span></span> <span data-ttu-id="26615-108">ソケットで新しい接続要求を受信すると、accept のコールバック メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="26615-108">The accept callback method is called when a new connection request is received on the socket.</span></span> <span data-ttu-id="26615-109">このコールバック メソッドは、接続を処理する **Socket** インスタンスを取得し、要求を処理するスレッドに **Socket** を渡す役割を持ちます。</span><span class="sxs-lookup"><span data-stu-id="26615-109">It is responsible for getting the **Socket** instance that will handle the connection and handing that **Socket** off to the thread that will process the request.</span></span> <span data-ttu-id="26615-110">accept のコールバック メソッドは <xref:System.AsyncCallback> デリゲートを実装しており、void を返して <xref:System.IAsyncResult> 型の 1 つのパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="26615-110">The accept callback method implements the <xref:System.AsyncCallback> delegate; it returns a void and takes a single parameter of type <xref:System.IAsyncResult>.</span></span> <span data-ttu-id="26615-111">accept のコールバック メソッドのシェルの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="26615-111">The following example is the shell of an accept callback method.</span></span>  
  
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
  
 <span data-ttu-id="26615-112">**BeginAccept** メソッドは 2 つのパラメーターを受け取ります。accept のコールバック メソッドを示す **AsyncCallback** デリゲートと、状態情報をコールバック メソッドに渡すために使用されるオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="26615-112">The **BeginAccept** method takes two parameters, an **AsyncCallback** delegate that points to the accept callback method and an object that is used to pass state information to the callback method.</span></span> <span data-ttu-id="26615-113">次の例では、リッスンしている **Socket** が *state* パラメーターを使用してコールバック メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="26615-113">In the following example, the listening **Socket** is passed to the callback method through the *state* parameter.</span></span> <span data-ttu-id="26615-114">この例では、**AsyncCallback** デリゲートを作成し、ネットワークから接続の受け入れを開始します。</span><span class="sxs-lookup"><span data-stu-id="26615-114">This example creates an **AsyncCallback** delegate and starts accepting connections from the network.</span></span>  
  
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
  
 <span data-ttu-id="26615-115">非同期ソケットは、システム スレッド プールの複数のスレッドを使用して、受信接続を処理します。</span><span class="sxs-lookup"><span data-stu-id="26615-115">Asynchronous sockets use threads from the system thread pool to process incoming connections.</span></span> <span data-ttu-id="26615-116">接続の受け入れに使用されるスレッド、各受信接続の処理に使用されるスレッド、接続からデータを受け取るために使用されるスレッドがあります。</span><span class="sxs-lookup"><span data-stu-id="26615-116">One thread is responsible for accepting connections, another thread is used to handle each incoming connection, and another thread is responsible for receiving data from the connection.</span></span> <span data-ttu-id="26615-117">スレッド プールが割り当てるスレッドによっては、これらのスレッドが同じスレッドになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="26615-117">These could be the same thread, depending on which thread is assigned by the thread pool.</span></span> <span data-ttu-id="26615-118">次の例では、<xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> クラスがメイン スレッドの実行を停止し、実行を続行できるようになったらシグナルを送ります。</span><span class="sxs-lookup"><span data-stu-id="26615-118">In the following example, the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class suspends execution of the main thread and signals when execution can continue.</span></span>  
  
 <span data-ttu-id="26615-119">ローカル コンピューター上に非同期 TCP/IP Socket を作成し、接続の受け入れを開始する非同期メソッドの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="26615-119">The following example shows an asynchronous method that creates an asynchronous TCP/IP socket on the local computer and begins accepting connections.</span></span> <span data-ttu-id="26615-120">`allDone` というグローバル **ManualResetEvent** があり、メソッドが `SocketListener` というクラスのメンバーであり、`acceptCallback` というコールバック メソッドが定義されているとします。</span><span class="sxs-lookup"><span data-stu-id="26615-120">It assumes that there is a global **ManualResetEvent** named `allDone`, that the method is a member of a class named `SocketListener`, and that a callback method named `acceptCallback` is defined.</span></span>  
  
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
  
 <span data-ttu-id="26615-121">accept のコールバック メソッド (前の例では `acceptCallback`) は、処理を継続するためにメイン アプリケーション スレッドにシグナルを送り、クライアントとの接続を確立し、クライアントからデータの非同期読み取りを開始します。</span><span class="sxs-lookup"><span data-stu-id="26615-121">The accept callback method (`acceptCallback` in the preceding example) is responsible for signaling the main application thread to continue processing, establishing the connection with the client, and starting the asynchronous read of data from the client.</span></span> <span data-ttu-id="26615-122">次の例は、`acceptCallback` メソッドの実装の最初の部分です。</span><span class="sxs-lookup"><span data-stu-id="26615-122">The following example is the first part of an implementation of the `acceptCallback` method.</span></span> <span data-ttu-id="26615-123">このメソッドのセクションでは、処理を継続するためにメイン アプリケーション スレッドに信号を送り、クライアントへの接続を確立しています。</span><span class="sxs-lookup"><span data-stu-id="26615-123">This section of the method signals the main application thread to continue processing and establishes the connection to the client.</span></span> <span data-ttu-id="26615-124">`allDone` というグローバル **ManualResetEvent** があるとします。</span><span class="sxs-lookup"><span data-stu-id="26615-124">It assumes a global **ManualResetEvent** named `allDone`.</span></span>  
  
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
  
 <span data-ttu-id="26615-125">クライアント ソケットからデータを読み取るには、非同期呼び出しの間で値を渡す状態オブジェクトが必要です。</span><span class="sxs-lookup"><span data-stu-id="26615-125">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="26615-126">次の例では、リモート クライアントから文字列を受信する状態オブジェクトを実装しています。</span><span class="sxs-lookup"><span data-stu-id="26615-126">The following example implements a state object for receiving a string from the remote client.</span></span> <span data-ttu-id="26615-127">クライアント ソケットのフィールド、データを受信するデータ バッファー、クライアントから送信されるデータ文字列を作成する <xref:System.Text.StringBuilder> が含まれています。</span><span class="sxs-lookup"><span data-stu-id="26615-127">It contains fields for the client socket, a data buffer for receiving data, and a <xref:System.Text.StringBuilder> for creating the data string sent by the client.</span></span> <span data-ttu-id="26615-128">これらのフィールドを状態オブジェクトに格納することで、複数の呼び出し間で値を保持し、クライアント ソケットからデータ読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="26615-128">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
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
  
 <span data-ttu-id="26615-129">クライアント ソケットからデータの受信を開始する `acceptCallback` メソッドのセクションでは、まず `StateObject` クラスのインスタンスを初期化してから、<xref:System.Net.Sockets.Socket.BeginReceive%2A> メソッドを呼び出してクライアント ソケットからデータの読み取りを非同期に開始します。</span><span class="sxs-lookup"><span data-stu-id="26615-129">The section of the `acceptCallback` method that starts receiving the data from the client socket first initializes an instance of the `StateObject` class and then calls the <xref:System.Net.Sockets.Socket.BeginReceive%2A> method to start reading the data from the client socket asynchronously.</span></span>  
  
 <span data-ttu-id="26615-130">`acceptCallback` メソッドのサンプル コード全体を次に示します。</span><span class="sxs-lookup"><span data-stu-id="26615-130">The following example shows the complete `acceptCallback` method.</span></span> <span data-ttu-id="26615-131">`StateObject` クラスが定義されている `allDone,` というグローバル **ManualResetEvent** があり、`readCallback` メソッドが `SocketListener` というクラスで定義されているとします。</span><span class="sxs-lookup"><span data-stu-id="26615-131">It assumes that there is a global **ManualResetEvent** named `allDone,` that the `StateObject` class is defined, and that the `readCallback` method is defined in a class named `SocketListener`.</span></span>  
  
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
  
 <span data-ttu-id="26615-132">非同期ソケット サーバーのために実装が必要な最後のメソッドは、クライアントから送信されたデータを返す read のコールバック メソッドです。</span><span class="sxs-lookup"><span data-stu-id="26615-132">The final method that needs to be implemented for the asynchronous socket server is the read callback method that returns the data sent by the client.</span></span> <span data-ttu-id="26615-133">accept のコールバック メソッドと同様に、read のコールバック メソッドは **AsyncCallback** デリゲートです。</span><span class="sxs-lookup"><span data-stu-id="26615-133">Like the accept callback method, the read callback method is an **AsyncCallback** delegate.</span></span> <span data-ttu-id="26615-134">このメソッドは、クライアント ソケットからデータ バッファーに 1 から数バイトのデータを読み取ってから、クライアントから送信されたデータが完了するまで、**BeginReceive** メソッドを再び呼び出します。</span><span class="sxs-lookup"><span data-stu-id="26615-134">This method reads one or more bytes from the client socket into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="26615-135">メッセージ全体がクライアントから読み取られたら、コンソールに文字列が表示され、クライアントへの接続を処理するサーバー ソケットが閉じられます。</span><span class="sxs-lookup"><span data-stu-id="26615-135">Once the entire message has been read from the client, the string is displayed on the console and the server socket handling the connection to the client is closed.</span></span>  
  
 <span data-ttu-id="26615-136">`readCallback` メソッドを実装する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="26615-136">The following sample implements the `readCallback` method.</span></span> <span data-ttu-id="26615-137">`StateObject` クラスが定義されているとします。</span><span class="sxs-lookup"><span data-stu-id="26615-137">It assumes that the `StateObject` class is defined.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="26615-138">参照</span><span class="sxs-lookup"><span data-stu-id="26615-138">See Also</span></span>  
 [<span data-ttu-id="26615-139">同期サーバー ソケットの使用</span><span class="sxs-lookup"><span data-stu-id="26615-139">Using a Synchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)  
 [<span data-ttu-id="26615-140">非同期サーバー ソケットの例</span><span class="sxs-lookup"><span data-stu-id="26615-140">Asynchronous Server Socket Example</span></span>](../../../docs/framework/network-programming/asynchronous-server-socket-example.md)  
 [<span data-ttu-id="26615-141">スレッド化</span><span class="sxs-lookup"><span data-stu-id="26615-141">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="26615-142">リッスン (ソケットで)</span><span class="sxs-lookup"><span data-stu-id="26615-142">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)

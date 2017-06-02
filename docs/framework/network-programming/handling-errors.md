---
title: "エラー処理 | Microsoft Docs"
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
  - "インターネット、WebRequest クラスおよび WebResponse クラスの例外"
  - "Status プロパティ"
  - "WebExceptions クラス, WebExceptions クラスの概要"
  - "Timeout 列挙型のメンバー"
  - "ConnectFailure 列挙型のメンバー"
  - "TrustFailure 列挙型のメンバー"
  - "WebRequest クラス、例外"
  - "要求 (インターネットからデータを)、エラー処理"
  - "Success 列挙型のメンバー"
  - "受信 (データを)、エラー"
  - "ProtocolError 列挙型のメンバー"
  - "ダウンロード (インターネット リソースの)、エラー処理"
  - "WebResponse クラス、例外"
  - "SendFailure 列挙型のメンバー"
  - "エラー [.NET Framework]、WebRequest クラスと WebResponse クラスの例外"
  - "送信 (データを)、エラー"
  - "インターネット要求への応答、エラー処理"
  - "NameResolutionFailure 列挙型のメンバー"
  - "KeepAliveFailure 列挙型のメンバー"
  - "ネットワーク リソース、WebRequest クラスと WebResponse クラスの例外"
  - "RequestCanceled 列挙型のメンバー"
  - "ReceiveFailure 列挙型のメンバー"
  - "ServerProtocolViolation 列挙型のメンバー"
  - "ConnectionClosed 列挙型のメンバー"
  - "SecureChannelFailure 列挙型のメンバー"
ms.assetid: 657141cd-5cf5-4fdb-a4b2-4c040eba84b5
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# エラー処理
<xref:System.Net.WebRequest> と <xref:System.Net.WebResponse> \(クラス <xref:System.Net.WebRequest.GetResponse%2A> 方法で投げられる [WebExceptions](frlrfsystemnetwebexceptionclasstopic) であるシステムの両方\) 例外 \(<xref:System.ArgumentException>など\) および Web 特定の例外投げます。  
  
 各 **WebException** は <xref:System.Net.WebExceptionStatus> の列挙型の値を含む <xref:System.Net.WebException.Status%2A> のプロパティがあります。  エラーを確認するに **\[状態\]** のプロパティを確認し、未収エラーを解決するために必要な手順を実行します。  
  
 次の表に、**\[状態\]** のプロパティの使用可能な値を示します。  
  
|状態|説明|  
|--------|--------|  
|ConnectFailure|リモートに、サービス レベルで連絡できませんでした。|  
|ConnectionClosed|関連付けは、時期早尚に閉じられました。|  
|KeepAliveFailure|サーバーはキープアライブ ヘッダーのセットによる接続を閉じました。|  
|NameResolutionFailure|名前のサービスをホスト名を解決しませんでした。|  
|ProtocolError|サーバーから受信された回答が完了が、セキュリティ レベルでエラーが指定された。|  
|ReceiveFailure|リモート サーバーから完全な応答が受信されませんでした。|  
|RequestCanceled|要求は取り消されました。|  
|SecureChannelFailure|エラーは保護されたチャネルのリンクにしました。|  
|SendFailure|完全な要求をリモート サーバーに送信できませんでした。|  
|ServerProtocolViolation|サーバー応答が有効な HTTP 応答ではありません。|  
|成功|エラーは発生しませんでした。|  
|タイムアウト|予想される反応はありません要求のタイムアウトのセット内で受領されています。|  
|TrustFailure|サーバー証明書を検証できませんでした。|  
|MessageLengthLimitExceeded|サーバーに要求を送信、またはサーバーからの応答を受信しているときに、制限長を超えるメッセージが渡されました。|  
|保留|内部非同期要求が保留中です。|  
|PipelineFailure|この値は、.NET Framework の下部組織をサポートし、自分のコードで直接使用されるものではありません。|  
|ProxyNameResolutionFailure|名前解決サービスがプロキシ ホスト名を解決できませんでした。|  
|UnknownError|未知の種類の例外が発生しました。|  
  
 サーバーからの応答を含む **\[状態\]** のプロパティが **WebExceptionStatus.ProtocolError**すると、**WebResponse** が使用できます。  プロトコル エラーの実際のソースを決定するためにこの応答を確認できます。  
  
 次の例で **WebException**をつかまえる方法を示します。  
  
```csharp  
try   
{  
    // Create a request instance.  
    WebRequest myRequest =   
    WebRequest.Create("http://www.contoso.com");  
    // Get the response.  
    WebResponse myResponse = myRequest.GetResponse();  
    //Get a readable stream from the server.   
    Stream sr = myResponse.GetResponseStream();  
  
    //Read from the stream and write any data to the console.  
    bytesread = sr.Read( myBuffer, 0, length);  
    while( bytesread > 0 )   
    {  
        for (int i=0; i<bytesread; i++) {  
            Console.Write( "{0}", myBuffer[i]);  
        }  
        Console.WriteLine();  
        bytesread = sr.Read( myBuffer, 0, length);  
    }  
    sr.Close();  
    myResponse.Close();  
}  
catch (WebException webExcp)   
{  
    // If you reach this point, an exception has been caught.  
    Console.WriteLine("A WebException has been caught.");  
    // Write out the WebException message.  
    Console.WriteLine(webExcp.ToString());  
    // Get the WebException status code.  
    WebExceptionStatus status =  webExcp.Status;  
    // If status is WebExceptionStatus.ProtocolError,   
    //   there has been a protocol error and a WebResponse   
    //   should exist. Display the protocol error.  
    if (status == WebExceptionStatus.ProtocolError) {  
        Console.Write("The server returned protocol error ");  
        // Get HttpWebResponse so that you can check the HTTP status code.  
        HttpWebResponse httpResponse = (HttpWebResponse)webExcp.Response;  
        Console.WriteLine((int)httpResponse.StatusCode + " - "  
           + httpResponse.StatusCode);  
    }  
}  
catch (Exception e)   
{  
    // Code to catch other exceptions goes here.  
}  
```  
  
```vb  
Try  
    ' Create a request instance.  
    Dim myRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
    ' Get the response.  
    Dim myResponse As WebResponse = myRequest.GetResponse()  
    'Get a readable stream from the server.   
    Dim sr As Stream = myResponse.GetResponseStream()  
  
    Dim i As Integer      
    'Read from the stream and write any data to the console.  
    bytesread = sr.Read(myBuffer, 0, length)  
    While bytesread > 0  
        For i = 0 To bytesread - 1  
            Console.Write("{0}", myBuffer(i))  
        Next i  
        Console.WriteLine()  
        bytesread = sr.Read(myBuffer, 0, length)  
    End While  
    sr.Close()  
    myResponse.Close()  
Catch webExcp As WebException  
    ' If you reach this point, an exception has been caught.  
    Console.WriteLine("A WebException has been caught.")  
    ' Write out the WebException message.  
    Console.WriteLine(webExcp.ToString())  
    ' Get the WebException status code.  
    Dim status As WebExceptionStatus = webExcp.Status  
    ' If status is WebExceptionStatus.ProtocolError,   
    '   there has been a protocol error and a WebResponse   
    '   should exist. Display the protocol error.  
    If status = WebExceptionStatus.ProtocolError Then  
        Console.Write("The server returned protocol error ")  
        ' Get HttpWebResponse so that you can check the HTTP status code.  
        Dim httpResponse As HttpWebResponse = _  
           CType(webExcp.Response, HttpWebResponse)  
        Console.WriteLine(CInt(httpResponse.StatusCode).ToString() & _  
           " - " & httpResponse.StatusCode.ToString())  
    End If  
Catch e As Exception  
    ' Code to catch other exceptions goes here.  
End Try  
```  
  
 エラーが Windows のソケットで計上ときに <xref:System.Net.Sockets.Socket> クラスの投球 [SocketExceptions](frlrfsystemnetsocketssocketexceptionclasstopic) を使用するアプリケーション。  [TCPListener](frlrfsystemnetsocketstcplistenerclasstopic)と [UDPClient](frlrfsystemnetsocketsudpclientclasstopic) の [&#91;TCPClient&#93;](frlrfsystemnetsocketstcpclientclasstopic)、クラスは、**\[ソケット\]** クラスの上に構築、**SocketExceptions** も投げます。  
  
 **SocketException** が投げられると、**SocketException** のクラスが未収最後のオペレーティング システムのソケットのエラーに <xref:System.Net.Sockets.SocketException.ErrorCode%2A> のプロパティを設定します。  ソケットのエラー コードの詳細については、MSDN の Winsock 2.0 の API のエラー コードのドキュメントを参照してください。  
  
## 参照  
 [例外処理の基本事項](../../../docs/standard/exceptions/exception-handling-fundamentals.md)   
 [データの要求](../../../docs/framework/network-programming/requesting-data.md)
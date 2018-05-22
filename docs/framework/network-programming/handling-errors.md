---
title: エラー処理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Internet, WebRequest and WebResponse classes exceptions
- Status property
- WebExceptions class, about WebExceptions class
- Timeout enumeration member
- ConnectFailure enumeration member
- TrustFailure enumeration member
- WebRequest class, exceptions
- requesting data from Internet, error handling
- Success enumeration member
- receiving data, errors
- ProtocolError enumeration member
- downloading Internet resources, error handling
- WebResponse class, exceptions
- SendFailure enumeration member
- errors [.NET Framework], WebRequest and WebResponse classes exceptions
- sending data, errors
- response to Internet request, error handling
- NameResolutionFailure enumeration member
- KeepAliveFailure enumeration member
- network resources, WebRequest and WebResponse classes exceptions
- RequestCanceled enumeration member
- ReceiveFailure enumeration member
- ServerProtocolViolation enumeration member
- ConnectionClosed enumeration member
- SecureChannelFailure enumeration member
ms.assetid: 657141cd-5cf5-4fdb-a4b2-4c040eba84b5
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8020a92345ba85a99c0b46b2d4247d677defd054
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="handling-errors"></a><span data-ttu-id="f42c1-102">エラー処理</span><span class="sxs-lookup"><span data-stu-id="f42c1-102">Handling Errors</span></span>
<span data-ttu-id="f42c1-103"><xref:System.Net.WebRequest> および <xref:System.Net.WebResponse> クラスでは、システム例外 (<xref:System.ArgumentException> など) と Web 固有の例外 (<xref:System.Net.WebRequest.GetResponse%2A> メソッドでスローされる <xref:System.Net.WebException>) の両方がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f42c1-103">The <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes throw both system exceptions (such as <xref:System.ArgumentException>) and Web-specific exceptions (which are <xref:System.Net.WebException> thrown by the <xref:System.Net.WebRequest.GetResponse%2A> method).</span></span>  
  
 <span data-ttu-id="f42c1-104">各 **WebException** には、<xref:System.Net.WebExceptionStatus> 列挙体からの値を含む <xref:System.Net.WebException.Status%2A> プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="f42c1-104">Each **WebException** includes a <xref:System.Net.WebException.Status%2A> property that contains a value from the <xref:System.Net.WebExceptionStatus> enumeration.</span></span> <span data-ttu-id="f42c1-105">**Status** プロパティを調べることで、発生したエラーを特定し、エラーを解決するための適切な手順を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="f42c1-105">You can examine the **Status** property to determine the error that occurred and take the proper steps to resolve the error.</span></span>  
  
 <span data-ttu-id="f42c1-106">**Status** プロパティの有効な値を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="f42c1-106">The following table describes the possible values for the **Status** property.</span></span>  
  
|<span data-ttu-id="f42c1-107">Status</span><span class="sxs-lookup"><span data-stu-id="f42c1-107">Status</span></span>|<span data-ttu-id="f42c1-108">説明</span><span class="sxs-lookup"><span data-stu-id="f42c1-108">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="f42c1-109">ConnectFailure</span><span class="sxs-lookup"><span data-stu-id="f42c1-109">ConnectFailure</span></span>|<span data-ttu-id="f42c1-110">トランスポート レベルでリモート サービスに接続できませんでした。</span><span class="sxs-lookup"><span data-stu-id="f42c1-110">The remote service could not be contacted at the transport level.</span></span>|  
|<span data-ttu-id="f42c1-111">ConnectionClosed</span><span class="sxs-lookup"><span data-stu-id="f42c1-111">ConnectionClosed</span></span>|<span data-ttu-id="f42c1-112">接続は処理の途中で中断されました。</span><span class="sxs-lookup"><span data-stu-id="f42c1-112">The connection was closed prematurely.</span></span>|  
|<span data-ttu-id="f42c1-113">KeepAliveFailure</span><span class="sxs-lookup"><span data-stu-id="f42c1-113">KeepAliveFailure</span></span>|<span data-ttu-id="f42c1-114">サーバーは、Keep-alive ヘッダーの設定による接続を閉じました。</span><span class="sxs-lookup"><span data-stu-id="f42c1-114">The server closed a connection made with the Keep-alive header set.</span></span>|  
|<span data-ttu-id="f42c1-115">NameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="f42c1-115">NameResolutionFailure</span></span>|<span data-ttu-id="f42c1-116">ドメイン サービスがホスト名を解決できませんでした。</span><span class="sxs-lookup"><span data-stu-id="f42c1-116">The name service could not resolve the host name.</span></span>|  
|<span data-ttu-id="f42c1-117">ProtocolError</span><span class="sxs-lookup"><span data-stu-id="f42c1-117">ProtocolError</span></span>|<span data-ttu-id="f42c1-118">サーバーから受信された応答は完全でしたが、プロトコル レベルのエラーが示されています。</span><span class="sxs-lookup"><span data-stu-id="f42c1-118">The response received from the server was complete but indicated an error at the protocol level.</span></span>|  
|<span data-ttu-id="f42c1-119">ReceiveFailure</span><span class="sxs-lookup"><span data-stu-id="f42c1-119">ReceiveFailure</span></span>|<span data-ttu-id="f42c1-120">完全な応答がリモート サーバーから受信されませんでした。</span><span class="sxs-lookup"><span data-stu-id="f42c1-120">A complete response was not received from the remote server.</span></span>|  
|<span data-ttu-id="f42c1-121">RequestCanceled</span><span class="sxs-lookup"><span data-stu-id="f42c1-121">RequestCanceled</span></span>|<span data-ttu-id="f42c1-122">要求は取り消されました。</span><span class="sxs-lookup"><span data-stu-id="f42c1-122">The request was canceled.</span></span>|  
|<span data-ttu-id="f42c1-123">SecureChannelFailure</span><span class="sxs-lookup"><span data-stu-id="f42c1-123">SecureChannelFailure</span></span>|<span data-ttu-id="f42c1-124">セキュリティで保護されたチャネル リンクでエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f42c1-124">An error occurred in a secure channel link.</span></span>|  
|<span data-ttu-id="f42c1-125">SendFailure</span><span class="sxs-lookup"><span data-stu-id="f42c1-125">SendFailure</span></span>|<span data-ttu-id="f42c1-126">リモート サーバーに完全な要求を送信できませでした。</span><span class="sxs-lookup"><span data-stu-id="f42c1-126">A complete request could not be sent to the remote server.</span></span>|  
|<span data-ttu-id="f42c1-127">ServerProtocolViolation</span><span class="sxs-lookup"><span data-stu-id="f42c1-127">ServerProtocolViolation</span></span>|<span data-ttu-id="f42c1-128">サーバーの応答が有効な HTTP 応答ではありません。</span><span class="sxs-lookup"><span data-stu-id="f42c1-128">The server response was not a valid HTTP response.</span></span>|  
|<span data-ttu-id="f42c1-129">成功</span><span class="sxs-lookup"><span data-stu-id="f42c1-129">Success</span></span>|<span data-ttu-id="f42c1-130">エラーは発生しませんでした。</span><span class="sxs-lookup"><span data-stu-id="f42c1-130">No error was encountered.</span></span>|  
|<span data-ttu-id="f42c1-131">Timeout</span><span class="sxs-lookup"><span data-stu-id="f42c1-131">Timeout</span></span>|<span data-ttu-id="f42c1-132">要求に対して設定されたタイムアウト時間内で応答が受信されませんでした。</span><span class="sxs-lookup"><span data-stu-id="f42c1-132">No response was received within the time-out set for the request.</span></span>|  
|<span data-ttu-id="f42c1-133">TrustFailure</span><span class="sxs-lookup"><span data-stu-id="f42c1-133">TrustFailure</span></span>|<span data-ttu-id="f42c1-134">サーバー証明書を検証できませんでした。</span><span class="sxs-lookup"><span data-stu-id="f42c1-134">A server certificate could not be validated.</span></span>|  
|<span data-ttu-id="f42c1-135">MessageLengthLimitExceeded</span><span class="sxs-lookup"><span data-stu-id="f42c1-135">MessageLengthLimitExceeded</span></span>|<span data-ttu-id="f42c1-136">要求の送信時またはサーバーから応答の受信時に指定された制限を超えるメッセージが受信されました。</span><span class="sxs-lookup"><span data-stu-id="f42c1-136">A message was received that exceeded the specified limit when sending a request or receiving a response from the server.</span></span>|  
|<span data-ttu-id="f42c1-137">保留</span><span class="sxs-lookup"><span data-stu-id="f42c1-137">Pending</span></span>|<span data-ttu-id="f42c1-138">内部非同期要求が保留中です。</span><span class="sxs-lookup"><span data-stu-id="f42c1-138">An internal asynchronous request is pending.</span></span>|  
|<span data-ttu-id="f42c1-139">PipelineFailure</span><span class="sxs-lookup"><span data-stu-id="f42c1-139">PipelineFailure</span></span>|<span data-ttu-id="f42c1-140">この値は .NET Framework インフラストラクチャをサポートします。独自に作成したコードで直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="f42c1-140">This value supports the .NET Framework infrastructure and is not intended to be used directly in your code.</span></span>|  
|<span data-ttu-id="f42c1-141">ProxyNameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="f42c1-141">ProxyNameResolutionFailure</span></span>|<span data-ttu-id="f42c1-142">ネーム リゾルバー サービスがプロキシ ホスト名を解決できませんでした。</span><span class="sxs-lookup"><span data-stu-id="f42c1-142">The name resolver service could not resolve the proxy host name.</span></span>|  
|<span data-ttu-id="f42c1-143">UnknownError</span><span class="sxs-lookup"><span data-stu-id="f42c1-143">UnknownError</span></span>|<span data-ttu-id="f42c1-144">不明な種類の例外が発生しました。</span><span class="sxs-lookup"><span data-stu-id="f42c1-144">An exception of unknown type has occurred.</span></span>|  
  
 <span data-ttu-id="f42c1-145">**Status** プロパティが **WebExceptionStatus.ProtocolError** である場合は、サーバーからの応答を含む **WebResponse** を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f42c1-145">When the **Status** property is **WebExceptionStatus.ProtocolError**, a **WebResponse** that contains the response from the server is available.</span></span> <span data-ttu-id="f42c1-146">この応答を調べることで、プロトコル エラーの実際の原因を判別できます。</span><span class="sxs-lookup"><span data-stu-id="f42c1-146">You can examine this response to determine the actual source of the protocol error.</span></span>  
  
 <span data-ttu-id="f42c1-147">次の例は、**WebException** をキャッチする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f42c1-147">The following example shows how to catch a **WebException**.</span></span>  
  
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
  
 <span data-ttu-id="f42c1-148">Windows ソケットでエラーが発生した場合、<xref:System.Net.Sockets.Socket> クラスを使用するアプリケーションは <xref:System.Net.Sockets.SocketException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="f42c1-148">Applications that use the <xref:System.Net.Sockets.Socket> class throw <xref:System.Net.Sockets.SocketException> when errors occur on the Windows socket.</span></span> <span data-ttu-id="f42c1-149"><xref:System.Net.Sockets.TcpClient>、<xref:System.Net.Sockets.TcpListener>、および <xref:System.Net.Sockets.UdpClient> は **Socket** クラスに基づくものであり、同様に **SocketExceptions** をスローします。</span><span class="sxs-lookup"><span data-stu-id="f42c1-149">The <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes are built on top of the **Socket** class and throw **SocketExceptions** as well.</span></span>  
  
 <span data-ttu-id="f42c1-150">**SocketException** がスローされると、**SocketException** クラスは <xref:System.Net.Sockets.SocketException.ErrorCode%2A> プロパティを、最後に発生したオペレーティング システムのソケット エラーに設定します。</span><span class="sxs-lookup"><span data-stu-id="f42c1-150">When a **SocketException** is thrown, the **SocketException** class sets the <xref:System.Net.Sockets.SocketException.ErrorCode%2A> property to the last operating system socket error that occurred.</span></span> <span data-ttu-id="f42c1-151">ソケット エラー コードの詳細については、MSDN の Winsock 2.0 API エラー コードに関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f42c1-151">For more information about socket error codes, see the Winsock 2.0 API error code documentation in MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f42c1-152">参照</span><span class="sxs-lookup"><span data-stu-id="f42c1-152">See Also</span></span>  
 [<span data-ttu-id="f42c1-153">例外処理の基本事項</span><span class="sxs-lookup"><span data-stu-id="f42c1-153">Exception Handling Fundamentals</span></span>](../../../docs/standard/exceptions/exception-handling-fundamentals.md)  
 [<span data-ttu-id="f42c1-154">データの要求</span><span class="sxs-lookup"><span data-stu-id="f42c1-154">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)

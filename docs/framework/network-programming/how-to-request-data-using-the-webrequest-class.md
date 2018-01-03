---
title: "方法: WebRequest クラスを使用してデータを要求する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- downloading Internet resources, steps
- requesting data from Internet, steps
- WebRequest class, receiving data
- receiving data, using WebRequest class
- Internet, requesting data
ms.assetid: 368b8d0f-dc5e-4469-a8b8-b2adbf5dd800
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: bd714a9e006f87a817ca931757aaaaed920f50f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-request-data-using-the-webrequest-class"></a><span data-ttu-id="a79e6-102">方法: WebRequest クラスを使用してデータを要求する</span><span class="sxs-lookup"><span data-stu-id="a79e6-102">How to: Request Data Using the WebRequest Class</span></span>
<span data-ttu-id="a79e6-103">次の手順では、たとえば、Web ページやファイルなどのリソースをサーバーから要求するための手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="a79e6-103">The following procedure describes the steps used to request a resource from a server, for example, a Web page or file.</span></span> <span data-ttu-id="a79e6-104">リソースは URI で識別される必要があります。</span><span class="sxs-lookup"><span data-stu-id="a79e6-104">The resource must be identified by a URI.</span></span>  
  
### <a name="to-request-data-from-a-host-server"></a><span data-ttu-id="a79e6-105">ホスト サーバーからデータを要求するには</span><span class="sxs-lookup"><span data-stu-id="a79e6-105">To request data from a host server</span></span>  
  
1.  <span data-ttu-id="a79e6-106">リソースの URI を指定して <xref:System.Net.WebRequest.Create%2A> を呼び出して <xref:System.Net.WebRequest> インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="a79e6-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A> with the URI of the resource.</span></span>  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="a79e6-107">.NET Framework は、"http:"、"https:'、"ftp:" および"file:" で始まる URI に対応する **WebRequest** と **WebResponse** から派生したプロトコル固有のクラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="a79e6-107">The .NET Framework provides protocol-specific classes derived from **WebRequest** and **WebResponse** for URIs that begin with "http:", "https:'', "ftp:", and "file:".</span></span> <span data-ttu-id="a79e6-108">その他のプロトコルを使用してリソースにアクセスするには、**WebRequest** と **WebResponse** から派生したプロトコル固有のクラスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a79e6-108">To access resources using other protocols, you must implement protocol-specific classes that derive from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="a79e6-109">詳細については、「[Programming Pluggable Protocols](../../../docs/framework/network-programming/programming-pluggable-protocols.md)」(プラグ可能なプロトコルのプログラミング) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a79e6-109">For more information, see [Programming Pluggable Protocols](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .</span></span>  
  
2.  <span data-ttu-id="a79e6-110">**WebRequest** で必要なプロパティの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="a79e6-110">Set any property values that you need in the **WebRequest**.</span></span> <span data-ttu-id="a79e6-111">たとえば、認証を有効にするには、**Credentials** プロパティを <xref:System.Net.NetworkCredential> クラスのインスタンスに設定します。</span><span class="sxs-lookup"><span data-stu-id="a79e6-111">For example, to enable authentication, set the **Credentials** property to an instance of the <xref:System.Net.NetworkCredential> class.</span></span>  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
     <span data-ttu-id="a79e6-112">ほとんどの場合、データを受信するには、**WebRequest** クラスで十分です。</span><span class="sxs-lookup"><span data-stu-id="a79e6-112">In most cases, the **WebRequest** class is sufficient to receive data.</span></span> <span data-ttu-id="a79e6-113">ただし、プロトコル固有のプロパティを設定する必要がある場合、**WebRequest** をプロトコル固有の型にキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a79e6-113">However, if you need to set protocol-specific properties, you must cast the **WebRequest** to the protocol-specific type.</span></span> <span data-ttu-id="a79e6-114">たとえば、<xref:System.Net.HttpWebRequest> の HTTP 固有のプロパティにアクセスするには、**WebRequest** を **HttpWebRequest** 参照にキャストします。</span><span class="sxs-lookup"><span data-stu-id="a79e6-114">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebRequest>, cast the **WebRequest** to an **HttpWebRequest** reference.</span></span> <span data-ttu-id="a79e6-115">次のコードの例は、HTTP 固有の <xref:System.Net.HttpWebRequest.UserAgent%2A> プロパティを設定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a79e6-115">The following code example shows how to set the HTTP-specific <xref:System.Net.HttpWebRequest.UserAgent%2A> property.</span></span>  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  <span data-ttu-id="a79e6-116">サーバーに要求を送信するには、<xref:System.Net.HttpWebRequest.GetResponse%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a79e6-116">To send the request to the server, call <xref:System.Net.HttpWebRequest.GetResponse%2A>.</span></span> <span data-ttu-id="a79e6-117">返された **WebResponse** オブジェクトの実際の型は、要求された URI のスキームで決定されます。</span><span class="sxs-lookup"><span data-stu-id="a79e6-117">The actual type of the returned **WebResponse** object is determined by the scheme of the requested URI.</span></span>  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="a79e6-118"><xref:System.Net.WebResponse> オブジェクトの使用が完了した後、<xref:System.Net.WebResponse.Close%2A> メソッドを呼び出して終了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a79e6-118">After you are finished with a <xref:System.Net.WebResponse> object, you must close it by calling the <xref:System.Net.WebResponse.Close%2A> method.</span></span> <span data-ttu-id="a79e6-119">代わりに、応答オブジェクトから応答ストリームを取得した場合、<xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> メソッドを呼び出してストリームを閉じることができます。</span><span class="sxs-lookup"><span data-stu-id="a79e6-119">Alternatively, if you have gotten the response stream from the response object, you can close the stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a79e6-120">応答またはストリームのいずれかを閉じない場合、アプリケーションからサーバーへの接続が不足し、追加の要求を処理できなくなります。</span><span class="sxs-lookup"><span data-stu-id="a79e6-120">If you do not close either the response or the stream, your application can run out of connections to the server and become unable to process additional requests.</span></span>  
  
4.  <span data-ttu-id="a79e6-121">**WebResponse** のプロパティにアクセスするか、または **WebResponse** をプロトコル固有インスタンスにキャストして、プロトコル固有のプロパティを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="a79e6-121">You can access the properties of the **WebResponse** or cast the **WebResponse** to a protocol-specific instance to read protocol-specific properties.</span></span> <span data-ttu-id="a79e6-122">たとえば、<xref:System.Net.HttpWebResponse> の HTTP 固有のプロパティにアクセスするには、**WebResponse** を **HttpWebResponse** 参照にキャストします。</span><span class="sxs-lookup"><span data-stu-id="a79e6-122">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast the **WebResponse** to a **HttpWebResponse** reference.</span></span> <span data-ttu-id="a79e6-123">次のコード例では、応答で送信される状態情報を表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a79e6-123">The following code example shows how to display the status information sent with a response.</span></span>  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  <span data-ttu-id="a79e6-124">サーバーによって送信された応答データを格納しているストリームを取得するには、**WebResponse** の <xref:System.Net.HttpWebResponse.GetResponseStream%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="a79e6-124">To get the stream containing response data sent by the server, use the <xref:System.Net.HttpWebResponse.GetResponseStream%2A> method of the **WebResponse**.</span></span>  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream ();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6.  <span data-ttu-id="a79e6-125">応答からのデータの読み取り後、**Stream.Close** メソッドを使用して応答ストリームを閉じるか、**WebResponse.Close** メソッドを使用して応答を閉じる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a79e6-125">After reading the data from the response, you must either close the response stream using the **Stream.Close** method or close the response using the **WebResponse.Close** method.</span></span> <span data-ttu-id="a79e6-126">応答ストリームと **WebResponse** の両方で **Close** メソッドを呼び出す必要はありませんが、そのようにしても問題はありません。</span><span class="sxs-lookup"><span data-stu-id="a79e6-126">It is not necessary to call the **Close** method on both the response stream and the **WebResponse**, but doing so is not harmful.</span></span> <span data-ttu-id="a79e6-127">**WebResponse.Close** は応答を閉じるときに **Stream.Close** を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a79e6-127">**WebResponse.Close** calls **Stream.Close** when closing the response.</span></span>  
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a><span data-ttu-id="a79e6-128">例</span><span class="sxs-lookup"><span data-stu-id="a79e6-128">Example</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestGetExample  
    {  
        public static void Main ()  
        {  
            // Create a request for the URL.   
            WebRequest request = WebRequest.Create (  
              "http://www.contoso.com/default.html");  
            // If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials;  
            // Get the response.  
            WebResponse response = request.GetResponse ();  
            // Display the status.  
            Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
            // Get the stream containing content returned by the server.  
            Stream dataStream = response.GetResponseStream ();  
            // Open the stream using a StreamReader for easy access.  
            StreamReader reader = new StreamReader (dataStream);  
            // Read the content.  
            string responseFromServer = reader.ReadToEnd ();  
            // Display the content.  
            Console.WriteLine (responseFromServer);  
            // Clean up the streams and the response.  
            reader.Close ();  
            response.Close ();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Net  
Imports System.Text  
Namespace Examples.System.Net  
    Public Class WebRequestGetExample  
  
        Public Shared Sub Main()  
            ' Create a request for the URL.   
            Dim request As WebRequest = _  
              WebRequest.Create("http://www.contoso.com/default.html")  
            ' If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials  
            ' Get the response.  
            Dim response As WebResponse = request.GetResponse()  
            ' Display the status.  
            Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
            ' Get the stream containing content returned by the server.  
            Dim dataStream As Stream = response.GetResponseStream()  
            ' Open the stream using a StreamReader for easy access.  
            Dim reader As New StreamReader(dataStream)  
            ' Read the content.  
            Dim responseFromServer As String = reader.ReadToEnd()  
            ' Display the content.  
            Console.WriteLine(responseFromServer)  
            ' Clean up the streams and the response.  
            reader.Close()  
            response.Close()  
        End Sub   
    End Class   
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="a79e6-129">参照</span><span class="sxs-lookup"><span data-stu-id="a79e6-129">See Also</span></span>  
 [<span data-ttu-id="a79e6-130">インターネット要求の作成</span><span class="sxs-lookup"><span data-stu-id="a79e6-130">Creating Internet Requests</span></span>](../../../docs/framework/network-programming/creating-internet-requests.md)  
 [<span data-ttu-id="a79e6-131">ネットワーク上でストリームを使用する</span><span class="sxs-lookup"><span data-stu-id="a79e6-131">Using Streams on the Network</span></span>](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [<span data-ttu-id="a79e6-132">プロキシを介したインターネットへのアクセス</span><span class="sxs-lookup"><span data-stu-id="a79e6-132">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="a79e6-133">データの要求</span><span class="sxs-lookup"><span data-stu-id="a79e6-133">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)  
 [<span data-ttu-id="a79e6-134">方法: WebRequest クラスを使用してデータを送信する</span><span class="sxs-lookup"><span data-stu-id="a79e6-134">How to: Send Data Using the WebRequest Class</span></span>](../../../docs/framework/network-programming/how-to-send-data-using-the-webrequest-class.md)

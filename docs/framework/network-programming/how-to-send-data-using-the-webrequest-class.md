---
title: "方法: WebRequest クラスを使用してデータを送信する"
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
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: b4cc524b3b3c1dbe42f3fe3926ed44c1e917e871
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-send-data-using-the-webrequest-class"></a><span data-ttu-id="5eb0e-102">方法: WebRequest クラスを使用してデータを送信する</span><span class="sxs-lookup"><span data-stu-id="5eb0e-102">How to: Send Data Using the WebRequest Class</span></span>
<span data-ttu-id="5eb0e-103">次の手順では、サーバーにデータを送信するための手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-103">The following procedure describes the steps used to send data to a server.</span></span> <span data-ttu-id="5eb0e-104">この手順は、通常、Web ページへのデータをポストするときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-104">This procedure is commonly used to post data to a Web page.</span></span>  
  
### <a name="to-send-data-to-a-host-server"></a><span data-ttu-id="5eb0e-105">ホスト サーバーにデータを送信するには</span><span class="sxs-lookup"><span data-stu-id="5eb0e-105">To send data to a host server</span></span>  
  
1.  <span data-ttu-id="5eb0e-106">たとえばスクリプトや ASP.NET ページなどの、データを受け取るリソースの URI を指定して <xref:System.Net.WebRequest.Create%2A> を呼び出すことによって <xref:System.Net.WebRequest> インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A> with the URI of the resource that accepts data, for example, a script or ASP.NET page.</span></span>  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="5eb0e-107">.NET Framework は、"http:"、"https:'、"ftp:" および"file:" で始まる URI に対応する **WebRequest** と **WebResponse** から派生したプロトコル固有のクラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-107">The .NET Framework provides protocol-specific classes derived from **WebRequest** and **WebResponse** for URIs that begin with "http:", "https:'', "ftp:", and "file:".</span></span> <span data-ttu-id="5eb0e-108">その他のプロトコルを使用してリソースにアクセスするには、**WebRequest** と **WebResponse** から派生したプロトコル固有のクラスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-108">To access resources using other protocols, you must implement protocol-specific classes that derive from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="5eb0e-109">詳細については、「[Programming Pluggable Protocols](../../../docs/framework/network-programming/programming-pluggable-protocols.md)」(プラグ可能なプロトコルのプログラミング) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-109">For more information, see [Programming Pluggable Protocols](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .</span></span>  
  
2.  <span data-ttu-id="5eb0e-110">**WebRequest** で必要なプロパティの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-110">Set any property values that you need in the **WebRequest**.</span></span> <span data-ttu-id="5eb0e-111">たとえば、認証を有効にするには、**Credentials** プロパティを <xref:System.Net.NetworkCredential> クラスのインスタンスに設定します。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-111">For example, to enable authentication, set the **Credentials** property to an instance of the <xref:System.Net.NetworkCredential> class.</span></span>  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
     <span data-ttu-id="5eb0e-112">ほとんどの場合、データを送信するには、**WebRequest** インスタンスだけで十分です。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-112">In most cases, the **WebRequest** instance itself is sufficient to send data.</span></span> <span data-ttu-id="5eb0e-113">ただし、プロトコル固有のプロパティを設定する必要がある場合、**WebRequest** をプロトコル固有の型にキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-113">However, if you need to set protocol-specific properties, you must cast the **WebRequest** to the protocol-specific type.</span></span> <span data-ttu-id="5eb0e-114">たとえば、<xref:System.Net.HttpWebRequest> の HTTP 固有のプロパティにアクセスするには、**WebRequest** を **HttpWebRequest** 参照にキャストします。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-114">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebRequest>, cast the **WebRequest** to an **HttpWebRequest** reference.</span></span> <span data-ttu-id="5eb0e-115">次のコードの例は、HTTP 固有の <xref:System.Net.HttpWebRequest.UserAgent%2A> プロパティを設定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-115">The following code example shows how to set the HTTP-specific <xref:System.Net.HttpWebRequest.UserAgent%2A> property.</span></span>  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  <span data-ttu-id="5eb0e-116">HTTP **POST** メソッドなど、要求と共にデータを送信することを許可するプロトコル メソッドを指定します。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-116">Specify a protocol method that permits data to be sent with a request, such as the HTTP **POST** method.</span></span>  
  
    ```csharp  
    request.Method = "POST";  
    ```  
  
    ```vb  
    request.Method = "POST"  
    ```  
  
4.  <span data-ttu-id="5eb0e-117">**ContentLength** プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-117">Set the **ContentLength** property.</span></span>  
  
    ```csharp  
    request.ContentLength = byteArray.Length;  
    ```  
  
    ```vb  
    request.ContentLength = byteArray.Length  
    ```  
  
5.  <span data-ttu-id="5eb0e-118">**ContentType** プロパティを適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-118">Set the **ContentType** property to an appropriate value.</span></span>  
  
    ```csharp  
    request.ContentType = "application/x-www-form-urlencoded";  
    ```  
  
    ```vb  
    request.ContentType = "application/x-www-form-urlencoded"  
    ```  
  
6.  <span data-ttu-id="5eb0e-119"><xref:System.Net.WebRequest.GetRequestStream%2A> メソッドを呼び出すことで、要求のデータを保持するストリームを取得します。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-119">Get the stream that holds request data by calling the <xref:System.Net.WebRequest.GetRequestStream%2A> method.</span></span>  
  
    ```csharp  
    Stream dataStream = request.GetRequestStream ();  
    ```  
  
    ```vb  
    Stream dataStream = request.GetRequestStream ()  
    ```  
  
7.  <span data-ttu-id="5eb0e-120">このメソッドによって返される <xref:System.IO.Stream> オブジェクトにデータを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-120">Write the data to the <xref:System.IO.Stream> object returned by this method.</span></span>  
  
    ```csharp  
    dataStream.Write (byteArray, 0, byteArray.Length);  
    ```  
  
    ```vb  
    dataStream.Write (byteArray, 0, byteArray.Length)  
    ```  
  
8.  <span data-ttu-id="5eb0e-121">**Stream.Close** メソッドを呼び出すことで、要求のストリームを閉じます。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-121">Close the request stream by calling the **Stream.Close** method.</span></span>  
  
    ```csharp  
    dataStream.Close ();  
    ```  
  
    ```vb  
    dataStream.Close ()  
    ```  
  
9. <span data-ttu-id="5eb0e-122"><xref:System.Net.WebRequest.GetResponse%2A> を呼び出してサーバーに要求を送信します。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-122">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A>.</span></span> <span data-ttu-id="5eb0e-123">このメソッドは、サーバーの応答を格納するオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-123">This method returns an object containing the server's response.</span></span> <span data-ttu-id="5eb0e-124">返された <xref:System.Net.WebResponse> オブジェクトの型は、要求の URI のスキームで決定されます。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-124">The returned <xref:System.Net.WebResponse> object's type is determined by the scheme of the request's URI.</span></span>  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="5eb0e-125"><xref:System.Net.WebResponse> オブジェクトの使用が完了した後、<xref:System.Net.WebResponse.Close%2A> メソッドを呼び出して閉じる必要があります。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-125">After you are finished with a <xref:System.Net.WebResponse> object, you must close it by calling the <xref:System.Net.WebResponse.Close%2A> method.</span></span> <span data-ttu-id="5eb0e-126">代わりに、応答オブジェクトから応答ストリームを取得した場合、<xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> メソッドを呼び出してストリームを閉じることができます。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-126">Alternatively, if you have gotten the response stream from the response object, you can close the stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5eb0e-127">応答またはストリームを閉じない場合、アプリケーションからサーバーへの接続が不足し、追加の要求を処理できなくなります。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-127">If you do not close the response or the stream, your application can run out of connections to the server and become unable to process additional requests.</span></span>  
  
10. <span data-ttu-id="5eb0e-128">**WebResponse** のプロパティにアクセスするか、または **WebResponse** をプロトコル固有インスタンスにキャストして、プロトコル固有のプロパティを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-128">You can access the properties of the **WebResponse** or cast the **WebResponse** to a protocol-specific instance to read protocol-specific properties.</span></span> <span data-ttu-id="5eb0e-129">たとえば、<xref:System.Net.HttpWebResponse> の HTTP 固有のプロパティにアクセスするには、**WebResponse** を **HttpWebResponse** 参照にキャストします。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-129">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast the **WebResponse** to an **HttpWebResponse** reference.</span></span>  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. <span data-ttu-id="5eb0e-130">サーバーによって送信された応答データを格納しているストリームを取得するには、**WebResponse** の <xref:System.Net.WebResponse.GetResponseStream%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-130">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A> method of the **WebResponse**.</span></span>  
  
    ```csharp  
    Stream data = response.GetResponseStream;  
    ```  
  
    ```vb  
    Dim data As Stream = response.GetResponseStream  
    ```  
  
12. <span data-ttu-id="5eb0e-131">応答からのデータの読み取り後、**Stream.Close** メソッドを使用して応答ストリームを閉じるか、**WebResponse.Close** メソッドを使用して応答を閉じる必要があります。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-131">After reading the data from the response, you must either close the response stream using the **Stream.Close** method or close the response using the **WebResponse.Close** method.</span></span> <span data-ttu-id="5eb0e-132">応答ストリームと **WebResponse** の両方で **Close** メソッドを呼び出す必要はありませんが、そのようにしても問題はありません。</span><span class="sxs-lookup"><span data-stu-id="5eb0e-132">It is not necessary to call the **Close** method on both the response stream and the **WebResponse**, but doing so is not harmful.</span></span>  
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a><span data-ttu-id="5eb0e-133">例</span><span class="sxs-lookup"><span data-stu-id="5eb0e-133">Example</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestPostExample  
    {  
        public static void Main ()  
        {  
            // Create a request using a URL that can receive a post.   
            WebRequest request = WebRequest.Create ("http://www.contoso.com/PostAccepter.aspx ");  
            // Set the Method property of the request to POST.  
            request.Method = "POST";  
            // Create POST data and convert it to a byte array.  
            string postData = "This is a test that posts this string to a Web server.";  
            byte[] byteArray = Encoding.UTF8.GetBytes (postData);  
            // Set the ContentType property of the WebRequest.  
            request.ContentType = "application/x-www-form-urlencoded";  
            // Set the ContentLength property of the WebRequest.  
            request.ContentLength = byteArray.Length;  
            // Get the request stream.  
            Stream dataStream = request.GetRequestStream ();  
            // Write the data to the request stream.  
            dataStream.Write (byteArray, 0, byteArray.Length);  
            // Close the Stream object.  
            dataStream.Close ();  
            // Get the response.  
            WebResponse response = request.GetResponse ();  
            // Display the status.  
            Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
            // Get the stream containing content returned by the server.  
            dataStream = response.GetResponseStream ();  
            // Open the stream using a StreamReader for easy access.  
            StreamReader reader = new StreamReader (dataStream);  
            // Read the content.  
            string responseFromServer = reader.ReadToEnd ();  
            // Display the content.  
            Console.WriteLine (responseFromServer);  
            // Clean up the streams.  
            reader.Close ();  
            dataStream.Close ();  
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
    Public Class WebRequestPostExample  
  
        Public Shared Sub Main()  
            ' Create a request using a URL that can receive a post.   
            Dim request As WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx ")  
            ' Set the Method property of the request to POST.  
            request.Method = "POST"  
            ' Create POST data and convert it to a byte array.  
            Dim postData As String = "This is a test that posts this string to a Web server."  
            Dim byteArray As Byte() = Encoding.UTF8.GetBytes(postData)  
            ' Set the ContentType property of the WebRequest.  
            request.ContentType = "application/x-www-form-urlencoded"  
            ' Set the ContentLength property of the WebRequest.  
            request.ContentLength = byteArray.Length  
            ' Get the request stream.  
            Dim dataStream As Stream = request.GetRequestStream()  
            ' Write the data to the request stream.  
            dataStream.Write(byteArray, 0, byteArray.Length)  
            ' Close the Stream object.  
            dataStream.Close()  
            ' Get the response.  
            Dim response As WebResponse = request.GetResponse()  
            ' Display the status.  
            Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
            ' Get the stream containing content returned by the server.  
            dataStream = response.GetResponseStream()  
            ' Open the stream using a StreamReader for easy access.  
            Dim reader As New StreamReader(dataStream)  
            ' Read the content.  
            Dim responseFromServer As String = reader.ReadToEnd()  
            ' Display the content.  
            Console.WriteLine(responseFromServer)  
            ' Clean up the streams.  
            reader.Close()  
            dataStream.Close()  
            response.Close()  
        End Sub  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="5eb0e-134">参照</span><span class="sxs-lookup"><span data-stu-id="5eb0e-134">See Also</span></span>  
 [<span data-ttu-id="5eb0e-135">インターネット要求の作成</span><span class="sxs-lookup"><span data-stu-id="5eb0e-135">Creating Internet Requests</span></span>](../../../docs/framework/network-programming/creating-internet-requests.md)  
 [<span data-ttu-id="5eb0e-136">ネットワーク上でストリームを使用する</span><span class="sxs-lookup"><span data-stu-id="5eb0e-136">Using Streams on the Network</span></span>](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [<span data-ttu-id="5eb0e-137">プロキシを介したインターネットへのアクセス</span><span class="sxs-lookup"><span data-stu-id="5eb0e-137">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="5eb0e-138">データの要求</span><span class="sxs-lookup"><span data-stu-id="5eb0e-138">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)  
 [<span data-ttu-id="5eb0e-139">方法: WebRequest クラスを使用してデータを要求する</span><span class="sxs-lookup"><span data-stu-id="5eb0e-139">How to: Request Data Using the WebRequest Class</span></span>](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)

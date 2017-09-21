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
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
caps.latest.revision: 12
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c840792182c012ba74b3ba3ef297748f58e4b92a
ms.contentlocale: ja-jp
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-send-data-using-the-webrequest-class"></a>方法: WebRequest クラスを使用してデータを送信する
次の手順では、サーバーにデータを送信するための手順について説明します。 この手順は、通常、Web ページへのデータをポストするときに使用されます。  
  
### <a name="to-send-data-to-a-host-server"></a>ホスト サーバーにデータを送信するには  
  
1.  たとえばスクリプトや ASP.NET ページなどの、データを受け取るリソースの URI を指定して <xref:System.Net.WebRequest.Create%2A> を呼び出すことによって <xref:System.Net.WebRequest> インスタンスを作成します。  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
    ```  
  
    > [!NOTE]
    >  .NET Framework は、"http:"、"https:'、"ftp:" および"file:" で始まる URI に対応する **WebRequest** と **WebResponse** から派生したプロトコル固有のクラスを提供します。 その他のプロトコルを使用してリソースにアクセスするには、**WebRequest** と **WebResponse** から派生したプロトコル固有のクラスを実装する必要があります。 詳細については、「[Programming Pluggable Protocols](../../../docs/framework/network-programming/programming-pluggable-protocols.md)」(プラグ可能なプロトコルのプログラミング) を参照してください。  
  
2.  **WebRequest** で必要なプロパティの値を設定します。 たとえば、認証を有効にするには、**Credentials** プロパティを <xref:System.Net.NetworkCredential> クラスのインスタンスに設定します。  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
     ほとんどの場合、データを送信するには、**WebRequest** インスタンスだけで十分です。 ただし、プロトコル固有のプロパティを設定する必要がある場合、**WebRequest** をプロトコル固有の型にキャストする必要があります。 たとえば、<xref:System.Net.HttpWebRequest> の HTTP 固有のプロパティにアクセスするには、**WebRequest** を **HttpWebRequest** 参照にキャストします。 次のコードの例は、HTTP 固有の <xref:System.Net.HttpWebRequest.UserAgent%2A> プロパティを設定する方法を示しています。  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  HTTP **POST** メソッドなど、要求と共にデータを送信することを許可するプロトコル メソッドを指定します。  
  
    ```csharp  
    request.Method = "POST";  
    ```  
  
    ```vb  
    request.Method = "POST"  
    ```  
  
4.  **ContentLength** プロパティを設定します。  
  
    ```csharp  
    request.ContentLength = byteArray.Length;  
    ```  
  
    ```vb  
    request.ContentLength = byteArray.Length  
    ```  
  
5.  **ContentType** プロパティを適切な値に設定します。  
  
    ```csharp  
    request.ContentType = "application/x-www-form-urlencoded";  
    ```  
  
    ```vb  
    request.ContentType = "application/x-www-form-urlencoded"  
    ```  
  
6.  <xref:System.Net.WebRequest.GetRequestStream%2A> メソッドを呼び出すことで、要求のデータを保持するストリームを取得します。  
  
    ```csharp  
    Stream dataStream = request.GetRequestStream ();  
    ```  
  
    ```vb  
    Stream dataStream = request.GetRequestStream ()  
    ```  
  
7.  このメソッドによって返される <xref:System.IO.Stream> オブジェクトにデータを書き込みます。  
  
    ```csharp  
    dataStream.Write (byteArray, 0, byteArray.Length);  
    ```  
  
    ```vb  
    dataStream.Write (byteArray, 0, byteArray.Length)  
    ```  
  
8.  **Stream.Close** メソッドを呼び出すことで、要求のストリームを閉じます。  
  
    ```csharp  
    dataStream.Close ();  
    ```  
  
    ```vb  
    dataStream.Close ()  
    ```  
  
9. <xref:System.Net.WebRequest.GetResponse%2A> を呼び出してサーバーに要求を送信します。 このメソッドは、サーバーの応答を格納するオブジェクトを返します。 返された <xref:System.Net.WebResponse> オブジェクトの型は、要求の URI のスキームで決定されます。  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  <xref:System.Net.WebResponse> オブジェクトの使用が完了した後、<xref:System.Net.WebResponse.Close%2A> メソッドを呼び出して閉じる必要があります。 代わりに、応答オブジェクトから応答ストリームを取得した場合、<xref:System.IO.Stream.Close%2A?displayProperty=fullName> メソッドを呼び出してストリームを閉じることができます。 応答またはストリームを閉じない場合、アプリケーションからサーバーへの接続が不足し、追加の要求を処理できなくなります。  
  
10. **WebResponse** のプロパティにアクセスするか、または **WebResponse** をプロトコル固有インスタンスにキャストして、プロトコル固有のプロパティを読み取ることができます。 たとえば、<xref:System.Net.HttpWebResponse> の HTTP 固有のプロパティにアクセスするには、**WebResponse** を **HttpWebResponse** 参照にキャストします。  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. サーバーによって送信された応答データを格納しているストリームを取得するには、**WebResponse** の <xref:System.Net.WebResponse.GetResponseStream%2A> メソッドを呼び出します。  
  
    ```csharp  
    Stream data = response.GetResponseStream;  
    ```  
  
    ```vb  
    Dim data As Stream = response.GetResponseStream  
    ```  
  
12. 応答からのデータの読み取り後、**Stream.Close** メソッドを使用して応答ストリームを閉じるか、**WebResponse.Close** メソッドを使用して応答を閉じる必要があります。 応答ストリームと **WebResponse** の両方で **Close** メソッドを呼び出す必要はありませんが、そのようにしても問題はありません。  
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a>例  
  
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
  
## <a name="see-also"></a>関連項目  
 [インターネット要求の作成](../../../docs/framework/network-programming/creating-internet-requests.md)   
 [ネットワーク上でストリームを使用する](../../../docs/framework/network-programming/using-streams-on-the-network.md)   
 [プロキシを介したインターネットへのアクセス](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)   
 [データの要求](../../../docs/framework/network-programming/requesting-data.md)   
 [方法: WebRequest クラスを使用してデータを要求する](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)


---
title: '方法: WebRequest クラスを使用してデータを要求する'
ms.date: 03/30/2017
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e02ad4772d3ba84a2735a2e146a9979862d75989
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-request-data-using-the-webrequest-class"></a>方法: WebRequest クラスを使用してデータを要求する
次の手順では、たとえば、Web ページやファイルなどのリソースをサーバーから要求するための手順について説明します。 リソースは URI で識別される必要があります。  
  
### <a name="to-request-data-from-a-host-server"></a>ホスト サーバーからデータを要求するには  
  
1.  リソースの URI を指定して <xref:System.Net.WebRequest.Create%2A> を呼び出して <xref:System.Net.WebRequest> インスタンスを作成します。  
  
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
  
     ほとんどの場合、データを受信するには、**WebRequest** クラスで十分です。 ただし、プロトコル固有のプロパティを設定する必要がある場合、**WebRequest** をプロトコル固有の型にキャストする必要があります。 たとえば、<xref:System.Net.HttpWebRequest> の HTTP 固有のプロパティにアクセスするには、**WebRequest** を **HttpWebRequest** 参照にキャストします。 次のコードの例は、HTTP 固有の <xref:System.Net.HttpWebRequest.UserAgent%2A> プロパティを設定する方法を示しています。  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  サーバーに要求を送信するには、<xref:System.Net.HttpWebRequest.GetResponse%2A> を呼び出します。 返された **WebResponse** オブジェクトの実際の型は、要求された URI のスキームで決定されます。  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  <xref:System.Net.WebResponse> オブジェクトの使用が完了した後、<xref:System.Net.WebResponse.Close%2A> メソッドを呼び出して終了する必要があります。 代わりに、応答オブジェクトから応答ストリームを取得した場合、<xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> メソッドを呼び出してストリームを閉じることができます。 応答またはストリームのいずれかを閉じない場合、アプリケーションからサーバーへの接続が不足し、追加の要求を処理できなくなります。  
  
4.  **WebResponse** のプロパティにアクセスするか、または **WebResponse** をプロトコル固有インスタンスにキャストして、プロトコル固有のプロパティを読み取ることができます。 たとえば、<xref:System.Net.HttpWebResponse> の HTTP 固有のプロパティにアクセスするには、**WebResponse** を **HttpWebResponse** 参照にキャストします。 次のコード例では、応答で送信される状態情報を表示する方法を示します。  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  サーバーによって送信された応答データを格納しているストリームを取得するには、**WebResponse** の <xref:System.Net.HttpWebResponse.GetResponseStream%2A> メソッドを使用します。  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6.  応答からのデータの読み取り後、**Stream.Close** メソッドを使用して応答ストリームを閉じるか、**WebResponse.Close** メソッドを使用して応答を閉じる必要があります。 応答ストリームと **WebResponse** の両方で **Close** メソッドを呼び出す必要はありませんが、そのようにしても問題はありません。 **WebResponse.Close** は応答を閉じるときに **Stream.Close** を呼び出します。  
  
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
    public class WebRequestGetExample  
    {  
        public static void Main()  
        {  
            // Create a request for the URL.   
            WebRequest request = WebRequest.Create(  
              "http://www.contoso.com/default.html");  
            // If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials;  
            // Get the response.  
            WebResponse response = request.GetResponse();  
            // Display the status.  
            Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
            // Get the stream containing content returned by the server.  
            Stream dataStream = response.GetResponseStream();  
            // Open the stream using a StreamReader for easy access.  
            StreamReader reader = new StreamReader(dataStream);  
            // Read the content.  
            string responseFromServer = reader.ReadToEnd();  
            // Display the content.  
            Console.WriteLine(responseFromServer);  
            // Clean up the streams and the response.  
            reader.Close();  
            response.Close();  
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
  
## <a name="see-also"></a>参照  
 [インターネット要求の作成](../../../docs/framework/network-programming/creating-internet-requests.md)  
 [ネットワーク上でストリームを使用する](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [プロキシを介したインターネットへのアクセス](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [データの要求](../../../docs/framework/network-programming/requesting-data.md)  
 [方法: WebRequest クラスを使用してデータを送信する](../../../docs/framework/network-programming/how-to-send-data-using-the-webrequest-class.md)

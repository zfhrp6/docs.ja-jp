---
title: "方法: WebRequest クラスを使用してデータを送信する | Microsoft Docs"
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
  - "WebRequest クラス、ホストにデータを送信する"
  - "ホストにデータを送信する、WebRequest クラスを使用する"
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# 方法: WebRequest クラスを使用してデータを送信する
次のプロシージャはサーバーにデータを送信するために使用するステップについて説明します。  このプロシージャは一般的 Web ページへのデータの掲示する必要があります。  
  
### データをホスト サーバーに送信します。  
  
1.  データ、たとえば、ASP.NET のスクリプトまたはページを使用するリソースの URI の <xref:System.Net.WebRequest.Create%2A> の呼び出し、<xref:System.Net.WebRequest> のインスタンスを作成します。  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
  
    ```  
  
    > [!NOTE]
    >  .NET Framework は、「http で始まる URI に **\[WebRequest\]** と **WebResponse** から派生したプロトコル対応クラスを提供します: 」、「https:'' 「ftp: 」、および「ファイル: 」  他のプロトコルを使用してリソースにアクセスするには、**\[WebRequest\]** と **WebResponse**から取得プロトコル対応クラスを行う必要があります。  詳細については、「[プラグ可能なプロトコルのプログラミング](../../../docs/framework/network-programming/programming-pluggable-protocols.md)」を参照してください。  
  
2.  、**\[WebRequest\]**で必要なプロパティ値を設定します。  たとえば、認証を有効にするには、<xref:System.Net.NetworkCredential> クラスのインスタンスに **\[資格情報\]** のプロパティを設定します。  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
  
    ```  
  
     ほとんどの場合、**\[WebRequest\]** のインスタンス自体はデータを送信十分です。  ただし、プロトコル対応するプロパティを設定する必要があるプロトコル タイプに対応 **\[WebRequest\]** をキャスト必要があります。  たとえば、<xref:System.Net.HttpWebRequest>の Http 固有のプロパティにアクセスするには、**HttpWebRequest** の参照に **\[WebRequest\]** をキャスト。  次の例は <xref:System.Net.HttpWebRequest.UserAgent%2A> コードの Http 固有のプロパティを設定する方法を示します。  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  データの要求に送信して HTTP の **\[投稿\]** する方法など、プロトコル方法を指定します。  
  
    ```csharp  
    request.Method = "POST";  
    ```  
  
    ```vb  
    request.Method = "POST"  
    ```  
  
4.  **\[ContentLength\]** のプロパティを設定します。  
  
    ```csharp  
    request.ContentLength = byteArray.Length;  
    ```  
  
    ```vb  
    request.ContentLength = byteArray.Length  
    ```  
  
5.  適切な値に **\[ContentType\]** のプロパティを設定します。  
  
    ```csharp  
    request.ContentType = "application/x-www-form-urlencoded";  
    ```  
  
    ```vb  
    request.ContentType = "application/x-www-form-urlencoded"  
    ```  
  
6.  <xref:System.Net.WebRequest.GetRequestStream%2A> メソッド呼び出し、要求データを保持するストリームを取得します。  
  
    ```csharp  
    Stream dataStream = request.GetRequestStream ();  
    ```  
  
    ```vb  
    Stream dataStream = request.GetRequestStream ()  
    ```  
  
7.  この方法により、返品 <xref:System.IO.Stream> の対象にデータを記述します。  
  
    ```csharp  
    dataStream.Write (byteArray, 0, byteArray.Length);  
    ```  
  
    ```vb  
    dataStream.Write (byteArray, 0, byteArray.Length)  
    ```  
  
8.  **\[Stream.Close\]** メソッド呼び出し、要求のベースを閉じます。  
  
    ```csharp  
    dataStream.Close ();  
    ```  
  
    ```vb  
    dataStream.Close ()  
    ```  
  
9. <xref:System.Net.WebRequest.GetResponse%2A>の呼び出し、サーバーに要求を送信します。  この方法は、サーバーの応答を含むオブジェクトを返します。  <xref:System.Net.WebResponse> の返品オブジェクト タイプが需要 URI の設定によって決まります。  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
  
    ```  
  
    > [!NOTE]
    >  <xref:System.Net.WebResponse> のオブジェクトを終了したら、<xref:System.Net.WebResponse.Close%2A> 方法の名前と閉じなければ必要があります。  または応答オブジェクトからの応答ストリームを獲得したとき、<xref:System.IO.Stream.Close%2A?displayProperty=fullName> メソッド呼び出し、ストリームを決済できます。  応答またはストリームを閉じなければ、アプリケーションは、追加情報を処理してサーバーへの接続を使い果たし、なくすることができます。  
  
10. **WebResponse** のプロパティをアクセス プロトコルまたは対応のインスタンスに対応プロトコルのプロパティを読み取る場合に **WebResponse** をキャストできます。  たとえば、<xref:System.Net.HttpWebResponse>の Http 固有のプロパティにアクセスするには、**HttpWebResponse** の参照に **WebResponse** をキャスト。  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. サーバーが送信する応答のデータを含むストリームを取得するには **WebResponse**の <xref:System.Net.WebResponse.GetResponseStream%2A> 方法を追加します。  
  
    ```csharp  
    Stream data = response.GetResponseStream;  
    ```  
  
    ```vb  
    Dim data As Stream = response.GetResponseStream  
    ```  
  
12. 応答からのデータを読んだと、**\[Stream.Close\]** 方法を使用して応答のベースを決算または **\[WebResponse.Close\]** 方法を使用して応答を閉じなければ必要があります。  両方の **\[閉じる\]** 方法を応答のベースと **WebResponse**というする必要はありませんが、編集することで、破壊試験ではありません。  
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
  
    ```  
  
## 使用例  
  
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
  
## 参照  
 [インターネット要求の作成](../../../docs/framework/network-programming/creating-internet-requests.md)   
 [ネットワーク上でストリームを使用する](../../../docs/framework/network-programming/using-streams-on-the-network.md)   
 [プロキシを介したインターネットへのアクセス](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)   
 [データの要求](../../../docs/framework/network-programming/requesting-data.md)   
 [方法: WebRequest クラスを使用してデータを要求する](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)
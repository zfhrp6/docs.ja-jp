---
title: "方法: WebRequest クラスを使用してデータを要求する | Microsoft Docs"
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
  - "ダウンロード (インターネット リソースの)、手順"
  - "要求 (インターネットからデータを)、手順"
  - "WebRequest クラス、受信 (データを)"
  - "受信 (データを)、使用 (WebRequest クラスを)"
  - "インターネット、要求 (データを)"
ms.assetid: 368b8d0f-dc5e-4469-a8b8-b2adbf5dd800
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# 方法: WebRequest クラスを使用してデータを要求する
次のサーバー プロシージャは、たとえば、Web ページまたはファイルからリソースを要求する手順について説明します。  リソースは URI によって識別する必要があります。  
  
### ホスト サーバーからのデータを要求します。  
  
1.  リソースの URI の <xref:System.Net.WebRequest.Create%2A> の呼び出し、<xref:System.Net.WebRequest> のインスタンスを作成します。  
  
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
  
     ほとんどの場合、**\[WebRequest\]** のクラスは、データを受信する十分です。  ただし、プロトコル対応するプロパティを設定する必要があるプロトコル タイプに対応 **\[WebRequest\]** をキャスト必要があります。  たとえば、<xref:System.Net.HttpWebRequest>の Http 固有のプロパティにアクセスするには、**HttpWebRequest** の参照に **\[WebRequest\]** をキャスト。  次の例は <xref:System.Net.HttpWebRequest.UserAgent%2A> コードの Http 固有のプロパティを設定する方法を示します。  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
  
    ```  
  
3.  サーバーに要求を送信するには、<xref:System.Net.HttpWebRequest.GetResponse%2A>を追加します。  **WebResponse** の返品オブジェクトの実際の型は、要求された URI の設定によって決まります。  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
  
    ```  
  
    > [!NOTE]
    >  <xref:System.Net.WebResponse> のオブジェクトを終了したら、<xref:System.Net.WebResponse.Close%2A> 方法の名前と閉じなければ必要があります。  または応答オブジェクトからの応答ストリームを獲得したとき、<xref:System.IO.Stream.Close%2A?displayProperty=fullName> メソッド呼び出し、ストリームを決済できます。  応答またはストリームを閉じなければ、アプリケーションは、追加情報を処理してサーバーへの接続を使い果たし、なくすることができます。  
  
4.  **WebResponse** のプロパティをアクセス プロトコルまたは対応のインスタンスに対応プロトコルのプロパティを読み取る場合に **WebResponse** をキャストできます。  たとえば、<xref:System.Net.HttpWebResponse>の Http 固有のプロパティにアクセスするには、**HttpWebResponse** の参照に **WebResponse** をキャスト。  次の例では、応答コードととも状態情報を表示する方法を示します。  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  サーバーが送信する応答のデータを含むストリームを取得するには **WebResponse**の <xref:System.Net.HttpWebResponse.GetResponseStream%2A> 方法を使用します。  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream ();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
  
    ```  
  
6.  応答からのデータを読んだと、**\[Stream.Close\]** 方法を使用して応答のベースを決算または **\[WebResponse.Close\]** 方法を使用して応答を閉じなければ必要があります。  両方の **\[閉じる\]** 方法を応答のベースと **WebResponse**というする必要はありませんが、編集することで、破壊試験ではありません。  応答を閉じるときに**\[WebResponse.Close\]** の通話 **\[Stream.Close\]**。  
  
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
  
## 参照  
 [インターネット要求の作成](../../../docs/framework/network-programming/creating-internet-requests.md)   
 [ネットワーク上でストリームを使用する](../../../docs/framework/network-programming/using-streams-on-the-network.md)   
 [プロキシを介したインターネットへのアクセス](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)   
 [データの要求](../../../docs/framework/network-programming/requesting-data.md)   
 [方法: WebRequest クラスを使用してデータを送信する](../../../docs/framework/network-programming/how-to-send-data-using-the-webrequest-class.md)
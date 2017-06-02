---
title: "ネットワーク上でストリームを使用する | Microsoft Docs"
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
  - "要求 (インターネットからデータを)、ストリーム"
  - "ネットワーク"
  - "インターネット要求への応答、ストリーム"
  - "ネットワーク リソース、ストリームの機能"
  - "受信 (データを)、ストリームの機能"
  - "ネットワーク リソース"
  - "送信 (データを)、ストリームの機能"
  - "ダウンロード (インターネット リソースの)、ストリーム"
  - "ストリーム、機能"
  - "インターネット、ストリーム"
  - "ストリーム"
ms.assetid: 02b05fba-7235-45ce-94e5-060436ee0875
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# ネットワーク上でストリームを使用する
ネットワーク リソース ベースとしては、.NET Framework で表されます。  ストリームを総称的に処理することによって、.NET Framework は次の機能を提供します:  
  
-   Web データを送受信する一般的な方法。  データを送受信するために、HTML — XML ファイル、または物別のタイプ—の実際の内容が、アプリケーション <xref:System.IO.Stream.Write%2A?displayProperty=fullName> と <xref:System.IO.Stream.Read%2A?displayProperty=fullName> を使用する任意。  
  
-   .NET Framework にストリームと互換性。  ストリームは、.NET Framework 使用されますが、それらを処理するための下部組織で、豊富な。  たとえば、ストリームを初期化するいくつかのコード行を変更して <xref:System.Net.Sockets.NetworkStream> のデータを代わりに読み取る場合に <xref:System.IO.FileStream> の XML データの読み取りアプリケーションを変更できます。  **\[NetworkStream\]** クラスと他のベースとの主な違いは、<xref:System.Net.Sockets.NetworkStream.CanSeek%2A> のプロパティ常に返します **false**を **\[NetworkStream\]** が seekable ではないことで、<xref:System.Net.Sockets.NetworkStream.Seek%2A> と <xref:System.Net.Sockets.NetworkStream.Position%2A> 方法は <xref:System.NotSupportedException>を投げます。  
  
-   間に合うようにデータの処理。  ストリームは提供します。ダウンロードする全体のデータ セットを待つ、アプリケーションを強制的する代わりに、ネットワークから入庫としてデータへのアクセスを。  
  
 <xref:System.Net.Sockets> の名前空間は、ネットワーク リソース用の <xref:System.IO.Stream> クラスのみを実行する **\[NetworkStream\]** クラスなどがあります。  <xref:System.Net.Sockets> の名前空間のクラスがストリームを表すために **\[NetworkStream\]** クラスを使用します。  
  
 返品ストリームを使用してネットワークにデータを送信するには、の <xref:System.Net.WebRequest>の <xref:System.Net.WebRequest.GetRequestStream%2A> を追加します。  **\[WebRequest\]** はサーバーに要求を送信;ヘッダー その後、ネットワーク リソースに戻すストリームの <xref:System.IO.Stream.BeginWrite%2A>、<xref:System.IO.Stream.EndWrite%2A>、または <xref:System.IO.Stream.Write%2A> メソッド呼び出し、データを送信できます。  あるプロトコル、HTTP などのデータを送信する前にプロトコル対応するプロパティを設定する必要があります。  次のコード例では、データを送信するための Http 固有のプロパティを設定する方法を示します。  変数 `sendData` が送信するデータを含むされている変数 `sendLength` が送信するデータのバイト数であるとします。  
  
```csharp  
HttpWebRequest request =   
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
request.Method = "POST";  
request.ContentLength = sendLength;  
try  
{  
   Stream sendStream = request.GetRequestStream();  
   sendStream.Write(sendData,0,sendLength);  
   sendStream.Close();  
}  
catch  
{  
   // Handle errors . . .  
}  
  
```  
  
```vb  
Dim request As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
request.Method = "POST"  
request.ContentLength = sendLength  
Try  
   Dim sendStream As Stream = request.GetRequestStream()  
   sendStream.Write(sendData, 0, sendLength)  
   sendStream.Close()  
Catch  
   ' Handle errors . . .  
End Try  
```  
  
 ネットワークからデータを取得するには、の <xref:System.Net.WebResponse>の <xref:System.Net.WebResponse.GetResponseStream%2A> を追加します。  <xref:System.IO.Stream.BeginRead%2A>、<xref:System.IO.Stream.EndRead%2A>、または返品ストリームで <xref:System.IO.Stream.Read%2A> の方法として、ネットワーク リソースのデータの読み取りできます。  
  
 ネットワーク リソースからストリームを使用する場合、次の点を考えに留めてしてください:  
  
-   **\[CanSeek\]** のプロパティは **\[NetworkStream\]** クラスがストリームの位置を変更できなくなります **false** を常に返します。  **\[シーク\]** と **\[位置\]** 方法は **NotSupportedException**を投げます。  
  
-   **\[WebRequest\]** と **WebResponse**を使用すると、**GetResponseStream** の呼び出し、作成されたストリームのインスタンスは読み取り専用です **GetRequestStream** の呼び出し、作成されたストリームのインスタンスは、評価減専用です。  
  
-   エンコードを容易にするために <xref:System.IO.StreamReader> クラスを使用します。  次の例は **WebResponse** コードの ASCII ストリームを読み取るエンコードされたに **StreamReader** を使用します \(例は、要求を作成することなく\) を示します。  
  
-   **GetResponse** への電話のネットワーク リソースを使用できない場合はブロックできます。  <xref:System.Net.WebRequest.BeginGetResponse%2A> と <xref:System.Net.WebRequest.EndGetResponse%2A> 方法の非同期要求を使用することを考慮する必要があります。  
  
-   **GetRequestStream** への電話のサーバーへの接続が作成され、ブロックできます。  <xref:System.Net.WebRequest.BeginGetRequestStream%2A> と <xref:System.Net.WebRequest.EndGetRequestStream%2A> 方法のベースに対して非同期要求を使用することを考慮する必要があります。  
  
```csharp  
// Create a response object.  
WebResponse response = request.GetResponse();  
// Get a readable stream from the server.  
StreamReader sr =   
   new StreamReader(response.GetResponseStream(), Encoding.ASCII);  
// Use the stream. Remember when you are through with the stream to close it.  
sr.Close();  
```  
  
```vb  
' Create a response object.  
Dim response As WebResponse = request.GetResponse()  
' Get a readable stream from the server.  
Dim sr As _   
   New StreamReader(response.GetResponseStream(), Encoding.ASCII)  
' Use the stream. Remember when you are through with the stream to close it.  
sr.Close()  
```  
  
## 参照  
 [方法: WebRequest クラスを使用してデータを要求する](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)   
 [データの要求](../../../docs/framework/network-programming/requesting-data.md)
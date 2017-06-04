---
title: "データの要求 | Microsoft Docs"
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
  - "送信 (データを)"
  - "WebRequest クラス、送受信 (データを)"
  - "要求 (インターネットからデータを)、データ要求の概要"
  - "WebClient クラス、送受信 (データを)"
  - "ネットワーク、要求 (データを)"
  - "受信 (データを)"
  - "送信 (データを)、データ送信の概要"
  - "インターネット要求への応答、インターネット要求への応答の概要"
  - "データ要求"
  - "受信 (データを)、データ受信の概要"
  - "インターネット、要求 (データを)"
ms.assetid: df6f1e1d-6f2a-45dd-8141-4a85c3dafe1d
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# データの要求
今日のインターネット配送されるオペレーティング環境で実行されるアプリケーションを作成すると、すべての型のリソースからデータを取得するには有効で、使いやすい方法が必要です。  プラグイン可能なセキュリティは複数のインターネット プロトコルからデータを取得するために一つのインターフェイスを使用するアプリケーションを開発することができます。  
  
## インターネット サーバーからのデータをアップロードおよびダウンロードします  
 単純な要求と回答のトランザクションに対して、<xref:System.Net.WebClient> のクラスは、データをアップロードまたはインターネット サーバーからのデータをダウンロードする最も簡単な方法を提供します。  **WebClient** は、し、ファイルをダウンロードし、送信、ストリームを受け取るには、データをバッファ サーバーに送信と応答を表示する方法を提供します。  **WebClient** は、インターネットのリソースに実際の接続に <xref:System.Net.WebRequest> と <xref:System.Net.WebResponse> クラスを使用します。登録されたプラグイン可能なプロトコルでも使用できます。  
  
 さらに複雑なトランザクションを行う必要があるクライアント アプリケーションは **\[WebRequest\]** クラスを使用しているサーバーと子孫のデータが必要です。  **\[WebRequest\]** はサーバーに接続し、要求を送信および応答の入荷の詳細をカプセル化。  **\[WebRequest\]** はプラグイン可能なプロトコルを使用するすべてのアプリケーションに使用可能なおよびメソッドは一連のプロパティを定義する抽象型クラスです。  **\[WebRequest\]**その子孫、<xref:System.Net.HttpWebRequest>などの基になるプロトコルと一致している方法で **\[WebRequest\]** によって定義されたプロパティ、およびメソッドを実行します。  
  
 **\[WebRequest\]** クラスは、特定の派生クラスのインスタンスを判断 <xref:System.Net.WebRequest.Create%2A> 方法に渡される URI の値を使用して作成するに **\[WebRequest\]** その子孫プロトコル対応のインスタンスを作成します。  アプリケーションは要求を処理するために **\[WebRequest\]** のどの子孫が <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=fullName> 方法またはその子孫のコンストラクターの登録に使用する方法を示します。  
  
 要求は、インターネットのリソースに **\[WebRequest\]**で <xref:System.Net.WebRequest.GetResponse%2A> 方法を呼び出しに従って行われます。  **GetResponse** 方法は **\[WebRequest\]**のプロパティからプロトコル対応する要求を組み立てましたり、サーバーへの TCP または UDP ソケットの接続を行い、要求を送信します。  HTTP **\[投稿\]** または FTP の **Put** などのサーバーにデータを要求する要求の場合、<xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=fullName> 方法は、データを送信するネットワーク ストリームを提供します。  
  
 **WebRequest.**に一致する **GetResponse** 方法はプロトコル対応する **WebResponse** を返します  
  
 **WebResponse** クラスは、プラグイン可能なプロトコルを使用するすべてのアプリケーションに使用可能なおよびメソッド プロパティを定義する抽象型クラスです。  **WebResponse** その子孫は、その基になるプロトコルのこれらのプロパティおよびメソッドを実行します。  <xref:System.Net.HttpWebResponse> クラスは、たとえば、HTTP の **WebResponse** クラスが実装されます。  
  
 サーバーが返品データは <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=fullName> 方法によって返されたベースのアプリケーションに表示されます。  次の例で示すように、他のすべての期間にストリームも、使用できます。  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## 参照  
 [.NET Framework のネットワーク プログラミング](../../../docs/framework/network-programming/index.md)   
 [方法: Web ページを要求し、ストリームとして結果を取得する](../../../docs/framework/network-programming/how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)   
 [方法: WebRequest に一致するプロトコル固有の WebResponse を取得する](../../../docs/framework/network-programming/how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
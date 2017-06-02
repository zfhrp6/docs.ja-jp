---
title: "プラグ可能なプロトコルの概要 | Microsoft Docs"
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
  - "データ要求、プラグ可能なプロトコル"
  - "WebRequest クラス、プラグ可能なプロトコル"
  - "インターネット要求への応答、プラグ可能なプロトコル"
  - "URI"
  - "Windows ソケット"
  - "要求/応答モデル"
  - "送信 (データを)、プラグ可能なプロトコル"
  - "プラグ可能なプロトコル"
  - "WebClient クラス、WebClient クラスの概要"
  - "プラグ可能なプロトコル、プラグ可能なプロトコルの概要"
  - "インターネット、プラグ可能なプロトコル"
  - "パスの識別子"
  - "Uniform Resource Identifier"
  - "アプリケーション開発 [.NET Framework]、プラグ可能なプロトコル"
  - "要求 (インターネットからデータを)、プラグ可能なプロトコル"
  - "受信 (データを)、プラグ可能なプロトコル"
  - "プロトコル、プラグ可能"
  - "サーバーの識別子"
  - "スキーマの識別子"
ms.assetid: 4b48e22d-e4e5-48f0-be80-d549bda97415
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# プラグ可能なプロトコルの概要
Microsoft .NET Framework 層に、スケーラブルを提供し、アプリケーションに迅速かつ簡単に統合できます。インターネット サービスの実装を管理します。  <xref:System.Net> インターネット アクセスのクラスおよび <xref:System.Net.Sockets> の名前空間が Web ベースおよびインターネット ベースのアプリケーションを実行することもできます。  
  
## Internet Application  
 インターネット アプリケーションは 2 種類によって分類できます: クライアントの情報の返信サーバーおよびアプリケーション情報を要求するクライアント アプリケーション。  Web サーバーで世界的に格納されているドキュメントおよびそのほかのデータにアクセスするに古典的のインターネットのクライアント サーバー アプリケーションが World Wide Web ブラウザの使用をです。  
  
 アプリケーションはこれらのロールで、1 に限られません; たとえば、よく知られた中間層のアプリケーション サーバー、クライアントからの要求を別のサーバーからのデータの要求と作成者、サーバーとクライアントの両方として機能すると、回答します。  
  
 クライアント アプリケーションは、要求されたリソースのインターネット プロトコルの ID と配送に必要と回答に使用する要求を作成します。  必要に応じて、クライアントもプロキシの場所または認証情報 \(ユーザー名、パスワード完了するために必要な追加データをなど\) などの要求を提供します。  一度要求は、要求サーバーに送信できます形作られます。  
  
## リソースの ID  
 .NET Framework は、要求されたインターネットのリソースと通信プロトコルを識別するために Uniform Resource Identifier \(URI\) を使用します。  URI 場合は、少なくとも 3 と 4 の片から構成されています: 要求と回答の通信プロトコルを識別する設定の ID \(; ドメイン ネーム システム \(DNS\) のホスト名またはインターネット サーバーを区別する TCP の住所から構成されるサーバーの ID \(; サーバーの要求された情報を探すパスの ID \(; およびクライアントからサーバーへ情報を渡すオプション クエリの文字列。  たとえば、URI 「http:\/\/www.contoso.com\/whatsnew.aspx?date\=today」\> 設定の ID のから「」http、サーバーの ID 「www.contoso.com」、および「\/whatsnew.aspx」、クエリの文字列または「構成されます。」date\=today。  
  
 サーバーが要求を受信した、応答を処理した後、クライアント アプリケーションへの応答を返します。  応答でコンテンツ タイプなどの追加の情報が含まれます \(未加工テキストまたは XML データなど\)。  
  
## .NET Framework の要求および応答  
 要求または応答のモデルをインターネットでのリソースにアクセスするために必要な 3 情報を提供する .NET Framework を使用:特定のクラス インターネットのリソースの URI を含む <xref:System.Uri> クラス、検索;します。リソースの要求を含む <xref:System.Net.WebRequest> クラス、; および受け取った応答にコンテナを提供する <xref:System.Net.WebResponse> クラス。  
  
 クライアント アプリケーションは <xref:System.Net.WebRequest.Create%2A> 方法、ネットワーク リソースの URI を渡すことによって、`WebRequest` のインスタンスを作成します。  この方法は、静的 HTTP など、特定のプロトコルの `WebRequest` を作成します。  `WebRequest` は、返品サーバーに要求と要求時に送信されるデータ ストリームへのアクセスを制御するプロパティの両方にアクセスできます。  `WebRequest` の <xref:System.Net.WebRequest.GetResponse%2A> 方法は、クライアント アプリケーションから URI で指定されているサーバーに要求を送信します。  回答の遅延可能性がある場合は、要求は **\[WebRequest\]**で <xref:System.Net.WebRequest.BeginGetResponse%2A> 方法を使用して回答は非同期的に作成 <xref:System.Net.WebRequest.EndGetResponse%2A> 方法を使用して後から戻すこともできます。  
  
 **GetResponse** と **EndGetResponse** 方法は **WebResponse** を返しますサーバーが返品データへアクセスできる。  このデータは <xref:System.Net.WebResponse.GetResponseStream%2A> 方法でストリームとして要求のアプリケーションに配送されるため、アプリケーションのデータ ストリーム常にで使用されます使用できます。  
  
 **WebResponse** の **\[WebRequest\]** およびクラスはプラグイン可能な基準プロトコル セキュリティ—特定の詳細を設定した各リソースの使用を継続するインターネットでのリソースを使用するアプリケーションを作成できるネットワーク サービスの実装です。  **\[WebRequest\]** その子孫のクラスが **\[WebRequest\]** のクラスとインターネットのリソースへの実績な接続詳細を管理する登録されます。  
  
 、例として、<xref:System.Net.HttpWebRequest> のクラスは、HTTP を使用してインターネットのリソースに接続の詳細を管理します。  **\[WebRequest.Create\]** 方法が「http で始まる URI が検出と、既定では: 」や「https: 」 \(File、および安全な HTTP のプロトコル ID\) は、**\[WebRequest\]** **HttpWebRequest** に戻るように使用するプロパティをアクセス プロトコル対応することができます、です型にはめます。  ほとんどの場合、**\[WebRequest\]** 要求はすべての必要な情報を提供します。  
  
 要求または応答のトランザクションとして表すことができる、プロトコルでも **\[WebRequest\]**で使用できます。  **\[WebRequest\]** と **WebResponse** からプロトコル対応クラスを取得し、を <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=fullName> の静的な方法のアプリケーションに使用する、品目を登録できます。  
  
 インターネット要求のクライアントの認証が必要な場合は、**\[WebRequest\]** の <xref:System.Net.WebRequest.Credentials%2A> のプロパティは、必要な資格情報が提供されます。  これらの資格情報は、NTLM または Kerberos 認証用に設定されている名前とパスワード\/ドメイン基本 HTTP の簡単な名前やパスワードの組み合わせ。また、認証を消化できます。  1 日付セットの資格情報は、[NetworkCredentials](frlrfsystemnetnetworkcredentialclasstopic) のインスタンスに保管するか、複数のセットは <xref:System.Net.CredentialCache> のインスタンス上で同時に保存できます。  **\[CredentialCache\]** は、その要求と認証スキーム URI のサーバーをサポート サーバーに送信いる資格情報を決定します。  
  
## Web クライアントの簡単な要求  
 インターネットのリソースの簡単な要求をする必要があるアプリケーションの場合は <xref:System.Net.WebClient> のクラスは、データをアップロードまたはインターネット サーバーからのデータをダウンロードするに一般的な方法を提供します。  **WebClient** は **\[WebRequest\]** クラスにインターネットのリソースへアクセスできるする際にも; したがって、**WebClient** クラスは登録済プラグイン可能なプロトコルを使用できます。  
  
 要求または応答のモデルを使用できないのアプリケーション用にまたはネットワーク上でリッスン、または要求を送信する必要があるアプリケーション **System.Net.Sockets** の名前空間が [TCPListener](frlrfsystemnetsocketstcplistenerclasstopic)と [UDPClient](frlrfsystemnetsocketsudpclientclasstopic) の [&#91;TCPClient&#93;](frlrfsystemnetsocketstcpclientclasstopic)、クラスを提供します。  これらのクラスは、さまざまなトランスポート プロトコルを使用して接続のための詳細を処理し、ネットワーク接続をストリームとしてアプリケーションに公開します。  
  
 Windows ソケットをよく知られた開発者が接続するか、**System.Net.Sockets** クラスのニーズを満たすことがレベルでソケット プログラミングに用意されているコントロールを必要とするユーザーは、判明します。  **System.Net.Sockets** のクラスが管理の **\[System.Net\]** クラス内のネイティブ コードに遷移ポイントです。  ほとんどの場合、**System.Net.Sockets** クラスは、Windows の 32 ビット物にデータをマーシャリングし、必要なセキュリティ検査を処理します。  
  
## 参照  
 [プラグ可能なプロトコルのプログラミング](../../../docs/framework/network-programming/programming-pluggable-protocols.md)   
 [.NET Framework のネットワーク プログラミング](../../../docs/framework/network-programming/index.md)   
 [ネットワーク プログラミングのサンプル](../../../docs/framework/network-programming/network-programming-samples.md)   
 [MSDN Code Gallery .NET のネットワーキングのサンプル](http://code.msdn.microsoft.com/Wiki/View.aspx?ProjectName=nclsamples)
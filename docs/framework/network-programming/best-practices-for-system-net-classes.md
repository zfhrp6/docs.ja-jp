---
title: "System.Net クラスのベスト プラクティス | Microsoft Docs"
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
  - "データ送信、ベスト プラクティス"
  - "要求 (インターネットからデータを)、ベスト プラクティス"
  - "WebRequest クラス、ベスト プラクティス"
  - "データ要求、ベスト プラクティス"
  - "WebResponse クラス、ベスト プラクティス"
  - "ベスト プラクティス、データ要求"
  - "データ受信、ベスト プラクティス"
ms.assetid: 716decc6-5952-47b7-9c5a-ba6fc5698684
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# System.Net クラスのベスト プラクティス
次の推奨で最適な利点に <xref:System.Net> に含まれているクラスを使用できます:  
  
-   子孫クラスにキャスト型の代わりに <xref:System.Net.WebRequest> 可能な場合、<xref:System.Net.WebResponse> を使用します。  **\[WebRequest\]** と **WebResponse** を使用するアプリケーションは広範なコードは必要ではありません変更、新しいインターネット プロトコルを使用できます。  
  
-   **\[System.Net\]** クラスを使用しているサーバーで実行 ASP.NET のアプリケーションを書き込む場合 <xref:System.Net.WebRequest.GetResponse%2A> と <xref:System.Net.WebResponse.GetResponseStream%2A>に対して非同期な方法を使用するには、通常、パフォーマンスの視点から、ほど。  
  
-   開くインターネットのリソースへの接続数は、ネットワーク パフォーマンス、スループットの重要な影響することができます。  **\[System.Net\]** がホストごとのアプリケーションごとの 2 種類の接続を既定で使用されます。  自分のアプリケーションの <xref:System.Net.ServicePoint> の <xref:System.Net.ServicePoint.ConnectionLimit%2A> のプロパティの設定はホストするには、この数は、増やすことができます。  <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=fullName> のプロパティを設定すると、すべてのホストするために、この既定値を高めることができます。  
  
-   <xref:System.Net.Sockets.Socket>に入力する代わりに [&#91;TCPClient&#93;](frlrfsystemnetsocketstcpclientclasstopic) または [UDPClient](frlrfsystemnetsocketsudpclientclasstopic) を直接可能であれば使用するソケット レベルのセキュリティを書き込んだ場合、送信  これら二つのクラスはクライアント接続の詳細の処理に必要とせずに TCP UDP ソケットの作成をカプセル化。  
  
-   資格情報を要求するアクセスと、サービス拠点を使用して、すべての要求を供給する代わりに、資格情報のキャッシュを作成するに <xref:System.Net.CredentialCache> をクラス。  **\[CredentialCache\]** のクラスが URL に基づいて資格情報を作成および表示職責の軽減する要求を示す適切な信任状を検索するようにキャッシュが検索されます。  
  
## 参照  
 [.NET Framework のネットワーク プログラミング](../../../docs/framework/network-programming/index.md)
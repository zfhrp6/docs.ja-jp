---
title: "ネットワーク アプリケーションのキャッシュ管理 | Microsoft Docs"
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
  - "キャッシュ [.NET Framework]、ネットワーク アプリケーション"
  - "ネットワーク リソース、キャッシュ"
  - "インターネット、キャッシュ"
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# ネットワーク アプリケーションのキャッシュ管理
このトピックでは、関連のサブトピック <xref:System.Net.WebClient>、<xref:System.Net.WebRequest>、<xref:System.Net.HttpWebRequest>と <xref:System.Net.FtpWebRequest> クラスを使用して派生リソースに対してキャッシュについて説明します。  
  
 キャッシュとは、アプリケーションによって要求されたリソースの一時的なストレージです。  アプリケーションで同じリソースを複数回必要な場合は、リソースがサーバーからの再の間接費要求を回避キャッシュから返されるできます。  キャッシュが必要な時間を小さくすると要求されたリソースを取得するためにアプリケーションのパフォーマンスが向上します。  キャッシュは、サーバーに出張の数を減らすことにより、ネットワーク トラフィックを減らすことができます。  キャッシュすることはパフォーマンスを改善するときに、アプリケーションに戻るリソースが古いキャッシュして使用中の場合と送信サーバーによってリソースに同一でないことを意味するリスクを強化します。  
  
 キャッシュは無許可のユーザーまたはプロセスが機密データの読み取りようにする場合があります。  キャッシュ Windows 認証された応答は追加の認証なしでキャッシュから取得される場合があります。  キャッシュすることが有効になっている場合、この要求のキャッシュを無効にする <xref:System.Net.Cache.RequestCacheLevel> または <xref:System.Net.Cache.RequestCacheLevel> に <xref:System.Net.WebRequest.CachePolicy%2A> の変更。  
  
 安保問題により、キャッシュすると、中間層のシナリオで推奨される **not** です。  
  
## このセクションの内容  
 [キャッシュ ポリシー](../../../docs/framework/network-programming/cache-policy.md)  
 キャッシュされたもののポリシーと 1 種類を定義する方法について説明します。  
  
 [場所ベースのキャッシュ ポリシー](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 アプリケーション転送プロトコル \(https\) http およびリソースの場所に基づくキャッシュのポリシーに使用可能な各タイプを定義します。  
  
 [時間ベースのキャッシュ ポリシー](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 時間ベースのキャッシュのポリシーをカスタマイズするために使用できる条件について説明します。  
  
 [ネットワーク アプリケーションでのキャッシュの構成](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 プログラムでは、キャッシュのポリシーを作成する方法について、キャッシュ使用する必要があります。  
  
## 関連項目  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>、<xref:System.Net.HttpWebRequest>と <xref:System.Net.FtpWebRequest> クラスを使用して派生したリソースのキャッシュのポリシーを定義するために使用された型および列挙型を定義します。
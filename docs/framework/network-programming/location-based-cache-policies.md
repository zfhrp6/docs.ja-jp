---
title: "場所ベースのキャッシュ ポリシー | Microsoft Docs"
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
  - ""利用可能ならキャッシュを使用" ポリシー"
  - "ポリシーの再読み込み"
  - "場所ベースのキャッシュ ポリシー"
  - ""キャッシュのみを使用" ポリシー"
  - "ローカル キャッシュ"
  - "中間キャッシュ"
  - ""キャッシュを使用せず格納しない" ポリシー"
  - "キャッシュ [.NET Framework]、場所ベースのポリシー"
  - "再検証ポリシー"
  - "キャッシュされたリソースの更新の確認間隔"
  - ""キャッシュまたは次のキャッシュのみを使用" ポリシー"
  - "更新ポリシー"
ms.assetid: e41d7f1a-0a6a-4dee-97d1-c6a8b6a07fc2
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# 場所ベースのキャッシュ ポリシー
場所に基づくキャッシュのポリシーに基づいて有効なキャッシュされたエントリ要求されたリソースのソースにから取得できるかの新鮮さを定義します。  キャッシュされたリソースは、を使用することに違反するサーバー指定された revalidation の要件に有効です。  場所に基づくキャッシュのポリシーは <xref:System.Net.Cache.RequestCachePolicy> または <xref:System.Net.Cache.HttpRequestCachePolicy> クラスのコンストラクターを使用して、的に作成されます。  場所ベースのポリシー タイプは <xref:System.Net.Cache.RequestCacheLevel> または <xref:System.Net.Cache.HttpRequestCacheLevel> の列挙型の値を使用するコンストラクターに渡されます。  場所に基づくキャッシュのポリシーを作成するコード例では、[方法へまたは: アプリケーションの場所に基づくキャッシュのポリシーを設定します](../../../docs/framework/network-programming/how-to-set-a-location-based-cache-policy-for-an-application.md)を参照してください。  次のセクションでは、アプリケーション転送プロトコル \(https\) http およびリソースの場所に基づくキャッシュのポリシーの各タイプについて説明します。  
  
## キャッシュの利用可能なポリシー  
 有効で要求されたリソースがローカル キャッシュの場合、キャッシュされたリソースが使用されます; それ以外の場合は、リソースのは、サーバーに送信されます。  要求されたリソースがクライアントとサーバー間のすべてのキャッシュで使用可能な場合は、要求は中間キャッシュによって請求できます。  
  
## キャッシュのポリシーのみ  
 有効で要求されたリソースがローカル キャッシュの場合、キャッシュされたリソースが使用されます。  このキャッシュのポリシー レベルが指定されている場合、<xref:System.Net.WebException> の例外が、品目がローカルにあるキャッシュ投げられます。  
  
## キャッシュが次のキャッシュのポリシーのみ  
 有効で要求されたリソースがローカル エリア ネットワークのローカル キャッシュまたは中間キャッシュの場合、キャッシュされたリソースが使用されます。  このような操作を行わない場合、<xref:System.Net.WebException> 例外がスローされます。  プロトコルをキャッシュする HTTP では、出荷がキャッシュされたキャッシュのコントロールの指令を使用して実行されます。  
  
## キャッシュ \(店舗のポリシーなし  
 要求されたリソースは、キャッシュからは使用されず、すべてのキャッシュには設定されません。  要求されたリソースがローカル キャッシュに応じて削除されます。  このポリシー レベルは、中間キャッシュによって、リソースを削除する必要があることを示します。  プロトコルをキャッシュするには、HTTP これは、店舗のキャッシュのコントロールの指令を使用して実行されます。  
  
## 最新の情報を更新のポリシー  
 要求されたリソースがサーバーから取得されるとき、またはキャッシュ以外の場合、ローカル キャッシュ使用できます。  中間キャッシュで要求に応じる前に、中間キャッシュに格納されているエントリをサーバーで再検証する必要があります。  プロトコルをキャッシュするには、HTTP これは、最大年齢を使用して \= 指導的な 0 のキャッシュのコントロールと非キャッシュのヘッダー PRAGMA 実行されます。  
  
## ポリシーの再読み込み  
 要求されたリソースがサーバーから取得する必要があります。  応答キャッシュがローカルに保存されている場合があります。  プロトコルをキャッシュするには、HTTP これは、指導的な非キャッシュのキャッシュのコントロールと非キャッシュ PRAGMA のヘッダーを使用して実行されます。  
  
## Revalidate ポリシー  
 キャッシュされたリソースのコピーをサーバー上のコピーと比較します。  サーバー上のコピーの方が新しい場合、そのコピーを使用して要求に応じ、キャッシュのコピーを置き換えます。  キャッシュのコピーがサーバー上のコピーと同じ場合は、キャッシュにされたコピーが使用されます。  HTTP キャッシュ プロトコルの場合、これは条件付き要求を使用して実現されます。  
  
## 参照  
 [ネットワーク アプリケーションのキャッシュ管理](../../../docs/framework/network-programming/cache-management-for-network-applications.md)   
 [キャッシュ ポリシー](../../../docs/framework/network-programming/cache-policy.md)   
 [時間ベースのキャッシュ ポリシー](../../../docs/framework/network-programming/time-based-cache-policies.md)   
 [ネットワーク アプリケーションでのキャッシュの構成](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)   
 [\<requestCaching\> 要素 \(ネットワーク設定\)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
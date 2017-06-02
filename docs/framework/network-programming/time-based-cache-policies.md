---
title: "時間ベースのキャッシュ ポリシー | Microsoft Docs"
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
  - "時間ベースのキャッシュ ポリシー"
  - "キャッシュの同期の日付のポリシー"
  - "キャッシュ [.NET Framework]、時間ベースのポリシー"
  - "キャッシュされたリソースの更新の確認間隔"
  - "時間、キャッシュされたリソース"
  - "最大保存期間ポリシー"
  - "同期、キャッシュ"
  - "キャッシュされたリソースの期限切れ"
  - "既定の時間ベースのキャッシュ ポリシー"
  - "最大の期限切れポリシー"
  - "コンテンツのキャッシュ ポリシー"
  - "期限切れのコンテンツ"
  - "最小の期限切れポリシー"
  - "キャッシュされたリソースの保存期間"
ms.assetid: 74f0bcaf-5c95-40c1-9967-f3bbf1d2360a
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# 時間ベースのキャッシュ ポリシー
時間ベースのキャッシュのポリシーは、リソースが取得された時間を使用してキャッシュされたエントリの新鮮さを定義し、ヘッダーは、リソースおよび現在時間と返品済です。  時間ベースのキャッシュのポリシーを設定すると、<xref:System.Net.Cache.HttpRequestCacheLevel> の時間ベースのポリシーを使用し、カスタマイズされた時間ベースのポリシーを作成できます。  既定の時間ベースのポリシーをアプリケーション \(File Transfer Protocol\) を使用してのリソースに使用するとキャッシュの正確な動作は、キャッシュされた回答に含まれるヘッダーと RFC 2616 の使用可能なセクション 13 と 14 で [http:\/\/www.ietf.org](http://www.ietf.org/)指定された動作によって決まります。  HTTP のリソースの既定の時間ベースのポリシーを設定することを示すコード例では、[方法: アプリケーションの既定の時間ベースのキャッシュのポリシーを設定します](../../../docs/framework/network-programming/how-to-set-the-default-time-based-cache-policy-for-an-application.md)を参照してください。  キャッシュのポリシーを作成し、使用方法を示すコード例では、[ネットワーク アプリケーションのキャッシュのコンフィギュレーション](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)を参照してください。  
  
## キャッシュされたエントリの新鮮さを決定する条件  
 時間ベースのキャッシュのポリシーをカスタマイズするには、キャッシュされたエントリの新鮮さを決定するには、次の基準の一つ以上を使用することを指定できます:  
  
-   最大期日が経過する  
  
-   最大 staleness  
  
-   最小新鮮さ  
  
-   キャッシュの同期の日付  
  
> [!NOTE]
>  既定の時間ベースのキャッシュのポリシーを使用して、アプリケーションの既定のキャッシュのポリシーの配置と混同しないでください。  既定の時間ベースのポリシーは、アプリケーション レベル依頼して使用できる特定のポリシーです。  自分のアプリケーションの既定のキャッシュのポリシーは、ポリシーが必須に設定されていない場合、そのポリシー \(場所ベースまたは時間ベースの\) 適用されます。  自分のアプリケーションの既定のキャッシュのポリシーの設定の詳細については、<xref:System.Net.WebRequest.DefaultCachePolicy%2A>を参照してください。  
  
### 最大の年齢  
 最大期日が経過するポリシーの基準は、リソースのキャッシュされたコピーを使用できる時間を指定します。  リソースのキャッシュされたコピーが指定された時間過ぎている場合にリソースで選択した内容に対してそのチェックすることにより revalidated 必要があります。  切れると最大期日が経過したリソースが使用されるようにする場合は、条件を遵守されません staleness の最大値が指定されていない場合、この。  
  
### 最大 Staleness  
 最大 staleness ポリシーの基準時間はを使用すると、リソースのキャッシュされたコピーができるコンテンツ指定された有効期限。  これが切れるとリソースが使用されるようにする唯一のキャッシュ ポリシーの基準です。  
  
### 最小新鮮さ  
 最小新鮮さポリシーの基準時間はを使用する前に、リソースのキャッシュされたコピーができるコンテンツ有効期限指定します。  このポリシーはキャッシュのエントリを有効期限前になるために影響を与えます; したがって、最小および最大新鮮さ staleness の設定は相互に排他的です。  
  
## キャッシュの同期の日付  
 キャッシュの同期の日付のポリシーの基準は、リソースのキャッシュされたコピーがサーバーまたはの内容に対してそのチェックに、いつ revalidated があるかが決まります。  品目は、キャッシュされてから内容を変更する場合は、サーバーから取得され、キャッシュに保管、およびアプリケーションになります。  内容を変更します、タイムスタンプが更新され、アプリケーションは、キャッシュされた内容が表示されます。  
  
 キャッシュ同期日時により、キャッシュされたコンテンツの再検証が必要となる具体的な日時を指定できます。  新しいキャッシュのエントリがキャッシュの同期の日付以前に最後に revalidated、サーバーとの revalidation も行われます。  キャッシュの同期の日付が、ここでキャッシュされたエントリを無効にする追加の新鮮さまたはサーバーの revalidation の条件ではないとキャッシュのエントリが revalidated、キャッシュのエントリが使用されます。  キャッシュ同期日時が将来の日付に設定されている場合、エントリは、キャッシュ同期日時が過ぎるまで、要求されるたびに再検証されます。  
  
 次のトピックでは、時間ベースのキャッシュのポリシーの条件を組み合わせた影響について説明します:  
  
-   [キャッシュ ポリシーの相互作用 — 最大有効期間と最大期限延長](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
-   [キャッシュ ポリシーの相互作用 — 最大有効期間と最小鮮度](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## 参照  
 [ネットワーク アプリケーションのキャッシュ管理](../../../docs/framework/network-programming/cache-management-for-network-applications.md)   
 [キャッシュ ポリシー](../../../docs/framework/network-programming/cache-policy.md)   
 [場所ベースのキャッシュ ポリシー](../../../docs/framework/network-programming/location-based-cache-policies.md)   
 [ネットワーク アプリケーションでのキャッシュの構成](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)   
 [\<requestCaching\> 要素 \(ネットワーク設定\)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
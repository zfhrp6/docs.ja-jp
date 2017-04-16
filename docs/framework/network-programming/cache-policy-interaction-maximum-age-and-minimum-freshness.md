---
title: "キャッシュ ポリシーの相互作用 — 最大有効期間と最小鮮度 | Microsoft Docs"
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
  - "再検証ポリシー"
  - "キャッシュ [.NET Framework]、時間ベースのポリシー"
  - "キャッシュされたリソースの鮮度"
  - "最大有効期間ポリシー"
  - "最小鮮度ポリシー"
  - "キャッシュされたリソースの経過期間"
ms.assetid: 6567d451-ecec-496c-95a3-a415b99ba52a
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# キャッシュ ポリシーの相互作用 — 最大有効期間と最小鮮度
最も新しいコンテンツがクライアント アプリケーションに戻ることを保証するには、のクライアントのキャッシュ ポリシーの相互作用とサーバーの revalidation の条件は、保守的なキャッシュのポリシーは常になります。  このトピックのすべての例は 1 年 1 月 1 日にキャッシュされ、1 年 4.日が切れるリソースのキャッシュのポリシーについて説明します。  
  
 次の例は、最大期日が経過する \(`maxAge`\)、最小新鮮さ \(`minFresh`\) の値の相互作用の結果キャッシュのポリシーについて説明します。  
  
-   キャッシュのポリシーが `maxAge` を \= 2 日時、`minFresh` が指定されていない場合、内容が 1 年 3 月 3 日に revalidated。.  
  
-   キャッシュ ポリシーのセットが `maxAge` \= 2 日と `minFresh` \= 1 日、`maxAge`内容に従って、1 年 12 月 3 日まで新しければ。.  `minFresh`に従って、内容が 1 年 3 月 3 日まで新しいです。.  したがって、内容は月 1 日に 3. revalidated 必要があります。  
  
-   キャッシュ ポリシーのセットが `maxAge`\= 2 日と `minFresh` \= 2 日、`maxAge`内容に従って、1 年 12 月 3 日まで新しければ。.  `minFresh` に従って内容は 1 年 12 月 2 日まで新しいです。.  したがって、内容は月 1 日に 2. revalidated 必要があります。  
  
## 参照  
 [ネットワーク アプリケーションのキャッシュ管理](../../../docs/framework/network-programming/cache-management-for-network-applications.md)   
 [キャッシュ ポリシー](../../../docs/framework/network-programming/cache-policy.md)   
 [場所ベースのキャッシュ ポリシー](../../../docs/framework/network-programming/location-based-cache-policies.md)   
 [時間ベースのキャッシュ ポリシー](../../../docs/framework/network-programming/time-based-cache-policies.md)   
 [ネットワーク アプリケーションでのキャッシュの構成](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)   
 [キャッシュ ポリシーの相互作用 — 最大有効期間と最大期限延長](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)
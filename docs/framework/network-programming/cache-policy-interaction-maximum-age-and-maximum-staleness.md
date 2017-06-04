---
title: "キャッシュ ポリシーの相互作用 — 最大有効期間と最大期限延長 | Microsoft Docs"
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
  - "最大期限延長"
  - "キャッシュされたリソースの更新の確認間隔"
  - "時間、キャッシュされたリソース"
  - "最大保存期間ポリシー"
  - "キャッシュされたリソースの期限からの経過期間"
  - "キャッシュされたリソースの経過期間"
ms.assetid: 7f775925-89a1-4956-ba90-c869c1749a94
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# キャッシュ ポリシーの相互作用 — 最大有効期間と最大期限延長
最も新しいコンテンツがクライアント アプリケーションに戻ることを保証するには、のクライアントのキャッシュ ポリシーの相互作用とサーバーの revalidation の条件は、保守的なキャッシュのポリシーは常になります。  このトピックのすべての例は 1 年 1 月 1 日にキャッシュされ、1 年 4.日が切れるリソースのキャッシュのポリシーについて説明します。  
  
 次の例では、最大 staleness の値 \(`maxStale`\) は、最大期日が経過する \(`maxAge`\) とともに使用されます:  
  
-   キャッシュのポリシーが `maxAge` \= 5 日時を指定する必要 `maxStale` の値は、`maxAge` の値に応じて、コンテンツ月 1 日まで 6.使用できます。  ただし、サーバーの revalidation 要件に基づいて、内容が 1 年 3 月 4 日に期限が切れます。.  コンテンツ有効期限は、保守的 \(すぐに\) であるため、`maxAge` ポリシーよりも優先されます。  したがって、内容は 1 年 12 月 4 日に最大期日が経過するが達成されていない場合でも、revalidated 切れ必要があります。  
  
-   キャッシュ ポリシーのセットが `maxAge` \= 5 日と `maxStale` \= 3 日、`maxAge` の値に応じて、コンテンツ月 1 日まで 6.使用可能な場合\)。  `maxStale` の値に応じて、内容が 1.月 7 日まで使用できます。  したがって、内容は月 1 日に 6. revalidated 表示されます。  
  
-   キャッシュ ポリシーのセットが `maxAge` \= 5 日と `maxStale` \= 1 日、`maxAge` の値に応じて、コンテンツ月 1 日まで 6.使用可能な場合\)。  `maxStale` の値に応じて、内容が 1.月 5 日まで使用できます。  したがって、内容は月 1 日に 5. revalidated 表示されます。  
  
 最大期日が経過したコンテンツ有効期限未満の場合より、キャッシュの保守的な動作は常にや、最大の staleness の値は無効です。  次の例では、内容が期限切れに最大期日が経過する \(`maxAge`\) に達すると、最大 staleness \(`maxStale`\) の値を設定する場合の影響を示しています:  
  
-   キャッシュのポリシーが `maxAge` を \= 1 日時、`maxStale` の値の値を指定する、内容が 1 年 3 月 2 日に期限切れになっていない準備して revalidated。  
  
-   より保守的なポリシーの設定を適用するキャッシュのポリシーの設定`maxAge` が 1 年 3 月 2 日に \= 1 日と `maxStale` \= 3 日、内容 revalidated。  
  
-   キャッシュ ポリシーのセット `maxAge` が 1 年 3 月 2 日に. \= 1 日と `maxStale` \= 1 日、内容 revalidated。  
  
## 参照  
 [ネットワーク アプリケーションのキャッシュ管理](../../../docs/framework/network-programming/cache-management-for-network-applications.md)   
 [キャッシュ ポリシー](../../../docs/framework/network-programming/cache-policy.md)   
 [場所ベースのキャッシュ ポリシー](../../../docs/framework/network-programming/location-based-cache-policies.md)   
 [時間ベースのキャッシュ ポリシー](../../../docs/framework/network-programming/time-based-cache-policies.md)   
 [ネットワーク アプリケーションでのキャッシュの構成](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)   
 [キャッシュ ポリシーの相互作用 — 最大有効期間と最小鮮度](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)
---
title: "キャッシュ ポリシー | Microsoft Docs"
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
  - "場所ベースのキャッシュ ポリシー"
  - "キャッシュ [.NET Framework]、ポリシー"
  - "要求のキャッシュ ポリシー"
  - "キャッシュされたリソースの鮮度"
  - "コンテンツのキャッシュ ポリシー"
  - "期限切れのコンテンツ"
ms.assetid: 1a7e04ec-7872-41c2-96c6-52566dcb412b
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# キャッシュ ポリシー
要求されたリソースのキャッシュ コピーで要求を満たせるかどうかの判断は、キャッシュ ポリシーによって定義した規則に基づいて行われます。  アプリケーションは新鮮さのクライアントのキャッシュ要件を指定しますが、有効なキャッシュのポリシーは、クライアントのキャッシュ要件、サーバーのコンテンツ有効期限の条件とサーバーの revalidation の条件によって決まります。  クライアントとサーバーのキャッシュのポリシー要件の相互作用が、保守的なキャッシュ ポリシーに、新しいコンテンツがクライアント アプリケーションに戻ることを保証するために、常になります。  
  
 キャッシュのポリシーは、場所ベースまたは時間ベースです。  場所に基づくキャッシュのポリシーに基づいてキャッシュされたエントリ要求されたリソースのソースにから取得できるかの新鮮さを定義します。  時間ベースのキャッシュのポリシーは、リソースが取得されたリソースで返される時間、ヘッダー、現在時間を使用してキャッシュされたエントリの新鮮さを定義します。  ほとんどのアプリケーションは RFC 2616 で指定されたキャッシュのポリシーを実装する既定の時間ベースのキャッシュのポリシー、使用可能な [http:\/\/www.ietf.org](http://www.ietf.org/)使用できます。  
  
 次の表に示すクラスがキャッシュのポリシーを指定するために使用されます。  
  
|クラス名|説明|  
|----------|--------|  
|<xref:System.Net.Cache.HttpRequestCachePolicy>|<xref:System.Net.HttpWebRequest> のオブジェクトを使用して必要なリソースの場所ベースおよび時間ベースのキャッシュのポリシーを表します。|  
|<xref:System.Net.Cache.RequestCachePolicy>|場所に基づくキャッシュのポリシーを表しますまたは <xref:System.Net.WebRequest> を使用して必要なリソースの <xref:System.Net.Cache.RequestCacheLevel> の時間ベースのキャッシュのポリシーは、counter します。|  
|<xref:System.Net.Cache.HttpCacheAgeControl>|<xref:System.Net.Cache.HttpRequestCachePolicy> の時間ベースのオブジェクトを作成するために使用する値を指定します。|  
|<xref:System.Net.Cache.HttpRequestCacheLevel>|<xref:System.Net.Cache.HttpRequestCachePolicy> の場所ベースおよび時間ベースのオブジェクトを作成するために使用する値を指定します。|  
|<xref:System.Net.Cache.RequestCacheLevel>|場所ベースの作成に使用される値または <xref:System.Net.Cache.RequestCacheLevel> 時間ベースの <xref:System.Net.Cache.RequestCachePolicy> のオブジェクトを指定します。|  
  
 自分のアプリケーションによるすべての要求または個々のキャッシュのポリシーを定義できます。  アプリケーション レベルのキャッシュのポリシーを指定し、その要求レベルがポリシーをキャッシュすると、要求レベルのポリシーが使用されます。  プログラムで、アプリケーションや機械コンフィギュレーション コンフィギュレーション ファイルを使用してアプリケーション レベルのキャッシュのポリシーを指定できます。  詳細については、「[\<requestCaching\> 要素 \(ネットワーク設定\)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)」を参照してください。  
  
 キャッシュのポリシーを作成するには、<xref:System.Net.Cache.RequestCachePolicy> または <xref:System.Net.Cache.HttpRequestCachePolicy> クラス インスタンスの作成によってポリシーのオブジェクトを作成する必要があります。  要求のポリシーを指定するには、ポリシーの対象に要求の <xref:System.Net.WebRequest.CachePolicy%2A> のプロパティを設定します。  アプリケーション レベルのポリシーをプログラムでに設定する場合は、ポリシーの対象に <xref:System.Net.HttpWebRequest.DefaultCachePolicy%2A> のプロパティを設定します。  
  
 キャッシュのポリシーを作成し、使用方法を示すコード例では、[ネットワーク アプリケーションのキャッシュのコンフィギュレーション](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)を参照してください。  
  
## 参照  
 [ネットワーク アプリケーションのキャッシュ管理](../../../docs/framework/network-programming/cache-management-for-network-applications.md)   
 [場所ベースのキャッシュ ポリシー](../../../docs/framework/network-programming/location-based-cache-policies.md)   
 [時間ベースのキャッシュ ポリシー](../../../docs/framework/network-programming/time-based-cache-policies.md)   
 [ネットワーク アプリケーションでのキャッシュの構成](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)
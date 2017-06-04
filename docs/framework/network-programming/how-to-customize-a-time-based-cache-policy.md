---
title: "方法: 時間ベースのキャッシュ ポリシーをカスタマイズする | Microsoft Docs"
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
  - "時間ベースのキャッシュ ポリシーのカスタマイズ"
  - "キャッシュ [.NET Framework]、時間ベースのポリシー"
ms.assetid: 8d84f936-2376-4356-9264-03162e0f9279
caps.latest.revision: 15
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 15
---
# 方法: 時間ベースのキャッシュ ポリシーをカスタマイズする
時間ベースのキャッシュのポリシーを作成すると、最大期日が経過する新鮮さ、最小、最大の staleness、またはキャッシュの同期の日付値を指定することによってキャッシュの動作をカスタマイズできます。  <xref:System.Net.Cache.HttpRequestCachePolicy> のオブジェクトは、これらの値の有効な組み合わせを指定できるようにする複数のコンストラクターを提供します。  
  
### キャッシュの同期の日付を使用する時間ベースのキャッシュのポリシーを作成します。  
  
-   <xref:System.Net.Cache.HttpRequestCachePolicy> のコンストラクターに <xref:System.DateTime> のオブジェクトを渡すことによって、キャッシュの同期の日付を使用する時間ベースのキャッシュのポリシーを作成します。  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateLastSyncPolicy(DateTime when)  
    {  
        HttpRequestCachePolicy policy =   
            new HttpRequestCachePolicy(when);  
        Console.WriteLine("When: {0}", when);  
        Console.WriteLine(policy.ToString());  
        return policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Function CreateLastSyncPolicy([when] As DateTime) As HttpRequestCachePolicy  
        Dim policy As New HttpRequestCachePolicy([when])  
        Console.WriteLine("When: {0}", [when])  
        Console.WriteLine(policy.ToString())  
        Return policy  
    End Function  
    ```  
  
 出荷は次に似ています:  
  
```  
When: 1/14/2004 8:07:30 AM  
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM  
```  
  
### 最小新鮮さに基づく時間ベースのキャッシュのポリシーを作成します。  
  
-   最小新鮮さに `cacheAgeControl` パラメータ値として <xref:System.Net.Cache.HttpCacheAgeControl> を指定し、<xref:System.Net.Cache.HttpRequestCachePolicy> のコンストラクターに <xref:System.TimeSpan> のオブジェクトを渡すことに基づく時間ベースのキャッシュのポリシーを作成します。  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateMinFreshPolicy(TimeSpan span)  
    {  
        HttpRequestCachePolicy policy =   
            new HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span);  
        Console.WriteLine(policy.ToString());  
        return policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Function CreateMinFreshPolicy(span As TimeSpan) As HttpRequestCachePolicy  
        Dim policy As New HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span)  
        Console.WriteLine(policy.ToString())  
        Return policy  
    End Function  
    ```  
  
 次の通話の場合:  
  
```  
CreateMinFreshPolicy(new TimeSpan(1,0,0));  
```  
  
```  
Level:Default MinFresh:3600  
  
```  
  
### 新鮮さ最小と最大期日が経過に基づく時間ベースのキャッシュのポリシーを作成します。  
  
-   最大期日が経過すると最小新鮮さに `cacheAgeControl` パラメータ値として <xref:System.Net.Cache.HttpCacheAgeControl> を指定し、<xref:System.Net.Cache.HttpRequestCachePolicy> のコンストラクターに <xref:System.TimeSpan> の 2 種類のオブジェクトを渡すことに基づく時間ベースのキャッシュのポリシーを、許可されるキャッシュから返されるオブジェクトに最小新鮮さを指定するためにリソースおよび秒\) の間の最大期日が経過するを指定する 1 件作成します。  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateFreshAndAgePolicy(TimeSpan freshMinimum, TimeSpan ageMaximum)  
    {  
        HttpRequestCachePolicy policy =   
        new HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum);  
        Console.WriteLine(policy.ToString());  
        return policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Function CreateFreshAndAgePolicy(freshMinimum As TimeSpan, ageMaximum As TimeSpan) As HttpRequestCachePolicy  
        Dim policy As New HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum)  
        Console.WriteLine(policy.ToString())  
        Return policy  
    End Function  
    ```  
  
 次の通話の場合:  
  
```  
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  
  
```  
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## 参照  
 [ネットワーク アプリケーションのキャッシュ管理](../../../docs/framework/network-programming/cache-management-for-network-applications.md)   
 [キャッシュ ポリシー](../../../docs/framework/network-programming/cache-policy.md)   
 [場所ベースのキャッシュ ポリシー](../../../docs/framework/network-programming/location-based-cache-policies.md)   
 [時間ベースのキャッシュ ポリシー](../../../docs/framework/network-programming/time-based-cache-policies.md)   
 [\<requestCaching\> 要素 \(ネットワーク設定\)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
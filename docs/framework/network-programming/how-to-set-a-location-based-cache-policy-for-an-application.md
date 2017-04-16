---
title: "方法: アプリケーションの場所ベースのキャッシュ ポリシーを設定します。 | Microsoft Docs"
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
  - "キャッシュ動作の明示的な定義"
  - "場所ベースのキャッシュ ポリシー"
  - "ローカル キャッシュ"
  - "要求のキャッシュ ポリシー"
  - "キャッシュ [.NET Framework]、場所ベースのポリシー"
ms.assetid: 683bb88e-3411-4f46-9686-3411b6ba511c
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# 方法: アプリケーションの場所ベースのキャッシュ ポリシーを設定します。
場所に基づくキャッシュのポリシーがオフに要求されたリソースの場所に基づいてキャッシュの動作を定義するアプリケーションができます。  このトピックでは、キャッシュのポリシーを割り当てる的にすることを示します。  コンフィギュレーション ファイルを使用してアプリケーションのポリシーを設定することについては、[\<requestCaching\> 要素 \(ネットワーク設定\)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)を参照してください。  
  
### アプリケーションの場所に基づくキャッシュのポリシーを設定する  
  
1.  <xref:System.Net.Cache.RequestCachePolicy> または <xref:System.Net.Cache.HttpRequestCachePolicy> のオブジェクトを作成します。  
  
2.  アプリケーション ドメインの既定値としてポリシーのオブジェクトを設定します。  
  
### キャッシュから要求されたリソースのポリシーを設定する  
  
-   必要に応じてキャッシュから要求されたリソースの、別の方法で送信すると、要求の作成 <xref:System.Net.Cache.HttpRequestCacheLevel>にキャッシュのレベルに設定することにより、サーバーを、ポリシー。  要求は、キャッシュを含むクライアントとサーバー間のすべてのキャッシュによって、実行できます。  
  
    ```csharp  
    public static void UseCacheIfAvailable()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
            (HttpRequestCacheLevel.CacheIfAvailable);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
  
    ```  
  
    ```vb  
    Public Shared Sub UseCacheIfAvailable()  
        Dim policy As New HttpRequestCachePolicy _  
             (HttpRequestCacheLevel.CacheIfAvailable)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### 供給のリソースからキャッシュがポリシーを設定する  
  
-   すべてのキャッシュが <xref:System.Net.Cache.HttpRequestCacheLevel>ことをキャッシュのレベルに設定することにより、要求されたリソースを供給することを妨げるポリシーを作成します。  このポリシー レベルは、ローカル キャッシュからこれらは、リソースを削除することを存在する場合\)、削除、キャッシュにリソースを示します。  
  
    ```csharp  
    public static void DoNotUseCache()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.NoCacheNoStore);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.NoCacheNoStore)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### ローカル キャッシュ場合にのみ、要求されたリソースを返品ポリシーを設定する  
  
-   ローカル キャッシュにキャッシュの <xref:System.Net.Cache.HttpRequestCacheLevel>にレベルに設定してある場合にのみ、要求されたリソースを返品ポリシーを作成します。  要求されたリソースがキャッシュにある場合は、<xref:System.Net.WebException> の例外は投げられます。  
  
    ```csharp  
    public static void OnlyUseCache()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.CacheOnly);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub OnlyUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.CacheOnly)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### 供給のリソースからキャッシュがローカル ポリシーを設定する  
  
-   ローカル キャッシュが <xref:System.Net.Cache.HttpRequestCacheLevel>ことをキャッシュのレベルに設定することにより、要求されたリソースを供給することを妨げるポリシーを作成します。  要求されたリソースが中間キャッシュに、正常に revalidated、中間キャッシュは、要求されたリソースを提供できます。  
  
    ```csharp  
    public static void DoNotUseLocalCache()  
    {  
     HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.Refresh);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseLocalCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Refresh)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### すべてのキャッシュが要求されたリソースを供給することを妨げるポリシーを設定する  
  
-   すべてのキャッシュが <xref:System.Net.Cache.HttpRequestCacheLevel>ことをキャッシュのレベルに設定することにより、要求されたリソースを供給することを妨げるポリシーを作成します。  サーバーが返品リソースは、キャッシュに保存できます。  
  
    ```csharp  
    public static void SendToServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.Reload);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub SendToServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Reload)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### サーバーのリソースがキャッシュが要求されたリソースを提供するためにするキャッシュされたコピーを新しくなければポリシーを設定する  
  
-   サーバーのリソースがキャッシュが <xref:System.Net.Cache.HttpRequestCacheLevel>にキャッシュのレベルに設定することにより、キャッシュされたコピーを新しくなかったら要求されたリソースを提供するためにするポリシーを作成します。  
  
    ```csharp  
    public static void CheckServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
             (HttpRequestCacheLevel.Revalidate);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub CheckServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Revalidate)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
## 参照  
 [ネットワーク アプリケーションのキャッシュ管理](../../../docs/framework/network-programming/cache-management-for-network-applications.md)   
 [キャッシュ ポリシー](../../../docs/framework/network-programming/cache-policy.md)   
 [場所ベースのキャッシュ ポリシー](../../../docs/framework/network-programming/location-based-cache-policies.md)   
 [時間ベースのキャッシュ ポリシー](../../../docs/framework/network-programming/time-based-cache-policies.md)   
 [\<requestCaching\> 要素 \(ネットワーク設定\)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
---
title: "方法: アプリケーションの既定の時間ベースのキャッシュ ポリシーを設定します。 | Microsoft Docs"
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
  - "キャッシュ [.NET Framework]、時間ベースのポリシー"
  - "既定の時間ベースのキャッシュ ポリシー"
ms.assetid: 6bfce066-a2e7-4add-a05e-85c12ec9f07f
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# 方法: アプリケーションの既定の時間ベースのキャッシュ ポリシーを設定します。
既定の時間ベースのキャッシュのポリシーは、アプリケーションでキャッシュされたリソースに送信されるヘッダーで定義したキャッシュの動作と RFC 2616 の使用可能なセクション 13 と 14 で [http:\/\/www.ietf.org](http://www.ietf.org/)定義されたキャッシュの動作がことができます。  これは、ほとんどのアプリケーション用に適切なキャッシュの動作です。  
  
### アプリケーションの既定の自動ポリシーを設定する  
  
1.  既定の時間ベースのポリシー オブジェクトを作成します。  
  
2.  アプリケーション ドメインの既定値としてポリシーのオブジェクトを設定します。  
  
## 使用例  
 このセクションの 2 例は同じポリシーが作成されます。  
  
 次の例では、アプリケーション ドメインの既定値として既定の時間ベースのポリシーおよびセットが作成されます。  
  
```csharp  
public static void SetDefaultTimeBasedPolicy ()  
{  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy ();  
    HttpWebRequest.DefaultCachePolicy = policy ;  
}  
```  
  
```vb  
Public Shared Sub SetDefaultTimeBasedPolicy ()  
    Dim policy = New HttpRequestCachePolicy ()  
    HttpWebRequest.DefaultCachePolicy = policy  
End Sub  
```  
  
 次の例で示すように <xref:System.Net.Cache.RequestCachePolicy> クラスを使用して既定の時間ベースのキャッシュのポリシーを作成できます:  
  
```csharp  
public static void SetDefaultTimeBasedPolicy2()  
{  
    RequestCachePolicy policy = new RequestCachePolicy ();  
    HttpWebRequest.DefaultCachePolicy = policy ;  
}  
```  
  
```vb  
Public Shared Sub SetDefaultTimeBasedPolicy2()  
    Dim policy As New RequestCachePolicy()  
    HttpWebRequest.DefaultCachePolicy = policy  
End Sub  
  
```  
  
## 参照  
 [ネットワーク アプリケーションのキャッシュ管理](../../../docs/framework/network-programming/cache-management-for-network-applications.md)   
 [キャッシュ ポリシー](../../../docs/framework/network-programming/cache-policy.md)   
 [場所ベースのキャッシュ ポリシー](../../../docs/framework/network-programming/location-based-cache-policies.md)   
 [時間ベースのキャッシュ ポリシー](../../../docs/framework/network-programming/time-based-cache-policies.md)   
 [\<requestCaching\> 要素 \(ネットワーク設定\)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
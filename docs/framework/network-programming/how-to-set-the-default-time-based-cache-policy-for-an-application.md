---
title: "方法: アプリケーションの既定の時間ベースのキャッシュ ポリシーを設定します。"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- cache [.NET Framework], time-based policies
- default time-based cache policy
ms.assetid: 6bfce066-a2e7-4add-a05e-85c12ec9f07f
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 1d5166090a0682b71f74565e666c96ddadb7c6c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a><span data-ttu-id="db480-102">方法: アプリケーションの既定の時間ベースのキャッシュ ポリシーを設定します。</span><span class="sxs-lookup"><span data-stu-id="db480-102">How to: Set the Default Time-Based Cache Policy for an Application</span></span>
<span data-ttu-id="db480-103">既定の時間ベースのキャッシュ ポリシーにより、キャッシュされたリソースと共に送信されるヘッダーによってアプリケーションでキャッシュの動作を定義することができます。RFC 2616 のセクション 13 と 14 で定義されているキャッシュの動作については、[http://www.ietf.org](http://www.ietf.org/) を参照してください。これは、ほとんどのアプリケーションの適切なキャッシュの動作です。</span><span class="sxs-lookup"><span data-stu-id="db480-103">The default time-based cache policy allows an application to have its cache behavior defined by the headers sent with the cached resource and the cache behavior defined in sections 13 and 14 of RFC 2616, available at [http://www.ietf.org](http://www.ietf.org/). This is the appropriate cache behavior for most applications.</span></span>  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a><span data-ttu-id="db480-104">アプリケーションの既定の自動ポリシーを設定するには</span><span class="sxs-lookup"><span data-stu-id="db480-104">To set the default automatic policy for an application</span></span>  
  
1.  <span data-ttu-id="db480-105">既定の時間ベースのポリシー オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="db480-105">Create a default time-based policy object.</span></span>  
  
2.  <span data-ttu-id="db480-106">アプリケーション ドメインの既定値として、ポリシー オブジェクトを設定します。</span><span class="sxs-lookup"><span data-stu-id="db480-106">Set the policy object as the default for the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db480-107">例</span><span class="sxs-lookup"><span data-stu-id="db480-107">Example</span></span>  
 <span data-ttu-id="db480-108">このセクションの 2 つの例では、同一のポリシーを生成します。</span><span class="sxs-lookup"><span data-stu-id="db480-108">The two examples in this section produce identical policies.</span></span>  
  
 <span data-ttu-id="db480-109">次の例では、既定の時間ベースのポリシーを作成し、アプリケーション ドメインの既定値として設定します。</span><span class="sxs-lookup"><span data-stu-id="db480-109">The following example creates a default time-based policy and sets it as the default for the application domain.</span></span>  
  
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
  
 <span data-ttu-id="db480-110">次の例に示すように、<xref:System.Net.Cache.RequestCachePolicy> クラスを使用して既定の時間ベースのキャッシュ ポリシーを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="db480-110">You can also create the default time-based cache policy using the <xref:System.Net.Cache.RequestCachePolicy> class as shown in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="db480-111">参照</span><span class="sxs-lookup"><span data-stu-id="db480-111">See Also</span></span>  
 [<span data-ttu-id="db480-112">ネットワーク アプリケーションのキャッシュ管理</span><span class="sxs-lookup"><span data-stu-id="db480-112">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="db480-113">キャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="db480-113">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="db480-114">場所ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="db480-114">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="db480-115">時間ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="db480-115">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="db480-116">\<requestCaching> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="db480-116">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)

---
title: "ネットワーク アプリケーションでのキャッシュの構成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cache [.NET Framework], configuring
ms.assetid: 3f694a1c-de5d-47cf-a6eb-cfc369fb8a9f
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: fe70c8952451f5af8ac46549919ca164816819e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-caching-in-network-applications"></a><span data-ttu-id="52959-102">ネットワーク アプリケーションでのキャッシュの構成</span><span class="sxs-lookup"><span data-stu-id="52959-102">Configuring Caching in Network Applications</span></span>
<span data-ttu-id="52959-103">キャッシュを構成するには、アプリケーションまたは <xref:System.Net.WebRequest> レベルでキャッシュ ポリシーを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52959-103">To configure caching, you must specify a cache policy at the application or <xref:System.Net.WebRequest> level.</span></span> <span data-ttu-id="52959-104">以下のトピックでは、キャッシュを使用するようにアプリケーションと要求を構成するコード例が提供されています。</span><span class="sxs-lookup"><span data-stu-id="52959-104">The following topics provide code examples that demonstrate configuring applications and requests to use caching.</span></span>  
  
-   [<span data-ttu-id="52959-105">方法: アプリケーションの場所ベースのキャッシュ ポリシーを設定する</span><span class="sxs-lookup"><span data-stu-id="52959-105">How to: Set a Location-Based Cache Policy for an Application</span></span>](../../../docs/framework/network-programming/how-to-set-a-location-based-cache-policy-for-an-application.md)  
  
-   [<span data-ttu-id="52959-106">方法: アプリケーションの既定の時間ベースのキャッシュ ポリシーを設定する</span><span class="sxs-lookup"><span data-stu-id="52959-106">How to: Set the Default Time-Based Cache Policy for an Application</span></span>](../../../docs/framework/network-programming/how-to-set-the-default-time-based-cache-policy-for-an-application.md)  
  
-   [<span data-ttu-id="52959-107">方法: 時間ベースのキャッシュ ポリシーをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="52959-107">How to: Customize a Time-Based Cache Policy</span></span>](../../../docs/framework/network-programming/how-to-customize-a-time-based-cache-policy.md)  
  
-   [<span data-ttu-id="52959-108">方法: 要求のキャッシュ ポリシーを設定する</span><span class="sxs-lookup"><span data-stu-id="52959-108">How to: Set Cache Policy for a Request</span></span>](../../../docs/framework/network-programming/how-to-set-cache-policy-for-a-request.md)  
  
 <span data-ttu-id="52959-109">アプリケーションまたはマシン構成ファイルを使用して、キャッシュ ポリシーを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="52959-109">You can also configure cache policy using application or machine configuration files.</span></span> <span data-ttu-id="52959-110">詳細については、「[\<requestCaching> 要素 (ネットワーク設定)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52959-110">For more information, see &#124; [\<requestCaching> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52959-111">参照</span><span class="sxs-lookup"><span data-stu-id="52959-111">See Also</span></span>  
 [<span data-ttu-id="52959-112">ネットワーク アプリケーションのキャッシュ管理</span><span class="sxs-lookup"><span data-stu-id="52959-112">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="52959-113">キャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="52959-113">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="52959-114">場所ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="52959-114">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="52959-115">時間ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="52959-115">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)

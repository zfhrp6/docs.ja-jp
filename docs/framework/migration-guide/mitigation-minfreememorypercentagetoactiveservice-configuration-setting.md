---
title: "軽減策: minFreeMemoryPercentageToActiveService 構成の設定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7875f26-0da8-4afe-9846-7a21778f757b
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f7f228890476d45517a21bc09806538139c5e389
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-minfreememorypercentagetoactiveservice-configuration-setting"></a><span data-ttu-id="9d1ed-102">軽減策: minFreeMemoryPercentageToActiveService 構成の設定</span><span class="sxs-lookup"><span data-stu-id="9d1ed-102">Mitigation: minFreeMemoryPercentageToActiveService Configuration Setting</span></span>
<span data-ttu-id="9d1ed-103">[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] では、Web サーバーの使用可能なメモリが [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) 構成設定で指定されたパーセンテージより小さい場合に例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="9d1ed-103">In the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], an exception is thrown if the available memory on the web server is less than the percentage specified by the [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) configuration setting.</span></span> <span data-ttu-id="9d1ed-104">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、この設定は無視されます。</span><span class="sxs-lookup"><span data-stu-id="9d1ed-104">In the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], this setting was ignored.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="9d1ed-105">影響</span><span class="sxs-lookup"><span data-stu-id="9d1ed-105">Impact</span></span>  
 <span data-ttu-id="9d1ed-106">ほとんどの場合、[minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) 設定に従うことによる影響は望ましいものです。制約されたメモリを持つシステムで Windows Communication Foundation (WCF) サービスが開始されるときに発生する可能性のある <xref:System.OutOfMemoryException> 例外を防ぐことによってシステムの安定性が向上します。</span><span class="sxs-lookup"><span data-stu-id="9d1ed-106">In most cases, the impact of observing the [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) setting is desirable: It improves system stability by preventing the <xref:System.OutOfMemoryException> exceptions that can occur when a Windows Communication Foundation (WCF) service is started on a system that has constrained memory.</span></span>  
  
 <span data-ttu-id="9d1ed-107">ただし、以前は正常に開始されたサービスが起動できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="9d1ed-107">However, in some cases, a service that previously started successfully may be unable to start.</span></span> <span data-ttu-id="9d1ed-108">その場合、詳細なエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9d1ed-108">In that case, a detailed error message appears:</span></span>  
  
```console
Memory gates checking failed because the free memory (nnnn bytes) is less than nn% of total memory. As a result, the service will not be available for incoming requests. To resolve this, either reduce the load on the machine or adjust the value of minFreeMemoryPercentageToActivateService on the serviceHostingEnvironment config element.
```
  
## <a name="mitigation"></a><span data-ttu-id="9d1ed-109">軽減策</span><span class="sxs-lookup"><span data-stu-id="9d1ed-109">Mitigation</span></span>  
 <span data-ttu-id="9d1ed-110">[minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) 設定が無視された、前の動作に戻すには、次に示すように web.config ファイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="9d1ed-110">To revert to the previous behavior where the [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) setting was ignored, modify the web.config file as follows:</span></span>  
  
```xml
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"   
                           minFreeMemoryPercentageToActivateService="0">  
   <serviceActivations>  
   ...  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9d1ed-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d1ed-111">See Also</span></span>  
 [<span data-ttu-id="9d1ed-112">ランタイムの変更点</span><span class="sxs-lookup"><span data-stu-id="9d1ed-112">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)


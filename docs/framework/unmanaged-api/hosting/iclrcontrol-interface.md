---
title: "ICLRControl インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl
helpviewer_keywords:
- ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b93d87107e1a69b0a047dbf156124fe49cd95d16
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="6e377-102">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6e377-102">ICLRControl Interface</span></span>
<span data-ttu-id="6e377-103">ホストへの参照を取得できるように、共通言語ランタイム (CLR) の要素を構成するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="6e377-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6e377-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="6e377-104">Methods</span></span>  
  
|<span data-ttu-id="6e377-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="6e377-105">Method</span></span>|<span data-ttu-id="6e377-106">説明</span><span class="sxs-lookup"><span data-stu-id="6e377-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6e377-107">GetCLRManager メソッド</span><span class="sxs-lookup"><span data-stu-id="6e377-107">GetCLRManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="6e377-108">ホストが CLR を構成に使用できる、マネージャーの種類のいずれかのインスタンスへのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="6e377-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="6e377-109">SetAppDomainManagerType メソッド</span><span class="sxs-lookup"><span data-stu-id="6e377-109">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="6e377-110">派生した型を設定<xref:System.AppDomainManager>アプリケーション ドメイン マネージャーの種類として。</span><span class="sxs-lookup"><span data-stu-id="6e377-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6e377-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="6e377-111">Requirements</span></span>  
 <span data-ttu-id="6e377-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6e377-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e377-113">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6e377-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6e377-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="6e377-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e377-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e377-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e377-116">参照</span><span class="sxs-lookup"><span data-stu-id="6e377-116">See Also</span></span>  
 [<span data-ttu-id="6e377-117">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6e377-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="6e377-118">ICLRDebugManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6e377-118">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="6e377-119">ICLRGCManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6e377-119">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 [<span data-ttu-id="6e377-120">ICLRHostBindingPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6e377-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 [<span data-ttu-id="6e377-121">ICLRHostProtectionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6e377-121">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [<span data-ttu-id="6e377-122">ICLROnEventManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6e377-122">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [<span data-ttu-id="6e377-123">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6e377-123">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="6e377-124">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6e377-124">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="6e377-125">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6e377-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

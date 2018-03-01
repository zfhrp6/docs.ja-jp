---
title: "IHostControl インターフェイス"
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
- IHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl
helpviewer_keywords:
- IHostControl interface [.NET Framework hosting]
ms.assetid: a4ae0d1f-ade9-4b0a-a122-93ed11a5e6b3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d0eaecef4cc34549c7d37953a5c8144bdd983692
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="de548-102">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="de548-102">IHostControl Interface</span></span>
<span data-ttu-id="de548-103">アセンブリの読み込みを設定して、ホストがサポートするホスト インターフェイスを決定するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="de548-103">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="de548-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="de548-104">Methods</span></span>  
  
|<span data-ttu-id="de548-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="de548-105">Method</span></span>|<span data-ttu-id="de548-106">説明</span><span class="sxs-lookup"><span data-stu-id="de548-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="de548-107">GetHostManager メソッド</span><span class="sxs-lookup"><span data-stu-id="de548-107">GetHostManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="de548-108">指定したホストのインターフェイスの実装へのインターフェイス ポインターを取得`IID`です。</span><span class="sxs-lookup"><span data-stu-id="de548-108">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="de548-109">SetAppDomainManager メソッド</span><span class="sxs-lookup"><span data-stu-id="de548-109">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="de548-110">アプリケーション ドメインが作成されているホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="de548-110">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="de548-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="de548-111">Requirements</span></span>  
 <span data-ttu-id="de548-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="de548-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de548-113">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="de548-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="de548-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="de548-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="de548-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de548-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de548-116">参照</span><span class="sxs-lookup"><span data-stu-id="de548-116">See Also</span></span>  
 <xref:System.AppDomainManager>  
 [<span data-ttu-id="de548-117">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="de548-117">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [<span data-ttu-id="de548-118">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="de548-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="de548-119">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="de548-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

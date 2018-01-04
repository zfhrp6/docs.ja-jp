---
title: "ICorConfiguration::SetGCHostControl メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorConfiguration.SetGCHostControl
api_location: mscoree.dll
api_type: COM
f1_keywords: SetGCHostControl
helpviewer_keywords:
- ICorConfiguration::SetGCHostControl method [.NET Framework hosting]
- SetGCHostControl method [.NET Framework hosting]
ms.assetid: bca6bd79-e288-475a-aa46-6bf81541d966
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98f36fea9705d212b01a0220cca321192b8193d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="af2f3-102">ICorConfiguration::SetGCHostControl メソッド</span><span class="sxs-lookup"><span data-stu-id="af2f3-102">ICorConfiguration::SetGCHostControl Method</span></span>
<span data-ttu-id="af2f3-103">仮想メモリの制限を変更するホストに要求、ガベージ コレクターが使用するコールバック インターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="af2f3-103">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af2f3-104">構文</span><span class="sxs-lookup"><span data-stu-id="af2f3-104">Syntax</span></span>  
  
```  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="af2f3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="af2f3-105">Parameters</span></span>  
 `pGCHostControl`  
 <span data-ttu-id="af2f3-106">[in]ポインター、 [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)ガベージ コレクターは、仮想メモリの制限を変更するホストを要求できるようにするオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="af2f3-106">[in] A pointer to an [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af2f3-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="af2f3-107">Requirements</span></span>  
 <span data-ttu-id="af2f3-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="af2f3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af2f3-109">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="af2f3-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="af2f3-110">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="af2f3-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="af2f3-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af2f3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af2f3-112">参照</span><span class="sxs-lookup"><span data-stu-id="af2f3-112">See Also</span></span>  
 [<span data-ttu-id="af2f3-113">ICorConfiguration インターフェイス</span><span class="sxs-lookup"><span data-stu-id="af2f3-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)

---
title: "ICorConfiguration::SetGCThreadControl メソッド"
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
- ICorConfiguration.SetGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCThreadControl
helpviewer_keywords:
- ICorConfiguration::SetGCThreadControl method [.NET Framework hosting]
- SetGCThreadControl method [.NET Framework hosting]
ms.assetid: 72e38e61-3d56-4ae3-b8f6-0ab7922aaf11
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6b6b28b67f924df4d7f587d0364bce2a853f60b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a><span data-ttu-id="c856f-102">ICorConfiguration::SetGCThreadControl メソッド</span><span class="sxs-lookup"><span data-stu-id="c856f-102">ICorConfiguration::SetGCThreadControl Method</span></span>
<span data-ttu-id="c856f-103">それ以外の場合のみがブロックされるガベージ コレクションの非ランタイム タスクのスレッドのスケジュールのコールバック インターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="c856f-103">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c856f-104">構文</span><span class="sxs-lookup"><span data-stu-id="c856f-104">Syntax</span></span>  
  
```  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c856f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c856f-105">Parameters</span></span>  
 `pGCThreadControl`  
 <span data-ttu-id="c856f-106">[in]ポインター、 [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)非ランタイム タスクのスレッドの中断に関するホストに通知するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c856f-106">[in] A pointer to an [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) object that notifies the host about the suspension of threads for non-runtime tasks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c856f-107">コメント</span><span class="sxs-lookup"><span data-stu-id="c856f-107">Remarks</span></span>  
 <span data-ttu-id="c856f-108">内でホストを選択ことがあります、 [igcthreadcontrol::threadisblockingforsuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)コールバック スレッドのスケジュールを変更するかどうか。</span><span class="sxs-lookup"><span data-stu-id="c856f-108">The host may choose within the [IGCThreadControl::ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c856f-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="c856f-109">Requirements</span></span>  
 <span data-ttu-id="c856f-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c856f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c856f-111">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c856f-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c856f-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="c856f-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c856f-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c856f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c856f-114">参照</span><span class="sxs-lookup"><span data-stu-id="c856f-114">See Also</span></span>  
 [<span data-ttu-id="c856f-115">ICorConfiguration インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c856f-115">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)

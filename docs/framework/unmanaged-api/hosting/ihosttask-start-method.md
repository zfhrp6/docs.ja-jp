---
title: "IHostTask::Start メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.Start
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::Start
helpviewer_keywords:
- IHostTask::Start method [.NET Framework hosting]
- Start method, IHostTask interface [.NET Framework hosting]
ms.assetid: b18742b0-d8c4-401c-ae89-e6eccdaa81d0
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f1a289099245228b8806639cb98f579bc56317b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="177d5-102">IHostTask::Start メソッド</span><span class="sxs-lookup"><span data-stu-id="177d5-102">IHostTask::Start Method</span></span>
<span data-ttu-id="177d5-103">ホストが現在のタスクを移動要求[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)インスタンス、中断したからコードを実行できる状態にします。</span><span class="sxs-lookup"><span data-stu-id="177d5-103">Requests that the host move the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="177d5-104">構文</span><span class="sxs-lookup"><span data-stu-id="177d5-104">Syntax</span></span>  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="177d5-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="177d5-105">Return Value</span></span>  
  
|<span data-ttu-id="177d5-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="177d5-106">HRESULT</span></span>|<span data-ttu-id="177d5-107">説明</span><span class="sxs-lookup"><span data-stu-id="177d5-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="177d5-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="177d5-108">S_OK</span></span>|<span data-ttu-id="177d5-109">開始は正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="177d5-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="177d5-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="177d5-110">E_FAIL</span></span>|<span data-ttu-id="177d5-111">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="177d5-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="177d5-112">メソッドには、E_FAIL が返される、ときに、共通言語ランタイム (CLR) は、プロセス内で使用可能ではありません。</span><span class="sxs-lookup"><span data-stu-id="177d5-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="177d5-113">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="177d5-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="177d5-114">コメント</span><span class="sxs-lookup"><span data-stu-id="177d5-114">Remarks</span></span>  
 <span data-ttu-id="177d5-115">`Start`常にどこに致命的なエラーが発生した場合を除き、s_ok HRESULT 値を返します。</span><span class="sxs-lookup"><span data-stu-id="177d5-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="177d5-116">要件</span><span class="sxs-lookup"><span data-stu-id="177d5-116">Requirements</span></span>  
 <span data-ttu-id="177d5-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="177d5-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="177d5-118">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="177d5-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="177d5-119">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="177d5-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="177d5-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="177d5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="177d5-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="177d5-121">See Also</span></span>  
 [<span data-ttu-id="177d5-122">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="177d5-122">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="177d5-123">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="177d5-123">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="177d5-124">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="177d5-124">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="177d5-125">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="177d5-125">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)

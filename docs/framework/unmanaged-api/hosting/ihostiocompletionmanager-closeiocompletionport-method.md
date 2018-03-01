---
title: "IHostIoCompletionManager::CloseIoCompletionPort メソッド"
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
- IHostIoCompletionManager.CloseIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort method [.NET Framework hosting]
- CloseIoCompletionPort method [.NET Framework hosting]
ms.assetid: e86ad7be-3758-498a-a972-5522d69dfbb3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e74803cad610d5550ce8b52ce04295247617d907
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="bbf35-102">IHostIoCompletionManager::CloseIoCompletionPort メソッド</span><span class="sxs-lookup"><span data-stu-id="bbf35-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="bbf35-103">ホストが事前に呼び出したを通じて開かれたポートを閉じることを要求[CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="bbf35-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbf35-104">構文</span><span class="sxs-lookup"><span data-stu-id="bbf35-104">Syntax</span></span>  
  
```  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bbf35-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bbf35-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="bbf35-106">[in]ポートを閉じるのハンドル。</span><span class="sxs-lookup"><span data-stu-id="bbf35-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bbf35-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="bbf35-107">Return Value</span></span>  
  
|<span data-ttu-id="bbf35-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bbf35-108">HRESULT</span></span>|<span data-ttu-id="bbf35-109">説明</span><span class="sxs-lookup"><span data-stu-id="bbf35-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bbf35-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bbf35-110">S_OK</span></span>|<span data-ttu-id="bbf35-111">`CloseIoCompletionPort`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="bbf35-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="bbf35-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bbf35-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bbf35-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="bbf35-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bbf35-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bbf35-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bbf35-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="bbf35-115">The call timed out.</span></span>|  
|<span data-ttu-id="bbf35-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bbf35-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bbf35-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="bbf35-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bbf35-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bbf35-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bbf35-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="bbf35-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bbf35-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bbf35-120">E_FAIL</span></span>|<span data-ttu-id="bbf35-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="bbf35-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bbf35-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="bbf35-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bbf35-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="bbf35-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bbf35-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="bbf35-124">E_INVALIDARG</span></span>|<span data-ttu-id="bbf35-125">無効なポート ハンドルが渡されました。</span><span class="sxs-lookup"><span data-stu-id="bbf35-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbf35-126">コメント</span><span class="sxs-lookup"><span data-stu-id="bbf35-126">Remarks</span></span>  
 <span data-ttu-id="bbf35-127">`hPort`以前の呼び出しによって作成されたポートへのハンドルをする必要があります`CreateIoCompletionPort`です。</span><span class="sxs-lookup"><span data-stu-id="bbf35-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbf35-128">必要条件</span><span class="sxs-lookup"><span data-stu-id="bbf35-128">Requirements</span></span>  
 <span data-ttu-id="bbf35-129">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bbf35-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbf35-130">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bbf35-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bbf35-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="bbf35-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bbf35-132">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbf35-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbf35-133">参照</span><span class="sxs-lookup"><span data-stu-id="bbf35-133">See Also</span></span>  
 [<span data-ttu-id="bbf35-134">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bbf35-134">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="bbf35-135">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bbf35-135">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)

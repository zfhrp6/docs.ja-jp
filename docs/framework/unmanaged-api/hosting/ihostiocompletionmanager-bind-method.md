---
title: "IHostIoCompletionManager::Bind メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.Bind
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::Bind
helpviewer_keywords:
- IHostIoCompletionManager::Bind method [.NET Framework hosting]
- Bind method [.NET Framework hosting]
ms.assetid: acd74cb5-7e22-4a07-83c3-82288e1abd9f
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d5eba258065c5ddbbf6fad474aed700065b155a4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="dcde9-102">IHostIoCompletionManager::Bind メソッド</span><span class="sxs-lookup"><span data-stu-id="dcde9-102">IHostIoCompletionManager::Bind Method</span></span>
<span data-ttu-id="dcde9-103">以前の呼び出しによって作成されている I/O 完了ポートを指定したハンドルにバインド[CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="dcde9-103">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcde9-104">構文</span><span class="sxs-lookup"><span data-stu-id="dcde9-104">Syntax</span></span>  
  
```  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dcde9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dcde9-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="dcde9-106">[in]バインドする I/O 完了ポート`hHandle`です。</span><span class="sxs-lookup"><span data-stu-id="dcde9-106">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="dcde9-107">場合の値`hPort`が null、`hHandle`は、既定の I/O 完了ポートにバインドします。</span><span class="sxs-lookup"><span data-stu-id="dcde9-107">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="dcde9-108">[in]オペレーティング システム ハンドルにバインドする`hPort`です。</span><span class="sxs-lookup"><span data-stu-id="dcde9-108">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dcde9-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="dcde9-109">Return Value</span></span>  
  
|<span data-ttu-id="dcde9-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dcde9-110">HRESULT</span></span>|<span data-ttu-id="dcde9-111">説明</span><span class="sxs-lookup"><span data-stu-id="dcde9-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dcde9-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="dcde9-112">S_OK</span></span>|<span data-ttu-id="dcde9-113">`Bind`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="dcde9-113">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="dcde9-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dcde9-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dcde9-115">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="dcde9-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dcde9-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dcde9-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dcde9-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="dcde9-117">The call timed out.</span></span>|  
|<span data-ttu-id="dcde9-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dcde9-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dcde9-119">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="dcde9-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dcde9-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dcde9-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dcde9-121">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="dcde9-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dcde9-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dcde9-122">E_FAIL</span></span>|<span data-ttu-id="dcde9-123">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="dcde9-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dcde9-124">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="dcde9-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dcde9-125">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="dcde9-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dcde9-126">コメント</span><span class="sxs-lookup"><span data-stu-id="dcde9-126">Remarks</span></span>  
 <span data-ttu-id="dcde9-127">呼び出しを使用して、I/O 完了ポートを作成`CreateIoCompletionPort`です。</span><span class="sxs-lookup"><span data-stu-id="dcde9-127">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="dcde9-128">CLR 呼び出し`Bind`そのポートへのハンドルにバインドします。</span><span class="sxs-lookup"><span data-stu-id="dcde9-128">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dcde9-129">I/O 要求が完了すると、ホストで呼び出す必要があります、 [iclriocompletionmanager::oncomplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="dcde9-129">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcde9-130">要件</span><span class="sxs-lookup"><span data-stu-id="dcde9-130">Requirements</span></span>  
 <span data-ttu-id="dcde9-131">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dcde9-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcde9-132">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dcde9-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dcde9-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="dcde9-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dcde9-134">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcde9-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcde9-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="dcde9-135">See Also</span></span>  
 [<span data-ttu-id="dcde9-136">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dcde9-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)

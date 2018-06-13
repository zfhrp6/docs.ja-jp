---
title: ICLRIoCompletionManager::OnComplete メソッド
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager.OnComplete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager::OnComplete
helpviewer_keywords:
- OnComplete method [.NET Framework hosting]
- ICLRIoCompletionManager::OnComplete method [.NET Framework hosting]
ms.assetid: 003f6974-9727-4322-bed5-e330d1224d0b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c11fa66ed583df93accc8ff1e5e95164d4de659d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434455"
---
# <a name="iclriocompletionmanageroncomplete-method"></a><span data-ttu-id="8325b-102">ICLRIoCompletionManager::OnComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="8325b-102">ICLRIoCompletionManager::OnComplete Method</span></span>
<span data-ttu-id="8325b-103">共通言語ランタイム (CLR) にへの呼び出しを使用して行われた I/O 要求の状態の通知、 [ihostiocompletionmanager::bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="8325b-103">Notifies the common language runtime (CLR) of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8325b-104">構文</span><span class="sxs-lookup"><span data-stu-id="8325b-104">Syntax</span></span>  
  
```  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8325b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8325b-105">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="8325b-106">[in]バインド操作の状態を示す HRESULT 値。</span><span class="sxs-lookup"><span data-stu-id="8325b-106">[in] An HRESULT value that indicates the status of the bind operation.</span></span>  
  
-   <span data-ttu-id="8325b-107">S_OK では、操作が正常に完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="8325b-107">S_OK indicates that the operation completed successfully.</span></span>  
  
-   <span data-ttu-id="8325b-108">HOST_E_INTERRUPTED では、呼び出しが完了する前に終了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="8325b-108">HOST_E_INTERRUPTED indicates that the call terminated before completion.</span></span>  
  
-   <span data-ttu-id="8325b-109">E_FAIL は、未知の回復不能な致命的なエラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="8325b-109">E_FAIL indicates that an unknown, unrecoverable, catastrophic failure occurred.</span></span>  
  
 `NumberOfBytesTransferred`  
 <span data-ttu-id="8325b-110">[in]I/O 要求の処理中に転送されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="8325b-110">[in] The number of bytes transferred during the processing of the I/O request.</span></span>  
  
 `pvOverlapped`  
 <span data-ttu-id="8325b-111">[in]ポインター、`OVERLAPPED`への呼び出しに渡された構造体、`IHostIoCompletionManager::Bind`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="8325b-111">[in] A pointer to the `OVERLAPPED` structure that was passed to the call to the `IHostIoCompletionManager::Bind` method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8325b-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="8325b-112">Return Value</span></span>  
  
|<span data-ttu-id="8325b-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8325b-113">HRESULT</span></span>|<span data-ttu-id="8325b-114">説明</span><span class="sxs-lookup"><span data-stu-id="8325b-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8325b-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="8325b-115">S_OK</span></span>|<span data-ttu-id="8325b-116">`OnComplete` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="8325b-116">`OnComplete` returned successfully.</span></span>|  
|<span data-ttu-id="8325b-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8325b-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8325b-118">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="8325b-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8325b-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8325b-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8325b-120">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="8325b-120">The call timed out.</span></span>|  
|<span data-ttu-id="8325b-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8325b-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8325b-122">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="8325b-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8325b-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8325b-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8325b-124">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="8325b-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8325b-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8325b-125">E_FAIL</span></span>|<span data-ttu-id="8325b-126">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="8325b-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8325b-127">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="8325b-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8325b-128">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="8325b-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8325b-129">コメント</span><span class="sxs-lookup"><span data-stu-id="8325b-129">Remarks</span></span>  
 <span data-ttu-id="8325b-130">ホストは、I/O 完了の抽象化を実装する場合、CLR は、ホスト経由 I/O 要求のメソッドを使用によって[IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="8325b-130">If the host implements an I/O completion abstraction, the CLR makes I/O requests through the host by using methods of [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md).</span></span> <span data-ttu-id="8325b-131">ホストが呼び出したし、`OnComplete`このような要求の結果をランタイムに通知するメソッド。</span><span class="sxs-lookup"><span data-stu-id="8325b-131">The host then calls the `OnComplete` method to notify the runtime of the outcome of such requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8325b-132">要件</span><span class="sxs-lookup"><span data-stu-id="8325b-132">Requirements</span></span>  
 <span data-ttu-id="8325b-133">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8325b-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8325b-134">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8325b-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8325b-135">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="8325b-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8325b-136">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8325b-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8325b-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="8325b-137">See Also</span></span>  
 [<span data-ttu-id="8325b-138">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8325b-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="8325b-139">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8325b-139">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [<span data-ttu-id="8325b-140">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8325b-140">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)

---
title: "IHostIoCompletionManager::InitializeHostOverlapped メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.InitializeHostOverlapped
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 26e8f9d963e6924a8c6abd73c3e025543c7d5b83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="9c6d3-102">IHostIoCompletionManager::InitializeHostOverlapped メソッド</span><span class="sxs-lookup"><span data-stu-id="9c6d3-102">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>
<span data-ttu-id="9c6d3-103">ホストは、Win32 に追加するカスタム データを初期化するために営業案件`OVERLAPPED`非同期 I/O 要求に使用される構造です。</span><span class="sxs-lookup"><span data-stu-id="9c6d3-103">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c6d3-104">構文</span><span class="sxs-lookup"><span data-stu-id="9c6d3-104">Syntax</span></span>  
  
```  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c6d3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9c6d3-105">Parameters</span></span>  
 `pvOverlapped`  
 <span data-ttu-id="9c6d3-106">[in]Win32 へのポインター `OVERLAPPED` I/O 要求に含まれる構造体。</span><span class="sxs-lookup"><span data-stu-id="9c6d3-106">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c6d3-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="9c6d3-107">Return Value</span></span>  
  
|<span data-ttu-id="9c6d3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9c6d3-108">HRESULT</span></span>|<span data-ttu-id="9c6d3-109">説明</span><span class="sxs-lookup"><span data-stu-id="9c6d3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9c6d3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9c6d3-110">S_OK</span></span>|<span data-ttu-id="9c6d3-111">`InitializeHostOverlapped`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="9c6d3-111">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="9c6d3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9c6d3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9c6d3-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="9c6d3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9c6d3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9c6d3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9c6d3-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="9c6d3-115">The call timed out.</span></span>|  
|<span data-ttu-id="9c6d3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9c6d3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9c6d3-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="9c6d3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9c6d3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9c6d3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9c6d3-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="9c6d3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9c6d3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9c6d3-120">E_FAIL</span></span>|<span data-ttu-id="9c6d3-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="9c6d3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9c6d3-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="9c6d3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9c6d3-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="9c6d3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9c6d3-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="9c6d3-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="9c6d3-125">十分なメモリは、要求されたリソースを割り当てることができませんでした。</span><span class="sxs-lookup"><span data-stu-id="9c6d3-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c6d3-126">コメント</span><span class="sxs-lookup"><span data-stu-id="9c6d3-126">Remarks</span></span>  
 <span data-ttu-id="9c6d3-127">Windows プラットフォームの機能を使用して、`OVERLAPPED`非同期 I/O 要求の状態を格納する構造体。</span><span class="sxs-lookup"><span data-stu-id="9c6d3-127">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="9c6d3-128">CLR の呼び出し、`InitializeHostOverlapped`ホストのカスタム データを追加する機会を与えるためにメソッド、`OVERLAPPED`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="9c6d3-128">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9c6d3-129">得るには、カスタム データ ブロックの先頭に、ホストは、のサイズにオフセットを設定する必要があります、`OVERLAPPED`構造 (`sizeof(OVERLAPPED)`)。</span><span class="sxs-lookup"><span data-stu-id="9c6d3-129">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="9c6d3-130">E_OUTOFMEMORY の戻り値は、そのカスタム データを初期化するために、ホストが失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="9c6d3-130">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="9c6d3-131">この場合、CLR では、エラーを報告して、呼び出しが失敗します。</span><span class="sxs-lookup"><span data-stu-id="9c6d3-131">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c6d3-132">要件</span><span class="sxs-lookup"><span data-stu-id="9c6d3-132">Requirements</span></span>  
 <span data-ttu-id="9c6d3-133">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9c6d3-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c6d3-134">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9c6d3-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9c6d3-135">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="9c6d3-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9c6d3-136">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c6d3-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c6d3-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c6d3-137">See Also</span></span>  
 [<span data-ttu-id="9c6d3-138">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9c6d3-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="9c6d3-139">GetHostOverlappedSize メソッド</span><span class="sxs-lookup"><span data-stu-id="9c6d3-139">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)  
 [<span data-ttu-id="9c6d3-140">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9c6d3-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)

---
title: "IHostIoCompletionManager::InitializeHostOverlapped メソッド"
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
- IHostIoCompletionManager.InitializeHostOverlapped
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6b558d638e598ba6e3d0055e3a842976896e99d3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="28365-102">IHostIoCompletionManager::InitializeHostOverlapped メソッド</span><span class="sxs-lookup"><span data-stu-id="28365-102">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>
<span data-ttu-id="28365-103">ホストは、Win32 に追加するカスタム データを初期化するために営業案件`OVERLAPPED`非同期 I/O 要求に使用される構造です。</span><span class="sxs-lookup"><span data-stu-id="28365-103">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28365-104">構文</span><span class="sxs-lookup"><span data-stu-id="28365-104">Syntax</span></span>  
  
```  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="28365-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="28365-105">Parameters</span></span>  
 `pvOverlapped`  
 <span data-ttu-id="28365-106">[in]Win32 へのポインター `OVERLAPPED` I/O 要求に含まれる構造体。</span><span class="sxs-lookup"><span data-stu-id="28365-106">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28365-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="28365-107">Return Value</span></span>  
  
|<span data-ttu-id="28365-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="28365-108">HRESULT</span></span>|<span data-ttu-id="28365-109">説明</span><span class="sxs-lookup"><span data-stu-id="28365-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="28365-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="28365-110">S_OK</span></span>|<span data-ttu-id="28365-111">`InitializeHostOverlapped`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="28365-111">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="28365-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="28365-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="28365-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="28365-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="28365-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="28365-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="28365-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="28365-115">The call timed out.</span></span>|  
|<span data-ttu-id="28365-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="28365-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="28365-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="28365-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="28365-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="28365-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="28365-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="28365-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="28365-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="28365-120">E_FAIL</span></span>|<span data-ttu-id="28365-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="28365-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="28365-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="28365-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="28365-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="28365-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="28365-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="28365-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="28365-125">十分なメモリは、要求されたリソースを割り当てることができませんでした。</span><span class="sxs-lookup"><span data-stu-id="28365-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28365-126">コメント</span><span class="sxs-lookup"><span data-stu-id="28365-126">Remarks</span></span>  
 <span data-ttu-id="28365-127">Windows プラットフォームの機能を使用して、`OVERLAPPED`非同期 I/O 要求の状態を格納する構造体。</span><span class="sxs-lookup"><span data-stu-id="28365-127">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="28365-128">CLR の呼び出し、`InitializeHostOverlapped`ホストのカスタム データを追加する機会を与えるためにメソッド、`OVERLAPPED`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="28365-128">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="28365-129">得るには、カスタム データ ブロックの先頭に、ホストは、のサイズにオフセットを設定する必要があります、`OVERLAPPED`構造 (`sizeof(OVERLAPPED)`)。</span><span class="sxs-lookup"><span data-stu-id="28365-129">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="28365-130">E_OUTOFMEMORY の戻り値は、そのカスタム データを初期化するために、ホストが失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="28365-130">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="28365-131">この場合、CLR では、エラーを報告して、呼び出しが失敗します。</span><span class="sxs-lookup"><span data-stu-id="28365-131">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28365-132">必要条件</span><span class="sxs-lookup"><span data-stu-id="28365-132">Requirements</span></span>  
 <span data-ttu-id="28365-133">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="28365-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28365-134">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="28365-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="28365-135">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="28365-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="28365-136">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28365-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28365-137">参照</span><span class="sxs-lookup"><span data-stu-id="28365-137">See Also</span></span>  
 [<span data-ttu-id="28365-138">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="28365-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="28365-139">GetHostOverlappedSize メソッド</span><span class="sxs-lookup"><span data-stu-id="28365-139">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)  
 [<span data-ttu-id="28365-140">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="28365-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)

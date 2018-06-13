---
title: IHostIoCompletionManager::GetHostOverlappedSize メソッド
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetHostOverlappedSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize
helpviewer_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize method [.NET Framework hosting]
- GetHostOverlappedSize method [.NET Framework hosting]
ms.assetid: 2902578b-d5e2-4f8d-a103-0c7b6dceda9e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6713fdb822babf607752c1823a32dae43a7d567e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439605"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a><span data-ttu-id="6cad4-102">IHostIoCompletionManager::GetHostOverlappedSize メソッド</span><span class="sxs-lookup"><span data-stu-id="6cad4-102">IHostIoCompletionManager::GetHostOverlappedSize Method</span></span>
<span data-ttu-id="6cad4-103">ホストが、I/O 要求に追加しようとしています。 カスタム データのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="6cad4-103">Gets the size of any custom data the host intends to append to I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cad4-104">構文</span><span class="sxs-lookup"><span data-stu-id="6cad4-104">Syntax</span></span>  
  
```  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6cad4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6cad4-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="6cad4-106">[out]Win32 のサイズだけでなく、共通言語ランタイム (CLR) を割り当てる必要がありますバイト数へのポインター`OVERLAPPED`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="6cad4-106">[out] A pointer to the number of bytes that the common language runtime (CLR) should allocate in addition to the size of the Win32 `OVERLAPPED` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6cad4-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="6cad4-107">Return Value</span></span>  
  
|<span data-ttu-id="6cad4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6cad4-108">HRESULT</span></span>|<span data-ttu-id="6cad4-109">説明</span><span class="sxs-lookup"><span data-stu-id="6cad4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6cad4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6cad4-110">S_OK</span></span>|<span data-ttu-id="6cad4-111">`GetHostOverlappedSize` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="6cad4-111">`GetHostOverlappedSize` returned successfully.</span></span>|  
|<span data-ttu-id="6cad4-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6cad4-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6cad4-113">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="6cad4-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6cad4-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6cad4-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6cad4-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="6cad4-115">The call timed out.</span></span>|  
|<span data-ttu-id="6cad4-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6cad4-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6cad4-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="6cad4-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6cad4-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6cad4-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6cad4-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="6cad4-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6cad4-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6cad4-120">E_FAIL</span></span>|<span data-ttu-id="6cad4-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="6cad4-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6cad4-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="6cad4-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6cad4-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="6cad4-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cad4-124">コメント</span><span class="sxs-lookup"><span data-stu-id="6cad4-124">Remarks</span></span>  
 <span data-ttu-id="6cad4-125">Windows api のプラットフォームのすべての非同期 I/O 呼び出しかかる Win32`OVERLAPPED`ファイル ポインターの位置などの情報を提供するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="6cad4-125">All asynchronous I/O calls to Windows Platform APIs take a Win32 `OVERLAPPED` object, which provides information such as the file pointer position.</span></span> <span data-ttu-id="6cad4-126">状態を維持するためには、通常 I/O の非同期呼び出しを実行するアプリケーションは、カスタム データを構造に追加します。</span><span class="sxs-lookup"><span data-stu-id="6cad4-126">To maintain state, applications that make asynchronous I/O calls typically add custom data to the structure.</span></span> <span data-ttu-id="6cad4-127">`GetHostOverlappedSize` および[ihostiocompletionmanager::initializehostoverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)ホストをこのようなカスタム データを含む機会を提供します。</span><span class="sxs-lookup"><span data-stu-id="6cad4-127">`GetHostOverlappedSize` and [IHostIoCompletionManager::InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) provide an opportunity for the host to include such custom data.</span></span>  
  
 <span data-ttu-id="6cad4-128">CLR の呼び出し、`GetHostOverlappedSize`ホストに追加しようとしました。 カスタムのデータのサイズを決定するメソッド、`OVERLAPPED`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="6cad4-128">The CLR calls the `GetHostOverlappedSize` method to determine the size of the custom data that the host intends to append to the `OVERLAPPED` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6cad4-129">`GetHostOverlappedSize` 1 回だけ呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6cad4-129">`GetHostOverlappedSize` is called only once.</span></span> <span data-ttu-id="6cad4-130">ホストのカスタム データは、すべての I/O 要求のサイズと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="6cad4-130">The host's custom data must be the same size for every I/O request.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6cad4-131">サイズ、`OVERLAPPED`オブジェクト自体がの値に含まれていない`pcbSize`です。</span><span class="sxs-lookup"><span data-stu-id="6cad4-131">The size of the `OVERLAPPED` object itself is not included in the value of `pcbSize`.</span></span>  
  
 <span data-ttu-id="6cad4-132">詳細については、`OVERLAPPED`構造体、Windows プラットフォームのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6cad4-132">For more information about the `OVERLAPPED` structure, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cad4-133">要件</span><span class="sxs-lookup"><span data-stu-id="6cad4-133">Requirements</span></span>  
 <span data-ttu-id="6cad4-134">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6cad4-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cad4-135">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6cad4-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6cad4-136">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="6cad4-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6cad4-137">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cad4-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cad4-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="6cad4-138">See Also</span></span>  
 <xref:System.Threading.NativeOverlapped>  
 [<span data-ttu-id="6cad4-139">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6cad4-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="6cad4-140">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6cad4-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)

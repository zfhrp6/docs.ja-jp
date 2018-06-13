---
title: IHostCrst::TryEnter メソッド
ms.date: 03/30/2017
api_name:
- IHostCrst.TryEnter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::TryEnter
helpviewer_keywords:
- IHostCrst::TryEnter method [.NET Framework hosting]
- TryEnter method [.NET Framework hosting]
ms.assetid: a922fa98-beab-4f09-a342-cc94fc65687f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3773ad1c6e279d38231e778bb0a81dd765aff82a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438985"
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="bbdc3-102">IHostCrst::TryEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="bbdc3-102">IHostCrst::TryEnter Method</span></span>
<span data-ttu-id="bbdc3-103">現在によって表されるクリティカル セクションを入力しようとしています。 [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="bbdc3-103">Attempts to enter the critical section represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbdc3-104">構文</span><span class="sxs-lookup"><span data-stu-id="bbdc3-104">Syntax</span></span>  
  
```  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bbdc3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bbdc3-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="bbdc3-106">[in]1 つ、 [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)場合、ホストが実行するアクションを示す値、操作がブロックされます。</span><span class="sxs-lookup"><span data-stu-id="bbdc3-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="bbdc3-107">[out]`true`クリティカル セクションを指定できる入力した、それ以外の場合`false`です。</span><span class="sxs-lookup"><span data-stu-id="bbdc3-107">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bbdc3-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="bbdc3-108">Return Value</span></span>  
  
|<span data-ttu-id="bbdc3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bbdc3-109">HRESULT</span></span>|<span data-ttu-id="bbdc3-110">説明</span><span class="sxs-lookup"><span data-stu-id="bbdc3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bbdc3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="bbdc3-111">S_OK</span></span>|<span data-ttu-id="bbdc3-112">`TryEnter` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="bbdc3-112">`TryEnter` returned successfully.</span></span>|  
|<span data-ttu-id="bbdc3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bbdc3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bbdc3-114">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="bbdc3-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bbdc3-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bbdc3-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bbdc3-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="bbdc3-116">The call timed out.</span></span>|  
|<span data-ttu-id="bbdc3-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bbdc3-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bbdc3-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="bbdc3-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bbdc3-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bbdc3-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bbdc3-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="bbdc3-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bbdc3-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bbdc3-121">E_FAIL</span></span>|<span data-ttu-id="bbdc3-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="bbdc3-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bbdc3-123">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="bbdc3-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bbdc3-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="bbdc3-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbdc3-125">コメント</span><span class="sxs-lookup"><span data-stu-id="bbdc3-125">Remarks</span></span>  
 <span data-ttu-id="bbdc3-126">`TryEnter` すぐに返し、呼び出し元のスレッドがクリティカル セクションを入力するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="bbdc3-126">`TryEnter` returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="bbdc3-127">このメソッドは、Wind32 をミラー化`TryEnterCriticalSection`関数。</span><span class="sxs-lookup"><span data-stu-id="bbdc3-127">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbdc3-128">要件</span><span class="sxs-lookup"><span data-stu-id="bbdc3-128">Requirements</span></span>  
 <span data-ttu-id="bbdc3-129">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bbdc3-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbdc3-130">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bbdc3-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bbdc3-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="bbdc3-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bbdc3-132">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbdc3-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbdc3-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="bbdc3-133">See Also</span></span>  
 [<span data-ttu-id="bbdc3-134">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bbdc3-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="bbdc3-135">IHostCrst インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bbdc3-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="bbdc3-136">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bbdc3-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)

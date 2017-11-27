---
title: "ICLRDebugManager::IsDebuggerAttached メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager.IsDebuggerAttached
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager::IsDebuggerAttached
helpviewer_keywords:
- IsDebuggerAttached method, ICLRDebugManager interface [.NET Framework hosting]
- ICLRDebugManager::IsDebuggerAttached method [.NET Framework hosting]
ms.assetid: 2f105fe0-f52d-49c5-bda5-583fb27e3aa6
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 986c9ab7853324d1a2f0fc104399141068ae9a09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="3d5f6-102">ICLRDebugManager::IsDebuggerAttached メソッド</span><span class="sxs-lookup"><span data-stu-id="3d5f6-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>
<span data-ttu-id="3d5f6-103">デバッガーがプロセスにアタッチされているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="3d5f6-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d5f6-104">構文</span><span class="sxs-lookup"><span data-stu-id="3d5f6-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d5f6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3d5f6-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="3d5f6-106">[out]`true`デバッガーがプロセスに接続されている、それ以外の場合`false`です。</span><span class="sxs-lookup"><span data-stu-id="3d5f6-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d5f6-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="3d5f6-107">Return Value</span></span>  
  
|<span data-ttu-id="3d5f6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3d5f6-108">HRESULT</span></span>|<span data-ttu-id="3d5f6-109">説明</span><span class="sxs-lookup"><span data-stu-id="3d5f6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3d5f6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3d5f6-110">S_OK</span></span>|<span data-ttu-id="3d5f6-111">`IsDebuggerAttached`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="3d5f6-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="3d5f6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3d5f6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3d5f6-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="3d5f6-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3d5f6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3d5f6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3d5f6-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="3d5f6-115">The call timed out.</span></span>|  
|<span data-ttu-id="3d5f6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3d5f6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3d5f6-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="3d5f6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3d5f6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3d5f6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3d5f6-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="3d5f6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3d5f6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3d5f6-120">E_FAIL</span></span>|<span data-ttu-id="3d5f6-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="3d5f6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3d5f6-122">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="3d5f6-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3d5f6-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="3d5f6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d5f6-124">コメント</span><span class="sxs-lookup"><span data-stu-id="3d5f6-124">Remarks</span></span>  
 <span data-ttu-id="3d5f6-125">`IsDebuggerAttached`クエリをデバッガーがプロセスにアタッチされているかどうかを決定する CLR をホストできるようにします。</span><span class="sxs-lookup"><span data-stu-id="3d5f6-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d5f6-126">要件</span><span class="sxs-lookup"><span data-stu-id="3d5f6-126">Requirements</span></span>  
 <span data-ttu-id="3d5f6-127">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3d5f6-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d5f6-128">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3d5f6-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3d5f6-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="3d5f6-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3d5f6-130">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d5f6-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d5f6-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d5f6-131">See Also</span></span>  
 [<span data-ttu-id="3d5f6-132">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3d5f6-132">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="3d5f6-133">ICLRDebugManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3d5f6-133">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="3d5f6-134">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3d5f6-134">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)

---
title: "ICLRGCManager::GetStats メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager.GetStats
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager::GetStats
helpviewer_keywords:
- GetStats method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::GetStats method [.NET Framework hosting]
ms.assetid: ce259d1d-cd81-4490-a7a1-0d0ea0804872
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 06d52bd0348e4667f1e3ec43a371021922f12ded
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="deb15-102">ICLRGCManager::GetStats メソッド</span><span class="sxs-lookup"><span data-stu-id="deb15-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="deb15-103">共通言語ランタイムのガベージ コレクション システムに関する現在の統計情報のセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="deb15-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="deb15-104">構文</span><span class="sxs-lookup"><span data-stu-id="deb15-104">Syntax</span></span>  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="deb15-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="deb15-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="deb15-106">[入力、出力].A [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)要求の統計情報を含むインスタンス。</span><span class="sxs-lookup"><span data-stu-id="deb15-106">[in, out] A [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="deb15-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="deb15-107">Return Value</span></span>  
  
|<span data-ttu-id="deb15-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="deb15-108">HRESULT</span></span>|<span data-ttu-id="deb15-109">説明</span><span class="sxs-lookup"><span data-stu-id="deb15-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="deb15-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="deb15-110">S_OK</span></span>|<span data-ttu-id="deb15-111">`GetStats`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="deb15-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="deb15-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="deb15-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="deb15-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="deb15-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="deb15-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="deb15-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="deb15-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="deb15-115">The call timed out.</span></span>|  
|<span data-ttu-id="deb15-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="deb15-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="deb15-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="deb15-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="deb15-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="deb15-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="deb15-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="deb15-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="deb15-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="deb15-120">E_FAIL</span></span>|<span data-ttu-id="deb15-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="deb15-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="deb15-122">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="deb15-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="deb15-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="deb15-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="deb15-124">コメント</span><span class="sxs-lookup"><span data-stu-id="deb15-124">Remarks</span></span>  
 <span data-ttu-id="deb15-125">CLR を計算しで指定されている統計情報のみを返す、`Flags`フィールド`pStats`です。</span><span class="sxs-lookup"><span data-stu-id="deb15-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="deb15-126">設定、`Flags`フィールドの 1 つ以上の値を[COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)で統計情報を指定する列挙体、 [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)構造は設定します。</span><span class="sxs-lookup"><span data-stu-id="deb15-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="deb15-127">使用状況の例は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="deb15-127">An example of the usage is as follows:</span></span>  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="deb15-128">要件</span><span class="sxs-lookup"><span data-stu-id="deb15-128">Requirements</span></span>  
 <span data-ttu-id="deb15-129">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="deb15-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="deb15-130">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="deb15-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="deb15-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="deb15-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="deb15-132">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="deb15-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deb15-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="deb15-133">See Also</span></span>  
 [<span data-ttu-id="deb15-134">自動メモリ管理</span><span class="sxs-lookup"><span data-stu-id="deb15-134">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="deb15-135">COR_GC_STATS 構造体</span><span class="sxs-lookup"><span data-stu-id="deb15-135">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="deb15-136">COR_GC_STAT_TYPES 列挙型</span><span class="sxs-lookup"><span data-stu-id="deb15-136">COR_GC_STAT_TYPES Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)  
 [<span data-ttu-id="deb15-137">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="deb15-137">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)  
 [<span data-ttu-id="deb15-138">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="deb15-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="deb15-139">ICLRGCManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="deb15-139">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 [<span data-ttu-id="deb15-140">CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="deb15-140">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="deb15-141">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="deb15-141">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="deb15-142">ホスティング</span><span class="sxs-lookup"><span data-stu-id="deb15-142">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)

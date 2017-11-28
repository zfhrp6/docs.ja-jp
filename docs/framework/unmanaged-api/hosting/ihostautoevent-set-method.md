---
title: "IHostAutoEvent::Set メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAutoEvent.Set
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAutoEvent::Set
helpviewer_keywords:
- Set method, IHostAutoEvent interface [.NET Framework hosting]
- IHostAutoEvent::Set method [.NET Framework hosting]
ms.assetid: 46becf3e-bc0e-4338-85c0-9ab0df76a1d0
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 07de2321c1c7760293c53ad77dd3bbdf7f82a564
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihostautoeventset-method"></a><span data-ttu-id="f8868-102">IHostAutoEvent::Set メソッド</span><span class="sxs-lookup"><span data-stu-id="f8868-102">IHostAutoEvent::Set Method</span></span>
<span data-ttu-id="f8868-103">現在の設定[IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)インスタンスがシグナル状態にします。</span><span class="sxs-lookup"><span data-stu-id="f8868-103">Sets the current [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8868-104">構文</span><span class="sxs-lookup"><span data-stu-id="f8868-104">Syntax</span></span>  
  
```  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f8868-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="f8868-105">Return Value</span></span>  
  
|<span data-ttu-id="f8868-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f8868-106">HRESULT</span></span>|<span data-ttu-id="f8868-107">説明</span><span class="sxs-lookup"><span data-stu-id="f8868-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f8868-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="f8868-108">S_OK</span></span>|<span data-ttu-id="f8868-109">`Set`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="f8868-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="f8868-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f8868-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f8868-111">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="f8868-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f8868-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f8868-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f8868-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="f8868-113">The call timed out.</span></span>|  
|<span data-ttu-id="f8868-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f8868-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f8868-115">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="f8868-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f8868-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f8868-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f8868-117">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="f8868-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f8868-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f8868-118">E_FAIL</span></span>|<span data-ttu-id="f8868-119">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f8868-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f8868-120">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="f8868-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f8868-121">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="f8868-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f8868-122">要件</span><span class="sxs-lookup"><span data-stu-id="f8868-122">Requirements</span></span>  
 <span data-ttu-id="f8868-123">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f8868-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8868-124">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f8868-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f8868-125">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="f8868-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8868-126">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8868-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8868-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8868-127">See Also</span></span>  
 [<span data-ttu-id="f8868-128">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8868-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="f8868-129">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8868-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="f8868-130">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8868-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="f8868-131">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8868-131">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)

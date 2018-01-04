---
title: "ICLRRuntimeHost::Start メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.Start
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::Start
helpviewer_keywords:
- ICLRRuntimeHost::Start method [.NET Framework hosting]
- Start method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: c0a6dce5-0a8d-42e8-808b-6ca14df9d289
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9705e4449da3b485bef7e7250ca08473d51387b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehoststart-method"></a><span data-ttu-id="1462e-102">ICLRRuntimeHost::Start メソッド</span><span class="sxs-lookup"><span data-stu-id="1462e-102">ICLRRuntimeHost::Start Method</span></span>
<span data-ttu-id="1462e-103">プロセスには、共通言語ランタイム (CLR) を初期化します。</span><span class="sxs-lookup"><span data-stu-id="1462e-103">Initializes the common language runtime (CLR) into a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1462e-104">構文</span><span class="sxs-lookup"><span data-stu-id="1462e-104">Syntax</span></span>  
  
```  
HRESULT Start();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1462e-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="1462e-105">Return Value</span></span>  
  
|<span data-ttu-id="1462e-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1462e-106">HRESULT</span></span>|<span data-ttu-id="1462e-107">説明</span><span class="sxs-lookup"><span data-stu-id="1462e-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1462e-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="1462e-108">S_OK</span></span>|<span data-ttu-id="1462e-109">`Start`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="1462e-109">`Start` returned successfully.</span></span>|  
|<span data-ttu-id="1462e-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1462e-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1462e-111">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="1462e-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1462e-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1462e-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1462e-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="1462e-113">The call timed out.</span></span>|  
|<span data-ttu-id="1462e-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1462e-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1462e-115">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="1462e-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1462e-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1462e-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1462e-117">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="1462e-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1462e-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1462e-118">E_FAIL</span></span>|<span data-ttu-id="1462e-119">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="1462e-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1462e-120">メソッドには、E_FAIL が返された場合、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="1462e-120">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1462e-121">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="1462e-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1462e-122">コメント</span><span class="sxs-lookup"><span data-stu-id="1462e-122">Remarks</span></span>  
 <span data-ttu-id="1462e-123">多くのシナリオで必要はありませんを呼び出す`Start`ランタイムは自動的に初期化をマネージ コードを実行する最初の要求時にあるため、します。</span><span class="sxs-lookup"><span data-stu-id="1462e-123">In many scenarios it is not necessary to call `Start`, because the runtime will initialize itself automatically upon the first request to run managed code.</span></span> <span data-ttu-id="1462e-124">ただし、使用することができます、`Start`を正確にすると、ランタイムを初期化するを指定します。</span><span class="sxs-lookup"><span data-stu-id="1462e-124">You can, however, use `Start` to specify exactly when the runtime should be initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1462e-125">必要条件</span><span class="sxs-lookup"><span data-stu-id="1462e-125">Requirements</span></span>  
 <span data-ttu-id="1462e-126">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1462e-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1462e-127">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1462e-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1462e-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="1462e-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1462e-129">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1462e-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1462e-130">参照</span><span class="sxs-lookup"><span data-stu-id="1462e-130">See Also</span></span>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="1462e-131">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1462e-131">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)

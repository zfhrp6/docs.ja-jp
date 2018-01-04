---
title: "IHostSecurityContext::Capture メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityContext.Capture
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityContext::Capture
helpviewer_keywords:
- Capture method [.NET Framework hosting]
- IHostSecurityContext::Capture method [.NET Framework hosting]
ms.assetid: ae0836d0-1170-4494-bac5-d0e809df51a2
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: def431dd40c6dd7aa6688a638971d3676bbd1ffb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritycontextcapture-method"></a><span data-ttu-id="294be-102">IHostSecurityContext::Capture メソッド</span><span class="sxs-lookup"><span data-stu-id="294be-102">IHostSecurityContext::Capture Method</span></span>
<span data-ttu-id="294be-103">複製を取得、 [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)への呼び出しから返されるインスタンス[ihostsecuritymanager::getsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="294be-103">Gets a clone of the [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="294be-104">構文</span><span class="sxs-lookup"><span data-stu-id="294be-104">Syntax</span></span>  
  
```  
HRESULT Capture (  
    [out] IHostSecurityContext** ppClonedContext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="294be-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="294be-105">Parameters</span></span>  
 `ppClonedContext`  
 <span data-ttu-id="294be-106">[out]複製のアドレスへのポインター、`IHostSecurityContext`をキャプチャするオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="294be-106">[out] A pointer to the address of a clone of the `IHostSecurityContext` object to be captured.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="294be-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="294be-107">Return Value</span></span>  
  
|<span data-ttu-id="294be-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="294be-108">HRESULT</span></span>|<span data-ttu-id="294be-109">説明</span><span class="sxs-lookup"><span data-stu-id="294be-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="294be-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="294be-110">S_OK</span></span>|<span data-ttu-id="294be-111">`Capture`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="294be-111">`Capture` returned successfully.</span></span>|  
|<span data-ttu-id="294be-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="294be-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="294be-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="294be-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="294be-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="294be-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="294be-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="294be-115">The call timed out.</span></span>|  
|<span data-ttu-id="294be-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="294be-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="294be-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="294be-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="294be-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="294be-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="294be-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="294be-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="294be-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="294be-120">E_FAIL</span></span>|<span data-ttu-id="294be-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="294be-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="294be-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="294be-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="294be-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="294be-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="294be-124">コメント</span><span class="sxs-lookup"><span data-stu-id="294be-124">Remarks</span></span>  
 <span data-ttu-id="294be-125">返されたインターフェイス ポインター`Capture`キャプチャされたコンテキストのクローンであります。</span><span class="sxs-lookup"><span data-stu-id="294be-125">The interface pointer returned from `Capture` is a clone of the captured context.</span></span> <span data-ttu-id="294be-126">この情報は、移動すると、非同期コード ポイント間を対象となる呼び出しが行われたポインターからその有効期間が区切られます。</span><span class="sxs-lookup"><span data-stu-id="294be-126">When this information is moved across an asynchronous code point, its lifetime is separated from that of the pointer against which the call was made.</span></span> <span data-ttu-id="294be-127">元のポインターを解放できます。</span><span class="sxs-lookup"><span data-stu-id="294be-127">The original pointer can therefore be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="294be-128">必要条件</span><span class="sxs-lookup"><span data-stu-id="294be-128">Requirements</span></span>  
 <span data-ttu-id="294be-129">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="294be-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="294be-130">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="294be-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="294be-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="294be-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="294be-132">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="294be-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="294be-133">参照</span><span class="sxs-lookup"><span data-stu-id="294be-133">See Also</span></span>  
 [<span data-ttu-id="294be-134">IHostSecurityContext インターフェイス</span><span class="sxs-lookup"><span data-stu-id="294be-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="294be-135">IHostSecurityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="294be-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)

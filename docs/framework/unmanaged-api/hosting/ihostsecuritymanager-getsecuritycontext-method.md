---
title: "IHostSecurityManager::GetSecurityContext メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.GetSecurityContext
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::GetSecurityContext
helpviewer_keywords:
- GetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::GetSecurityContext method [.NET Framework hosting]
ms.assetid: 958970d6-f6a2-4b84-b32a-f555cbaf8f61
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b150700c50842791a2413688583e7e1289852d62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="4f99b-102">IHostSecurityManager::GetSecurityContext メソッド</span><span class="sxs-lookup"><span data-stu-id="4f99b-102">IHostSecurityManager::GetSecurityContext Method</span></span>
<span data-ttu-id="4f99b-103">要求された取得[IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)ホストからです。</span><span class="sxs-lookup"><span data-stu-id="4f99b-103">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f99b-104">構文</span><span class="sxs-lookup"><span data-stu-id="4f99b-104">Syntax</span></span>  
  
```  
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,   
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4f99b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4f99b-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="4f99b-106">[in]1 つ、 [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)を返すのセキュリティ コンテキストの種類を示す値。</span><span class="sxs-lookup"><span data-stu-id="4f99b-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="4f99b-107">[out]インターフェイス ポインターのアドレス、`IHostSecurityContext`の`eContextType`します。</span><span class="sxs-lookup"><span data-stu-id="4f99b-107">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f99b-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="4f99b-108">Return Value</span></span>  
  
|<span data-ttu-id="4f99b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4f99b-109">HRESULT</span></span>|<span data-ttu-id="4f99b-110">説明</span><span class="sxs-lookup"><span data-stu-id="4f99b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4f99b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4f99b-111">S_OK</span></span>|<span data-ttu-id="4f99b-112">`GetSecurityContext`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="4f99b-112">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="4f99b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4f99b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4f99b-114">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="4f99b-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4f99b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4f99b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4f99b-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="4f99b-116">The call timed out.</span></span>|  
|<span data-ttu-id="4f99b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4f99b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4f99b-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="4f99b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4f99b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4f99b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4f99b-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="4f99b-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4f99b-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4f99b-121">E_FAIL</span></span>|<span data-ttu-id="4f99b-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="4f99b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4f99b-123">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="4f99b-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4f99b-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="4f99b-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f99b-125">コメント</span><span class="sxs-lookup"><span data-stu-id="4f99b-125">Remarks</span></span>  
 <span data-ttu-id="4f99b-126">ホストは、CLR とユーザーの両方のコードでスレッド トークンへのすべてのコード アクセスを制御できます。</span><span class="sxs-lookup"><span data-stu-id="4f99b-126">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="4f99b-127">ように、完全なセキュリティ コンテキスト情報は、非同期操作または制限付きのコード アクセス権を持つコード ポイントを越えて渡されます。</span><span class="sxs-lookup"><span data-stu-id="4f99b-127">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="4f99b-128">`IHostSecurityContext`このが CLR に対して非透過的セキュリティ コンテキスト情報をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="4f99b-128">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="4f99b-129">CLR では、この情報をキャプチャし、スレッド プールのワーカーのアイテムのディスパッチ、ファイナライザーの実行、およびモジュールとクラスの構築の間で移動します。</span><span class="sxs-lookup"><span data-stu-id="4f99b-129">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f99b-130">要件</span><span class="sxs-lookup"><span data-stu-id="4f99b-130">Requirements</span></span>  
 <span data-ttu-id="4f99b-131">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4f99b-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f99b-132">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4f99b-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4f99b-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="4f99b-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4f99b-134">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f99b-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f99b-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f99b-135">See Also</span></span>  
 [<span data-ttu-id="4f99b-136">EContextType 列挙型</span><span class="sxs-lookup"><span data-stu-id="4f99b-136">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)  
 [<span data-ttu-id="4f99b-137">IHostSecurityContext インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4f99b-137">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="4f99b-138">IHostSecurityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4f99b-138">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)

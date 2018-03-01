---
title: "IHostAssemblyManager::GetAssemblyStore メソッド"
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
- IHostAssemblyManager.GetAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetAssemblyStore
helpviewer_keywords:
- IHostAssemblyManager::GetAssemblyStore method [.NET Framework hosting]
- GetAssemblyStore method [.NET Framework hosting]
ms.assetid: d0f74593-9bb1-4a11-8096-e29734b20698
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 347947622601475147663b8838bef5f36a1f7e32
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="1e2f6-102">IHostAssemblyManager::GetAssemblyStore メソッド</span><span class="sxs-lookup"><span data-stu-id="1e2f6-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>
<span data-ttu-id="1e2f6-103">インターフェイス ポインターを取得、 [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)ホストによって読み込まれるアセンブリの一覧を表すです。</span><span class="sxs-lookup"><span data-stu-id="1e2f6-103">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e2f6-104">構文</span><span class="sxs-lookup"><span data-stu-id="1e2f6-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1e2f6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e2f6-105">Parameters</span></span>  
 `ppAssemblyStore`  
 <span data-ttu-id="1e2f6-106">[out]関数ポインター、`IHostAssemblyStore`インスタンス、またはホストを実装しない場合は、null`IHostAssemblyStore`です。</span><span class="sxs-lookup"><span data-stu-id="1e2f6-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e2f6-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e2f6-107">Return Value</span></span>  
  
|<span data-ttu-id="1e2f6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1e2f6-108">HRESULT</span></span>|<span data-ttu-id="1e2f6-109">説明</span><span class="sxs-lookup"><span data-stu-id="1e2f6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1e2f6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1e2f6-110">S_OK</span></span>|<span data-ttu-id="1e2f6-111">`GetAssemblyStore`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="1e2f6-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="1e2f6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1e2f6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1e2f6-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="1e2f6-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1e2f6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1e2f6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1e2f6-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="1e2f6-115">The call timed out.</span></span>|  
|<span data-ttu-id="1e2f6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1e2f6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1e2f6-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="1e2f6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1e2f6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1e2f6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1e2f6-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="1e2f6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1e2f6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1e2f6-120">E_FAIL</span></span>|<span data-ttu-id="1e2f6-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="1e2f6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1e2f6-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="1e2f6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1e2f6-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="1e2f6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1e2f6-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="1e2f6-124">E_NOINTERFACE</span></span>|<span data-ttu-id="1e2f6-125">ホストがの実装を提供していない`IHostAssemblyStore`です。</span><span class="sxs-lookup"><span data-stu-id="1e2f6-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e2f6-126">コメント</span><span class="sxs-lookup"><span data-stu-id="1e2f6-126">Remarks</span></span>  
 <span data-ttu-id="1e2f6-127">`IHostAssemblyStore`ホストがアセンブリと CLR とは無関係にモジュールをバインドできるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="1e2f6-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="1e2f6-128">ホストは、通常、ファイル システム以外の形式から読み込まれるアセンブリを許可するアセンブリ ストアを提供します。</span><span class="sxs-lookup"><span data-stu-id="1e2f6-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e2f6-129">ホストを実装しない場合`IHostAssemblyStore`、 `GetAssemblyStore` 、HRESULT の戻り値は E_NOINTERFACE、および設定する必要があります`ppAssemblyStore`を null にします。</span><span class="sxs-lookup"><span data-stu-id="1e2f6-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e2f6-130">必要条件</span><span class="sxs-lookup"><span data-stu-id="1e2f6-130">Requirements</span></span>  
 <span data-ttu-id="1e2f6-131">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1e2f6-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e2f6-132">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1e2f6-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1e2f6-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="1e2f6-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e2f6-134">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e2f6-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e2f6-135">参照</span><span class="sxs-lookup"><span data-stu-id="1e2f6-135">See Also</span></span>  
 [<span data-ttu-id="1e2f6-136">IHostAssemblyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1e2f6-136">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="1e2f6-137">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1e2f6-137">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)

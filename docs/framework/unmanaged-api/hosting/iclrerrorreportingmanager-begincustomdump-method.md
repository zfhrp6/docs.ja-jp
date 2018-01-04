---
title: "ICLRErrorReportingManager::BeginCustomDump メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRErrorReportingManager.BeginCustomDump
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRErrorReportingManager::BeginCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::BeginCustomDump method [.NET Framework hosting]
- BeginCustomDump method
ms.assetid: 93424a87-ba13-4fa1-b4dc-69d44437b7ae
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d09afd9fe0a2905c79ffb2d50b342041865b593b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="408e6-102">ICLRErrorReportingManager::BeginCustomDump メソッド</span><span class="sxs-lookup"><span data-stu-id="408e6-102">ICLRErrorReportingManager::BeginCustomDump Method</span></span>
<span data-ttu-id="408e6-103">エラー報告用にカスタムのヒープ ダンプの構成を指定します。</span><span class="sxs-lookup"><span data-stu-id="408e6-103">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="408e6-104">構文</span><span class="sxs-lookup"><span data-stu-id="408e6-104">Syntax</span></span>  
  
```  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="408e6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="408e6-105">Parameters</span></span>  
 `dwFlavor`  
 <span data-ttu-id="408e6-106">[in]A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)カスタム ヒープ ダンプを構築するためのヒープ ダンプの種類を示す値。</span><span class="sxs-lookup"><span data-stu-id="408e6-106">[in] A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="408e6-107">[in]長さ、`items`配列。</span><span class="sxs-lookup"><span data-stu-id="408e6-107">[in] The length of the `items` array.</span></span> <span data-ttu-id="408e6-108">場合`dwFlavor`が DUMP_FLAVOR_Mini、 `dwNumItems` 0 にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="408e6-108">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="408e6-109">[in]配列[CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)インスタンス、ミニ ダンプに追加する項目を指定します。</span><span class="sxs-lookup"><span data-stu-id="408e6-109">[in] An array of [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="408e6-110">場合`dwFlavor`が DUMP_FLAVOR_Mini、 `items` null にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="408e6-110">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="408e6-111">[in]将来使用するために予約されています。</span><span class="sxs-lookup"><span data-stu-id="408e6-111">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="408e6-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="408e6-112">Return Value</span></span>  
  
|<span data-ttu-id="408e6-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="408e6-113">HRESULT</span></span>|<span data-ttu-id="408e6-114">説明</span><span class="sxs-lookup"><span data-stu-id="408e6-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="408e6-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="408e6-115">S_OK</span></span>|<span data-ttu-id="408e6-116">メソッドが正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="408e6-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="408e6-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="408e6-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="408e6-118">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="408e6-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="408e6-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="408e6-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="408e6-120">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="408e6-120">The call timed out.</span></span>|  
|<span data-ttu-id="408e6-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="408e6-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="408e6-122">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="408e6-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="408e6-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="408e6-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="408e6-124">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="408e6-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="408e6-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="408e6-125">E_FAIL</span></span>|<span data-ttu-id="408e6-126">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="408e6-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="408e6-127">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="408e6-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="408e6-128">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="408e6-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="408e6-129">コメント</span><span class="sxs-lookup"><span data-stu-id="408e6-129">Remarks</span></span>  
 <span data-ttu-id="408e6-130">`BeginCustomDump`メソッドは、カスタム ヒープ ダンプ構成を設定します。</span><span class="sxs-lookup"><span data-stu-id="408e6-130">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="408e6-131">[EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)メソッドは、カスタム ヒープ ダンプ構成をクリアし、その関連付けられた状態を解放します。</span><span class="sxs-lookup"><span data-stu-id="408e6-131">The [EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="408e6-132">これはカスタム ヒープ ダンプの完了後に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="408e6-132">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="408e6-133">呼び出しに失敗する`EndCustomDump`によってメモリ リークが発生します。</span><span class="sxs-lookup"><span data-stu-id="408e6-133">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="408e6-134">必要条件</span><span class="sxs-lookup"><span data-stu-id="408e6-134">Requirements</span></span>  
 <span data-ttu-id="408e6-135">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="408e6-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="408e6-136">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="408e6-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="408e6-137">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="408e6-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="408e6-138">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="408e6-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="408e6-139">参照</span><span class="sxs-lookup"><span data-stu-id="408e6-139">See Also</span></span>  
 [<span data-ttu-id="408e6-140">CustomDumpItem 構造体</span><span class="sxs-lookup"><span data-stu-id="408e6-140">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)  
 [<span data-ttu-id="408e6-141">ECustomDumpFlavor 列挙型</span><span class="sxs-lookup"><span data-stu-id="408e6-141">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)  
 [<span data-ttu-id="408e6-142">ICLRErrorReportingManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="408e6-142">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)

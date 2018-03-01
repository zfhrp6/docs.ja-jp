---
title: "ICLRErrorReportingManager::EndCustomDump メソッド"
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
- ICLRErrorReportingManager.EndCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::EndCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::EndCustomDump method [.NET Framework hosting]
- EndCustomDump method [.NET Framework hosting]
ms.assetid: 88a5da04-8729-4108-82c4-af206a7d483e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 709ef121294a92353b21363ae12919e8e147efab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrerrorreportingmanagerendcustomdump-method"></a><span data-ttu-id="c18a5-102">ICLRErrorReportingManager::EndCustomDump メソッド</span><span class="sxs-lookup"><span data-stu-id="c18a5-102">ICLRErrorReportingManager::EndCustomDump Method</span></span>
<span data-ttu-id="c18a5-103">以前の呼び出しで指定されているカスタム スタック ダンプ構成を削除、 [iclrerrorreportingmanager::begincustomdump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="c18a5-103">Removes the custom stack dump configuration that was specified in an earlier call to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c18a5-104">構文</span><span class="sxs-lookup"><span data-stu-id="c18a5-104">Syntax</span></span>  
  
```  
HRESULT EndCustomDump ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c18a5-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="c18a5-105">Return Value</span></span>  
  
|<span data-ttu-id="c18a5-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c18a5-106">HRESULT</span></span>|<span data-ttu-id="c18a5-107">説明</span><span class="sxs-lookup"><span data-stu-id="c18a5-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c18a5-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="c18a5-108">S_OK</span></span>|<span data-ttu-id="c18a5-109">`EndCustomDump`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="c18a5-109">`EndCustomDump` returned successfully.</span></span>|  
|<span data-ttu-id="c18a5-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c18a5-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c18a5-111">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="c18a5-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c18a5-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c18a5-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c18a5-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="c18a5-113">The call timed out.</span></span>|  
|<span data-ttu-id="c18a5-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c18a5-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c18a5-115">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="c18a5-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c18a5-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c18a5-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c18a5-117">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="c18a5-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c18a5-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c18a5-118">E_FAIL</span></span>|<span data-ttu-id="c18a5-119">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="c18a5-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c18a5-120">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="c18a5-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c18a5-121">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="c18a5-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c18a5-122">コメント</span><span class="sxs-lookup"><span data-stu-id="c18a5-122">Remarks</span></span>  
 <span data-ttu-id="c18a5-123">`EndCustomDump`メソッドは、カスタム スタック ダンプ構成セットを以前の呼び出しによって、クリア、`BeginCustomDump`メソッドと、関連付けられた状態を解放します。</span><span class="sxs-lookup"><span data-stu-id="c18a5-123">The `EndCustomDump` method clears the custom stack dump configuration set by an earlier call to the `BeginCustomDump` method and frees any associated state.</span></span> <span data-ttu-id="c18a5-124">これはカスタム スタック ダンプの完了後に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="c18a5-124">It should be called after the custom stack dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c18a5-125">呼び出しに失敗する`EndCustomDump`によってメモリ リークが発生します。</span><span class="sxs-lookup"><span data-stu-id="c18a5-125">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c18a5-126">必要条件</span><span class="sxs-lookup"><span data-stu-id="c18a5-126">Requirements</span></span>  
 <span data-ttu-id="c18a5-127">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c18a5-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c18a5-128">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c18a5-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c18a5-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="c18a5-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c18a5-130">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c18a5-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c18a5-131">参照</span><span class="sxs-lookup"><span data-stu-id="c18a5-131">See Also</span></span>  
 [<span data-ttu-id="c18a5-132">CustomDumpItem 構造体</span><span class="sxs-lookup"><span data-stu-id="c18a5-132">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)  
 [<span data-ttu-id="c18a5-133">ECustomDumpFlavor 列挙型</span><span class="sxs-lookup"><span data-stu-id="c18a5-133">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)  
 [<span data-ttu-id="c18a5-134">ICLRErrorReportingManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c18a5-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)

---
title: "ICLRControl::GetCLRManager メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRControl.GetCLRManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRControl::GetCLRManager
helpviewer_keywords:
- GetCLRManager method [.NET Framework hosting]
- ICLRControl::GetCLRManager method [.NET Framework hosting]
ms.assetid: 8a11bfa4-cbb0-4082-82b5-f9fba66c93f5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f3dc6f707511f9d6f4883aecbd2a26a587a902c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrcontrolgetclrmanager-method"></a><span data-ttu-id="7e9f7-102">ICLRControl::GetCLRManager メソッド</span><span class="sxs-lookup"><span data-stu-id="7e9f7-102">ICLRControl::GetCLRManager Method</span></span>
<span data-ttu-id="7e9f7-103">ホストが共通言語ランタイム (CLR) の構成に使用できる、マネージャーの種類のいずれかのインスタンスへのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="7e9f7-103">Gets an interface pointer to an instance of any of the manager types the host can use to configure the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e9f7-104">構文</span><span class="sxs-lookup"><span data-stu-id="7e9f7-104">Syntax</span></span>  
  
```  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7e9f7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7e9f7-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="7e9f7-106">[in]`IID`のマネージャーの種類を返します。</span><span class="sxs-lookup"><span data-stu-id="7e9f7-106">[in] The `IID` of the manager type to return.</span></span> <span data-ttu-id="7e9f7-107">次`IID`値はサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7e9f7-107">The following `IID` values are supported.</span></span>  
  
-   <span data-ttu-id="7e9f7-108">IID_ICLRDebugManager: を指定する`ppObject`型である[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="7e9f7-108">IID_ICLRDebugManager: Specifies that `ppObject` will be of type [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="7e9f7-109">IID_ICLRErrorReportingManager: を指定する`ppObject`型である[ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="7e9f7-109">IID_ICLRErrorReportingManager: Specifies that `ppObject` will be of type [ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="7e9f7-110">IID_ICLRGCManager: を指定する`ppObject`型である[ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="7e9f7-110">IID_ICLRGCManager: Specifies that `ppObject` will be of type [ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="7e9f7-111">IID_ICLRHostProtectionManager: を指定する`ppObject`型である[ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="7e9f7-111">IID_ICLRHostProtectionManager: Specifies that `ppObject` will be of type [ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="7e9f7-112">IID_ICLROnEventManager: を指定する`ppObject`型である[ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="7e9f7-112">IID_ICLROnEventManager: Specifies that `ppObject` will be of type [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="7e9f7-113">IID_ICLRPolicyManager: を指定する`ppObject`型である[ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="7e9f7-113">IID_ICLRPolicyManager: Specifies that `ppObject` will be of type [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>  
  
-   <span data-ttu-id="7e9f7-114">IID_ICLRTaskManager: speciries を`ppObject`型である[ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="7e9f7-114">IID_ICLRTaskManager: speciries that `ppObject` will be of type [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).</span></span>  
  
 `ppObject`  
 <span data-ttu-id="7e9f7-115">[out]要求されたマネージャー、または、無効なマネージャーの種類が要求された場合は null にインターフェイス ポインター。</span><span class="sxs-lookup"><span data-stu-id="7e9f7-115">[out] An interface pointer to the requested manager, or null, if an invalid manager type was requested.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e9f7-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="7e9f7-116">Return Value</span></span>  
  
|<span data-ttu-id="7e9f7-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7e9f7-117">HRESULT</span></span>|<span data-ttu-id="7e9f7-118">説明</span><span class="sxs-lookup"><span data-stu-id="7e9f7-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7e9f7-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="7e9f7-119">S_OK</span></span>|<span data-ttu-id="7e9f7-120">メソッドが正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="7e9f7-120">The method returned successfully.</span></span>|  
|<span data-ttu-id="7e9f7-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7e9f7-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7e9f7-122">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="7e9f7-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7e9f7-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7e9f7-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7e9f7-124">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="7e9f7-124">The call timed out.</span></span>|  
|<span data-ttu-id="7e9f7-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7e9f7-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7e9f7-126">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="7e9f7-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7e9f7-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7e9f7-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7e9f7-128">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="7e9f7-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7e9f7-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7e9f7-129">E_FAIL</span></span>|<span data-ttu-id="7e9f7-130">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="7e9f7-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7e9f7-131">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="7e9f7-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7e9f7-132">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="7e9f7-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7e9f7-133">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="7e9f7-133">E_NOINTERFACE</span></span>|<span data-ttu-id="7e9f7-134">インターフェイス型はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="7e9f7-134">The interface type is not supported.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7e9f7-135">要件</span><span class="sxs-lookup"><span data-stu-id="7e9f7-135">Requirements</span></span>  
 <span data-ttu-id="7e9f7-136">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7e9f7-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e9f7-137">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7e9f7-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7e9f7-138">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="7e9f7-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e9f7-139">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e9f7-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e9f7-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e9f7-140">See Also</span></span>  
 [<span data-ttu-id="7e9f7-141">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7e9f7-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="7e9f7-142">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7e9f7-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)

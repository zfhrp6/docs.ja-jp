---
title: "ICLRControl::SetAppDomainManagerType メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRControl.SetAppDomainManagerType
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRControl::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRControl interface [.NET Framework hosting]
- ICLRControl::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ec57828b-2aad-496d-a35a-e45d4bd7fe77
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6632417cb0cfe17d7bde16ecf47ae1c001f43f2b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="ee202-102">ICLRControl::SetAppDomainManagerType メソッド</span><span class="sxs-lookup"><span data-stu-id="ee202-102">ICLRControl::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="ee202-103">派生した型を設定<xref:System.AppDomainManager>アプリケーション ドメイン マネージャーの種類として。</span><span class="sxs-lookup"><span data-stu-id="ee202-103">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee202-104">構文</span><span class="sxs-lookup"><span data-stu-id="ee202-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ee202-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ee202-105">Parameters</span></span>  
 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="ee202-106">[in]要求された型の派生アセンブリの名前<xref:System.AppDomainManager>は実装されています。</span><span class="sxs-lookup"><span data-stu-id="ee202-106">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="ee202-107">[in]実装された型の名前、`pwzAppDomainManagerAssembly`パラメーターの機能を実装する<xref:System.AppDomainManager>です。</span><span class="sxs-lookup"><span data-stu-id="ee202-107">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ee202-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="ee202-108">Return Value</span></span>  
  
|<span data-ttu-id="ee202-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ee202-109">HRESULT</span></span>|<span data-ttu-id="ee202-110">説明</span><span class="sxs-lookup"><span data-stu-id="ee202-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ee202-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ee202-111">S_OK</span></span>|<span data-ttu-id="ee202-112">メソッドが正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="ee202-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="ee202-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ee202-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ee202-114">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="ee202-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ee202-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ee202-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ee202-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="ee202-116">The call timed out.</span></span>|  
|<span data-ttu-id="ee202-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ee202-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ee202-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="ee202-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ee202-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ee202-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ee202-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="ee202-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ee202-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ee202-121">E_FAIL</span></span>|<span data-ttu-id="ee202-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="ee202-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ee202-123">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="ee202-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ee202-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="ee202-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ee202-125">要件</span><span class="sxs-lookup"><span data-stu-id="ee202-125">Requirements</span></span>  
 <span data-ttu-id="ee202-126">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ee202-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee202-127">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ee202-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ee202-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="ee202-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ee202-129">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee202-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee202-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="ee202-130">See Also</span></span>  
 [<span data-ttu-id="ee202-131">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ee202-131">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="ee202-132">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ee202-132">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)

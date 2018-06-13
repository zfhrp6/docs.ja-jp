---
title: ICLRControl::SetAppDomainManagerType メソッド
ms.date: 03/30/2017
api_name:
- ICLRControl.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRControl interface [.NET Framework hosting]
- ICLRControl::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ec57828b-2aad-496d-a35a-e45d4bd7fe77
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be778fed910b2cbdbf5e9ae7754abae437ef6bec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433735"
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="37c1b-102">ICLRControl::SetAppDomainManagerType メソッド</span><span class="sxs-lookup"><span data-stu-id="37c1b-102">ICLRControl::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="37c1b-103">派生した型を設定<xref:System.AppDomainManager>アプリケーション ドメイン マネージャーの種類として。</span><span class="sxs-lookup"><span data-stu-id="37c1b-103">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37c1b-104">構文</span><span class="sxs-lookup"><span data-stu-id="37c1b-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="37c1b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="37c1b-105">Parameters</span></span>  
 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="37c1b-106">[in]要求された型の派生アセンブリの名前<xref:System.AppDomainManager>は実装されています。</span><span class="sxs-lookup"><span data-stu-id="37c1b-106">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="37c1b-107">[in]実装された型の名前、`pwzAppDomainManagerAssembly`パラメーターの機能を実装する<xref:System.AppDomainManager>です。</span><span class="sxs-lookup"><span data-stu-id="37c1b-107">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37c1b-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="37c1b-108">Return Value</span></span>  
  
|<span data-ttu-id="37c1b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="37c1b-109">HRESULT</span></span>|<span data-ttu-id="37c1b-110">説明</span><span class="sxs-lookup"><span data-stu-id="37c1b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="37c1b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="37c1b-111">S_OK</span></span>|<span data-ttu-id="37c1b-112">メソッドが正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="37c1b-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="37c1b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="37c1b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="37c1b-114">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="37c1b-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="37c1b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="37c1b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="37c1b-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="37c1b-116">The call timed out.</span></span>|  
|<span data-ttu-id="37c1b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="37c1b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="37c1b-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="37c1b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="37c1b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="37c1b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="37c1b-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="37c1b-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="37c1b-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="37c1b-121">E_FAIL</span></span>|<span data-ttu-id="37c1b-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="37c1b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="37c1b-123">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="37c1b-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="37c1b-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="37c1b-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="37c1b-125">要件</span><span class="sxs-lookup"><span data-stu-id="37c1b-125">Requirements</span></span>  
 <span data-ttu-id="37c1b-126">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="37c1b-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37c1b-127">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="37c1b-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="37c1b-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="37c1b-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37c1b-129">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37c1b-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37c1b-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="37c1b-130">See Also</span></span>  
 [<span data-ttu-id="37c1b-131">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="37c1b-131">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="37c1b-132">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="37c1b-132">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)

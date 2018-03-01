---
title: "ICorRuntimeHost::UnloadDomain メソッド"
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
- ICorRuntimeHost.UnloadDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::UnloadDomain
helpviewer_keywords:
- ICorRuntimeHost::UnloadDomain method [.NET Framework hosting]
- UnloadDomain method [.NET Framework hosting]
ms.assetid: dd9e9204-a80d-44f3-8192-779224b35056
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 067b60b9da02300e9e7316712d0058a61ab8a697
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="94c74-102">ICorRuntimeHost::UnloadDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="94c74-102">ICorRuntimeHost::UnloadDomain Method</span></span>
<span data-ttu-id="94c74-103">現在のプロセスから指定されたアプリケーション ドメインをアンロードします。</span><span class="sxs-lookup"><span data-stu-id="94c74-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94c74-104">構文</span><span class="sxs-lookup"><span data-stu-id="94c74-104">Syntax</span></span>  
  
```  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="94c74-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="94c74-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="94c74-106">[in]型のポインター<xref:System._AppDomain?displayProperty=nameWithType>をアンロードできるドメインを表すです。</span><span class="sxs-lookup"><span data-stu-id="94c74-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94c74-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="94c74-107">Return Value</span></span>  
  
|<span data-ttu-id="94c74-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="94c74-108">HRESULT</span></span>|<span data-ttu-id="94c74-109">説明</span><span class="sxs-lookup"><span data-stu-id="94c74-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="94c74-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="94c74-110">S_OK</span></span>|<span data-ttu-id="94c74-111">操作が正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="94c74-111">The operation was successful.</span></span>|  
|<span data-ttu-id="94c74-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="94c74-112">S_FALSE</span></span>|<span data-ttu-id="94c74-113">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="94c74-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="94c74-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="94c74-114">E_FAIL</span></span>|<span data-ttu-id="94c74-115">未知の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="94c74-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="94c74-116">メソッドには、E_FAIL が返されます、共通言語ランタイム (CLR) は、プロセスで使用可能なできなくします。</span><span class="sxs-lookup"><span data-stu-id="94c74-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="94c74-117">Api をホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="94c74-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="94c74-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="94c74-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="94c74-119">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="94c74-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="94c74-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="94c74-120">Requirements</span></span>  
 <span data-ttu-id="94c74-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="94c74-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94c74-122">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="94c74-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="94c74-123">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="94c74-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="94c74-124">**.NET framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="94c74-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94c74-125">参照</span><span class="sxs-lookup"><span data-stu-id="94c74-125">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="94c74-126">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="94c74-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)

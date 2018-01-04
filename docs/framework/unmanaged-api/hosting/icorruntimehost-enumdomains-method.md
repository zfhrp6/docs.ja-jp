---
title: "ICorRuntimeHost::EnumDomains メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.EnumDomains
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::EnumDomains
helpviewer_keywords:
- ICorRuntimeHost::EnumDomains method [.NET Framework hosting]
- EnumDomains method [.NET Framework hosting]
ms.assetid: 96b74995-0cde-4876-b6df-7fc164e6a5d1
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f12135134e38b3f52c66aa951d61a3da7cf5fa50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="e1308-102">ICorRuntimeHost::EnumDomains メソッド</span><span class="sxs-lookup"><span data-stu-id="e1308-102">ICorRuntimeHost::EnumDomains Method</span></span>
<span data-ttu-id="e1308-103">現在のプロセスで、ドメインの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="e1308-103">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1308-104">構文</span><span class="sxs-lookup"><span data-stu-id="e1308-104">Syntax</span></span>  
  
```  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1308-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e1308-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="e1308-106">[out]ドメインの列挙子。</span><span class="sxs-lookup"><span data-stu-id="e1308-106">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1308-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="e1308-107">Return Value</span></span>  
  
|<span data-ttu-id="e1308-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e1308-108">HRESULT</span></span>|<span data-ttu-id="e1308-109">説明</span><span class="sxs-lookup"><span data-stu-id="e1308-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e1308-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e1308-110">S_OK</span></span>|<span data-ttu-id="e1308-111">操作が正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="e1308-111">The operation was successful.</span></span>|  
|<span data-ttu-id="e1308-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e1308-112">S_FALSE</span></span>|<span data-ttu-id="e1308-113">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="e1308-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="e1308-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e1308-114">E_FAIL</span></span>|<span data-ttu-id="e1308-115">未知の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="e1308-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="e1308-116">メソッドには、E_FAIL が返されます、共通言語ランタイム (CLR) は、プロセスで使用可能なできなくします。</span><span class="sxs-lookup"><span data-stu-id="e1308-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="e1308-117">Api をホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="e1308-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e1308-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e1308-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e1308-119">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="e1308-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e1308-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="e1308-120">Requirements</span></span>  
 <span data-ttu-id="e1308-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e1308-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1308-122">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e1308-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e1308-123">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="e1308-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e1308-124">**.NET framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="e1308-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1308-125">参照</span><span class="sxs-lookup"><span data-stu-id="e1308-125">See Also</span></span>  
 [<span data-ttu-id="e1308-126">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e1308-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)

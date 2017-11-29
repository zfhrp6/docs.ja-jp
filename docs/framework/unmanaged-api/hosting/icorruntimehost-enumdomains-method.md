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
ms.openlocfilehash: c63e4345815a073fe6aa422018b6fadf45bd5370
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="8cb21-102">ICorRuntimeHost::EnumDomains メソッド</span><span class="sxs-lookup"><span data-stu-id="8cb21-102">ICorRuntimeHost::EnumDomains Method</span></span>
<span data-ttu-id="8cb21-103">現在のプロセスで、ドメインの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="8cb21-103">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cb21-104">構文</span><span class="sxs-lookup"><span data-stu-id="8cb21-104">Syntax</span></span>  
  
```  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8cb21-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8cb21-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="8cb21-106">[out]ドメインの列挙子。</span><span class="sxs-lookup"><span data-stu-id="8cb21-106">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8cb21-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="8cb21-107">Return Value</span></span>  
  
|<span data-ttu-id="8cb21-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8cb21-108">HRESULT</span></span>|<span data-ttu-id="8cb21-109">説明</span><span class="sxs-lookup"><span data-stu-id="8cb21-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8cb21-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8cb21-110">S_OK</span></span>|<span data-ttu-id="8cb21-111">操作が正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="8cb21-111">The operation was successful.</span></span>|  
|<span data-ttu-id="8cb21-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="8cb21-112">S_FALSE</span></span>|<span data-ttu-id="8cb21-113">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="8cb21-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="8cb21-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8cb21-114">E_FAIL</span></span>|<span data-ttu-id="8cb21-115">未知の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="8cb21-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="8cb21-116">メソッドには、E_FAIL が返されます、共通言語ランタイム (CLR) は、プロセスで使用可能なできなくします。</span><span class="sxs-lookup"><span data-stu-id="8cb21-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="8cb21-117">Api をホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="8cb21-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8cb21-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8cb21-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8cb21-119">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="8cb21-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8cb21-120">要件</span><span class="sxs-lookup"><span data-stu-id="8cb21-120">Requirements</span></span>  
 <span data-ttu-id="8cb21-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8cb21-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cb21-122">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8cb21-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8cb21-123">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="8cb21-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8cb21-124">**.NET framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="8cb21-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cb21-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="8cb21-125">See Also</span></span>  
 [<span data-ttu-id="8cb21-126">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8cb21-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)

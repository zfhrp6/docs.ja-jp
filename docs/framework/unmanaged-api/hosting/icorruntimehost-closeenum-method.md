---
title: "ICorRuntimeHost::CloseEnum メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CloseEnum
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CloseEnum
helpviewer_keywords:
- CloseEnum method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::CloseEnum method [.NET Framework hosting]
ms.assetid: f7ce7e8c-0a3e-4587-a180-063e2b85940e
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 677ab3a97b7fcceccd8ceb0943c62df8bc999649
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="89d0a-102">ICorRuntimeHost::CloseEnum メソッド</span><span class="sxs-lookup"><span data-stu-id="89d0a-102">ICorRuntimeHost::CloseEnum Method</span></span>
<span data-ttu-id="89d0a-103">ドメイン リストの先頭に戻るには、ドメインの列挙子をリセットします。</span><span class="sxs-lookup"><span data-stu-id="89d0a-103">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89d0a-104">構文</span><span class="sxs-lookup"><span data-stu-id="89d0a-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="89d0a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="89d0a-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="89d0a-106">[in]リセットする列挙子。</span><span class="sxs-lookup"><span data-stu-id="89d0a-106">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89d0a-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="89d0a-107">Return Value</span></span>  
  
|<span data-ttu-id="89d0a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="89d0a-108">HRESULT</span></span>|<span data-ttu-id="89d0a-109">説明</span><span class="sxs-lookup"><span data-stu-id="89d0a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="89d0a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="89d0a-110">S_OK</span></span>|<span data-ttu-id="89d0a-111">操作が正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="89d0a-111">The operation was successful.</span></span>|  
|<span data-ttu-id="89d0a-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="89d0a-112">S_FALSE</span></span>|<span data-ttu-id="89d0a-113">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="89d0a-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="89d0a-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="89d0a-114">E_FAIL</span></span>|<span data-ttu-id="89d0a-115">未知の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="89d0a-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="89d0a-116">メソッドには、E_FAIL が返されます、共通言語ランタイム (CLR) は、プロセスで使用可能なできなくします。</span><span class="sxs-lookup"><span data-stu-id="89d0a-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="89d0a-117">Api をホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="89d0a-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="89d0a-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="89d0a-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="89d0a-119">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="89d0a-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="89d0a-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="89d0a-120">Requirements</span></span>  
 <span data-ttu-id="89d0a-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="89d0a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89d0a-122">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="89d0a-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="89d0a-123">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="89d0a-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89d0a-124">**.NET framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="89d0a-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89d0a-125">参照</span><span class="sxs-lookup"><span data-stu-id="89d0a-125">See Also</span></span>  
 [<span data-ttu-id="89d0a-126">CorBindToRuntimeEx 関数</span><span class="sxs-lookup"><span data-stu-id="89d0a-126">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="89d0a-127">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="89d0a-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)

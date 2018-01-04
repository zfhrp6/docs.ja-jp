---
title: "CLRCreateInstance 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLRCreateInstance
api_location:
- mscoree.dll
- mscoreei.dll
api_type: COM
f1_keywords: CLRCreateInstance
helpviewer_keywords: CLRCreateInstance function [.NET Framework hosting]
ms.assetid: 5de13327-96c6-4697-a89e-b8bf40717855
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d95815dd0b2a1cdbddcb28a2e176bc12d3270ed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="clrcreateinstance-function"></a><span data-ttu-id="33c3b-102">CLRCreateInstance 関数</span><span class="sxs-lookup"><span data-stu-id="33c3b-102">CLRCreateInstance Function</span></span>
<span data-ttu-id="33c3b-103">3 つのインターフェイスのいずれかの提供: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)、 [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)、または[ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="33c3b-103">Provides one of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33c3b-104">構文</span><span class="sxs-lookup"><span data-stu-id="33c3b-104">Syntax</span></span>  
  
```  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33c3b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="33c3b-105">Parameters</span></span>  
 `clsid`  
 <span data-ttu-id="33c3b-106">[in]次の 3 つのクラス識別子のいずれかの: CLSID_CLRMetaHost、CLSID_CLRMetaHostPolicy、または CLSID_CLRDebugging です。</span><span class="sxs-lookup"><span data-stu-id="33c3b-106">[in] One of three class identifiers: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy, or CLSID_CLRDebugging.</span></span>  
  
 `riid`  
 <span data-ttu-id="33c3b-107">[in]次の 3 つのインターフェイス id (Iid) のいずれかの: IID_ICLRMetaHost、IID_ICLRMetaHostPolicy、または IID_ICLRDebugging です。</span><span class="sxs-lookup"><span data-stu-id="33c3b-107">[in] One of three interface identifiers (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy, or IID_ICLRDebugging.</span></span>  
  
 `ppInterface`  
 <span data-ttu-id="33c3b-108">[out]3 つのインターフェイスのいずれかの: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)、 [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)、または[ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="33c3b-108">[out] One of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33c3b-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="33c3b-109">Return Value</span></span>  
 <span data-ttu-id="33c3b-110">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="33c3b-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="33c3b-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="33c3b-111">HRESULT</span></span>|<span data-ttu-id="33c3b-112">説明</span><span class="sxs-lookup"><span data-stu-id="33c3b-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="33c3b-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="33c3b-113">S_OK</span></span>|<span data-ttu-id="33c3b-114">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="33c3b-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="33c3b-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="33c3b-115">E_POINTER</span></span>|<span data-ttu-id="33c3b-116">`ppInterface` が null です。</span><span class="sxs-lookup"><span data-stu-id="33c3b-116">`ppInterface` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33c3b-117">コメント</span><span class="sxs-lookup"><span data-stu-id="33c3b-117">Remarks</span></span>  
 <span data-ttu-id="33c3b-118">次の表は、サポートされる組み合わせの`clsid`と`riid`です。</span><span class="sxs-lookup"><span data-stu-id="33c3b-118">The following table shows the supported combinations for `clsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="33c3b-119">CLSID_CLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="33c3b-119">CLSID_CLRMetaHost</span></span>|<span data-ttu-id="33c3b-120">IID_ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="33c3b-120">IID_ICLRMetaHost</span></span>|  
|<span data-ttu-id="33c3b-121">CLSID_CLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="33c3b-121">CLSID_CLRMetaHostPolicy</span></span>|<span data-ttu-id="33c3b-122">IID_ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="33c3b-122">IID_ICLRMetaHostPolicy</span></span>|  
|<span data-ttu-id="33c3b-123">CLSID_CLRDebugging</span><span class="sxs-lookup"><span data-stu-id="33c3b-123">CLSID_CLRDebugging</span></span>|<span data-ttu-id="33c3b-124">IID_ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="33c3b-124">IID_ICLRDebugging</span></span>|  
  
 <span data-ttu-id="33c3b-125">次のコードは、使用する方法を示しています。`CLRCreateInstance`を 3 つすべてのインターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="33c3b-125">The following code shows how to use `CLRCreateInstance` to get all three interfaces:</span></span>  
  
```  
#include <metahost.h>  
#pragma comment(lib, "mscoree.lib")  
  
ICLRMetaHost       *pMetaHost       = NULL;  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
ICLRDebugging      *pCLRDebugging   = NULL;  
HRESULT hr;  
hr = CLRCreateInstance(CLSID_CLRMetaHost, IID_ICLRMetaHost,  
                    (LPVOID*)&pMetaHost);  
hr = CLRCreateInstance (CLSID_CLRMetaHostPolicy, IID_ICLRMetaHostPolicy,  
                    (LPVOID*)&pMetaHostPolicy);  
hr = CLRCreateInstance (CLSID_CLRDebugging, IID_ICLRDebugging,  
                    (LPVOID*)&pCLRDebugging);  
```  
  
## <a name="requirements"></a><span data-ttu-id="33c3b-126">必要条件</span><span class="sxs-lookup"><span data-stu-id="33c3b-126">Requirements</span></span>  
 <span data-ttu-id="33c3b-127">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="33c3b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33c3b-128">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="33c3b-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="33c3b-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="33c3b-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="33c3b-130">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33c3b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33c3b-131">参照</span><span class="sxs-lookup"><span data-stu-id="33c3b-131">See Also</span></span>  
 [<span data-ttu-id="33c3b-132">ホスティング</span><span class="sxs-lookup"><span data-stu-id="33c3b-132">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)

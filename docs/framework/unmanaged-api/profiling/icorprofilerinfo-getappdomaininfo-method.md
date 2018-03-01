---
title: "ICorProfilerInfo::GetAppDomainInfo メソッド"
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
- ICorProfilerInfo.GetAppDomainInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetAppDomainInfo
helpviewer_keywords:
- ICorProfilerInfo::GetAppDomainInfo method [.NET Framework profiling]
- GetAppDomainInfo method [.NET Framework profiling]
ms.assetid: a6bf5a04-e03e-44f0-917a-96f6a6d3cc96
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e9f7f4db595966293e87b5b115437df1bec56c00
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="9181d-102">ICorProfilerInfo::GetAppDomainInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="9181d-102">ICorProfilerInfo::GetAppDomainInfo Method</span></span>
<span data-ttu-id="9181d-103">アプリケーション ドメイン ID を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="9181d-103">Accepts an application domain ID.</span></span> <span data-ttu-id="9181d-104">アプリケーション ドメインの名前と、そのアプリケーション ドメインを含むプロセスの ID を返します。</span><span class="sxs-lookup"><span data-stu-id="9181d-104">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9181d-105">構文</span><span class="sxs-lookup"><span data-stu-id="9181d-105">Syntax</span></span>  
  
```  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9181d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9181d-106">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="9181d-107">[in] アプリケーション ドメインの ID。</span><span class="sxs-lookup"><span data-stu-id="9181d-107">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="9181d-108">[in] `szName` 戻りバッファーの長さ (文字単位)。</span><span class="sxs-lookup"><span data-stu-id="9181d-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="9181d-109">[out] アプリケーション ドメイン名の文字列長の合計へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9181d-109">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="9181d-110">[out] 呼び出し元が提供したワイド文字バッファー。</span><span class="sxs-lookup"><span data-stu-id="9181d-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="9181d-111">このメソッドから制御が戻ると、`szName` にはアプリケーション ドメイン名の全部または一部が格納されます。</span><span class="sxs-lookup"><span data-stu-id="9181d-111">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="9181d-112">[out] アプリケーション ドメインを含むプロセスの ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9181d-112">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9181d-113">コメント</span><span class="sxs-lookup"><span data-stu-id="9181d-113">Remarks</span></span>  
 <span data-ttu-id="9181d-114">このメソッドから制御が戻った後で、`szName` バッファーのサイズが十分で、アプリケーション ドメインの完全名を格納できたかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9181d-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="9181d-115">これを行うには、`pcchName` が指している値を `cchName` パラメーターの値と比較します。</span><span class="sxs-lookup"><span data-stu-id="9181d-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="9181d-116">`pcchName` が指している値が `cchName` の値より大きい場合は、`szName` バッファーの割り当てを増やし、`cchName` を新しい大きいサイズに更新して、`GetAppDomainInfo` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9181d-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="9181d-117">別の方法として、最初に長さ 0 の `szName` バッファーで `GetAppDomainInfo` を呼び出すことで、適切なバッファーのサイズを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="9181d-117">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="9181d-118">その後、バッファーのサイズを `pcchName` で返された値に設定し、`GetAppDomainInfo` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9181d-118">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9181d-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="9181d-119">Requirements</span></span>  
 <span data-ttu-id="9181d-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9181d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9181d-121">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9181d-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9181d-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9181d-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9181d-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9181d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9181d-124">参照</span><span class="sxs-lookup"><span data-stu-id="9181d-124">See Also</span></span>  
 [<span data-ttu-id="9181d-125">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9181d-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="9181d-126">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9181d-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="9181d-127">プロファイル</span><span class="sxs-lookup"><span data-stu-id="9181d-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)

---
title: "ICorProfilerInfo3::GetAppDomainsContainingModule メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetAppDomainsContainingModule Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetAppDomainsContainingModule
helpviewer_keywords:
- GetAppDomainsContainingModule method [.NET Framework profiling]
- ICorProfilerInfo3::GetAppDomainsContainingModule method [.NET Framework profiling]
ms.assetid: 603b3881-ea94-4dca-95cd-91eebac873a0
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ff9f63fc004d7249b571d980561171464e74b9a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="73e9d-102">ICorProfilerInfo3::GetAppDomainsContainingModule メソッド</span><span class="sxs-lookup"><span data-stu-id="73e9d-102">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>
<span data-ttu-id="73e9d-103">指定したモジュールが読み込まれているアプリケーション ドメインの識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="73e9d-103">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73e9d-104">構文</span><span class="sxs-lookup"><span data-stu-id="73e9d-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73e9d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="73e9d-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="73e9d-106">[in] 読み込まれたモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="73e9d-106">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="73e9d-107">[in] `appDomainIds` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="73e9d-107">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="73e9d-108">[out] 返される要素の総数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="73e9d-108">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="73e9d-109">[out] アプリケーション ドメイン ID 値の配列。</span><span class="sxs-lookup"><span data-stu-id="73e9d-109">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73e9d-110">コメント</span><span class="sxs-lookup"><span data-stu-id="73e9d-110">Remarks</span></span>  
 <span data-ttu-id="73e9d-111">このメソッドは、呼び出し元が割り当てたバッファーを使用します。</span><span class="sxs-lookup"><span data-stu-id="73e9d-111">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73e9d-112">要件</span><span class="sxs-lookup"><span data-stu-id="73e9d-112">Requirements</span></span>  
 <span data-ttu-id="73e9d-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="73e9d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73e9d-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="73e9d-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="73e9d-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73e9d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73e9d-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73e9d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73e9d-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="73e9d-117">See Also</span></span>  
 [<span data-ttu-id="73e9d-118">ICorProfilerFunctionEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="73e9d-118">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="73e9d-119">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="73e9d-119">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="73e9d-120">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="73e9d-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="73e9d-121">プロファイル</span><span class="sxs-lookup"><span data-stu-id="73e9d-121">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)

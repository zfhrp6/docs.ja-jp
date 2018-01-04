---
title: "ICorProfilerCallback::AssemblyUnloadStarted メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AssemblyUnloadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AssemblyUnloadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted method [.NET Framework profiling]
- AssemblyUnloadStarted method [.NET Framework profiling]
ms.assetid: 6e47b7e5-0335-4dd3-8c42-d3c07d62b102
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9984cff1d3c4013d66bc9eb7dbe5dbe7b61d2ba3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="ef26d-102">ICorProfilerCallback::AssemblyUnloadStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="ef26d-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="ef26d-103">アセンブリがアンロードされることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="ef26d-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef26d-104">構文</span><span class="sxs-lookup"><span data-stu-id="ef26d-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef26d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ef26d-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="ef26d-106">[in]モジュールはアンロードされているアセンブリを識別します。</span><span class="sxs-lookup"><span data-stu-id="ef26d-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef26d-107">コメント</span><span class="sxs-lookup"><span data-stu-id="ef26d-107">Remarks</span></span>  
 <span data-ttu-id="ef26d-108">値`assemblyId`後情報の要求に対して無効です、`AssemblyUnloadStarted`メソッドを返します。-これは、プロファイラーの最後のチャンスをこのアセンブリに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="ef26d-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef26d-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="ef26d-109">Requirements</span></span>  
 <span data-ttu-id="ef26d-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ef26d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef26d-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ef26d-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ef26d-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef26d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef26d-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef26d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef26d-114">参照</span><span class="sxs-lookup"><span data-stu-id="ef26d-114">See Also</span></span>  
 [<span data-ttu-id="ef26d-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ef26d-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="ef26d-116">AssemblyUnloadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="ef26d-116">AssemblyUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)

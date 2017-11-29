---
title: "ICorProfilerCallback::JITCachedFunctionSearchFinished メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITCachedFunctionSearchFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITCachedFunctionSearchFinished
helpviewer_keywords:
- JITCachedFunctionSearchFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchFinished method [.NET Framework profiling]
ms.assetid: 3c325c82-cddd-4b00-b3da-e450c36abf62
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ffbe331399334d179cf8325e7d9e6773b5bf7012
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a><span data-ttu-id="d8cba-102">ICorProfilerCallback::JITCachedFunctionSearchFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="d8cba-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Method</span></span>
<span data-ttu-id="d8cba-103">ネイティブ イメージ ジェネレーター (NGen.exe) を使用して以前にコンパイルされた関数の検索が完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="d8cba-103">Notifies the profiler that a search has finished for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8cba-104">構文</span><span class="sxs-lookup"><span data-stu-id="d8cba-104">Syntax</span></span>  
  
```  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8cba-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d8cba-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d8cba-106">[in]検索の実行対象の関数の ID。</span><span class="sxs-lookup"><span data-stu-id="d8cba-106">[in] The ID of the function for which the search was performed.</span></span>  
  
 `result`  
 <span data-ttu-id="d8cba-107">[in]値、 [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)検索の結果を示す列挙です。</span><span class="sxs-lookup"><span data-stu-id="d8cba-107">[in] A value of the [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) enumeration that indicates the result of the search.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8cba-108">コメント</span><span class="sxs-lookup"><span data-stu-id="d8cba-108">Remarks</span></span>  
 <span data-ttu-id="d8cba-109">.NET framework version 2.0 では、 [icorprofilercallback::jitcachedfunctionsearchstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md)と`JITCachedFunctionSearchFinished`正規の NGen イメージのすべての関数のコールバックは行われません。</span><span class="sxs-lookup"><span data-stu-id="d8cba-109">In the .NET Framework version 2.0, the [ICorProfilerCallback::JITCachedFunctionSearchStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) and `JITCachedFunctionSearchFinished` callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="d8cba-110">NGen イメージのみが、プロファイラーの最適化は、すべての関数のコールバックをイメージに生成されます。</span><span class="sxs-lookup"><span data-stu-id="d8cba-110">Only NGen images optimized for a profiler will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="d8cba-111">ただし、追加のオーバーヘッドにより、プロファイラー NGen イメージのプロファイラー最適化する必要があります要求した場合、関数のコンパイル済みジャストでタイム (JIT) を強制的にこれらのコールバックを使用する場合にのみにします。</span><span class="sxs-lookup"><span data-stu-id="d8cba-111">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="d8cba-112">それ以外の場合、プロファイラーは、関数の情報を収集するため、限定的な戦略を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8cba-112">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8cba-113">要件</span><span class="sxs-lookup"><span data-stu-id="d8cba-113">Requirements</span></span>  
 <span data-ttu-id="d8cba-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d8cba-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8cba-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d8cba-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d8cba-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8cba-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8cba-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8cba-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8cba-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="d8cba-118">See Also</span></span>  
 [<span data-ttu-id="d8cba-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d8cba-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)

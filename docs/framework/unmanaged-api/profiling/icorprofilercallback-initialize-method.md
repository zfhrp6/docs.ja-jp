---
title: ICorProfilerCallback::Initialize メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Initialize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Initialize
helpviewer_keywords:
- Initialize method, ICorProfilerCallback interface [.NET Framework profiling]
- ICorProfilerCallback::Initialize method [.NET Framework profiling]
ms.assetid: dc5fab2a-4b45-4b12-8727-b89c9915f23e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cd53d74dfe8199617df47e46641b71203abf6e5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452349"
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="9bc9b-102">ICorProfilerCallback::Initialize メソッド</span><span class="sxs-lookup"><span data-stu-id="9bc9b-102">ICorProfilerCallback::Initialize Method</span></span>
<span data-ttu-id="9bc9b-103">新しい共通言語ランタイム (CLR) アプリケーションを起動するたびにコード プロファイラーを初期化するために呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="9bc9b-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bc9b-104">構文</span><span class="sxs-lookup"><span data-stu-id="9bc9b-104">Syntax</span></span>  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9bc9b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9bc9b-105">Parameters</span></span>  
 `pICorProfilerInfoUnk`  
 <span data-ttu-id="9bc9b-106">[に](/cpp/atl/iunknown)インターフェイスのクエリを実行する必要があります、プロファイラーを[ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)インターフェイス ポインター。</span><span class="sxs-lookup"><span data-stu-id="9bc9b-106">[in](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bc9b-107">コメント</span><span class="sxs-lookup"><span data-stu-id="9bc9b-107">Remarks</span></span>  
 <span data-ttu-id="9bc9b-108">`Initialize`呼び出しは不変のコールバックを有効にする (または無効化) することです。</span><span class="sxs-lookup"><span data-stu-id="9bc9b-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="9bc9b-109">コールバックを有効にすると、`Initialize`を呼び出すと、それを無効にできませんを使用して後で[icorprofilerinfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="9bc9b-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="9bc9b-110">COR_PRF_MONITOR_IMMUTABLE 値、 [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列挙型では、イベントは変更を示します。</span><span class="sxs-lookup"><span data-stu-id="9bc9b-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bc9b-111">要件</span><span class="sxs-lookup"><span data-stu-id="9bc9b-111">Requirements</span></span>  
 <span data-ttu-id="9bc9b-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9bc9b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bc9b-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9bc9b-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9bc9b-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9bc9b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9bc9b-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bc9b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bc9b-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="9bc9b-116">See Also</span></span>  
 [<span data-ttu-id="9bc9b-117">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9bc9b-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="9bc9b-118">Shutdown メソッド</span><span class="sxs-lookup"><span data-stu-id="9bc9b-118">Shutdown Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)

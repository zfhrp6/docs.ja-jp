---
title: "ICorProfilerInfo5::GetEventMask2 メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorProfilerInfo5.GetEventMask2
api_location: mscorwks.dll
api_type: COM
ms.assetid: f854b68f-009c-4ffb-89cd-ca874d1c0fb7
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: da1c4c11adaac21e9769330ee24beceff64e020b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo5geteventmask2-method"></a><span data-ttu-id="91ea4-102">ICorProfilerInfo5::GetEventMask2 メソッド</span><span class="sxs-lookup"><span data-stu-id="91ea4-102">ICorProfilerInfo5::GetEventMask2 Method</span></span>
<span data-ttu-id="91ea4-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="91ea4-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="91ea4-104">現在のイベント カテゴリを取得します。プロファイラーは、これに関する通知を共通言語ランタイム (CLR) から受け取ります。</span><span class="sxs-lookup"><span data-stu-id="91ea4-104">Gets the current event categories for which the profiler wants to receive notifications from the common language runtime (CLR).</span></span>  <span data-ttu-id="91ea4-105">指定されていない機能を提供、 [icorprofilerinfo::geteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="91ea4-105">It provides functionality not provided by the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91ea4-106">構文</span><span class="sxs-lookup"><span data-stu-id="91ea4-106">Syntax</span></span>  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="91ea4-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="91ea4-107">Parameters</span></span>  
 `pdwEventsLow`  
 <span data-ttu-id="91ea4-108">[out] イベントのカテゴリを指定する 4 バイト値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="91ea4-108">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="91ea4-109">各ビットは、異なる性能、動作、またはイベントの型を制御します。</span><span class="sxs-lookup"><span data-stu-id="91ea4-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="91ea4-110">Bits が説明されている、 [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列挙します。</span><span class="sxs-lookup"><span data-stu-id="91ea4-110">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `pdwEventsHigh`  
 <span data-ttu-id="91ea4-111">[out] イベントのカテゴリを指定する 4 バイト値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="91ea4-111">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="91ea4-112">各ビットは、異なる性能、動作、またはイベントの型を制御します。</span><span class="sxs-lookup"><span data-stu-id="91ea4-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="91ea4-113">Bits が説明されている、 [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)列挙します。</span><span class="sxs-lookup"><span data-stu-id="91ea4-113">The bits are described in the [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91ea4-114">コメント</span><span class="sxs-lookup"><span data-stu-id="91ea4-114">Remarks</span></span>  
 <span data-ttu-id="91ea4-115">`GetEventMask2` メソッドは、プロファイラーがサブスクライブしたコールバックを判断するのに使用します。</span><span class="sxs-lookup"><span data-stu-id="91ea4-115">The `GetEventMask2` method is used to determine which callbacks the profiler has subscribed to.</span></span> <span data-ttu-id="91ea4-116">通常の論理 OR を実行、`pdwEventsLow`と`pdwEventsHigh`値と新しいビットを設定すると、したい、 [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="91ea4-116">Typically, you perform a logical OR of the `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
 <span data-ttu-id="91ea4-117">このメソッドは、推奨される代替、 [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="91ea4-117">This method is the recommended alternative to the [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91ea4-118">要件</span><span class="sxs-lookup"><span data-stu-id="91ea4-118">Requirements</span></span>  
 <span data-ttu-id="91ea4-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="91ea4-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91ea4-120">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="91ea4-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="91ea4-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91ea4-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91ea4-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91ea4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91ea4-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="91ea4-123">See Also</span></span>  
 [<span data-ttu-id="91ea4-124">ICorProfilerInfo5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="91ea4-124">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 [<span data-ttu-id="91ea4-125">SetEventMask2 メソッド</span><span class="sxs-lookup"><span data-stu-id="91ea4-125">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)

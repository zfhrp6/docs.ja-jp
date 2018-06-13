---
title: ICorProfilerInfo::GetEventMask メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetEventMask
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetEventMask
helpviewer_keywords:
- GetEventMask method [.NET Framework profiling]
- ICorProfilerInfo::GetEventMask method [.NET Framework profiling]
ms.assetid: ec34cc13-45a3-4695-abc3-b3347d4e6fc2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 481c4a08f7fc8beefe8f6026bcacd5146ffb4992
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454571"
---
# <a name="icorprofilerinfogeteventmask-method"></a><span data-ttu-id="a2d50-102">ICorProfilerInfo::GetEventMask メソッド</span><span class="sxs-lookup"><span data-stu-id="a2d50-102">ICorProfilerInfo::GetEventMask Method</span></span>
<span data-ttu-id="a2d50-103">現在のイベント カテゴリを取得します。プロファイラーは、これに関するイベント通知を共通言語ランタイム (CLR) から受け取ります。</span><span class="sxs-lookup"><span data-stu-id="a2d50-103">Gets the current event categories for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2d50-104">構文</span><span class="sxs-lookup"><span data-stu-id="a2d50-104">Syntax</span></span>  
  
```  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a2d50-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a2d50-105">Parameters</span></span>  
 `pdwEvents`  
 <span data-ttu-id="a2d50-106">[out] イベントのカテゴリを指定する 4 バイト値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a2d50-106">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="a2d50-107">各ビットは、異なる性能、動作、またはイベントの型を制御します。</span><span class="sxs-lookup"><span data-stu-id="a2d50-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="a2d50-108">Bits が説明されている、 [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列挙します。</span><span class="sxs-lookup"><span data-stu-id="a2d50-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2d50-109">コメント</span><span class="sxs-lookup"><span data-stu-id="a2d50-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2d50-110">呼び出す必要があります、 [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)このメソッドではなくメソッドです。</span><span class="sxs-lookup"><span data-stu-id="a2d50-110">You should call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="a2d50-111">ただし、`SetEventMask`メソッドは引き続きサポートされて[GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)追加機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="a2d50-111">Although the `SetEventMask` method continues to be supported, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2d50-112">要件</span><span class="sxs-lookup"><span data-stu-id="a2d50-112">Requirements</span></span>  
 <span data-ttu-id="a2d50-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a2d50-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2d50-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a2d50-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a2d50-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2d50-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2d50-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2d50-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2d50-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="a2d50-117">See Also</span></span>  
 [<span data-ttu-id="a2d50-118">GetEventMask2 メソッド</span><span class="sxs-lookup"><span data-stu-id="a2d50-118">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)  
 [<span data-ttu-id="a2d50-119">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a2d50-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

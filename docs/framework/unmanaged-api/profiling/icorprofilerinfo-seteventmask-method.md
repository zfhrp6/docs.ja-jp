---
title: "ICorProfilerInfo::SetEventMask メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.SetEventMask
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::SetEventMask
helpviewer_keywords:
- ICorProfilerInfo::SetEventMask method [.NET Framework profiling]
- SetEventMask method [.NET Framework profiling]
ms.assetid: 44bc0f56-32fa-491e-a62d-52fc96d48125
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bb42be7f8e5722ec9924284c257e814a186564d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfoseteventmask-method"></a><span data-ttu-id="17d17-102">ICorProfilerInfo::SetEventMask メソッド</span><span class="sxs-lookup"><span data-stu-id="17d17-102">ICorProfilerInfo::SetEventMask Method</span></span>
<span data-ttu-id="17d17-103">共通言語ランタイム (CLR) からの通知を受け取るプロファイラーに対するイベントの種類を指定する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="17d17-103">Sets a value that specifies the types of events for which the profiler wants to receive notification from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17d17-104">構文</span><span class="sxs-lookup"><span data-stu-id="17d17-104">Syntax</span></span>  
  
```  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="17d17-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="17d17-105">Parameters</span></span>  
 `dwEvents`  
 <span data-ttu-id="17d17-106">[in] イベントのカテゴリを指定する 4 バイトの値。</span><span class="sxs-lookup"><span data-stu-id="17d17-106">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="17d17-107">各ビットは、異なる性能、動作、またはイベントの型を制御します。</span><span class="sxs-lookup"><span data-stu-id="17d17-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="17d17-108">Bits が説明されている、 [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列挙します。</span><span class="sxs-lookup"><span data-stu-id="17d17-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17d17-109">コメント</span><span class="sxs-lookup"><span data-stu-id="17d17-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17d17-110">呼び出す必要があります、 [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)このメソッドではなくメソッドです。</span><span class="sxs-lookup"><span data-stu-id="17d17-110">You should call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="17d17-111">ただし、`SetEventMask`メソッドは引き続きサポートされて[SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)追加機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="17d17-111">Although the `SetEventMask` method continues to be supported, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17d17-112">要件</span><span class="sxs-lookup"><span data-stu-id="17d17-112">Requirements</span></span>  
 <span data-ttu-id="17d17-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="17d17-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17d17-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="17d17-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="17d17-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17d17-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17d17-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17d17-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17d17-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="17d17-117">See Also</span></span>  
 [<span data-ttu-id="17d17-118">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="17d17-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="17d17-119">SetEventMask2 メソッド</span><span class="sxs-lookup"><span data-stu-id="17d17-119">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)

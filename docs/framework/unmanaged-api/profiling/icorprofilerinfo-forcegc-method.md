---
title: "ICorProfilerInfo::ForceGC メソッド"
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
- ICorProfilerInfo.ForceGC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::ForceGC
helpviewer_keywords:
- ICorProfilerInfo::ForceGC method [.NET Framework profiling]
- ForceGC method [.NET Framework profiling]
ms.assetid: 0da1ef80-d242-4636-87d0-43e0470b342a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 89e0e9534b5e074e5a22ceaec4e04467f752281e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="3a25c-102">ICorProfilerInfo::ForceGC メソッド</span><span class="sxs-lookup"><span data-stu-id="3a25c-102">ICorProfilerInfo::ForceGC Method</span></span>
<span data-ttu-id="3a25c-103">強制的にガベージ コレクションに共通言語ランタイム (CLR) 内で発生します。</span><span class="sxs-lookup"><span data-stu-id="3a25c-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a25c-104">構文</span><span class="sxs-lookup"><span data-stu-id="3a25c-104">Syntax</span></span>  
  
```  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="3a25c-105">コメント</span><span class="sxs-lookup"><span data-stu-id="3a25c-105">Remarks</span></span>  
 <span data-ttu-id="3a25c-106">`ForceGC`メソッドは、マネージ コードが一度も実行し、そのスタックのプロファイラー コールバックを持たないスレッドからのみ呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a25c-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="3a25c-107">呼び出して、プロファイラー内で別のスレッドを作成する最も便利な実装は、`ForceGC`シグナルを受け取るとします。</span><span class="sxs-lookup"><span data-stu-id="3a25c-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a25c-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="3a25c-108">Requirements</span></span>  
 <span data-ttu-id="3a25c-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3a25c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a25c-110">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3a25c-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3a25c-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a25c-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a25c-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a25c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a25c-113">参照</span><span class="sxs-lookup"><span data-stu-id="3a25c-113">See Also</span></span>  
 [<span data-ttu-id="3a25c-114">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a25c-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

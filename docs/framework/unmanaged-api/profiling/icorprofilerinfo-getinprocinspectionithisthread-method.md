---
title: ICorProfilerInfo::GetInprocInspectionIThisThread メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionIThisThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread
helpviewer_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread method [.NET Framework profiling]
- GetInprocInspectionIThisThread method [.NET Framework profiling]
ms.assetid: badddccd-f85c-416e-9f0f-419eab2c9d42
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d603d9bc7a343a41224cf8d889a69823875d9db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a><span data-ttu-id="486f0-102">ICorProfilerInfo::GetInprocInspectionIThisThread メソッド</span><span class="sxs-lookup"><span data-stu-id="486f0-102">ICorProfilerInfo::GetInprocInspectionIThisThread Method</span></span>
<span data-ttu-id="486f0-103">ICorDebugThread インターフェイスの照会されるオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="486f0-103">Gets an object that can be queried for the ICorDebugThread interface.</span></span> <span data-ttu-id="486f0-104">このメソッドは、.NET Framework version 2.0 廃止されています。</span><span class="sxs-lookup"><span data-stu-id="486f0-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="486f0-105">構文</span><span class="sxs-lookup"><span data-stu-id="486f0-105">Syntax</span></span>  
  
```  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="486f0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="486f0-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="486f0-107">[out](/cpp/atl/iunknown)のクエリ可能なオブジェクト、`ICorDebugThread`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="486f0-107">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="486f0-108">コメント</span><span class="sxs-lookup"><span data-stu-id="486f0-108">Remarks</span></span>  
 <span data-ttu-id="486f0-109">デバッグ サービスを共通言語ランタイム (CLR) では、プロセスで、.NET Framework version 1.0 でデバッグを制限をサポートします。</span><span class="sxs-lookup"><span data-stu-id="486f0-109">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="486f0-110">プロセスのデバッグには、プロファイラーは、デバッグ API の検査部分の使用が有効になります。</span><span class="sxs-lookup"><span data-stu-id="486f0-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="486f0-111">カスタマー フィードバックの結果として、インプロセスのデバッグがバージョン 2.0、.NET Framework から削除されに沿ってプロファイル API は、機能のセットに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="486f0-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="486f0-112">要件</span><span class="sxs-lookup"><span data-stu-id="486f0-112">Requirements</span></span>  
 <span data-ttu-id="486f0-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="486f0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="486f0-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="486f0-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="486f0-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="486f0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="486f0-116">**.NET framework のバージョン:** 1.0</span><span class="sxs-lookup"><span data-stu-id="486f0-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="486f0-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="486f0-117">See Also</span></span>  
 [<span data-ttu-id="486f0-118">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="486f0-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

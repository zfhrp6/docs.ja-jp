---
title: "ICorProfilerInfo::GetInprocInspectionInterface メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetInprocInspectionInterface
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetInprocInspectionInterface
helpviewer_keywords:
- GetInprocInspectionInterface method [.NET Framework profiling]
- ICorProfilerInfo::GetInprocInspectionInterface method [.NET Framework profiling]
ms.assetid: 22a92d1d-8849-4af6-8304-ecc53dd1d289
topic_type: apiref
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9088389df33b079fe2275f5c7e642a055fa8ee51
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="49611-102">ICorProfilerInfo::GetInprocInspectionInterface メソッド</span><span class="sxs-lookup"><span data-stu-id="49611-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>
<span data-ttu-id="49611-103">"ICorDebugProcess"インターフェイスの照会されるオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="49611-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="49611-104">このメソッドは、.NET Framework version 2.0 廃止されています。</span><span class="sxs-lookup"><span data-stu-id="49611-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49611-105">構文</span><span class="sxs-lookup"><span data-stu-id="49611-105">Syntax</span></span>  
  
```  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="49611-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="49611-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="49611-107">[out](/cpp/atl/iunknown)のクエリ可能なオブジェクト、`ICorDebugProcess`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="49611-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49611-108">コメント</span><span class="sxs-lookup"><span data-stu-id="49611-108">Remarks</span></span>  
 <span data-ttu-id="49611-109">デバッグ API 共通言語ランタイム (CLR) では、プロセスで、.NET Framework version 1.0 でデバッグを制限をサポートします。</span><span class="sxs-lookup"><span data-stu-id="49611-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="49611-110">プロセスのデバッグには、プロファイラーは、デバッグ API の検査部分の使用が有効になります。</span><span class="sxs-lookup"><span data-stu-id="49611-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="49611-111">カスタマー フィードバックの結果として、インプロセスのデバッグがバージョン 2.0、.NET Framework から削除されに沿ってプロファイル API は、機能のセットに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="49611-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49611-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="49611-112">Requirements</span></span>  
 <span data-ttu-id="49611-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="49611-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49611-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="49611-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="49611-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49611-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49611-116">**.NET framework のバージョン:** 1.0</span><span class="sxs-lookup"><span data-stu-id="49611-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49611-117">参照</span><span class="sxs-lookup"><span data-stu-id="49611-117">See Also</span></span>  
 [<span data-ttu-id="49611-118">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="49611-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

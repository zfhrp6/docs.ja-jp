---
title: ICorProfilerCallback::AssemblyLoadStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadStarted method [.NET Framework profiling]
- AssemblyLoadStarted method [.NET Framework profiling]
ms.assetid: 67e8209d-a0ca-4118-a6e6-c1ee0abc2221
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: af40d8b603d3bd13abbc5a1c06464583bfa7842d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450220"
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="e62d4-102">ICorProfilerCallback::AssemblyLoadStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="e62d4-102">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>
<span data-ttu-id="e62d4-103">アセンブリが読み込まれていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e62d4-103">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e62d4-104">構文</span><span class="sxs-lookup"><span data-stu-id="e62d4-104">Syntax</span></span>  
  
```  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e62d4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e62d4-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="e62d4-106">[in]読み込まれているアセンブリを識別します。</span><span class="sxs-lookup"><span data-stu-id="e62d4-106">[in] Identifies the assembly that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e62d4-107">コメント</span><span class="sxs-lookup"><span data-stu-id="e62d4-107">Remarks</span></span>  
 <span data-ttu-id="e62d4-108">値`assemblyId`まで情報の要求に対して無効です、 [icorprofilercallback::assemblyloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md)メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e62d4-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e62d4-109">要件</span><span class="sxs-lookup"><span data-stu-id="e62d4-109">Requirements</span></span>  
 <span data-ttu-id="e62d4-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e62d4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e62d4-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e62d4-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e62d4-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e62d4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e62d4-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e62d4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e62d4-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="e62d4-114">See Also</span></span>  
 [<span data-ttu-id="e62d4-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e62d4-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)

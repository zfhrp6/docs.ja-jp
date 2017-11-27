---
title: "ICorProfilerCallback::AssemblyLoadStarted メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AssemblyLoadStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AssemblyLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadStarted method [.NET Framework profiling]
- AssemblyLoadStarted method [.NET Framework profiling]
ms.assetid: 67e8209d-a0ca-4118-a6e6-c1ee0abc2221
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 654cc5fb445184bd07d145701898239bee3e9c8b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="f9352-102">ICorProfilerCallback::AssemblyLoadStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="f9352-102">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>
<span data-ttu-id="f9352-103">アセンブリが読み込まれていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="f9352-103">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9352-104">構文</span><span class="sxs-lookup"><span data-stu-id="f9352-104">Syntax</span></span>  
  
```  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9352-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f9352-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="f9352-106">[in]読み込まれているアセンブリを識別します。</span><span class="sxs-lookup"><span data-stu-id="f9352-106">[in] Identifies the assembly that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9352-107">コメント</span><span class="sxs-lookup"><span data-stu-id="f9352-107">Remarks</span></span>  
 <span data-ttu-id="f9352-108">値`assemblyId`まで情報の要求に対して無効です、 [icorprofilercallback::assemblyloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md)メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f9352-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9352-109">要件</span><span class="sxs-lookup"><span data-stu-id="f9352-109">Requirements</span></span>  
 <span data-ttu-id="f9352-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f9352-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9352-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f9352-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f9352-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9352-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9352-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9352-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9352-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9352-114">See Also</span></span>  
 [<span data-ttu-id="f9352-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9352-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)

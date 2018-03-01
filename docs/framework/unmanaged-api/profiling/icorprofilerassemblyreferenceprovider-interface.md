---
title: "ICorProfilerAssemblyReferenceProvider インターフェイス"
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
- ICorProfilerAssemblyReferenceProvider
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 17205116-66e1-4acc-8f01-532fb3867028
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 203362d2780d372236b05f753bedc0d59565d2b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a><span data-ttu-id="93080-102">ICorProfilerAssemblyReferenceProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="93080-102">ICorProfilerAssemblyReferenceProvider Interface</span></span>
<span data-ttu-id="93080-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="93080-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="93080-104">により、プロファイラーのプロファイラーを追加するアセンブリ参照の共通言語ランタイム (CLR) を通知するために、 [icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="93080-104">Enables the profiler to inform the common language runtime (CLR) of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93080-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="93080-105">Methods</span></span>  
  
|<span data-ttu-id="93080-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="93080-106">Method</span></span>|<span data-ttu-id="93080-107">説明</span><span class="sxs-lookup"><span data-stu-id="93080-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93080-108">AddAssemblyReference メソッド</span><span class="sxs-lookup"><span data-stu-id="93080-108">AddAssemblyReference Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|<span data-ttu-id="93080-109">プロファイラーを計画に追加するアセンブリ参照の CLR に通知、 [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="93080-109">Informs the CLR of an assembly reference that the profiler plans to add in the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93080-110">コメント</span><span class="sxs-lookup"><span data-stu-id="93080-110">Remarks</span></span>  
 <span data-ttu-id="93080-111">CLR はプロファイラーを渡す、`ICorProfilerAssemblyReferenceProvider`インターフェイス オブジェクトを[icorprofilercallback 6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="93080-111">The CLR passes the profiler an `ICorProfilerAssemblyReferenceProvider` interface object in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="93080-112">これにより、プロファイラーが後で追加する予定のあるアセンブリ参照の CLR を通知するために、プロファイラー、 [icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="93080-112">This enables the profiler to inform the CLR of assembly references that the profiler plans to add later in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).</span></span> <span data-ttu-id="93080-113">コールバック。</span><span class="sxs-lookup"><span data-stu-id="93080-113">callback.</span></span> <span data-ttu-id="93080-114">これにより、CLR のアセンブリ参照クロージャ ウォーカーの正確性とアセンブリが共有可能かどうかを判断するアルゴリズムが強化されます。</span><span class="sxs-lookup"><span data-stu-id="93080-114">This improves the accuracy of the CLR's assembly reference closure walker and its algorithms for determining whether assemblies may be shared.</span></span>  
  
 <span data-ttu-id="93080-115">このインターフェイスでのみ使用できます、 [icorprofilercallback 6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)このインターフェイス オブジェクトをプロファイラーに渡されるコールバック。</span><span class="sxs-lookup"><span data-stu-id="93080-115">This interface can be used only in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback that passes this interface object to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93080-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="93080-116">Requirements</span></span>  
 <span data-ttu-id="93080-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="93080-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93080-118">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="93080-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="93080-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93080-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93080-120">参照</span><span class="sxs-lookup"><span data-stu-id="93080-120">See Also</span></span>  
 [<span data-ttu-id="93080-121">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="93080-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)

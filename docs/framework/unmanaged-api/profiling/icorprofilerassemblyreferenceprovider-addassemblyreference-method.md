---
title: ICorProfilerAssemblyReferenceProvider::AddAssemblyReference メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerAssemblyReferenceProvider.AddAssemblyReference
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 3d5af8e7-c337-48f4-9fa6-97c83878b9b1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 33430db8f83f446bab21b1fc86a5c165aecef2af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452365"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a><span data-ttu-id="9ec6e-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference メソッド</span><span class="sxs-lookup"><span data-stu-id="9ec6e-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Method</span></span>
<span data-ttu-id="9ec6e-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="9ec6e-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="9ec6e-104">プロファイラーを計画に追加するアセンブリ参照の共通言語ランタイム (CLR) の通知、 [icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="9ec6e-104">Informs the common language runtime (CLR) of an assembly reference that the profiler plans to add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ec6e-105">構文</span><span class="sxs-lookup"><span data-stu-id="9ec6e-105">Syntax</span></span>  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ec6e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ec6e-106">Parameters</span></span>  
 <span data-ttu-id="9ec6e-107">pAssemblyRefInfo</span><span class="sxs-lookup"><span data-stu-id="9ec6e-107">pAssemblyRefInfo</span></span>  
 <span data-ttu-id="9ec6e-108">ポインター、 [COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) CLR をアセンブリ参照クロージャのウォークを実行するときに考慮するべきであるアセンブリ参照に関する情報を提供する構造体。</span><span class="sxs-lookup"><span data-stu-id="9ec6e-108">A pointer to a [COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) structure that provides the CLR with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ec6e-109">コメント</span><span class="sxs-lookup"><span data-stu-id="9ec6e-109">Remarks</span></span>  
 <span data-ttu-id="9ec6e-110">プロファイラーがで指定されたアセンブリから参照される対象アセンブリごとにこのメソッドを呼び出して、`wszAssemblyPath`の引数、 [icorprofilercallback 6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="9ec6e-110">The profiler calls this method for each target assembly it plans to reference from the assembly specified in the `wszAssemblyPath` argument of the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="9ec6e-111">[ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)プロファイラーのインターフェイスのオブジェクトが渡される[icorprofilercallback 6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)アセンブリのパスと名前と一緒に、コールバック、`wszAssemblyPath`引数。</span><span class="sxs-lookup"><span data-stu-id="9ec6e-111">The [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object is passed to the profiler's [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback, along with the assembly path and name in the `wszAssemblyPath` argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ec6e-112">要件</span><span class="sxs-lookup"><span data-stu-id="9ec6e-112">Requirements</span></span>  
 <span data-ttu-id="9ec6e-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ec6e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ec6e-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9ec6e-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9ec6e-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ec6e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ec6e-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ec6e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ec6e-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ec6e-117">See Also</span></span>  
 [<span data-ttu-id="9ec6e-118">ICorProfilerAssemblyReferenceProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ec6e-118">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 [<span data-ttu-id="9ec6e-119">GetAssemblyReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="9ec6e-119">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)  
 [<span data-ttu-id="9ec6e-120">ModuleLoadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="9ec6e-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)

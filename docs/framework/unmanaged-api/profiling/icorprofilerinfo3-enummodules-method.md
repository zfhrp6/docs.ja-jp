---
title: "ICorProfilerInfo3::EnumModules メソッド"
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
- ICorProfilerInfo3.EnumModules Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumModules
helpviewer_keywords:
- ICorProfilerInfo3::EnumModules method [.NET Framework profiling]
- EnumModules method [.NET Framework profiling]
ms.assetid: 1bf00b42-69da-4019-91b3-bf88026e83fb
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0215662439672aecc787530ceb68d16cc58bcc3f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3enummodules-method"></a><span data-ttu-id="d342d-102">ICorProfilerInfo3::EnumModules メソッド</span><span class="sxs-lookup"><span data-stu-id="d342d-102">ICorProfilerInfo3::EnumModules Method</span></span>
<span data-ttu-id="d342d-103">アプリケーションに読み込まれるマネージ モジュールのコレクションを順番に反復処理するメソッドを提供する列挙子を返します。</span><span class="sxs-lookup"><span data-stu-id="d342d-103">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d342d-104">構文</span><span class="sxs-lookup"><span data-stu-id="d342d-104">Syntax</span></span>  
  
```  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d342d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d342d-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="d342d-106">[out]ポインター、 [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="d342d-106">[out] A pointer to an [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d342d-107">コメント</span><span class="sxs-lookup"><span data-stu-id="d342d-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d342d-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="d342d-108">Requirements</span></span>  
 <span data-ttu-id="d342d-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d342d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d342d-110">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d342d-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d342d-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d342d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d342d-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d342d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d342d-113">参照</span><span class="sxs-lookup"><span data-stu-id="d342d-113">See Also</span></span>  
 [<span data-ttu-id="d342d-114">ICorProfilerFunctionEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d342d-114">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="d342d-115">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d342d-115">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="d342d-116">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d342d-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="d342d-117">プロファイル</span><span class="sxs-lookup"><span data-stu-id="d342d-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)

---
title: "ICorProfilerFunctionEnum::Clone メソッド"
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
- ICorProfilerFunctionEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Clone
helpviewer_keywords:
- ICorProfilerFunctionEnum::Clone method [.NET Framework profiling]
- Clone method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0c3d4835-e111-4e82-af6d-53f140b8f2c9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 449292d8bacd6bb965119da81671c739f12dc3a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="bdd51-102">ICorProfilerFunctionEnum::Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="bdd51-102">ICorProfilerFunctionEnum::Clone Method</span></span>
<span data-ttu-id="bdd51-103">これのコピーに対するインターフェイス ポインターを取得[ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="bdd51-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdd51-104">構文</span><span class="sxs-lookup"><span data-stu-id="bdd51-104">Syntax</span></span>  
  
```  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bdd51-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bdd51-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="bdd51-106">[out]さらに、このコピーをポイントするインターフェイス ポインターへのポインター [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="bdd51-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="bdd51-107">列挙子のコピーには、この列挙子から個別に独自の列挙状態が保持されます。</span><span class="sxs-lookup"><span data-stu-id="bdd51-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="bdd51-108">ただし、そのコピーの最初のカーソル位置は、この列挙子の現在のカーソル位置と同じです。</span><span class="sxs-lookup"><span data-stu-id="bdd51-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdd51-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="bdd51-109">Requirements</span></span>  
 <span data-ttu-id="bdd51-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bdd51-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdd51-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bdd51-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bdd51-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdd51-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdd51-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdd51-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdd51-114">参照</span><span class="sxs-lookup"><span data-stu-id="bdd51-114">See Also</span></span>  
 [<span data-ttu-id="bdd51-115">ICorProfilerFunctionEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bdd51-115">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="bdd51-116">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="bdd51-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)

---
title: "ICorProfilerModuleEnum::Clone メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerModuleEnum.Clone Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerModuleEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Clone method [.NET Framework profiling]
ms.assetid: 7dec7e36-8d88-416d-b437-abf98b76c1df
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bf6e700ea4a6c5981c83b6d5ac2c2358fb24eb5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilermoduleenumclone-method"></a><span data-ttu-id="46926-102">ICorProfilerModuleEnum::Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="46926-102">ICorProfilerModuleEnum::Clone Method</span></span>
<span data-ttu-id="46926-103">これのコピーに対するインターフェイス ポインターを取得[ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="46926-103">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46926-104">構文</span><span class="sxs-lookup"><span data-stu-id="46926-104">Syntax</span></span>  
  
```  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="46926-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="46926-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="46926-106">[out]さらに、このコピーを指すインターフェイス ポインターへのポインター [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="46926-106">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span> <span data-ttu-id="46926-107">列挙子のコピーには、この列挙子から個別に独自の列挙状態が保持されます。</span><span class="sxs-lookup"><span data-stu-id="46926-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="46926-108">ただし、そのコピーの最初のカーソル位置は、この列挙子の現在のカーソル位置と同じです。</span><span class="sxs-lookup"><span data-stu-id="46926-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46926-109">要件</span><span class="sxs-lookup"><span data-stu-id="46926-109">Requirements</span></span>  
 <span data-ttu-id="46926-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="46926-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46926-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="46926-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="46926-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46926-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46926-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46926-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46926-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="46926-114">See Also</span></span>  
 [<span data-ttu-id="46926-115">ICorProfilerModuleEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="46926-115">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [<span data-ttu-id="46926-116">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="46926-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)

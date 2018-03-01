---
title: "ICorProfilerModuleEnum::GetCount メソッド"
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
- ICorProfilerModuleEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::GetCount
helpviewer_keywords:
- ICorProfilerModuleEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: f0a4a5e0-4689-474b-b0f4-37ca0639c918
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 62cc7122e25d43998053f0f102e1079252d4d7ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilermoduleenumgetcount-method"></a><span data-ttu-id="5dabd-102">ICorProfilerModuleEnum::GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="5dabd-102">ICorProfilerModuleEnum::GetCount Method</span></span>
<span data-ttu-id="5dabd-103">アプリケーションによって読み込まれたマネージ モジュールの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="5dabd-103">Gets the number of managed modules that were loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dabd-104">構文</span><span class="sxs-lookup"><span data-stu-id="5dabd-104">Syntax</span></span>  
  
```  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5dabd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5dabd-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="5dabd-106">[out]コレクション内のランタイム モジュールの数。</span><span class="sxs-lookup"><span data-stu-id="5dabd-106">[out] The number of runtime modules in the collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dabd-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="5dabd-107">Requirements</span></span>  
 <span data-ttu-id="5dabd-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5dabd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5dabd-109">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5dabd-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5dabd-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5dabd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5dabd-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5dabd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dabd-112">参照</span><span class="sxs-lookup"><span data-stu-id="5dabd-112">See Also</span></span>  
 [<span data-ttu-id="5dabd-113">ICorProfilerModuleEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5dabd-113">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [<span data-ttu-id="5dabd-114">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="5dabd-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)

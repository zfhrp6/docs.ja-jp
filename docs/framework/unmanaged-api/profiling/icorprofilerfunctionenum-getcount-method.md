---
title: ICorProfilerFunctionEnum::GetCount メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::GetCount
helpviewer_keywords:
- ICorProfilerFunctionEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 62ec65e3-3e9d-400b-ae61-d24b8963995b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 413b860353d3a9e75771f9349ebf151d8f2e3579
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453296"
---
# <a name="icorprofilerfunctionenumgetcount-method"></a><span data-ttu-id="5c6a2-102">ICorProfilerFunctionEnum::GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="5c6a2-102">ICorProfilerFunctionEnum::GetCount Method</span></span>
<span data-ttu-id="5c6a2-103">アプリケーションによって読み込まれたか、またはプロファイラーによって強制的に読み込まれた関数の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="5c6a2-103">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c6a2-104">構文</span><span class="sxs-lookup"><span data-stu-id="5c6a2-104">Syntax</span></span>  
  
```  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c6a2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5c6a2-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="5c6a2-106">[out]読み込まれた関数の数。</span><span class="sxs-lookup"><span data-stu-id="5c6a2-106">[out] The number of functions that were loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c6a2-107">要件</span><span class="sxs-lookup"><span data-stu-id="5c6a2-107">Requirements</span></span>  
 <span data-ttu-id="5c6a2-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5c6a2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c6a2-109">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5c6a2-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5c6a2-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c6a2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c6a2-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c6a2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c6a2-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c6a2-112">See Also</span></span>  
 [<span data-ttu-id="5c6a2-113">ICorProfilerFunctionEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c6a2-113">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="5c6a2-114">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c6a2-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)

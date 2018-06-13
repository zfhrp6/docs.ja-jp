---
title: ICorProfilerModuleEnum::GetCount メソッド
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 91572887713216f94707e5d21e5767f4cc54e0d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456259"
---
# <a name="icorprofilermoduleenumgetcount-method"></a><span data-ttu-id="b8eb0-102">ICorProfilerModuleEnum::GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="b8eb0-102">ICorProfilerModuleEnum::GetCount Method</span></span>
<span data-ttu-id="b8eb0-103">アプリケーションによって読み込まれたマネージ モジュールの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="b8eb0-103">Gets the number of managed modules that were loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8eb0-104">構文</span><span class="sxs-lookup"><span data-stu-id="b8eb0-104">Syntax</span></span>  
  
```  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b8eb0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b8eb0-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="b8eb0-106">[out]コレクション内のランタイム モジュールの数。</span><span class="sxs-lookup"><span data-stu-id="b8eb0-106">[out] The number of runtime modules in the collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8eb0-107">要件</span><span class="sxs-lookup"><span data-stu-id="b8eb0-107">Requirements</span></span>  
 <span data-ttu-id="b8eb0-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b8eb0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8eb0-109">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b8eb0-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b8eb0-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8eb0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8eb0-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8eb0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8eb0-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8eb0-112">See Also</span></span>  
 [<span data-ttu-id="b8eb0-113">ICorProfilerModuleEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8eb0-113">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [<span data-ttu-id="b8eb0-114">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8eb0-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)

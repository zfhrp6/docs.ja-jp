---
title: ICorProfilerInfo4::EnumThreads メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumThreads
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumThreads
helpviewer_keywords:
- ICorProfilerInfo4::EnumThreads method [.NET Framework profiling]
- EnumThreads method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: bca7a5b4-c207-4894-918c-0733926296dd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6c394690f6c8d7f3618b385b0a1432fc396fb819
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458021"
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="e9718-102">ICorProfilerInfo4::EnumThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="e9718-102">ICorProfilerInfo4::EnumThreads Method</span></span>
<span data-ttu-id="e9718-103">プロファイリングされたプロセスのすべてのマネージ スレッドのコレクションを順番に反復処理するメソッドを提供する列挙子を返します。</span><span class="sxs-lookup"><span data-stu-id="e9718-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9718-104">構文</span><span class="sxs-lookup"><span data-stu-id="e9718-104">Syntax</span></span>  
  
```  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9718-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e9718-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="e9718-106">[out]ポインター、 [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="e9718-106">[out] A pointer to an [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9718-107">コメント</span><span class="sxs-lookup"><span data-stu-id="e9718-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9718-108">要件</span><span class="sxs-lookup"><span data-stu-id="e9718-108">Requirements</span></span>  
 <span data-ttu-id="e9718-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e9718-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9718-110">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e9718-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e9718-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9718-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9718-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9718-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9718-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="e9718-113">See Also</span></span>  
 [<span data-ttu-id="e9718-114">ICorProfilerThreadEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e9718-114">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="e9718-115">ICorProfilerInfo4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e9718-115">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="e9718-116">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="e9718-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="e9718-117">プロファイル</span><span class="sxs-lookup"><span data-stu-id="e9718-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)

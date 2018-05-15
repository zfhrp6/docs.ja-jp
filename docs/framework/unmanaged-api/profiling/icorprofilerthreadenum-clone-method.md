---
title: ICorProfilerThreadEnum::Clone メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Clone method [.NET Framework profiling]
ms.assetid: 5a278bc9-88e2-4c69-b035-9d550dd77081
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84a71ac3a1ba30e20bb6ec7e6a0e31db9d3b5738
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerthreadenumclone-method"></a><span data-ttu-id="94341-102">ICorProfilerThreadEnum::Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="94341-102">ICorProfilerThreadEnum::Clone Method</span></span>
<span data-ttu-id="94341-103">これのコピーに対するインターフェイス ポインターを取得[ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="94341-103">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94341-104">構文</span><span class="sxs-lookup"><span data-stu-id="94341-104">Syntax</span></span>  
  
```  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="94341-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="94341-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="94341-106">[out]さらに、このコピーをポイントするインターフェイス ポインターへのポインター [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="94341-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span> <span data-ttu-id="94341-107">列挙子のコピーには、この列挙子から個別に独自の列挙状態が保持されます。</span><span class="sxs-lookup"><span data-stu-id="94341-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="94341-108">ただし、コピーの最初のカーソル位置は、この列挙子の現在のカーソル位置と同じです。</span><span class="sxs-lookup"><span data-stu-id="94341-108">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94341-109">要件</span><span class="sxs-lookup"><span data-stu-id="94341-109">Requirements</span></span>  
 <span data-ttu-id="94341-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="94341-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94341-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="94341-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="94341-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94341-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94341-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94341-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94341-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="94341-114">See Also</span></span>  
 [<span data-ttu-id="94341-115">ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="94341-115">ICorProfilerThreadEnum</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="94341-116">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="94341-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)

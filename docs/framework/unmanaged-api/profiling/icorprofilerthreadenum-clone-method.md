---
title: "ICorProfilerThreadEnum::Clone メソッド"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d40ef6a9a666f06a46713c6295167cf5e0798ce5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerthreadenumclone-method"></a><span data-ttu-id="069bc-102">ICorProfilerThreadEnum::Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="069bc-102">ICorProfilerThreadEnum::Clone Method</span></span>
<span data-ttu-id="069bc-103">これのコピーに対するインターフェイス ポインターを取得[ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="069bc-103">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="069bc-104">構文</span><span class="sxs-lookup"><span data-stu-id="069bc-104">Syntax</span></span>  
  
```  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="069bc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="069bc-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="069bc-106">[out]さらに、このコピーをポイントするインターフェイス ポインターへのポインター [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="069bc-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span> <span data-ttu-id="069bc-107">列挙子のコピーには、この列挙子から個別に独自の列挙状態が保持されます。</span><span class="sxs-lookup"><span data-stu-id="069bc-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="069bc-108">ただし、コピーの最初のカーソル位置は、この列挙子の現在のカーソル位置と同じです。</span><span class="sxs-lookup"><span data-stu-id="069bc-108">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="069bc-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="069bc-109">Requirements</span></span>  
 <span data-ttu-id="069bc-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="069bc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="069bc-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="069bc-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="069bc-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="069bc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="069bc-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="069bc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="069bc-114">参照</span><span class="sxs-lookup"><span data-stu-id="069bc-114">See Also</span></span>  
 [<span data-ttu-id="069bc-115">ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="069bc-115">ICorProfilerThreadEnum</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="069bc-116">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="069bc-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)

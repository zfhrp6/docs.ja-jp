---
title: "ICorProfilerModuleEnum::Skip メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerModuleEnum.Skip Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerModuleEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Skip method [.NET Framework profiling]
ms.assetid: 8dc29c6a-e2ba-41d8-a1e0-0fdd21421e0b
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cb6d12af329b214c78866ea352d1817afe0fa718
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilermoduleenumskip-method"></a><span data-ttu-id="7e440-102">ICorProfilerModuleEnum::Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="7e440-102">ICorProfilerModuleEnum::Skip Method</span></span>
<span data-ttu-id="7e440-103">指定した数の要素がスキップされるように、この列挙子のカーソルを現在の位置から進めます。</span><span class="sxs-lookup"><span data-stu-id="7e440-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e440-104">構文</span><span class="sxs-lookup"><span data-stu-id="7e440-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7e440-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7e440-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="7e440-106">[in]スキップする要素の数。</span><span class="sxs-lookup"><span data-stu-id="7e440-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e440-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="7e440-107">Return Value</span></span>  
 <span data-ttu-id="7e440-108">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="7e440-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7e440-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7e440-109">HRESULT</span></span>|<span data-ttu-id="7e440-110">説明</span><span class="sxs-lookup"><span data-stu-id="7e440-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7e440-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7e440-111">S_OK</span></span>|<span data-ttu-id="7e440-112">`celt`要素がスキップされました。</span><span class="sxs-lookup"><span data-stu-id="7e440-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="7e440-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="7e440-113">S_FALSE</span></span>|<span data-ttu-id="7e440-114">少ない`celt`要素がスキップされた複数の要素ではありませんがあることを示します。</span><span class="sxs-lookup"><span data-stu-id="7e440-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e440-115">コメント</span><span class="sxs-lookup"><span data-stu-id="7e440-115">Remarks</span></span>  
 <span data-ttu-id="7e440-116">この列挙子のカーソルの新しい位置は、(現在の位置) +`celt`です。</span><span class="sxs-lookup"><span data-stu-id="7e440-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e440-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="7e440-117">Requirements</span></span>  
 <span data-ttu-id="7e440-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7e440-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e440-119">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7e440-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7e440-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e440-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e440-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e440-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e440-122">参照</span><span class="sxs-lookup"><span data-stu-id="7e440-122">See Also</span></span>  
 [<span data-ttu-id="7e440-123">ICorProfilerModuleEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7e440-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [<span data-ttu-id="7e440-124">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="7e440-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)

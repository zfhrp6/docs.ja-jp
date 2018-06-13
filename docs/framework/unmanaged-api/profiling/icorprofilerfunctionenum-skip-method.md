---
title: ICorProfilerFunctionEnum::Skip メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
- ICorProfilerFunctionEnum::Skip method [.NET Framework profiling]
ms.assetid: 051465b9-e479-494a-804b-c880323b4cbe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 95301c4a99253261721c7f524b99f79a6207feb1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453110"
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="b81df-102">ICorProfilerFunctionEnum::Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="b81df-102">ICorProfilerFunctionEnum::Skip Method</span></span>
<span data-ttu-id="b81df-103">指定した数の要素がスキップされるように、この列挙子のカーソルを現在の位置から進めます。</span><span class="sxs-lookup"><span data-stu-id="b81df-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b81df-104">構文</span><span class="sxs-lookup"><span data-stu-id="b81df-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b81df-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b81df-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="b81df-106">[in]スキップする要素の数。</span><span class="sxs-lookup"><span data-stu-id="b81df-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b81df-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="b81df-107">Return Value</span></span>  
 <span data-ttu-id="b81df-108">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="b81df-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b81df-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b81df-109">HRESULT</span></span>|<span data-ttu-id="b81df-110">説明</span><span class="sxs-lookup"><span data-stu-id="b81df-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b81df-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b81df-111">S_OK</span></span>|<span data-ttu-id="b81df-112">`celt` 要素がスキップされました。</span><span class="sxs-lookup"><span data-stu-id="b81df-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="b81df-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b81df-113">S_FALSE</span></span>|<span data-ttu-id="b81df-114">少ない`celt`要素がスキップされた複数の要素ではありませんがあることを示します。</span><span class="sxs-lookup"><span data-stu-id="b81df-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b81df-115">コメント</span><span class="sxs-lookup"><span data-stu-id="b81df-115">Remarks</span></span>  
 <span data-ttu-id="b81df-116">この列挙子のカーソルの新しい位置は、(現在の位置) +`celt`です。</span><span class="sxs-lookup"><span data-stu-id="b81df-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b81df-117">要件</span><span class="sxs-lookup"><span data-stu-id="b81df-117">Requirements</span></span>  
 <span data-ttu-id="b81df-118">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b81df-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b81df-119">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b81df-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b81df-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b81df-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b81df-121">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b81df-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b81df-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="b81df-122">See Also</span></span>  
 [<span data-ttu-id="b81df-123">ICorProfilerFunctionEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b81df-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="b81df-124">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="b81df-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)

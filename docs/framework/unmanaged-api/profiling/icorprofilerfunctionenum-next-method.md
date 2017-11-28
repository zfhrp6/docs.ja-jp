---
title: "ICorProfilerFunctionEnum::Next メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionEnum.Next Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionEnum::Next
helpviewer_keywords:
- ICorProfilerFunctionEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 5ed4aa83-ce56-4b9f-9237-5da7587787fe
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6cf37beced15305de60c3f57edb701adc7379a1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerfunctionenumnext-method"></a><span data-ttu-id="50b1a-102">ICorProfilerFunctionEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="50b1a-102">ICorProfilerFunctionEnum::Next Method</span></span>
<span data-ttu-id="50b1a-103">関数のシーケンシャル コレクションから、列挙子の現在の位置以降にある、指定した数の隣接する関数を取得します。</span><span class="sxs-lookup"><span data-stu-id="50b1a-103">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50b1a-104">構文</span><span class="sxs-lookup"><span data-stu-id="50b1a-104">Syntax</span></span>  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    COR_PRF_FUNCTION ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="50b1a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50b1a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="50b1a-106">[in] 取得する関数の数。</span><span class="sxs-lookup"><span data-stu-id="50b1a-106">[in] The number of functions to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="50b1a-107">[out] `COR_PRF_FUNCTION` 値の配列。それぞれの値は、取得された関数を表します。</span><span class="sxs-lookup"><span data-stu-id="50b1a-107">[out] An array of `COR_PRF_FUNCTION` values, each of which represents a retrieved function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="50b1a-108">[out] `ids` 配列で実際に返される関数の数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="50b1a-108">[out] A pointer to the number of functions actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50b1a-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="50b1a-109">Return Value</span></span>  
 <span data-ttu-id="50b1a-110">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="50b1a-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="50b1a-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="50b1a-111">HRESULT</span></span>|<span data-ttu-id="50b1a-112">説明</span><span class="sxs-lookup"><span data-stu-id="50b1a-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50b1a-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="50b1a-113">S_OK</span></span>|<span data-ttu-id="50b1a-114">`celt` 要素が返されました。</span><span class="sxs-lookup"><span data-stu-id="50b1a-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="50b1a-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="50b1a-115">S_FALSE</span></span>|<span data-ttu-id="50b1a-116">`celt` よりも少ない数の要素が返されました。これは、列挙が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="50b1a-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="50b1a-117">要件</span><span class="sxs-lookup"><span data-stu-id="50b1a-117">Requirements</span></span>  
 <span data-ttu-id="50b1a-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="50b1a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50b1a-119">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="50b1a-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="50b1a-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50b1a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50b1a-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50b1a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50b1a-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="50b1a-122">See Also</span></span>  
 [<span data-ttu-id="50b1a-123">ICorProfilerFunctionEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="50b1a-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="50b1a-124">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="50b1a-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)

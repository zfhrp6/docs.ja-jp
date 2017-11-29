---
title: "ICorProfilerFunctionControl::SetILFunctionBody メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionControl.SetILFunctionBody
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionControl::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 2c33f0f7-75b2-4c19-b2c7-c94b54997576
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9469435186a5aef130ca4ebef27a4613afeb921c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="7ccb2-102">ICorProfilerFunctionControl::SetILFunctionBody メソッド</span><span class="sxs-lookup"><span data-stu-id="7ccb2-102">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>
<span data-ttu-id="7ccb2-103">メソッドの中間共通言語 (CIL) 本体を置換します。</span><span class="sxs-lookup"><span data-stu-id="7ccb2-103">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ccb2-104">構文</span><span class="sxs-lookup"><span data-stu-id="7ccb2-104">Syntax</span></span>  
  
```  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7ccb2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7ccb2-105">Parameters</span></span>  
 `cbNewILMethodHeader`  
 <span data-ttu-id="7ccb2-106">[入力] ヘッダー、および本体の後に続く構造を含む、新しい CIL の合計サイズ。</span><span class="sxs-lookup"><span data-stu-id="7ccb2-106">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="7ccb2-107">[入力] 新しい CIL ヘッダーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7ccb2-107">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ccb2-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="7ccb2-108">Return Value</span></span>  
 <span data-ttu-id="7ccb2-109">このメソッドは、次の特定の HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="7ccb2-109">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="7ccb2-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7ccb2-110">HRESULT</span></span>|<span data-ttu-id="7ccb2-111">説明</span><span class="sxs-lookup"><span data-stu-id="7ccb2-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7ccb2-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="7ccb2-112">S_OK</span></span>|<span data-ttu-id="7ccb2-113">置換が成功しました。</span><span class="sxs-lookup"><span data-stu-id="7ccb2-113">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ccb2-114">コメント</span><span class="sxs-lookup"><span data-stu-id="7ccb2-114">Remarks</span></span>  
 <span data-ttu-id="7ccb2-115">異なり、 [icorprofilerinfo::setilfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) 、メソッド、`SetILFunctionBody`メソッドは、新しい CIL 本体に必要なメモリを管理します。</span><span class="sxs-lookup"><span data-stu-id="7ccb2-115">Unlike the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="7ccb2-116">つまりを使用して割り当てられる、プロファイラーが提供する CIL 本体がないこと、 [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)インターフェイスまたは特定の範囲内で割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="7ccb2-116">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="7ccb2-117">この本体は、どのヒープにも割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="7ccb2-117">It can be allocated on any heap.</span></span> <span data-ttu-id="7ccb2-118">プロファイラーは後、CIL 本体で使用されるメモリを解放できます`SetILFunctionBody`を返します。</span><span class="sxs-lookup"><span data-stu-id="7ccb2-118">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ccb2-119">要件</span><span class="sxs-lookup"><span data-stu-id="7ccb2-119">Requirements</span></span>  
 <span data-ttu-id="7ccb2-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7ccb2-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ccb2-121">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7ccb2-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7ccb2-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ccb2-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ccb2-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ccb2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ccb2-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ccb2-124">See Also</span></span>  
 [<span data-ttu-id="7ccb2-125">ICorProfilerFunctionControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7ccb2-125">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)

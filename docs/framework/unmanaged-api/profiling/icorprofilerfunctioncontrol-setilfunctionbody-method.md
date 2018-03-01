---
title: "ICorProfilerFunctionControl::SetILFunctionBody メソッド"
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
- ICorProfilerFunctionControl.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 2c33f0f7-75b2-4c19-b2c7-c94b54997576
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 56d31b93385a087949121a76587ef6009cd9d51e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="6d61a-102">ICorProfilerFunctionControl::SetILFunctionBody メソッド</span><span class="sxs-lookup"><span data-stu-id="6d61a-102">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>
<span data-ttu-id="6d61a-103">メソッドの中間共通言語 (CIL) 本体を置換します。</span><span class="sxs-lookup"><span data-stu-id="6d61a-103">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d61a-104">構文</span><span class="sxs-lookup"><span data-stu-id="6d61a-104">Syntax</span></span>  
  
```  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6d61a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6d61a-105">Parameters</span></span>  
 `cbNewILMethodHeader`  
 <span data-ttu-id="6d61a-106">[入力] ヘッダー、および本体の後に続く構造を含む、新しい CIL の合計サイズ。</span><span class="sxs-lookup"><span data-stu-id="6d61a-106">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="6d61a-107">[入力] 新しい CIL ヘッダーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6d61a-107">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d61a-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="6d61a-108">Return Value</span></span>  
 <span data-ttu-id="6d61a-109">このメソッドは、次の特定の HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="6d61a-109">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="6d61a-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6d61a-110">HRESULT</span></span>|<span data-ttu-id="6d61a-111">説明</span><span class="sxs-lookup"><span data-stu-id="6d61a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6d61a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="6d61a-112">S_OK</span></span>|<span data-ttu-id="6d61a-113">置換が成功しました。</span><span class="sxs-lookup"><span data-stu-id="6d61a-113">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d61a-114">コメント</span><span class="sxs-lookup"><span data-stu-id="6d61a-114">Remarks</span></span>  
 <span data-ttu-id="6d61a-115">異なり、 [icorprofilerinfo::setilfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) 、メソッド、`SetILFunctionBody`メソッドは、新しい CIL 本体に必要なメモリを管理します。</span><span class="sxs-lookup"><span data-stu-id="6d61a-115">Unlike the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="6d61a-116">つまりを使用して割り当てられる、プロファイラーが提供する CIL 本体がないこと、 [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)インターフェイスまたは特定の範囲内で割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="6d61a-116">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="6d61a-117">この本体は、どのヒープにも割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="6d61a-117">It can be allocated on any heap.</span></span> <span data-ttu-id="6d61a-118">プロファイラーは後、CIL 本体で使用されるメモリを解放できます`SetILFunctionBody`を返します。</span><span class="sxs-lookup"><span data-stu-id="6d61a-118">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d61a-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="6d61a-119">Requirements</span></span>  
 <span data-ttu-id="6d61a-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6d61a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d61a-121">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6d61a-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6d61a-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d61a-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d61a-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d61a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d61a-124">参照</span><span class="sxs-lookup"><span data-stu-id="6d61a-124">See Also</span></span>  
 [<span data-ttu-id="6d61a-125">ICorProfilerFunctionControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6d61a-125">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)

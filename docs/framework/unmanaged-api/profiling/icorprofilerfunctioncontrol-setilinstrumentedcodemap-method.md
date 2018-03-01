---
title: "ICorProfilerFunctionControl::SetILInstrumentedCodeMap メソッド"
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
- ICorProfilerFunctionControl.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetIILInstrumentedCodeMap method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: ecf56646-7e5f-46c4-8340-f3a04e88920f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 580d60fe0a6348a163fef9e215cddfc1bc4302b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a><span data-ttu-id="b0b82-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap メソッド</span><span class="sxs-lookup"><span data-stu-id="b0b82-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="b0b82-103">指定した共通中間言語 (CIL) マップ エントリを使用して、指定される関数のコード マップを設定します。</span><span class="sxs-lookup"><span data-stu-id="b0b82-103">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0b82-104">構文</span><span class="sxs-lookup"><span data-stu-id="b0b82-104">Syntax</span></span>  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b0b82-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b0b82-105">Parameters</span></span>  
 `cILMapEntries`  
 <span data-ttu-id="b0b82-106">[in] マップ内のエントリの数。</span><span class="sxs-lookup"><span data-stu-id="b0b82-106">[in] The number of entries in the map.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="b0b82-107">[in]COR_IL_MAP エントリの呼び出し元が割り当てた配列。</span><span class="sxs-lookup"><span data-stu-id="b0b82-107">[in] The caller-allocated array of COR_IL_MAP  entries.</span></span> <span data-ttu-id="b0b82-108">これらのエントリの解釈は同じである、 [icorprofilerinfo::setilinstrumentedcodemap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="b0b82-108">The interpretation of these entries is the same as for the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0b82-109">コメント</span><span class="sxs-lookup"><span data-stu-id="b0b82-109">Remarks</span></span>  
 <span data-ttu-id="b0b82-110">このメソッドを呼び出して、マッピングの設定により、デバッガーを呼び出して、マッピングの取得を[icordebugilcode 2::getinstrumentedilmap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="b0b82-110">Setting the mapping by calling this method allows the debugger to retrieve the mapping by calling [ICorDebugILCode2::GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span></span> <span data-ttu-id="b0b82-111">またデバッガーは、スタック トレースおよび可変的な有効期間に対する IL オフセットを計算するときに、マッピングを内部で使用できます。</span><span class="sxs-lookup"><span data-stu-id="b0b82-111">It also allows the debugger to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0b82-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="b0b82-112">Requirements</span></span>  
 <span data-ttu-id="b0b82-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b0b82-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0b82-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b0b82-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b0b82-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0b82-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0b82-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0b82-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0b82-117">参照</span><span class="sxs-lookup"><span data-stu-id="b0b82-117">See Also</span></span>  
 [<span data-ttu-id="b0b82-118">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b0b82-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

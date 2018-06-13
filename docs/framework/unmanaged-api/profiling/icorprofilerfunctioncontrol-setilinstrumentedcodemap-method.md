---
title: ICorProfilerFunctionControl::SetILInstrumentedCodeMap メソッド
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3cb4bfdf90099719e2584c3767965a53186ca8ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453259"
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a><span data-ttu-id="531e4-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap メソッド</span><span class="sxs-lookup"><span data-stu-id="531e4-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="531e4-103">指定した共通中間言語 (CIL) マップ エントリを使用して、指定される関数のコード マップを設定します。</span><span class="sxs-lookup"><span data-stu-id="531e4-103">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="531e4-104">構文</span><span class="sxs-lookup"><span data-stu-id="531e4-104">Syntax</span></span>  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="531e4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="531e4-105">Parameters</span></span>  
 `cILMapEntries`  
 <span data-ttu-id="531e4-106">[in] マップ内のエントリの数。</span><span class="sxs-lookup"><span data-stu-id="531e4-106">[in] The number of entries in the map.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="531e4-107">[in]COR_IL_MAP エントリの呼び出し元が割り当てた配列。</span><span class="sxs-lookup"><span data-stu-id="531e4-107">[in] The caller-allocated array of COR_IL_MAP  entries.</span></span> <span data-ttu-id="531e4-108">これらのエントリの解釈は同じである、 [icorprofilerinfo::setilinstrumentedcodemap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="531e4-108">The interpretation of these entries is the same as for the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="531e4-109">コメント</span><span class="sxs-lookup"><span data-stu-id="531e4-109">Remarks</span></span>  
 <span data-ttu-id="531e4-110">このメソッドを呼び出して、マッピングの設定により、デバッガーを呼び出して、マッピングの取得を[icordebugilcode 2::getinstrumentedilmap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="531e4-110">Setting the mapping by calling this method allows the debugger to retrieve the mapping by calling [ICorDebugILCode2::GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span></span> <span data-ttu-id="531e4-111">またデバッガーは、スタック トレースおよび可変的な有効期間に対する IL オフセットを計算するときに、マッピングを内部で使用できます。</span><span class="sxs-lookup"><span data-stu-id="531e4-111">It also allows the debugger to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="531e4-112">要件</span><span class="sxs-lookup"><span data-stu-id="531e4-112">Requirements</span></span>  
 <span data-ttu-id="531e4-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="531e4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="531e4-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="531e4-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="531e4-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="531e4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="531e4-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="531e4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="531e4-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="531e4-117">See Also</span></span>  
 [<span data-ttu-id="531e4-118">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="531e4-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

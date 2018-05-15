---
title: ICorProfilerInfo::SetILFunctionBody メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerInfo::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method [.NET Framework profiling]
ms.assetid: b159c712-00f4-4fc7-a990-40bf9f642e8f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 886bb706be30481c082012bf057a001f37903b16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a><span data-ttu-id="cd0f5-102">ICorProfilerInfo::SetILFunctionBody メソッド</span><span class="sxs-lookup"><span data-stu-id="cd0f5-102">ICorProfilerInfo::SetILFunctionBody Method</span></span>
<span data-ttu-id="cd0f5-103">指定したモジュール内の指定した関数の本体を置換します。</span><span class="sxs-lookup"><span data-stu-id="cd0f5-103">Replaces the body of the specified function in the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd0f5-104">構文</span><span class="sxs-lookup"><span data-stu-id="cd0f5-104">Syntax</span></span>  
  
```  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cd0f5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cd0f5-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="cd0f5-106">[in]関数が存在するモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="cd0f5-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodid`  
 <span data-ttu-id="cd0f5-107">[in]本文を置換する関数のトークンです。</span><span class="sxs-lookup"><span data-stu-id="cd0f5-107">[in] The token of the function for which to replace the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="cd0f5-108">[in]関数の新しいヘッダー。</span><span class="sxs-lookup"><span data-stu-id="cd0f5-108">[in] The new header for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd0f5-109">コメント</span><span class="sxs-lookup"><span data-stu-id="cd0f5-109">Remarks</span></span>  
 <span data-ttu-id="cd0f5-110">`SetILFunctionBody`関数の新しい本文をポイントし、必要に応じて、内部データ構造を調整できるように、メソッドは、メタデータ内の関数の相対仮想アドレスを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="cd0f5-110">The `SetILFunctionBody` method replaces the relative virtual address of the function in the metadata so that it points to the new function body, and adjusts any internal data structures as required.</span></span>  
  
 <span data-ttu-id="cd0f5-111">`SetILFunctionBody` ・ イン タイム (JIT) コンパイラでコンパイルされていることはありません関数だけにメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="cd0f5-111">The `SetILFunctionBody` method can be called on only those functions that have never been compiled by a just-in-time (JIT) compiler.</span></span>  
  
 <span data-ttu-id="cd0f5-112">使用して、 [icorprofilerinfo::getilfunctionbodyallocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)新しいメソッドがバッファーに互換性があることを確認する領域を割り当てるためのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="cd0f5-112">Use the [ICorProfilerInfo::GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md) method to allocate space for the new method to ensure that the buffer is compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd0f5-113">要件</span><span class="sxs-lookup"><span data-stu-id="cd0f5-113">Requirements</span></span>  
 <span data-ttu-id="cd0f5-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cd0f5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd0f5-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cd0f5-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cd0f5-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd0f5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd0f5-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd0f5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd0f5-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd0f5-118">See Also</span></span>  
 [<span data-ttu-id="cd0f5-119">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd0f5-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

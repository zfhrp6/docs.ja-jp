---
title: ICorProfilerCallback8::DynamicMethodJITCompilationStarted メソッド
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad74eeb4deeae73be40b3a0bc0f6a18ec2299780
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="97e1b-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="97e1b-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="97e1b-103">[.NET Framework 4.7 以降のバージョンでサポート]</span><span class="sxs-lookup"><span data-stu-id="97e1b-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="97e1b-104">動的メソッドの JIT コンパイルが開始されるたびに、プロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="97e1b-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97e1b-105">構文</span><span class="sxs-lookup"><span data-stu-id="97e1b-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="97e1b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="97e1b-106">Parameters</span></span>  
<span data-ttu-id="97e1b-107">[入力] `functionId`</span><span class="sxs-lookup"><span data-stu-id="97e1b-107">[in] `functionId`</span></span>  
<span data-ttu-id="97e1b-108">どの JIT のコンパイルが開始したメモリ内の関数の識別子です。</span><span class="sxs-lookup"><span data-stu-id="97e1b-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="97e1b-109">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="97e1b-109">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="97e1b-110">`true` そのブロックを示すためにランタイムになるこのコールバックから戻るには、呼び出し元のスレッドを待機するには`false`をブロックしていないに影響すること、ランタイムの動作を示します。</span><span class="sxs-lookup"><span data-stu-id="97e1b-110">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="97e1b-111">[in] `pILHeader`  </span><span class="sxs-lookup"><span data-stu-id="97e1b-111">[in] `pILHeader`  </span></span>  
<span data-ttu-id="97e1b-112">メソッドの IL ヘッダーの最初のバイトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="97e1b-112">A pointer to the first byte of the method's IL header.</span></span>   

<span data-ttu-id="97e1b-113">[in] `cbILHeader`  </span><span class="sxs-lookup"><span data-stu-id="97e1b-113">[in] `cbILHeader`  </span></span>  
<span data-ttu-id="97e1b-114">IL ヘッダー内のバイト数。</span><span class="sxs-lookup"><span data-stu-id="97e1b-114">The number of bytes in the IL header.</span></span> 

## <a name="remarks"></a><span data-ttu-id="97e1b-115">コメント</span><span class="sxs-lookup"><span data-stu-id="97e1b-115">Remarks</span></span>  

<span data-ttu-id="97e1b-116">動的メソッドが JIT でコンパイルされるたびに、このコールバックがトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="97e1b-116">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="97e1b-117">これには、さまざまな IL スタブと LCG メソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="97e1b-117">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="97e1b-118">その目標は、ユーザーにコンパイルされたメソッドを識別するための十分な情報を含むプロファイラー ライターを提供します。</span><span class="sxs-lookup"><span data-stu-id="97e1b-118">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="97e1b-119">`functionId` 値は、動的メソッドのメタデータがあるないため、メタデータ トークンを解決するのには使用できません。</span><span class="sxs-lookup"><span data-stu-id="97e1b-119">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="97e1b-120">`pILHeader`ポインターは、コールバック中にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="97e1b-120">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="97e1b-121">要件</span><span class="sxs-lookup"><span data-stu-id="97e1b-121">Requirements</span></span>  
 <span data-ttu-id="97e1b-122">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="97e1b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97e1b-123">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="97e1b-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="97e1b-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97e1b-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97e1b-125">**.NET framework のバージョン:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="97e1b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97e1b-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="97e1b-126">See Also</span></span>  
 [<span data-ttu-id="97e1b-127">DynamicMethodJITCompilationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="97e1b-127">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)  
 [<span data-ttu-id="97e1b-128">ICorProfilerCallback8 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="97e1b-128">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)

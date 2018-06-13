---
title: ICorProfilerCallback::ManagedToUnmanagedTransition メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ManagedToUnmanagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0735e4c59ba609ed87d61aca737c4f8a4dab757a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453487"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a><span data-ttu-id="d6055-102">ICorProfilerCallback::ManagedToUnmanagedTransition メソッド</span><span class="sxs-lookup"><span data-stu-id="d6055-102">ICorProfilerCallback::ManagedToUnmanagedTransition Method</span></span>
<span data-ttu-id="d6055-103">マネージ コードからアンマネージ コードへの移行が発生したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="d6055-103">Notifies the profiler that a transition from managed code to unmanaged code has occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6055-104">構文</span><span class="sxs-lookup"><span data-stu-id="d6055-104">Syntax</span></span>  
  
```  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6055-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d6055-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d6055-106">[in]呼び出される関数の ID。</span><span class="sxs-lookup"><span data-stu-id="d6055-106">[in] The ID of the function that is being called.</span></span>  
  
 `reason`  
 <span data-ttu-id="d6055-107">[in]値、 [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)をマネージ コードからアンマネージ コードに呼び出しのため、またはアンマネージによって呼び出されるマネージ関数の戻り値のために、移行が発生したかどうかを示す列挙体です。</span><span class="sxs-lookup"><span data-stu-id="d6055-107">[in] A value of the [COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) enumeration that indicates whether the transition occurred because of a call into unmanaged code from managed code, or because of a return from a managed function called by an unmanaged one.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6055-108">コメント</span><span class="sxs-lookup"><span data-stu-id="d6055-108">Remarks</span></span>  
 <span data-ttu-id="d6055-109">場合の値`reason`COR_PRF_TRANSITION_CALL、ID こと、アンマネージ関数は決してコンパイルされたジャスト イン タイムのコンパイラを使用してこの関数は、します。</span><span class="sxs-lookup"><span data-stu-id="d6055-109">If the value of `reason` is COR_PRF_TRANSITION_CALL, the function ID is that of the unmanaged function, which will never have been compiled using the just-in-time compiler.</span></span> <span data-ttu-id="d6055-110">アンマネージ関数には、名前とメタデータの一部など、それらに関連付けられている基本的な情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d6055-110">Unmanaged functions have basic information associated with them, such as a name and some metadata.</span></span> <span data-ttu-id="d6055-111">暗黙のプラットフォームを使用して、アンマネージ関数が呼び出された場合は、呼び出し (PInvoke)、ランタイムは、呼び出し先との値を特定できません`functionId`は null になります。</span><span class="sxs-lookup"><span data-stu-id="d6055-111">If the unmanaged function was called by using implicit platform invoke (PInvoke), the runtime cannot determine the destination of the call and the value of `functionId` will be null.</span></span> <span data-ttu-id="d6055-112">暗黙の PInvoke の詳細については、次を参照してください。[を使用して C++ Interop (暗黙の PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)です。</span><span class="sxs-lookup"><span data-stu-id="d6055-112">For more information on implicit PInvoke, see [Using C++ Interop (Implicit PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6055-113">要件</span><span class="sxs-lookup"><span data-stu-id="d6055-113">Requirements</span></span>  
 <span data-ttu-id="d6055-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d6055-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6055-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d6055-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d6055-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6055-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6055-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6055-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6055-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6055-118">See Also</span></span>  
 [<span data-ttu-id="d6055-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d6055-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="d6055-120">UnmanagedToManagedTransition メソッド</span><span class="sxs-lookup"><span data-stu-id="d6055-120">UnmanagedToManagedTransition Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)  
 [<span data-ttu-id="d6055-121">C++ での明示的な PInvoke (DllImport 属性) の使用方法</span><span class="sxs-lookup"><span data-stu-id="d6055-121">Using Explicit PInvoke in C++ (DllImport Attribute)</span></span>](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)

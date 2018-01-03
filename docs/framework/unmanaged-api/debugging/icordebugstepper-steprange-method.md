---
title: "ICorDebugStepper::StepRange メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.StepRange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a02efe1b701506cc3de695c5b79d5e9c84b25b8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsteppersteprange-method"></a><span data-ttu-id="b0026-102">ICorDebugStepper::StepRange メソッド</span><span class="sxs-lookup"><span data-stu-id="b0026-102">ICorDebugStepper::StepRange Method</span></span>
<span data-ttu-id="b0026-103">Icordebugstepper をシングル ステップ実行し、指定された範囲の最後以外のコードに達したときに返されるその格納スレッドを表示します。</span><span class="sxs-lookup"><span data-stu-id="b0026-103">Causes this ICorDebugStepper to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0026-104">構文</span><span class="sxs-lookup"><span data-stu-id="b0026-104">Syntax</span></span>  
  
```  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b0026-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b0026-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="b0026-106">[in]設定`true`スレッド内で呼び出される関数にステップ インします。</span><span class="sxs-lookup"><span data-stu-id="b0026-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="b0026-107">設定`false`をステップ オーバー関数。</span><span class="sxs-lookup"><span data-stu-id="b0026-107">Set to `false` to step over the function.</span></span>  
  
 `ranges`  
 <span data-ttu-id="b0026-108">[in]COR_DEBUG_STEP_RANGE 構造体の配列、それぞれの範囲を指定します。</span><span class="sxs-lookup"><span data-stu-id="b0026-108">[in] An array of COR_DEBUG_STEP_RANGE structures, each of which specifies a range.</span></span>  
  
 `cRangeCount`  
 <span data-ttu-id="b0026-109">[in] `ranges` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="b0026-109">[in] The size of the `ranges` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0026-110">コメント</span><span class="sxs-lookup"><span data-stu-id="b0026-110">Remarks</span></span>  
 <span data-ttu-id="b0026-111">`StepRange`のような方法は、機能、 [icordebugstepper::step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)メソッド、特定の範囲外のコードまでに完了しないする点を除いてに達した。</span><span class="sxs-lookup"><span data-stu-id="b0026-111">The `StepRange` method works like the [ICorDebugStepper::Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) method, except that it does not complete until code outside the given range is reached.</span></span>  
  
 <span data-ttu-id="b0026-112">これは、一度に 1 つの命令をステップ実行するよりも効率的で指定できます。</span><span class="sxs-lookup"><span data-stu-id="b0026-112">This can be more efficient than stepping one instruction at a time.</span></span> <span data-ttu-id="b0026-113">範囲は、ステッパのフレームの先頭からのオフセットのペアのリストとして指定します。</span><span class="sxs-lookup"><span data-stu-id="b0026-113">Ranges are specified as a list of offset pairs from the start of the stepper's frame.</span></span>  
  
 <span data-ttu-id="b0026-114">範囲は、メソッドの Microsoft intermediate language (MSIL) コードです。</span><span class="sxs-lookup"><span data-stu-id="b0026-114">Ranges are relative to the Microsoft intermediate language (MSIL) code of a method.</span></span> <span data-ttu-id="b0026-115">呼び出す[icordebugstepper::setrangeil](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)で`false`メソッドのネイティブ コードの基準とした範囲にします。</span><span class="sxs-lookup"><span data-stu-id="b0026-115">Call [ICorDebugStepper::SetRangeIL](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) with `false` to make the ranges relative to the native code of a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0026-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="b0026-116">Requirements</span></span>  
 <span data-ttu-id="b0026-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b0026-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0026-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0026-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0026-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0026-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0026-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0026-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

---
title: ICorDebugStepper::SetInterceptMask メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetInterceptMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7654a91180dd0b4148cfb85b35bf1ce730764f28
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422686"
---
# <a name="icordebugsteppersetinterceptmask-method"></a><span data-ttu-id="788b5-102">ICorDebugStepper::SetInterceptMask メソッド</span><span class="sxs-lookup"><span data-stu-id="788b5-102">ICorDebugStepper::SetInterceptMask Method</span></span>
<span data-ttu-id="788b5-103">ステップ インできるコードの型を指定する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="788b5-103">Sets a value that specifies the types of code that are stepped into.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="788b5-104">構文</span><span class="sxs-lookup"><span data-stu-id="788b5-104">Syntax</span></span>  
  
```  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="788b5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="788b5-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="788b5-106">[in]コードの種類を指定する CorDebugIntercept 列挙型の値の組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="788b5-106">[in] A combination of values of the CorDebugIntercept enumeration that specifies the types of code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="788b5-107">コメント</span><span class="sxs-lookup"><span data-stu-id="788b5-107">Remarks</span></span>  
 <span data-ttu-id="788b5-108">インターセプターのビットが設定されている場合のコードをインターセプトし、指定された型が検出されたときに、ステッパが終了します。</span><span class="sxs-lookup"><span data-stu-id="788b5-108">If the bit for an interceptor is set, the stepper will complete when the given type of intercepting code is encountered.</span></span> <span data-ttu-id="788b5-109">ビットがオフの場合は傍受のコードはスキップされます。</span><span class="sxs-lookup"><span data-stu-id="788b5-109">If the bit is cleared, the intercepting code will be skipped.</span></span>  
  
 <span data-ttu-id="788b5-110">`SetInterceptMask`メソッドには予期しない対話[icordebugstepper::setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (ユーザーの観点から)。</span><span class="sxs-lookup"><span data-stu-id="788b5-110">The `SetInterceptMask` method may have unforeseen interactions with [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (from the user's point of view).</span></span> <span data-ttu-id="788b5-111">たとえば場合、のみ表示 (は、非内部) クラスの初期化コードの一部のマッピング情報がないし、STOP_NO_MAPPING_INFO が設定されていない (を参照してください、 [icordebugstepper::setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)メソッドおよびCorDebugUnmappedStop 列挙型)、ステッパはステップ オーバーはクラスの初期化します。</span><span class="sxs-lookup"><span data-stu-id="788b5-111">For example, if the only visible (that is, non-internal) portion of class initialization code lacks mapping information and STOP_NO_MAPPING_INFO isn't set (see the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method and the CorDebugUnmappedStop enumeration), the stepper will step over the class initialization.</span></span> <span data-ttu-id="788b5-112">既定では、INTERCEPT_NONE 値のみ、`CorDebugIntercept`列挙が使用されます。</span><span class="sxs-lookup"><span data-stu-id="788b5-112">By default, only the INTERCEPT_NONE value of the `CorDebugIntercept` enumeration will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="788b5-113">要件</span><span class="sxs-lookup"><span data-stu-id="788b5-113">Requirements</span></span>  
 <span data-ttu-id="788b5-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="788b5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="788b5-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="788b5-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="788b5-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="788b5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="788b5-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="788b5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

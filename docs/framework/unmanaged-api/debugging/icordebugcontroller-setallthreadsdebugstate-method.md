---
title: ICorDebugController::SetAllThreadsDebugState メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.SetAllThreadsDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::SetAllThreadsDebugState
helpviewer_keywords:
- SetAllThreadsDebugState method [.NET Framework debugging]
- ICorDebugController::SetAllThreadsDebugState method [.NET Framework debugging]
ms.assetid: bdda4bd7-4743-4d58-a22b-8067e967db95
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ee396c512dca2bea0a7a9737d5515defce4b2b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415130"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="8e81d-102">ICorDebugController::SetAllThreadsDebugState メソッド</span><span class="sxs-lookup"><span data-stu-id="8e81d-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>
<span data-ttu-id="8e81d-103">プロセスのすべてのマネージ スレッドのデバッグ状態を設定します。</span><span class="sxs-lookup"><span data-stu-id="8e81d-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e81d-104">構文</span><span class="sxs-lookup"><span data-stu-id="8e81d-104">Syntax</span></span>  
  
```  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8e81d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8e81d-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="8e81d-106">[in]デバッグのスレッドの状態を指定する"CorDebugThreadState"列挙の値です。</span><span class="sxs-lookup"><span data-stu-id="8e81d-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="8e81d-107">[in]デバッグの状態の設定から除外するスレッドを表す"ICorDebugThread"オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8e81d-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="8e81d-108">この値が null の場合は、スレッドは除外されません。</span><span class="sxs-lookup"><span data-stu-id="8e81d-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e81d-109">コメント</span><span class="sxs-lookup"><span data-stu-id="8e81d-109">Remarks</span></span>  
 <span data-ttu-id="8e81d-110">`SetAllThreadsDebugState`経由で表示されていないスレッドの影響を与えるメソッド[EnumerateThreads メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)、そのスレッドで中断された、`SetAllThreadsDebugState`メソッドを再開する必要があります、`SetAllThreadsDebugState`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="8e81d-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e81d-111">要件</span><span class="sxs-lookup"><span data-stu-id="8e81d-111">Requirements</span></span>  
 <span data-ttu-id="8e81d-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8e81d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e81d-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8e81d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e81d-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e81d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e81d-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e81d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e81d-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="8e81d-116">See Also</span></span>  
 

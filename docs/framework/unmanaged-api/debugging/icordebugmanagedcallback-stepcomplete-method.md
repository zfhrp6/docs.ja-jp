---
title: "ICorDebugManagedCallback::StepComplete メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.StepComplete
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::StepComplete
helpviewer_keywords:
- StepComplete method [.NET Framework debugging]
- ICorDebugManagedCallback::StepComplete method [.NET Framework debugging]
ms.assetid: 5e1f2c47-81df-4530-826d-96489cd68719
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: eabc9a2730a1afdf574cee97a6f1b40bae34c7ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a><span data-ttu-id="eca66-102">ICorDebugManagedCallback::StepComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="eca66-102">ICorDebugManagedCallback::StepComplete Method</span></span>
<span data-ttu-id="eca66-103">ステップが完了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="eca66-103">Notifies the debugger that a step has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eca66-104">構文</span><span class="sxs-lookup"><span data-stu-id="eca66-104">Syntax</span></span>  
  
```  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eca66-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eca66-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="eca66-106">[in]ICorDebugAppDomain を表すオブジェクトを含む、ステップが終了するスレッドのアプリケーション ドメインへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eca66-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread in which the step has completed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="eca66-107">[in]ステップが終了するスレッドを表す ICorDebugThread オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eca66-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the step has completed.</span></span>  
  
 `pStepper`  
 <span data-ttu-id="eca66-108">[in]コードの実行のステップを表す ICorDebugStepper オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eca66-108">[in] A pointer to an ICorDebugStepper object that represents the step in code execution.</span></span>  
  
 `reason`  
 <span data-ttu-id="eca66-109">[in]個々 のステップの結果を示す CorDebugStepReason 列挙型の値です。</span><span class="sxs-lookup"><span data-stu-id="eca66-109">[in] A value of the CorDebugStepReason enumeration that indicates the outcome of an individual step.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eca66-110">コメント</span><span class="sxs-lookup"><span data-stu-id="eca66-110">Remarks</span></span>  
 <span data-ttu-id="eca66-111">ステッパは、ステップ実行を続ける場合は、必要に応じて、デバッグを終了しない限り、使用可能性があります。</span><span class="sxs-lookup"><span data-stu-id="eca66-111">The stepper may be used to continue stepping if desired, unless the debugging is terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eca66-112">要件</span><span class="sxs-lookup"><span data-stu-id="eca66-112">Requirements</span></span>  
 <span data-ttu-id="eca66-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="eca66-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eca66-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eca66-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eca66-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eca66-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eca66-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eca66-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eca66-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="eca66-117">See Also</span></span>  
 [<span data-ttu-id="eca66-118">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eca66-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

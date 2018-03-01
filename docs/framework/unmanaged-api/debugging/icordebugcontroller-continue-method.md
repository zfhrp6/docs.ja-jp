---
title: "ICorDebugController::Continue メソッド"
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
- ICorDebugController.Continue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e6a96145801aa8ef6482e30e9c00b763d2501f36
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollercontinue-method"></a><span data-ttu-id="2b581-102">ICorDebugController::Continue メソッド</span><span class="sxs-lookup"><span data-stu-id="2b581-102">ICorDebugController::Continue Method</span></span>
<span data-ttu-id="2b581-103">呼び出しの後にマネージ スレッドの実行を再開[Stop メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="2b581-103">Resumes execution of managed threads after a call to [Stop Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b581-104">構文</span><span class="sxs-lookup"><span data-stu-id="2b581-104">Syntax</span></span>  
  
```  
HRESULT Continue (  
    [in] BOOL fIsOutOfBand  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b581-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2b581-105">Parameters</span></span>  
 `fIsOutOfBand`  
 <span data-ttu-id="2b581-106">[in]設定`true`帯域外のイベントから操作を続行する場合がそれ以外の場合に設定`false`です。</span><span class="sxs-lookup"><span data-stu-id="2b581-106">[in] Set to `true` if continuing from an out-of-band event; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b581-107">コメント</span><span class="sxs-lookup"><span data-stu-id="2b581-107">Remarks</span></span>  
 <span data-ttu-id="2b581-108">`Continue`呼び出しの後にプロセスを続行、`ICorDebugController::Stop`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="2b581-108">`Continue` continues the process after a call to the `ICorDebugController::Stop` method.</span></span>  
  
 <span data-ttu-id="2b581-109">混合モード デバッグを行うときに呼び出すことはありません`Continue`win32 イベント スレッドの帯域外のイベントから続行する場合を除き、します。</span><span class="sxs-lookup"><span data-stu-id="2b581-109">When doing mixed-mode debugging, do not call `Continue` on the Win32 event thread unless you are continuing from an out-of-band event.</span></span>  
  
 <span data-ttu-id="2b581-110">*インバンド イベント*はマネージ イベントまたはデバッガーがプロセスの管理対象の状態との対話をサポートする通常のアンマネージ イベント。</span><span class="sxs-lookup"><span data-stu-id="2b581-110">An *in-band event* is either a managed event or a normal unmanaged event during which the debugger supports interaction with the managed state of the process.</span></span> <span data-ttu-id="2b581-111">この場合、デバッガーを受け取る、 [icordebugunmanagedcallback::debugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)でコールバックの`fOutOfBand`パラメーターに設定`false`です。</span><span class="sxs-lookup"><span data-stu-id="2b581-111">In this case, the debugger receives the [ICorDebugUnmanagedCallback::DebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) callback with its `fOutOfBand` parameter set to `false`.</span></span>  
  
 <span data-ttu-id="2b581-112">*帯域外のイベント*するプロセスの管理対象の状態との対話は、イベントのため、プロセスの停止中に管理されていないイベントします。</span><span class="sxs-lookup"><span data-stu-id="2b581-112">An *out-of-band event* is an unmanaged event during which interaction with the managed state of the process is impossible while the process is stopped due to the event.</span></span> <span data-ttu-id="2b581-113">この場合、デバッガーを受け取る、`ICorDebugUnmanagedCallback::DebugEvent`でコールバックの`fOutOfBand`パラメーターに設定`true`です。</span><span class="sxs-lookup"><span data-stu-id="2b581-113">In this case, the debugger receives the `ICorDebugUnmanagedCallback::DebugEvent` callback with its `fOutOfBand` parameter set to `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b581-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="2b581-114">Requirements</span></span>  
 <span data-ttu-id="2b581-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2b581-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b581-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b581-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b581-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b581-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b581-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b581-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b581-119">参照</span><span class="sxs-lookup"><span data-stu-id="2b581-119">See Also</span></span>  
 

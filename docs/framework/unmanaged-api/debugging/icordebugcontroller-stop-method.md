---
title: "ICorDebugController::Stop メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.Stop
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4b92d07f8d162123d20c6861d204d73789060906
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollerstop-method"></a><span data-ttu-id="1b8cc-102">ICorDebugController::Stop メソッド</span><span class="sxs-lookup"><span data-stu-id="1b8cc-102">ICorDebugController::Stop Method</span></span>
<span data-ttu-id="1b8cc-103">プロセスでマネージ コードを実行しているすべてのスレッドを協調停止を実行します。</span><span class="sxs-lookup"><span data-stu-id="1b8cc-103">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b8cc-104">構文</span><span class="sxs-lookup"><span data-stu-id="1b8cc-104">Syntax</span></span>  
  
```  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b8cc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1b8cc-105">Parameters</span></span>  
 `dwTimeoutIgnored`  
 <span data-ttu-id="1b8cc-106">使用しません。</span><span class="sxs-lookup"><span data-stu-id="1b8cc-106">Not used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b8cc-107">コメント</span><span class="sxs-lookup"><span data-stu-id="1b8cc-107">Remarks</span></span>  
 <span data-ttu-id="1b8cc-108">`Stop`プロセスの管理を実行しているすべてのスレッドでの協調停止コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="1b8cc-108">`Stop` performs a cooperative stop on all threads running managed code in the process.</span></span> <span data-ttu-id="1b8cc-109">マネージのみのデバッグ セッション中にアンマネージ スレッドは実行を続行 (ただし、マネージ コードを呼び出すしようとするときはブロックされます)。</span><span class="sxs-lookup"><span data-stu-id="1b8cc-109">During a managed-only debugging session, unmanaged threads may continue to run (but will be blocked when trying to call managed code).</span></span> <span data-ttu-id="1b8cc-110">相互運用機能デバッグ セッション中には、アンマネージ スレッドも停止されます。</span><span class="sxs-lookup"><span data-stu-id="1b8cc-110">During an interop debugging session, unmanaged threads will also be stopped.</span></span> <span data-ttu-id="1b8cc-111">`dwTimeoutIgnored`現在値が無視され、無限 (-1) として扱われます。</span><span class="sxs-lookup"><span data-stu-id="1b8cc-111">The `dwTimeoutIgnored` value is currently ignored and treated as INFINITE (-1).</span></span> <span data-ttu-id="1b8cc-112">協調停止は、デッドロックのため失敗すると、すべてのスレッドは中断され、E_TIMEOUT が返されます。</span><span class="sxs-lookup"><span data-stu-id="1b8cc-112">If the cooperative stop fails due to a deadlock, all threads are suspended and E_TIMEOUT is returned.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b8cc-113">`Stop`デバッグ API でのみ同期メソッドです。</span><span class="sxs-lookup"><span data-stu-id="1b8cc-113">`Stop` is the only synchronous method in the debugging API.</span></span> <span data-ttu-id="1b8cc-114">ときに`Stop`場合は s_ok、プロセスが停止します。</span><span class="sxs-lookup"><span data-stu-id="1b8cc-114">When `Stop` returns S_OK, the process is stopped.</span></span> <span data-ttu-id="1b8cc-115">リスナーに、停止の通知コールバックは与えられません。</span><span class="sxs-lookup"><span data-stu-id="1b8cc-115">No callback is given to notify listeners of the stop.</span></span> <span data-ttu-id="1b8cc-116">デバッガーを呼び出す必要があります[icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)を再開するプロセスが可能にします。</span><span class="sxs-lookup"><span data-stu-id="1b8cc-116">The debugger must call [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to allow the process to resume.</span></span>  
  
 <span data-ttu-id="1b8cc-117">デバッガーは、停止カウンターを保持します。</span><span class="sxs-lookup"><span data-stu-id="1b8cc-117">The debugger maintains a stop counter.</span></span> <span data-ttu-id="1b8cc-118">カウンターがゼロになる、コント ローラーが再開されます。</span><span class="sxs-lookup"><span data-stu-id="1b8cc-118">When the counter goes to zero, the controller is resumed.</span></span> <span data-ttu-id="1b8cc-119">各呼び出し`Stop`または各ディスパッチされたコールバックがカウンターをインクリメントします。</span><span class="sxs-lookup"><span data-stu-id="1b8cc-119">Each call to `Stop` or each dispatched callback increments the counter.</span></span> <span data-ttu-id="1b8cc-120">各呼び出し`ICorDebugController::Continue`デクリメント カウンターです。</span><span class="sxs-lookup"><span data-stu-id="1b8cc-120">Each call to `ICorDebugController::Continue` decrements the counter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b8cc-121">要件</span><span class="sxs-lookup"><span data-stu-id="1b8cc-121">Requirements</span></span>  
 <span data-ttu-id="1b8cc-122">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1b8cc-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b8cc-123">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b8cc-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b8cc-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b8cc-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b8cc-125">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b8cc-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b8cc-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b8cc-126">See Also</span></span>  
 

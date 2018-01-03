---
title: "ICorDebugManagedCallback2::ChangeConnection メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.ChangeConnection
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::ChangeConnection
helpviewer_keywords:
- ICorDebugManagedCallback2::ChangeConnection method [.NET Framework debugging]
- ChangeConnection method [.NET Framework debugging]
ms.assetid: 7263f9a9-4c0b-4d82-a181-288873fb2b18
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ba7e84c11f2fc8619b7046e222a742ee3298554
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a><span data-ttu-id="7a50e-102">ICorDebugManagedCallback2::ChangeConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="7a50e-102">ICorDebugManagedCallback2::ChangeConnection Method</span></span>
<span data-ttu-id="7a50e-103">指定した接続に関連付けられているタスクのセットが変更されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="7a50e-103">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a50e-104">構文</span><span class="sxs-lookup"><span data-stu-id="7a50e-104">Syntax</span></span>  
  
```  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a50e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7a50e-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="7a50e-106">[in]変更された接続を含むプロセスを表す"ICorDebugProcess"オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7a50e-106">[in] A pointer to an "ICorDebugProcess" object that represents the process containing the connection that changed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="7a50e-107">[in]変更された接続の ID。</span><span class="sxs-lookup"><span data-stu-id="7a50e-107">[in] The ID of the connection that changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a50e-108">コメント</span><span class="sxs-lookup"><span data-stu-id="7a50e-108">Remarks</span></span>  
 <span data-ttu-id="7a50e-109">A`ChangeConnection`コールバックは、次の場合のいずれかで発生します。</span><span class="sxs-lookup"><span data-stu-id="7a50e-109">A `ChangeConnection` callback will be fired in either of the following cases:</span></span>  
  
-   <span data-ttu-id="7a50e-110">デバッガーがいつ接続を含むプロセスにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="7a50e-110">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="7a50e-111">ここでは、ランタイムが生成されディスパッチ、 [icordebugmanagedcallback 2::createconnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)イベントおよび`ChangeConnection`プロセス内の各接続のイベントです。</span><span class="sxs-lookup"><span data-stu-id="7a50e-111">In this case, the runtime will generate and dispatch a [ICorDebugManagedCallback2::CreateConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md) event and a `ChangeConnection` event for each connection in the process.</span></span> <span data-ttu-id="7a50e-112">A`ChangeConnection`イベントが作成されてからその接続の一連のタスクが変更されたかどうかに関係なく、すべての既存の接続を生成します。</span><span class="sxs-lookup"><span data-stu-id="7a50e-112">A `ChangeConnection` event is generated for every existing connection, regardless of whether that connection’s set of tasks has been changed since its creation.</span></span>  
  
-   <span data-ttu-id="7a50e-113">ホストが呼び出したとき[iclrdebugmanager::setconnectiontasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)で、 [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="7a50e-113">When a host calls [ICLRDebugManager::SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
 <span data-ttu-id="7a50e-114">デバッガーは、新しい変更を取得するプロセスのすべてのスレッドをスキャンする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a50e-114">The debugger should scan all threads in the process to pick up the new changes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a50e-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="7a50e-115">Requirements</span></span>  
 <span data-ttu-id="7a50e-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7a50e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a50e-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a50e-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a50e-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a50e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a50e-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a50e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a50e-120">参照</span><span class="sxs-lookup"><span data-stu-id="7a50e-120">See Also</span></span>  
 [<span data-ttu-id="7a50e-121">ICorDebugManagedCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7a50e-121">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="7a50e-122">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7a50e-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

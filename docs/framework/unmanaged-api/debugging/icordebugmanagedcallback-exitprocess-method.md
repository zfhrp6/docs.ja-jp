---
title: "ICorDebugManagedCallback::ExitProcess メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.ExitProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7be74520fff65b113f54d82305a84dd183286876
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a><span data-ttu-id="08178-102">ICorDebugManagedCallback::ExitProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="08178-102">ICorDebugManagedCallback::ExitProcess Method</span></span>
<span data-ttu-id="08178-103">プロセスが終了していることをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="08178-103">Notifies the debugger that a process has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08178-104">構文</span><span class="sxs-lookup"><span data-stu-id="08178-104">Syntax</span></span>  
  
```  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08178-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="08178-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="08178-106">[in]ICorDebugProcess を表すオブジェクト、プロセスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="08178-106">[in] A pointer to an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08178-107">コメント</span><span class="sxs-lookup"><span data-stu-id="08178-107">Remarks</span></span>  
 <span data-ttu-id="08178-108">継続することはできません、`ExitProcess`イベント。</span><span class="sxs-lookup"><span data-stu-id="08178-108">You cannot continue from an `ExitProcess` event.</span></span> <span data-ttu-id="08178-109">このイベントが発生する非同期的に他のイベントに、停止するプロセスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="08178-109">This event may fire asynchronously to other events while the process appears to be stopped.</span></span> <span data-ttu-id="08178-110">これは、停止している間、通常の外的要因により、プロセスが終了した場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="08178-110">This can occur if the process terminates while stopped, usually due to some external force.</span></span>  
  
 <span data-ttu-id="08178-111">共通言語ランタイム (CLR) では、マネージ コールバックをディスパッチは既に場合、そのコールバックが返された後に、このイベントはまで延期されます。</span><span class="sxs-lookup"><span data-stu-id="08178-111">If the common language runtime (CLR) is already dispatching a managed callback, this event will be delayed until after that callback has returned.</span></span>  
  
 <span data-ttu-id="08178-112">`ExitProcess`イベントがシャット ダウン時に呼び出されることが保証する唯一の終了/アンロード イベント。</span><span class="sxs-lookup"><span data-stu-id="08178-112">The `ExitProcess` event is the only exit/unload event that is guaranteed to get called on shutdown.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08178-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="08178-113">Requirements</span></span>  
 <span data-ttu-id="08178-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="08178-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08178-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="08178-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08178-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08178-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08178-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08178-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08178-118">参照</span><span class="sxs-lookup"><span data-stu-id="08178-118">See Also</span></span>  
 [<span data-ttu-id="08178-119">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="08178-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

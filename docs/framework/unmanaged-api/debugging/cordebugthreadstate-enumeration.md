---
title: "CorDebugThreadState 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugThreadState
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugThreadState
helpviewer_keywords: CorDebugThreadState enumeration [.NET Framework debugging]
ms.assetid: a3ccdf18-4ec6-494d-9024-48e5c8c724f5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a5363282f2efed003238014390f50c448c529ce2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="e85d6-102">CorDebugThreadState 列挙型</span><span class="sxs-lookup"><span data-stu-id="e85d6-102">CorDebugThreadState Enumeration</span></span>
<span data-ttu-id="e85d6-103">デバッグのスレッドの状態を指定します。</span><span class="sxs-lookup"><span data-stu-id="e85d6-103">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e85d6-104">構文</span><span class="sxs-lookup"><span data-stu-id="e85d6-104">Syntax</span></span>  
  
```  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="e85d6-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="e85d6-105">Members</span></span>  
  
|<span data-ttu-id="e85d6-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="e85d6-106">Member</span></span>|<span data-ttu-id="e85d6-107">説明</span><span class="sxs-lookup"><span data-stu-id="e85d6-107">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="e85d6-108">スレッドは、デバッグ イベントが発生しない限り、自由に実行されます。</span><span class="sxs-lookup"><span data-stu-id="e85d6-108">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="e85d6-109">スレッドは実行できません。</span><span class="sxs-lookup"><span data-stu-id="e85d6-109">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e85d6-110">コメント</span><span class="sxs-lookup"><span data-stu-id="e85d6-110">Remarks</span></span>  
 <span data-ttu-id="e85d6-111">デバッガーを使用して、`CorDebugThreadState`スレッドの実行を制御する列挙です。</span><span class="sxs-lookup"><span data-stu-id="e85d6-111">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="e85d6-112">使用してスレッドの状態を設定することができます、 [icordebugthread::setdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)または[icordebugcontroller::setallthreadsdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e85d6-112">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="e85d6-113">渡されたコールバック、 [API をホストしている](../../../../docs/framework/unmanaged-api/hosting/index.md)中断状態は必要ありませんのでメッセージ ポンプを使用します。</span><span class="sxs-lookup"><span data-stu-id="e85d6-113">A callback provided to the [hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e85d6-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="e85d6-114">Requirements</span></span>  
 <span data-ttu-id="e85d6-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e85d6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e85d6-116">**ヘッダー:** CorDebug.idl、CorDegug.h</span><span class="sxs-lookup"><span data-stu-id="e85d6-116">**Header:** CorDebug.idl, CorDegug.h</span></span>  
  
 <span data-ttu-id="e85d6-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e85d6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e85d6-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e85d6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e85d6-119">参照</span><span class="sxs-lookup"><span data-stu-id="e85d6-119">See Also</span></span>  
 [<span data-ttu-id="e85d6-120">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="e85d6-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

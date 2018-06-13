---
title: CorDebugThreadState 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugThreadState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugThreadState
helpviewer_keywords:
- CorDebugThreadState enumeration [.NET Framework debugging]
ms.assetid: a3ccdf18-4ec6-494d-9024-48e5c8c724f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba8bca6d14308284c869b923853f7e27e045bca5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402940"
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="96b4a-102">CorDebugThreadState 列挙型</span><span class="sxs-lookup"><span data-stu-id="96b4a-102">CorDebugThreadState Enumeration</span></span>
<span data-ttu-id="96b4a-103">デバッグのスレッドの状態を指定します。</span><span class="sxs-lookup"><span data-stu-id="96b4a-103">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96b4a-104">構文</span><span class="sxs-lookup"><span data-stu-id="96b4a-104">Syntax</span></span>  
  
```  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="96b4a-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="96b4a-105">Members</span></span>  
  
|<span data-ttu-id="96b4a-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="96b4a-106">Member</span></span>|<span data-ttu-id="96b4a-107">説明</span><span class="sxs-lookup"><span data-stu-id="96b4a-107">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="96b4a-108">スレッドは、デバッグ イベントが発生しない限り、自由に実行されます。</span><span class="sxs-lookup"><span data-stu-id="96b4a-108">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="96b4a-109">スレッドは実行できません。</span><span class="sxs-lookup"><span data-stu-id="96b4a-109">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96b4a-110">コメント</span><span class="sxs-lookup"><span data-stu-id="96b4a-110">Remarks</span></span>  
 <span data-ttu-id="96b4a-111">デバッガーを使用して、`CorDebugThreadState`スレッドの実行を制御する列挙です。</span><span class="sxs-lookup"><span data-stu-id="96b4a-111">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="96b4a-112">使用してスレッドの状態を設定することができます、 [icordebugthread::setdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)または[icordebugcontroller::setallthreadsdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="96b4a-112">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="96b4a-113">渡されたコールバック、 [API をホストしている](../../../../docs/framework/unmanaged-api/hosting/index.md)中断状態は必要ありませんのでメッセージ ポンプを使用します。</span><span class="sxs-lookup"><span data-stu-id="96b4a-113">A callback provided to the [hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96b4a-114">要件</span><span class="sxs-lookup"><span data-stu-id="96b4a-114">Requirements</span></span>  
 <span data-ttu-id="96b4a-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="96b4a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96b4a-116">**ヘッダー:** CorDebug.idl、CorDegug.h</span><span class="sxs-lookup"><span data-stu-id="96b4a-116">**Header:** CorDebug.idl, CorDegug.h</span></span>  
  
 <span data-ttu-id="96b4a-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96b4a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96b4a-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96b4a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96b4a-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="96b4a-119">See Also</span></span>  
 [<span data-ttu-id="96b4a-120">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="96b4a-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

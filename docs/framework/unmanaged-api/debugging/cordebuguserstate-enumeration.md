---
title: CorDebugUserState 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUserState
helpviewer_keywords:
- CorDebugUserState enumeration [.NET Framework debugging]
ms.assetid: 5f6c2bcd-8102-4e3b-abc5-86ab0bd62def
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f489ab29726292f6c55151169ad9efc6f0fbfbcf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407795"
---
# <a name="cordebuguserstate-enumeration"></a><span data-ttu-id="00d71-102">CorDebugUserState 列挙型</span><span class="sxs-lookup"><span data-stu-id="00d71-102">CorDebugUserState Enumeration</span></span>
<span data-ttu-id="00d71-103">スレッドのユーザーの状態を示します。</span><span class="sxs-lookup"><span data-stu-id="00d71-103">Indicates the user state of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00d71-104">構文</span><span class="sxs-lookup"><span data-stu-id="00d71-104">Syntax</span></span>  
  
```  
typedef enum CorDebugUserState {  
    USER_STOP_REQUESTED     =  0x01,  
    USER_SUSPEND_REQUESTED  =  0x02,  
    USER_BACKGROUND         =  0x04,  
    USER_UNSTARTED          =  0x08,  
    USER_STOPPED            =  0x10,  
    USER_WAIT_SLEEP_JOIN    =  0x20,  
    USER_SUSPENDED          =  0x40,  
    USER_UNSAFE_POINT       =  0x80,  
    USER_THREADPOOL         = 0x100  
} CorDebugUserState;  
```  
  
## <a name="members"></a><span data-ttu-id="00d71-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="00d71-105">Members</span></span>  
  
|<span data-ttu-id="00d71-106">[値]</span><span class="sxs-lookup"><span data-stu-id="00d71-106">Value</span></span>|<span data-ttu-id="00d71-107">説明</span><span class="sxs-lookup"><span data-stu-id="00d71-107">Description</span></span>|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|<span data-ttu-id="00d71-108">スレッドの終了が要求されました。</span><span class="sxs-lookup"><span data-stu-id="00d71-108">A termination of the thread has been requested.</span></span>|  
|`USER_SUSPEND_REQUESTED`|<span data-ttu-id="00d71-109">スレッドの中断が要求されました。</span><span class="sxs-lookup"><span data-stu-id="00d71-109">A suspension of the thread has been requested.</span></span>|  
|`USER_BACKGROUND`|<span data-ttu-id="00d71-110">スレッドのバック グラウンドで実行します。</span><span class="sxs-lookup"><span data-stu-id="00d71-110">The thread is running in the background.</span></span>|  
|`USER_UNSTARTED`|<span data-ttu-id="00d71-111">スレッドは、実行を開始していません。</span><span class="sxs-lookup"><span data-stu-id="00d71-111">The thread has not started executing.</span></span>|  
|`USER_STOPPED`|<span data-ttu-id="00d71-112">スレッドが終了しました。</span><span class="sxs-lookup"><span data-stu-id="00d71-112">The thread has been terminated.</span></span>|  
|`USER_WAIT_SLEEP_JOIN`|<span data-ttu-id="00d71-113">スレッドは、別のスレッドにタスクの完了を待機しています。</span><span class="sxs-lookup"><span data-stu-id="00d71-113">The thread is waiting for another thread to complete a task.</span></span>|  
|`USER_SUSPENDED`|<span data-ttu-id="00d71-114">スレッドが中断されました。</span><span class="sxs-lookup"><span data-stu-id="00d71-114">The thread has been suspended.</span></span>|  
|`USER_UNSAFE_POINT`|<span data-ttu-id="00d71-115">スレッドは、アンセーフ ポイントでです。</span><span class="sxs-lookup"><span data-stu-id="00d71-115">The thread is at an unsafe point.</span></span> <span data-ttu-id="00d71-116">つまり、スレッドはポイントで実行ガベージ コレクションを妨げること可能性があります。</span><span class="sxs-lookup"><span data-stu-id="00d71-116">That is, the thread is at a point in execution where it may block garbage collection.</span></span><br /><br /> <span data-ttu-id="00d71-117">デバッグ イベントは、安全でないポイントからディスパッチすることがありますが、安全でない時点でスレッドを中断する可能性が高いデッドロックが発生スレッドが再開されるまでです。</span><span class="sxs-lookup"><span data-stu-id="00d71-117">Debug events may be dispatched from unsafe points, but suspending a thread at an unsafe point  will very likely cause a deadlock until the thread is resumed.</span></span> <span data-ttu-id="00d71-118">安全性と安全でないポイントは、・ イン タイム (JIT) とガベージ コレクションの実装によって決まります。</span><span class="sxs-lookup"><span data-stu-id="00d71-118">The safe and unsafe points are determined by the just-in-time (JIT) and garbage collection implementation.</span></span>|  
|`USER_THREADPOOL`|<span data-ttu-id="00d71-119">スレッドはスレッド プールです。</span><span class="sxs-lookup"><span data-stu-id="00d71-119">The thread is from the thread pool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00d71-120">コメント</span><span class="sxs-lookup"><span data-stu-id="00d71-120">Remarks</span></span>  
 <span data-ttu-id="00d71-121">スレッドのユーザーの状態は、スレッドが、デバッガーがチェック時に状態です。</span><span class="sxs-lookup"><span data-stu-id="00d71-121">The user state of a thread is the state that the thread has when the debugger examines it.</span></span> <span data-ttu-id="00d71-122">スレッドは、ユーザー状態の組み合わせがあります。</span><span class="sxs-lookup"><span data-stu-id="00d71-122">A thread may have a combination of user states.</span></span>  
  
 <span data-ttu-id="00d71-123">使用して、 [icordebugthread::getuserstate](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)スレッドのユーザー状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="00d71-123">Use the [ICorDebugThread::GetUserState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md) method to retrieve a thread's user state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00d71-124">要件</span><span class="sxs-lookup"><span data-stu-id="00d71-124">Requirements</span></span>  
 <span data-ttu-id="00d71-125">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="00d71-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00d71-126">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="00d71-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00d71-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00d71-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00d71-128">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00d71-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00d71-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="00d71-129">See Also</span></span>  
 [<span data-ttu-id="00d71-130">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="00d71-130">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

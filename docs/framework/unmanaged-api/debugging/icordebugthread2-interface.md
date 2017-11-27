---
title: ICorDebugThread2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread2
helpviewer_keywords: ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5d3a554d075adb56294e4693b234ce22735fb982
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthread2-interface1"></a><span data-ttu-id="f5a13-102">ICorDebugThread2 Interface1</span><span class="sxs-lookup"><span data-stu-id="f5a13-102">ICorDebugThread2 Interface1</span></span>
<span data-ttu-id="f5a13-103">ICorDebugThread インターフェイスを論理的に拡張として機能します。</span><span class="sxs-lookup"><span data-stu-id="f5a13-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f5a13-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="f5a13-104">Methods</span></span>  
  
|<span data-ttu-id="f5a13-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="f5a13-105">Method</span></span>|<span data-ttu-id="f5a13-106">説明</span><span class="sxs-lookup"><span data-stu-id="f5a13-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f5a13-107">GetActiveFunctions メソッド</span><span class="sxs-lookup"><span data-stu-id="f5a13-107">GetActiveFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="f5a13-108">スレッドのフレームでアクティブな関数に関するデータを含む COR_ACTIVE_FUNCTION インスタンスの配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="f5a13-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="f5a13-109">GetConnectionID メソッド</span><span class="sxs-lookup"><span data-stu-id="f5a13-109">GetConnectionID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="f5a13-110">この接続の識別子を取得`ICorDebugThread2`です。</span><span class="sxs-lookup"><span data-stu-id="f5a13-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="f5a13-111">GetTaskID メソッド</span><span class="sxs-lookup"><span data-stu-id="f5a13-111">GetTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|<span data-ttu-id="f5a13-112">このタスクの識別子を取得`ICorDebugThread2`です。</span><span class="sxs-lookup"><span data-stu-id="f5a13-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="f5a13-113">GetVolatileOSThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="f5a13-113">GetVolatileOSThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="f5a13-114">このオペレーティング システムのスレッド識別子を取得`ICorDebugThread2`です。</span><span class="sxs-lookup"><span data-stu-id="f5a13-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="f5a13-115">InterceptCurrentException メソッド</span><span class="sxs-lookup"><span data-stu-id="f5a13-115">InterceptCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="f5a13-116">スレッドで現在の例外をインターセプトするデバッガーを使用します。</span><span class="sxs-lookup"><span data-stu-id="f5a13-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5a13-117">コメント</span><span class="sxs-lookup"><span data-stu-id="f5a13-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5a13-118">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="f5a13-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5a13-119">要件</span><span class="sxs-lookup"><span data-stu-id="f5a13-119">Requirements</span></span>  
 <span data-ttu-id="f5a13-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f5a13-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5a13-121">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5a13-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5a13-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5a13-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5a13-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5a13-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5a13-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5a13-124">See Also</span></span>  
 [<span data-ttu-id="f5a13-125">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f5a13-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

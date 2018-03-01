---
title: "ICorDebugManagedCallback2 インターフェイス"
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
- ICorDebugManagedCallback2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2
helpviewer_keywords:
- ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: cf7b7cfa-1c4b-4d8c-be70-4f9ed15a788b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2a46e8e4f23c57391877d8cb6ba6b35d50de151b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2-interface"></a><span data-ttu-id="a2062-102">ICorDebugManagedCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a2062-102">ICorDebugManagedCallback2 Interface</span></span>
<span data-ttu-id="a2062-103">デバッガーの例外処理およびマネージ デバッグ アシスタント (MDA: Managed Debugging Assistants) をサポートするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a2062-103">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="a2062-104">`ICorDebugManagedCallback2`論理拡張機能は、 [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="a2062-104">`ICorDebugManagedCallback2` is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a2062-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a2062-105">Methods</span></span>  
  
|<span data-ttu-id="a2062-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="a2062-106">Method</span></span>|<span data-ttu-id="a2062-107">説明</span><span class="sxs-lookup"><span data-stu-id="a2062-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a2062-108">ChangeConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="a2062-108">ChangeConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|<span data-ttu-id="a2062-109">指定した接続に関連付けられているタスクのセットが変更されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="a2062-109">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>|  
|[<span data-ttu-id="a2062-110">CreateConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="a2062-110">CreateConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|<span data-ttu-id="a2062-111">新しい接続が作成されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="a2062-111">Notifies the debugger that a new connection has been created.</span></span>|  
|[<span data-ttu-id="a2062-112">DestroyConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="a2062-112">DestroyConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|<span data-ttu-id="a2062-113">指定された接続が終了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="a2062-113">Notifies the debugger that the specified connection has been terminated.</span></span>|  
|[<span data-ttu-id="a2062-114">Exception メソッド</span><span class="sxs-lookup"><span data-stu-id="a2062-114">Exception Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|<span data-ttu-id="a2062-115">例外ハンドラーの検索が開始されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="a2062-115">Notifies the debugger that a search for an exception handler has started.</span></span>|  
|[<span data-ttu-id="a2062-116">ExceptionUnwind メソッド</span><span class="sxs-lookup"><span data-stu-id="a2062-116">ExceptionUnwind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|<span data-ttu-id="a2062-117">例外のアンワインド処理中に状態の通知を提供します。</span><span class="sxs-lookup"><span data-stu-id="a2062-117">Provides a status notification during the exception unwinding process.</span></span>|  
|[<span data-ttu-id="a2062-118">FunctionRemapComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="a2062-118">FunctionRemapComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|<span data-ttu-id="a2062-119">コードの実行を編集された関数の新しいバージョンに切り替えたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="a2062-119">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>|  
|[<span data-ttu-id="a2062-120">FunctionRemapOpportunity メソッド</span><span class="sxs-lookup"><span data-stu-id="a2062-120">FunctionRemapOpportunity Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|<span data-ttu-id="a2062-121">コードの実行が編集された関数の古いバージョンのシーケンス ポイントに達したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="a2062-121">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>|  
|[<span data-ttu-id="a2062-122">MDANotification メソッド</span><span class="sxs-lookup"><span data-stu-id="a2062-122">MDANotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|<span data-ttu-id="a2062-123">コードの実行でマネージ デバッグ アシスタント (MDA) メッセージが発生したことの通知を提供します。</span><span class="sxs-lookup"><span data-stu-id="a2062-123">Provides notification that code execution has encountered a managed debugging assistant (MDA) message.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2062-124">コメント</span><span class="sxs-lookup"><span data-stu-id="a2062-124">Remarks</span></span>  
 <span data-ttu-id="a2062-125">`ICorDebugManagedCallback2`インターフェイスを拡張、`ICorDebugManagedCallback`を .NET Framework version 2.0 で導入された新しいデバッグ イベントを処理するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="a2062-125">The `ICorDebugManagedCallback2` interface extends the `ICorDebugManagedCallback` interface to handle new debug events introduced in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="a2062-126">デバッガーを実装する必要があります`ICorDebugManagedCallback2`場合は、.NET Framework 2.0 アプリケーションのデバッグします。</span><span class="sxs-lookup"><span data-stu-id="a2062-126">A debugger must implement `ICorDebugManagedCallback2` if it is debugging .NET Framework 2.0 applications.</span></span> <span data-ttu-id="a2062-127">インスタンス`ICorDebugManagedCallback`または`ICorDebugManagedCallback2`するコールバック オブジェクトとして渡される[icordebug::setmanagedhandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="a2062-127">An instance of `ICorDebugManagedCallback` or `ICorDebugManagedCallback2` is passed as the callback object to [ICorDebug::SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2062-128">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="a2062-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2062-129">必要条件</span><span class="sxs-lookup"><span data-stu-id="a2062-129">Requirements</span></span>  
 <span data-ttu-id="a2062-130">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a2062-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2062-131">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2062-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2062-132">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2062-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2062-133">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2062-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2062-134">参照</span><span class="sxs-lookup"><span data-stu-id="a2062-134">See Also</span></span>  
 [<span data-ttu-id="a2062-135">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="a2062-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="a2062-136">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a2062-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="a2062-137">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a2062-137">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

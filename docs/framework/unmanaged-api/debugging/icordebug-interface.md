---
title: "ICorDebug インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug
helpviewer_keywords: ICorDebug interface [.NET Framework debugging]
ms.assetid: 33f431d7-ab1a-494d-8af2-20ab15aba194
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 62a29133252277cbf614a1916af6fa4c6905a920
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebug-interface"></a><span data-ttu-id="9ba9a-102">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ba9a-102">ICorDebug Interface</span></span>
<span data-ttu-id="9ba9a-103">開発者は、共通言語ランタイム (CLR) 環境でアプリケーションをデバッグできるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9ba9a-103">Provides methods that allow developers to debug applications in the common language runtime (CLR) environment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ba9a-104">Windows 95、Windows 98 または Windows ME、または (IA64、AMD64 など) と x86 以外のプラットフォームでは、混合モード (マネージとネイティブ コード) デバッグはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="9ba9a-104">Mixed-mode (managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA64 and AMD64).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9ba9a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="9ba9a-105">Methods</span></span>  
  
|<span data-ttu-id="9ba9a-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="9ba9a-106">Method</span></span>|<span data-ttu-id="9ba9a-107">説明</span><span class="sxs-lookup"><span data-stu-id="9ba9a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9ba9a-108">CanLaunchOrAttach メソッド</span><span class="sxs-lookup"><span data-stu-id="9ba9a-108">CanLaunchOrAttach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|<span data-ttu-id="9ba9a-109">現在のコンピューターおよびランタイムの構成のコンテキスト内で、新しいプロセスの起動または特定のプロセスへのアタッチを実行するかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="9ba9a-109">Determines whether launching a new process or attaching to the given process is possible within the context of the current machine and runtime configuration.</span></span>|  
|[<span data-ttu-id="9ba9a-110">CreateProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="9ba9a-110">CreateProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|<span data-ttu-id="9ba9a-111">プロセスと、デバッガーの制御下で、プライマリ スレッドが起動します。</span><span class="sxs-lookup"><span data-stu-id="9ba9a-111">Launches a process and its primary thread under the control of the debugger.</span></span>|  
|[<span data-ttu-id="9ba9a-112">DebugActiveProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="9ba9a-112">DebugActiveProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|<span data-ttu-id="9ba9a-113">既存のプロセスにデバッガーをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="9ba9a-113">Attaches the debugger to an existing process.</span></span>|  
|[<span data-ttu-id="9ba9a-114">EnumerateProcesses メソッド</span><span class="sxs-lookup"><span data-stu-id="9ba9a-114">EnumerateProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|<span data-ttu-id="9ba9a-115">デバッグ中のプロセスの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="9ba9a-115">Gets an enumerator for the processes that are being debugged.</span></span>|  
|[<span data-ttu-id="9ba9a-116">GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="9ba9a-116">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|<span data-ttu-id="9ba9a-117">特定のプロセス ID に置き換えます。"ICorDebugProcess"オブジェクトを返します</span><span class="sxs-lookup"><span data-stu-id="9ba9a-117">Returns the "ICorDebugProcess" object with the given process ID.</span></span>|  
|[<span data-ttu-id="9ba9a-118">Initialize メソッド</span><span class="sxs-lookup"><span data-stu-id="9ba9a-118">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|<span data-ttu-id="9ba9a-119">初期化、`ICorDebug`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="9ba9a-119">Initializes the `ICorDebug` object.</span></span>|  
|[<span data-ttu-id="9ba9a-120">SetManagedHandler メソッド</span><span class="sxs-lookup"><span data-stu-id="9ba9a-120">SetManagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|<span data-ttu-id="9ba9a-121">マネージ イベントのイベント ハンドラー オブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="9ba9a-121">Specifies the event handler object for managed events.</span></span>|  
|[<span data-ttu-id="9ba9a-122">SetUnmanagedHandler メソッド</span><span class="sxs-lookup"><span data-stu-id="9ba9a-122">SetUnmanagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|<span data-ttu-id="9ba9a-123">管理されていないイベントのイベント ハンドラー オブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="9ba9a-123">Specifies the event handler object for unmanaged events.</span></span>|  
|[<span data-ttu-id="9ba9a-124">Terminate メソッド</span><span class="sxs-lookup"><span data-stu-id="9ba9a-124">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|<span data-ttu-id="9ba9a-125">終了、`ICorDebug`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="9ba9a-125">Terminates the `ICorDebug` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ba9a-126">コメント</span><span class="sxs-lookup"><span data-stu-id="9ba9a-126">Remarks</span></span>  
 <span data-ttu-id="9ba9a-127">`ICorDebug`デバッガー プロセスのイベントの処理ループを表します。</span><span class="sxs-lookup"><span data-stu-id="9ba9a-127">`ICorDebug` represents an event processing loop for a debugger process.</span></span> <span data-ttu-id="9ba9a-128">デバッガーが待つ必要があります、 [icordebugmanagedcallback::exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)このインターフェイスを解放する前に、デバッグ中のすべてのプロセスからのコールバック。</span><span class="sxs-lookup"><span data-stu-id="9ba9a-128">The debugger must wait for the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback from all processes being debugged before releasing this interface.</span></span>  
  
 <span data-ttu-id="9ba9a-129">`ICorDebug`オブジェクトは、初期のオブジェクトをさらに管理されているすべてのデバッグを制御します。</span><span class="sxs-lookup"><span data-stu-id="9ba9a-129">The `ICorDebug` object is the initial object to control all further managed debugging.</span></span> <span data-ttu-id="9ba9a-130">.NET Framework version 1.0 および 1.1 では、このオブジェクトは、 `CoClass` COM から作成されたオブジェクト</span><span class="sxs-lookup"><span data-stu-id="9ba9a-130">In the .NET Framework versions 1.0 and 1.1, this object was a `CoClass` object created from COM.</span></span> <span data-ttu-id="9ba9a-131">.NET Framework version 2.0 では、このオブジェクトが不要になった、`CoClass`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="9ba9a-131">In the .NET Framework version 2.0, this object is no longer a `CoClass` object.</span></span> <span data-ttu-id="9ba9a-132">作成する必要があります、 [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)は複数のバージョンに対応する関数。</span><span class="sxs-lookup"><span data-stu-id="9ba9a-132">It must be created by the [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) function, which is more version-aware.</span></span> <span data-ttu-id="9ba9a-133">この新しい作成関数により、クライアントの特定の実装を取得する`ICorDebug`もに、デバッグ API の特定のバージョンをエミュレートします。</span><span class="sxs-lookup"><span data-stu-id="9ba9a-133">This new creation function enables clients to get a specific implementation of `ICorDebug`, which also emulates a specific version of the debugging API.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ba9a-134">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="9ba9a-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ba9a-135">要件</span><span class="sxs-lookup"><span data-stu-id="9ba9a-135">Requirements</span></span>  
 <span data-ttu-id="9ba9a-136">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ba9a-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ba9a-137">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ba9a-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ba9a-138">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ba9a-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ba9a-139">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ba9a-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ba9a-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ba9a-140">See Also</span></span>  
 [<span data-ttu-id="9ba9a-141">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ba9a-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

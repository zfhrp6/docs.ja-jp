---
title: "Silverlight デバッグ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bf39d2dd12207d594c7bf5bd5b249d82c3f15d3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="silverlight-debugging"></a><span data-ttu-id="2f2af-102">Silverlight デバッグ</span><span class="sxs-lookup"><span data-stu-id="2f2af-102">Silverlight Debugging</span></span>
<span data-ttu-id="2f2af-103">このセクションのトピックでは、Windows オペレーティング システム上または Macintosh プラットフォーム上で動作している Silverlight ベースのアプリケーションのデバッグをサポートするために共通言語ランタイム (CLR: Common Language Runtime) で提供される環境とインターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2f2af-103">The topics in this section describe the environment and interfaces that the common language runtime (CLR) provides to support debugging Silverlight-based applications that are running on the Windows operating system, or on the Macintosh platform.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2f2af-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="2f2af-104">In This Section</span></span>  
 [<span data-ttu-id="2f2af-105">EnumerateCLRs 関数</span><span class="sxs-lookup"><span data-stu-id="2f2af-105">EnumerateCLRs Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 <span data-ttu-id="2f2af-106">プロセスで CLR を列挙するメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="2f2af-106">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
 [<span data-ttu-id="2f2af-107">CloseCLREnumeration 関数</span><span class="sxs-lookup"><span data-stu-id="2f2af-107">CloseCLREnumeration Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 <span data-ttu-id="2f2af-108">有効な CLR 継続スタートアップ イベントによって返されるハンドルの配列内にあるを閉じ、 [EnumerateCLRs 関数](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)、し、ハンドルおよび文字列パス配列のメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="2f2af-108">Closes any valid CLR continue-startup events located in an array of handles returned by the [EnumerateCLRs Function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
 [<span data-ttu-id="2f2af-109">CreateCoreClrDebugTarget 関数</span><span class="sxs-lookup"><span data-stu-id="2f2af-109">CreateCoreClrDebugTarget Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 <span data-ttu-id="2f2af-110">プロセスおよびランタイムの列挙のためのリモート ターゲットへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="2f2af-110">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="2f2af-111">CreateCordbObject 関数</span><span class="sxs-lookup"><span data-stu-id="2f2af-111">CreateCordbObject Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 <span data-ttu-id="2f2af-112">リモート プロセスでマネージ デバッグ セッションをインスタンス化するための機能を提供するデバッガー インターフェイスを作成します。</span><span class="sxs-lookup"><span data-stu-id="2f2af-112">Creates a debugger interface that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
 [<span data-ttu-id="2f2af-113">CreateVersionStringFromModule 関数</span><span class="sxs-lookup"><span data-stu-id="2f2af-113">CreateVersionStringFromModule Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 <span data-ttu-id="2f2af-114">対象プロセス内の CLR パスからバージョン文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="2f2af-114">Creates a version string from a CLR path in a target process.</span></span>  
  
 [<span data-ttu-id="2f2af-115">CreateDebuggingInterfaceFromVersion 関数</span><span class="sxs-lookup"><span data-stu-id="2f2af-115">CreateDebuggingInterfaceFromVersion Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 <span data-ttu-id="2f2af-116">返された CLR バージョン文字列を受け入れる[CreateVersionStringFromModule 関数](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)関数、および対応するデバッガー インターフェイスを返します。</span><span class="sxs-lookup"><span data-stu-id="2f2af-116">Accepts a CLR version string returned from [CreateVersionStringFromModule Function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)function, and returns a corresponding debugger interface.</span></span>  
  
 [<span data-ttu-id="2f2af-117">CoreClrDebugProcInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="2f2af-117">CoreClrDebugProcInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 <span data-ttu-id="2f2af-118">リモート コンピューターで実行されているプロセスを表します。</span><span class="sxs-lookup"><span data-stu-id="2f2af-118">Represents a process that is running on a remote machine.</span></span>  
  
 [<span data-ttu-id="2f2af-119">CoreClrDebugRuntimeInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="2f2af-119">CoreClrDebugRuntimeInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 <span data-ttu-id="2f2af-120">リモート コンピューター上のプロセスに読み込まれる CLR インスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="2f2af-120">Represents a CLR instance that is loaded in a process on a remote machine.</span></span>  
  
 [<span data-ttu-id="2f2af-121">GetStartupNotificationEvent 関数</span><span class="sxs-lookup"><span data-stu-id="2f2af-121">GetStartupNotificationEvent Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 <span data-ttu-id="2f2af-122">指定された対象プロセスに読み込まれている任意の共通言語ランタイム (CLR: Common Language Runtime) によって通知されるイベント ハンドルを作成または開きます。</span><span class="sxs-lookup"><span data-stu-id="2f2af-122">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
 [<span data-ttu-id="2f2af-123">ICoreClrDebugTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2f2af-123">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 <span data-ttu-id="2f2af-124">プロセスおよびランタイムの列挙のためのリモート ターゲットへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="2f2af-124">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="2f2af-125">InitDbgTransportManager 関数</span><span class="sxs-lookup"><span data-stu-id="2f2af-125">InitDbgTransportManager Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 <span data-ttu-id="2f2af-126">プロセスおよびランタイムの列挙のためにリモート ターゲットに接続するよう、トランスポート マネージャーを初期化します。</span><span class="sxs-lookup"><span data-stu-id="2f2af-126">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="2f2af-127">ShutdownDbgTransportManager 関数</span><span class="sxs-lookup"><span data-stu-id="2f2af-127">ShutdownDbgTransportManager Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 <span data-ttu-id="2f2af-128">リモート ターゲット コンピューターへの接続用のトランスポート マネージャーをシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="2f2af-128">Shuts down the transport manager for a connection to a remote target machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f2af-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f2af-129">See Also</span></span>  
 [<span data-ttu-id="2f2af-130">デバッグ コクラス</span><span class="sxs-lookup"><span data-stu-id="2f2af-130">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
 [<span data-ttu-id="2f2af-131">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="2f2af-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="2f2af-132">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="2f2af-132">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
 [<span data-ttu-id="2f2af-133">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="2f2af-133">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="2f2af-134">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="2f2af-134">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)

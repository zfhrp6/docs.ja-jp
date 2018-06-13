---
title: Silverlight デバッグ
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80cee666a05432099a380a5ac547a5ca28698c31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436034"
---
# <a name="silverlight-debugging"></a><span data-ttu-id="8fd02-102">Silverlight デバッグ</span><span class="sxs-lookup"><span data-stu-id="8fd02-102">Silverlight Debugging</span></span>
<span data-ttu-id="8fd02-103">このセクションのトピックでは、Windows オペレーティング システム上または Macintosh プラットフォーム上で動作している Silverlight ベースのアプリケーションのデバッグをサポートするために共通言語ランタイム (CLR: Common Language Runtime) で提供される環境とインターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8fd02-103">The topics in this section describe the environment and interfaces that the common language runtime (CLR) provides to support debugging Silverlight-based applications that are running on the Windows operating system, or on the Macintosh platform.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8fd02-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="8fd02-104">In This Section</span></span>  
 [<span data-ttu-id="8fd02-105">EnumerateCLRs 関数</span><span class="sxs-lookup"><span data-stu-id="8fd02-105">EnumerateCLRs Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 <span data-ttu-id="8fd02-106">プロセスで CLR を列挙するメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="8fd02-106">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
 [<span data-ttu-id="8fd02-107">CloseCLREnumeration 関数</span><span class="sxs-lookup"><span data-stu-id="8fd02-107">CloseCLREnumeration Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 <span data-ttu-id="8fd02-108">有効な CLR 継続スタートアップ イベントによって返されるハンドルの配列内にあるを閉じ、 [EnumerateCLRs 関数](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)、し、ハンドルおよび文字列パス配列のメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="8fd02-108">Closes any valid CLR continue-startup events located in an array of handles returned by the [EnumerateCLRs Function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
 [<span data-ttu-id="8fd02-109">CreateCoreClrDebugTarget 関数</span><span class="sxs-lookup"><span data-stu-id="8fd02-109">CreateCoreClrDebugTarget Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 <span data-ttu-id="8fd02-110">プロセスおよびランタイムの列挙のためのリモート ターゲットへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="8fd02-110">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="8fd02-111">CreateCordbObject 関数</span><span class="sxs-lookup"><span data-stu-id="8fd02-111">CreateCordbObject Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 <span data-ttu-id="8fd02-112">リモート プロセスでマネージ デバッグ セッションをインスタンス化するための機能を提供するデバッガー インターフェイスを作成します。</span><span class="sxs-lookup"><span data-stu-id="8fd02-112">Creates a debugger interface that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
 [<span data-ttu-id="8fd02-113">CreateVersionStringFromModule 関数</span><span class="sxs-lookup"><span data-stu-id="8fd02-113">CreateVersionStringFromModule Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 <span data-ttu-id="8fd02-114">対象プロセス内の CLR パスからバージョン文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="8fd02-114">Creates a version string from a CLR path in a target process.</span></span>  
  
 [<span data-ttu-id="8fd02-115">CreateDebuggingInterfaceFromVersion 関数</span><span class="sxs-lookup"><span data-stu-id="8fd02-115">CreateDebuggingInterfaceFromVersion Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 <span data-ttu-id="8fd02-116">返された CLR バージョン文字列を受け入れる[CreateVersionStringFromModule 関数](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)関数、および対応するデバッガー インターフェイスを返します。</span><span class="sxs-lookup"><span data-stu-id="8fd02-116">Accepts a CLR version string returned from [CreateVersionStringFromModule Function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)function, and returns a corresponding debugger interface.</span></span>  
  
 [<span data-ttu-id="8fd02-117">CoreClrDebugProcInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="8fd02-117">CoreClrDebugProcInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 <span data-ttu-id="8fd02-118">リモート コンピューターで実行されているプロセスを表します。</span><span class="sxs-lookup"><span data-stu-id="8fd02-118">Represents a process that is running on a remote machine.</span></span>  
  
 [<span data-ttu-id="8fd02-119">CoreClrDebugRuntimeInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="8fd02-119">CoreClrDebugRuntimeInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 <span data-ttu-id="8fd02-120">リモート コンピューター上のプロセスに読み込まれる CLR インスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="8fd02-120">Represents a CLR instance that is loaded in a process on a remote machine.</span></span>  
  
 [<span data-ttu-id="8fd02-121">GetStartupNotificationEvent 関数</span><span class="sxs-lookup"><span data-stu-id="8fd02-121">GetStartupNotificationEvent Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 <span data-ttu-id="8fd02-122">指定された対象プロセスに読み込まれている任意の共通言語ランタイム (CLR: Common Language Runtime) によって通知されるイベント ハンドルを作成または開きます。</span><span class="sxs-lookup"><span data-stu-id="8fd02-122">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
 [<span data-ttu-id="8fd02-123">ICoreClrDebugTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8fd02-123">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 <span data-ttu-id="8fd02-124">プロセスおよびランタイムの列挙のためのリモート ターゲットへの接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="8fd02-124">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="8fd02-125">InitDbgTransportManager 関数</span><span class="sxs-lookup"><span data-stu-id="8fd02-125">InitDbgTransportManager Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 <span data-ttu-id="8fd02-126">プロセスおよびランタイムの列挙のためにリモート ターゲットに接続するよう、トランスポート マネージャーを初期化します。</span><span class="sxs-lookup"><span data-stu-id="8fd02-126">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="8fd02-127">ShutdownDbgTransportManager 関数</span><span class="sxs-lookup"><span data-stu-id="8fd02-127">ShutdownDbgTransportManager Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 <span data-ttu-id="8fd02-128">リモート ターゲット コンピューターへの接続用のトランスポート マネージャーをシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="8fd02-128">Shuts down the transport manager for a connection to a remote target machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fd02-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="8fd02-129">See Also</span></span>  
 [<span data-ttu-id="8fd02-130">デバッグ コクラス</span><span class="sxs-lookup"><span data-stu-id="8fd02-130">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
 [<span data-ttu-id="8fd02-131">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8fd02-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8fd02-132">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="8fd02-132">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
 [<span data-ttu-id="8fd02-133">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="8fd02-133">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="8fd02-134">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="8fd02-134">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)

---
title: "マネージ スレッドの例外"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unhandled exceptions,in managed threads
- threading [.NET Framework],unhandled exceptions
- threading [.NET Framework],exceptions in managed threads
- managed threading
ms.assetid: 11294769-2e89-43cb-890e-ad4ad79cfbee
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4f68a7aebdb1625b149287d70fd91c2108a658b9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="exceptions-in-managed-threads"></a><span data-ttu-id="a6616-102">マネージ スレッドの例外</span><span class="sxs-lookup"><span data-stu-id="a6616-102">Exceptions in Managed Threads</span></span>
<span data-ttu-id="a6616-103">.NET Framework バージョン 2.0 以降では、共通言語ランタイムはスレッド内のほとんどのハンドルされない例外をそのまま続行させます。</span><span class="sxs-lookup"><span data-stu-id="a6616-103">Starting with the .NET Framework version 2.0, the common language runtime allows most unhandled exceptions in threads to proceed naturally.</span></span> <span data-ttu-id="a6616-104">ほとんどの場合、これはハンドルされない例外によってアプリケーションが終了することを意味します。</span><span class="sxs-lookup"><span data-stu-id="a6616-104">In most cases this means that the unhandled exception causes the application to terminate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6616-105">これは、スレッド プールのスレッド内でのハンドルされない例外など、多数のハンドルされない例外に関する安全策を提供している、.NET Framework バージョン 1.0 および 1.1 からの重要な変更です。</span><span class="sxs-lookup"><span data-stu-id="a6616-105">This is a significant change from the .NET Framework versions 1.0 and 1.1, which provide a backstop for many unhandled exceptions — for example, unhandled exceptions in thread pool threads.</span></span> <span data-ttu-id="a6616-106">このトピックの「[以前のバージョンからの変更](#ChangeFromPreviousVersions)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6616-106">See [Change from Previous Versions](#ChangeFromPreviousVersions) later in this topic.</span></span>  
  
 <span data-ttu-id="a6616-107">共通言語ランタイムには、プログラム フローの制御に使用する特定のハンドルされない例外について、次のような安全策が用意されています。</span><span class="sxs-lookup"><span data-stu-id="a6616-107">The common language runtime provides a backstop for certain unhandled exceptions that are used for controlling program flow:</span></span>  
  
-   <span data-ttu-id="a6616-108"><xref:System.Threading.Thread.Abort%2A> が呼び出されたため、スレッドで <xref:System.Threading.ThreadAbortException> がスローされる。</span><span class="sxs-lookup"><span data-stu-id="a6616-108">A <xref:System.Threading.ThreadAbortException> is thrown in a thread because <xref:System.Threading.Thread.Abort%2A> was called.</span></span>  
  
-   <span data-ttu-id="a6616-109">スレッドが実行中のアプリケーション ドメインがアンロードされると、スレッドで <xref:System.AppDomainUnloadedException> がスローされる。</span><span class="sxs-lookup"><span data-stu-id="a6616-109">An <xref:System.AppDomainUnloadedException> is thrown in a thread because the application domain in which the thread is executing is being unloaded.</span></span>  
  
-   <span data-ttu-id="a6616-110">共通言語ランタイムまたはホスト プロセスは、内部例外をスローすることによってスレッドを終了します。</span><span class="sxs-lookup"><span data-stu-id="a6616-110">The common language runtime or a host process terminates the thread by throwing an internal exception.</span></span>  
  
 <span data-ttu-id="a6616-111">共通言語ランタイムによって作成されたスレッドでこれらの例外がハンドルされない場合、その例外によってスレッドは終了しますが、共通言語ランタイムは例外を続行させません。</span><span class="sxs-lookup"><span data-stu-id="a6616-111">If any of these exceptions are unhandled in threads created by the common language runtime, the exception terminates the thread, but the common language runtime does not allow the exception to proceed further.</span></span>  
  
 <span data-ttu-id="a6616-112">メイン スレッドまたはアンマネージ コードからランタイムに入ったスレッドでこれらの例外がハンドルされない場合、例外は通常どおり続行するため、アプリケーションが終了します。</span><span class="sxs-lookup"><span data-stu-id="a6616-112">If these exceptions are unhandled in the main thread, or in threads that entered the runtime from unmanaged code, they proceed normally, resulting in termination of the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6616-113">マネージ コードが例外ハンドラーをインストールする機会を得る前に、ランタイムはハンドルされない例外をスローできます。</span><span class="sxs-lookup"><span data-stu-id="a6616-113">It is possible for the runtime to throw an unhandled exception before any managed code has had a chance to install an exception handler.</span></span> <span data-ttu-id="a6616-114">マネージ コードにこのような例外をハンドルする機会がない場合でも、例外を続行させることができます。</span><span class="sxs-lookup"><span data-stu-id="a6616-114">Even though managed code had no chance to handle such an exception, the exception is allowed to proceed naturally.</span></span>  
  
## <a name="exposing-threading-problems-during-development"></a><span data-ttu-id="a6616-115">開発時におけるスレッド処理の問題の露呈</span><span class="sxs-lookup"><span data-stu-id="a6616-115">Exposing Threading Problems During Development</span></span>  
 <span data-ttu-id="a6616-116">アプリケーションを終了せずに、スレッドが暗黙に失敗したまま放置されていると、プログラミングの深刻な問題が検出されない状態になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a6616-116">When threads are allowed to fail silently, without terminating the application, serious programming problems can go undetected.</span></span> <span data-ttu-id="a6616-117">長期間実行されるサービスや他のアプリケーションでは、これは特に問題となります。</span><span class="sxs-lookup"><span data-stu-id="a6616-117">This is a particular problem for services and other applications which run for extended periods.</span></span> <span data-ttu-id="a6616-118">スレッドが失敗すると、プログラムの状態が徐々に破損します。</span><span class="sxs-lookup"><span data-stu-id="a6616-118">As threads fail, program state gradually becomes corrupted.</span></span> <span data-ttu-id="a6616-119">アプリケーションのパフォーマンスが低下する場合もあれば、アプリケーションがハングする場合もあります。</span><span class="sxs-lookup"><span data-stu-id="a6616-119">Application performance may degrade, or the application might hang.</span></span>  
  
 <span data-ttu-id="a6616-120">スレッド内でハンドルされない例外を続行させておき、結果としてオペレーティング システムにそのプログラムを終了させることで、開発およびテスト中にこのような問題が明らかになります。</span><span class="sxs-lookup"><span data-stu-id="a6616-120">Allowing unhandled exceptions in threads to proceed naturally, until the operating system terminates the program, exposes such problems during development and testing.</span></span> <span data-ttu-id="a6616-121">プログラムの終了に関するエラー報告はデバッグをサポートします。</span><span class="sxs-lookup"><span data-stu-id="a6616-121">Error reports on program terminations support debugging.</span></span>  
  
<a name="ChangeFromPreviousVersions"></a>   
## <a name="change-from-previous-versions"></a><span data-ttu-id="a6616-122">以前のバージョンからの変更</span><span class="sxs-lookup"><span data-stu-id="a6616-122">Change from Previous Versions</span></span>  
 <span data-ttu-id="a6616-123">最も重要な変更は、マネージ スレッドに関する変更です。</span><span class="sxs-lookup"><span data-stu-id="a6616-123">The most significant change pertains to managed threads.</span></span> <span data-ttu-id="a6616-124">.NET Framework バージョン 1.0 および 1.1 では、共通言語ランタイムには、次の状況でのハンドルされない例外に関する安全策が用意されています。</span><span class="sxs-lookup"><span data-stu-id="a6616-124">In the .NET Framework versions 1.0 and 1.1, the common language runtime provides a backstop for unhandled exceptions in the following situations:</span></span>  
  
-   <span data-ttu-id="a6616-125">スレッド プールのスレッドのハンドルされない例外は存在しません。</span><span class="sxs-lookup"><span data-stu-id="a6616-125">There is no such thing as an unhandled exception on a thread pool thread.</span></span> <span data-ttu-id="a6616-126">タスクが例外をスローし、その例外がハンドルされない場合、ランタイムは例外のスタック トレースをコンソールに出力し、スレッドをスレッド プールに戻します。</span><span class="sxs-lookup"><span data-stu-id="a6616-126">When a task throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then returns the thread to the thread pool.</span></span>  
  
-   <span data-ttu-id="a6616-127"><xref:System.Threading.Thread> クラスの <xref:System.Threading.Thread.Start%2A> メソッドを使用して作成されたスレッドのハンドルされない例外は存在しません。</span><span class="sxs-lookup"><span data-stu-id="a6616-127">There is no such thing as an unhandled exception on a thread created with the <xref:System.Threading.Thread.Start%2A> method of the <xref:System.Threading.Thread> class.</span></span> <span data-ttu-id="a6616-128">このようなスレッド上で実行中のコードが例外をスローし、その例外がハンドルされない場合、ランタイムは例外のスタック トレースをコンソールに出力し、スレッドを適切に終了します。</span><span class="sxs-lookup"><span data-stu-id="a6616-128">When code running on such a thread throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then gracefully terminates the thread.</span></span>  
  
-   <span data-ttu-id="a6616-129">ファイナライザー スレッドのハンドルされない例外は存在しません。</span><span class="sxs-lookup"><span data-stu-id="a6616-129">There is no such thing as an unhandled exception on the finalizer thread.</span></span> <span data-ttu-id="a6616-130">ファイナライザーが例外をスローし、その例外がハンドルされない場合、ランタイムは例外のスタック トレースをコンソールに出力し、ファイナライザー スレッドがファイナライザーの実行を再開できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a6616-130">When a finalizer throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then allows the finalizer thread to resume running finalizers.</span></span>  
  
 <span data-ttu-id="a6616-131">マネージ スレッドのフォアグラウンドまたはバックグラウンドのステータスは、この動作に影響しません。</span><span class="sxs-lookup"><span data-stu-id="a6616-131">The foreground or background status of a managed thread does not affect this behavior.</span></span>  
  
 <span data-ttu-id="a6616-132">アンマネージ コードで作成されたスレッドのハンドルされない例外の場合、微妙な相違点があります。</span><span class="sxs-lookup"><span data-stu-id="a6616-132">For unhandled exceptions on threads originating in unmanaged code, the difference is more subtle.</span></span> <span data-ttu-id="a6616-133">ランタイムの JIT アタッチ ダイアログは、ネイティブ コードを通ってきたスレッド内でのマネージ例外またはネイティブ例外に関する、オペレーティング システム ダイアログより優先されます。</span><span class="sxs-lookup"><span data-stu-id="a6616-133">The runtime JIT-attach dialog preempts the operating system dialog for managed exceptions or native exceptions on threads that have passed through native code.</span></span> <span data-ttu-id="a6616-134">プロセスは常に終了します。</span><span class="sxs-lookup"><span data-stu-id="a6616-134">The process terminates in all cases.</span></span>  
  
### <a name="migrating-code"></a><span data-ttu-id="a6616-135">コードの移行</span><span class="sxs-lookup"><span data-stu-id="a6616-135">Migrating Code</span></span>  
 <span data-ttu-id="a6616-136">通常は、この変更によってこれまでに認識されていないプログラミングの問題が明らかになるため、問題を修正できます。</span><span class="sxs-lookup"><span data-stu-id="a6616-136">In general, the change will expose previously unrecognized programming problems so that they can be fixed.</span></span> <span data-ttu-id="a6616-137">ただし、プログラマがランタイムの安全策 (スレッドを終了するなど) を利用する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="a6616-137">In some cases, however, programmers might have taken advantage of the runtime backstop, for example to terminate threads.</span></span> <span data-ttu-id="a6616-138">状況によっては、プログラマは次の移行方法のいずれかを検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6616-138">Depending on the situation, they should consider one of the following migration strategies:</span></span>  
  
-   <span data-ttu-id="a6616-139">シグナルを受信したときに、スレッドが適切に終了するようにコードを再構築します。</span><span class="sxs-lookup"><span data-stu-id="a6616-139">Restructure the code so the thread exits gracefully when a signal is received.</span></span>  
  
-   <span data-ttu-id="a6616-140">スレッドを中止するには、<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="a6616-140">Use the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method to abort the thread.</span></span>  
  
-   <span data-ttu-id="a6616-141">プロセスを終了できるように、スレッドを中止する必要がある場合は、スレッドをバックグラウンド スレッドにして、プロセス終了時にスレッドが自動的に終了するようにします。</span><span class="sxs-lookup"><span data-stu-id="a6616-141">If a thread must be stopped so that process termination can proceed, make the thread a background thread so that it is automatically terminated on process exit.</span></span>  
  
 <span data-ttu-id="a6616-142">どのような場合でも、方法は例外に関するデザイン ガイドラインに従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6616-142">In all cases, the strategy should follow the design guidelines for exceptions.</span></span> <span data-ttu-id="a6616-143">「[例外のデザイン ガイドライン](../../../docs/standard/design-guidelines/exceptions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6616-143">See [Design Guidelines for Exceptions](../../../docs/standard/design-guidelines/exceptions.md).</span></span>  
  
### <a name="application-compatibility-flag"></a><span data-ttu-id="a6616-144">アプリケーション互換性フラグ</span><span class="sxs-lookup"><span data-stu-id="a6616-144">Application Compatibility Flag</span></span>  
 <span data-ttu-id="a6616-145">一時的な互換性対策として、管理者はアプリケーション構成ファイルの `<runtime>` セクションに互換性フラグを配置できます。</span><span class="sxs-lookup"><span data-stu-id="a6616-145">As a temporary compatibility measure, administrators can place a compatibility flag in the `<runtime>` section of the application configuration file.</span></span> <span data-ttu-id="a6616-146">これにより、共通言語ランタイムをバージョン 1.0 および 1.1 の動作に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="a6616-146">This causes the common language runtime to revert to the behavior of versions 1.0 and 1.1.</span></span>  
  
```xml  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## <a name="host-override"></a><span data-ttu-id="a6616-147">ホストのオーバーライド</span><span class="sxs-lookup"><span data-stu-id="a6616-147">Host Override</span></span>  
 <span data-ttu-id="a6616-148">.NET Framework バージョン 2.0 では、アンマネージ ホストはホスト API の [ICLRPolicyManager](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) インターフェイスを使用して、共通言語ランタイムの既定のハンドルされない例外ポリシーをオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="a6616-148">In the .NET Framework version 2.0, an unmanaged host can use the [ICLRPolicyManager](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface in the Hosting API to override the default unhandled exception policy of the common language runtime.</span></span> <span data-ttu-id="a6616-149">[ICLRPolicyManager::SetUnhandledExceptionPolicy](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) 関数を使用して、ハンドルされない例外のポリシーを設定します。</span><span class="sxs-lookup"><span data-stu-id="a6616-149">The [ICLRPolicyManager::SetUnhandledExceptionPolicy](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) function is used to set the policy for unhandled exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6616-150">参照</span><span class="sxs-lookup"><span data-stu-id="a6616-150">See Also</span></span>  
 [<span data-ttu-id="a6616-151">マネージ スレッド処理の基本</span><span class="sxs-lookup"><span data-stu-id="a6616-151">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)

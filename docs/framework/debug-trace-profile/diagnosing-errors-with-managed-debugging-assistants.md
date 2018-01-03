---
title: "マネージ デバッグ アシスタントによるエラーの診断"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EHMDA
helpviewer_keywords:
- run-time error debugging
- managed code, run-time debugging
- resource debugging
- registry, MDAs
- common language runtime, debugging
- MDAs (managed debugging assistants)
- configuration files [.NET Framework], debugging runtime events
- messages, managed debugging assistants
- application configuration files, managed debugging assistants
- debugging [.NET Framework], managed debugging assistants
- environment variables, MDAs
- access violation debugging [.NET Framework]
- diagnostics, managed debugging assistants
- unmanaged code, run-time debugging
- default debug output stream
- memory, debugging
- app.config files, managed debugging assistants
- managed debugging assistants (MDAs)
- debugging [.NET Framework], run-time errors
- trapping events
- runtime, error debugging
- disabling MDAs
- output, managed debugging assistants
- errors [.NET Framework], managed debugging assistants
ms.assetid: 76994ee6-9fa9-4059-b813-26578d24427c
caps.latest.revision: "63"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12a96068412f05d48b8b006385c66f3efbbf9870
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="diagnosing-errors-with-managed-debugging-assistants"></a><span data-ttu-id="5744c-102">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="5744c-102">Diagnosing Errors with Managed Debugging Assistants</span></span>
<span data-ttu-id="5744c-103">マネージ デバッグ アシスタント (MDA) は、共通言語ランタイム (CLR: Common Language Runtime) と連携してランタイム状態に関する情報を提供するデバッグ支援ツールです。</span><span class="sxs-lookup"><span data-stu-id="5744c-103">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span> <span data-ttu-id="5744c-104">MDA は、これ以外の方法ではトラップできないランタイム イベントに関する情報メッセージを生成します。</span><span class="sxs-lookup"><span data-stu-id="5744c-104">The assistants generate informational messages about runtime events that you cannot otherwise trap.</span></span> <span data-ttu-id="5744c-105">MDA を使用すると、マネージ コードからアンマネージ コードへの遷移時に発生する、検出が難しいアプリケーション バグを分離できます。</span><span class="sxs-lookup"><span data-stu-id="5744c-105">You can use MDAs to isolate hard-to-find application bugs that occur when transitioning between managed and unmanaged code.</span></span> <span data-ttu-id="5744c-106">すべての MDA を有効または無効にするには、Windows レジストリにキーを追加するか、環境変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="5744c-106">You can enable or disable all MDAs by adding a key to the Windows registry or by setting an environment variable.</span></span> <span data-ttu-id="5744c-107">特定の MDA を有効にするには、アプリケーション構成設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="5744c-107">You can enable specific MDAs by using application configuration settings.</span></span> <span data-ttu-id="5744c-108">一部の MDA については、アプリケーションの構成ファイルで追加の構成設定を個別に設定できます。</span><span class="sxs-lookup"><span data-stu-id="5744c-108">You can set additional configuration settings for some individual MDAs in the application's configuration file.</span></span> <span data-ttu-id="5744c-109">この構成ファイルはランタイムの読み込み時に解析されるため、MDA は、マネージ アプリケーションが起動する前に有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5744c-109">Because these configuration files are parsed when the runtime is loaded, you must enable the MDA before the managed application starts.</span></span> <span data-ttu-id="5744c-110">MDA は、既に起動しているアプリケーションに対して有効にできません。</span><span class="sxs-lookup"><span data-stu-id="5744c-110">You cannot enable it for applications that have already started.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5744c-111">MDA を有効にすると、コードをデバッガーで実行していないときでも MDA がアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="5744c-111">When an MDA is enabled, it is active even when your code is not executing under a debugger.</span></span> <span data-ttu-id="5744c-112">デバッガーが存在しない場合に MDA イベントが発生した場合、そのイベントはハンドルされない例外とは異なりますが、イベント メッセージはハンドルされない例外のダイアログ ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="5744c-112">If an MDA event is raised when a debugger is not present, the event message is presented in an unhandled exception dialog box, although it is not an unhandled exception.</span></span> <span data-ttu-id="5744c-113">このダイアログ ボックスが表示されないようにするには、デバッグ環境でコードを実行しているのではないときに、MDA を有効にする設定を削除します。</span><span class="sxs-lookup"><span data-stu-id="5744c-113">To avoid the dialog box, remove the MDA-enabling settings when your code is not executing in a debugging environment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5744c-114">Visual Studio の統合開発環境 (IDE: Integrated Development Environment) でコードを実行している場合は、特定の MDA イベントを示す例外のダイアログ ボックスを表示しないようにできます。</span><span class="sxs-lookup"><span data-stu-id="5744c-114">When your code is executing in the Visual Studio integrated development environment (IDE), you can avoid the exception dialog box that appears for specific MDA events.</span></span> <span data-ttu-id="5744c-115">これを行うには、**[デバッグ]** メニューの **[例外]** をクリックします </span><span class="sxs-lookup"><span data-stu-id="5744c-115">To do that, on the **Debug** menu, click **Exceptions**.</span></span> <span data-ttu-id="5744c-116">(**[デバッグ]** メニューに **[例外]** が表示されない場合は、**[ツール]** メニューの **[カスタマイズ]** をクリックし、メニュー項目を追加します)。**[例外]** ダイアログ ボックスで、**[マネージ デバッグ アシスタント]** の一覧を展開し、個々の MDA に対して **[スローされるとき]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="5744c-116">(If the **Debug** menu does not contain an **Exceptions** command, click **Customize** on the **Tools** menu to add it.) In the **Exceptions** dialog box, expand the **Managed Debugging Assistants** list, and then clear the **Thrown** check box for the individual MDA.</span></span> <span data-ttu-id="5744c-117">たとえば、[contextSwitchDeadlock](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md) の例外のダイアログ ボックスを表示しないようにするには、**[マネージ デバッグ アシスタント]** で、この名前の横にある **[スローされるとき]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="5744c-117">For example, to avoid the exception dialog box for a [contextSwitchDeadlock](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md) clear the **Thrown** check box next to its name in the **Managed Debugging Assistants** list.</span></span> <span data-ttu-id="5744c-118">このダイアログ ボックスを使用して、MDA 例外ダイアログ ボックスの表示を有効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="5744c-118">You can also use this dialog box to enable the display of MDA exception dialog boxes.</span></span>  
  
 <span data-ttu-id="5744c-119">.NET Framework に付属する MDA の一覧を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="5744c-119">The following table lists the MDAs that ship with the .NET Framework.</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="5744c-120">asynchronousThreadAbort</span><span class="sxs-lookup"><span data-stu-id="5744c-120">asynchronousThreadAbort</span></span>](../../../docs/framework/debug-trace-profile/asynchronousthreadabort-mda.md)|[<span data-ttu-id="5744c-121">bindingFailure</span><span class="sxs-lookup"><span data-stu-id="5744c-121">bindingFailure</span></span>](../../../docs/framework/debug-trace-profile/bindingfailure-mda.md)|  
|[<span data-ttu-id="5744c-122">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="5744c-122">callbackOnCollectedDelegate</span></span>](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)|[<span data-ttu-id="5744c-123">contextSwitchDeadlock</span><span class="sxs-lookup"><span data-stu-id="5744c-123">contextSwitchDeadlock</span></span>](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md)|  
|[<span data-ttu-id="5744c-124">dangerousThreadingAPI</span><span class="sxs-lookup"><span data-stu-id="5744c-124">dangerousThreadingAPI</span></span>](../../../docs/framework/debug-trace-profile/dangerousthreadingapi-mda.md)|[<span data-ttu-id="5744c-125">dateTimeInvalidLocalFormat</span><span class="sxs-lookup"><span data-stu-id="5744c-125">dateTimeInvalidLocalFormat</span></span>](../../../docs/framework/debug-trace-profile/datetimeinvalidlocalformat-mda.md)|  
|[<span data-ttu-id="5744c-126">dirtyCastAndCallOnInterface</span><span class="sxs-lookup"><span data-stu-id="5744c-126">dirtyCastAndCallOnInterface</span></span>](../../../docs/framework/debug-trace-profile/dirtycastandcalloninterface-mda.md)|[<span data-ttu-id="5744c-127">disconnectedContext</span><span class="sxs-lookup"><span data-stu-id="5744c-127">disconnectedContext</span></span>](../../../docs/framework/debug-trace-profile/disconnectedcontext-mda.md)|  
|[<span data-ttu-id="5744c-128">dllMainReturnsFalse</span><span class="sxs-lookup"><span data-stu-id="5744c-128">dllMainReturnsFalse</span></span>](../../../docs/framework/debug-trace-profile/dllmainreturnsfalse-mda.md)|[<span data-ttu-id="5744c-129">exceptionSwallowedOnCallFromCom</span><span class="sxs-lookup"><span data-stu-id="5744c-129">exceptionSwallowedOnCallFromCom</span></span>](../../../docs/framework/debug-trace-profile/exceptionswallowedoncallfromcom-mda.md)|  
|[<span data-ttu-id="5744c-130">failedQI</span><span class="sxs-lookup"><span data-stu-id="5744c-130">failedQI</span></span>](../../../docs/framework/debug-trace-profile/failedqi-mda.md)|[<span data-ttu-id="5744c-131">fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="5744c-131">fatalExecutionEngineError</span></span>](../../../docs/framework/debug-trace-profile/fatalexecutionengineerror-mda.md)|  
|[<span data-ttu-id="5744c-132">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="5744c-132">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)|[<span data-ttu-id="5744c-133">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="5744c-133">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)|  
|[<span data-ttu-id="5744c-134">illegalPrepareConstrainedRegion</span><span class="sxs-lookup"><span data-stu-id="5744c-134">illegalPrepareConstrainedRegion</span></span>](../../../docs/framework/debug-trace-profile/illegalprepareconstrainedregion-mda.md)|[<span data-ttu-id="5744c-135">invalidApartmentStateChange</span><span class="sxs-lookup"><span data-stu-id="5744c-135">invalidApartmentStateChange</span></span>](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md)|  
|[<span data-ttu-id="5744c-136">invalidCERCall</span><span class="sxs-lookup"><span data-stu-id="5744c-136">invalidCERCall</span></span>](../../../docs/framework/debug-trace-profile/invalidcercall-mda.md)|[<span data-ttu-id="5744c-137">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="5744c-137">invalidFunctionPointerInDelegate</span></span>](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)|  
|[<span data-ttu-id="5744c-138">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="5744c-138">invalidGCHandleCookie</span></span>](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)|[<span data-ttu-id="5744c-139">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="5744c-139">invalidIUnknown</span></span>](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)|  
|[<span data-ttu-id="5744c-140">invalidMemberDeclaration</span><span class="sxs-lookup"><span data-stu-id="5744c-140">invalidMemberDeclaration</span></span>](../../../docs/framework/debug-trace-profile/invalidmemberdeclaration-mda.md)|[<span data-ttu-id="5744c-141">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="5744c-141">invalidOverlappedToPinvoke</span></span>](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)|  
|[<span data-ttu-id="5744c-142">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="5744c-142">invalidVariant</span></span>](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)|[<span data-ttu-id="5744c-143">jitCompilationStart</span><span class="sxs-lookup"><span data-stu-id="5744c-143">jitCompilationStart</span></span>](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md)|  
|[<span data-ttu-id="5744c-144">loaderLock</span><span class="sxs-lookup"><span data-stu-id="5744c-144">loaderLock</span></span>](../../../docs/framework/debug-trace-profile/loaderlock-mda.md)|[<span data-ttu-id="5744c-145">loadFromContext</span><span class="sxs-lookup"><span data-stu-id="5744c-145">loadFromContext</span></span>](../../../docs/framework/debug-trace-profile/loadfromcontext-mda.md)|  
|[<span data-ttu-id="5744c-146">marshalCleanupError</span><span class="sxs-lookup"><span data-stu-id="5744c-146">marshalCleanupError</span></span>](../../../docs/framework/debug-trace-profile/marshalcleanuperror-mda.md)|[<span data-ttu-id="5744c-147">marshaling</span><span class="sxs-lookup"><span data-stu-id="5744c-147">marshaling</span></span>](../../../docs/framework/debug-trace-profile/marshaling-mda.md)|  
|[<span data-ttu-id="5744c-148">memberInfoCacheCreation</span><span class="sxs-lookup"><span data-stu-id="5744c-148">memberInfoCacheCreation</span></span>](../../../docs/framework/debug-trace-profile/memberinfocachecreation-mda.md)|[<span data-ttu-id="5744c-149">moduloObjectHashcode</span><span class="sxs-lookup"><span data-stu-id="5744c-149">moduloObjectHashcode</span></span>](../../../docs/framework/debug-trace-profile/moduloobjecthashcode-mda.md)|  
|[<span data-ttu-id="5744c-150">nonComVisibleBaseClass</span><span class="sxs-lookup"><span data-stu-id="5744c-150">nonComVisibleBaseClass</span></span>](../../../docs/framework/debug-trace-profile/noncomvisiblebaseclass-mda.md)|[<span data-ttu-id="5744c-151">notMarshalable</span><span class="sxs-lookup"><span data-stu-id="5744c-151">notMarshalable</span></span>](../../../docs/framework/debug-trace-profile/notmarshalable-mda.md)|  
|[<span data-ttu-id="5744c-152">openGenericCERCall</span><span class="sxs-lookup"><span data-stu-id="5744c-152">openGenericCERCall</span></span>](../../../docs/framework/debug-trace-profile/opengenericcercall-mda.md)|[<span data-ttu-id="5744c-153">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="5744c-153">overlappedFreeError</span></span>](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)|  
|[<span data-ttu-id="5744c-154">pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="5744c-154">pInvokeLog</span></span>](../../../docs/framework/debug-trace-profile/pinvokelog-mda.md)|[<span data-ttu-id="5744c-155">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="5744c-155">pInvokeStackImbalance</span></span>](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)|  
|[<span data-ttu-id="5744c-156">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="5744c-156">raceOnRCWCleanup</span></span>](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)|[<span data-ttu-id="5744c-157">reentrancy</span><span class="sxs-lookup"><span data-stu-id="5744c-157">reentrancy</span></span>](../../../docs/framework/debug-trace-profile/reentrancy-mda.md)|  
|[<span data-ttu-id="5744c-158">releaseHandleFailed</span><span class="sxs-lookup"><span data-stu-id="5744c-158">releaseHandleFailed</span></span>](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md)|[<span data-ttu-id="5744c-159">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="5744c-159">reportAvOnComRelease</span></span>](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)|  
|[<span data-ttu-id="5744c-160">streamWriterBufferedDataLost</span><span class="sxs-lookup"><span data-stu-id="5744c-160">streamWriterBufferedDataLost</span></span>](../../../docs/framework/debug-trace-profile/streamwriterbuffereddatalost-mda.md)|[<span data-ttu-id="5744c-161">virtualCERCall</span><span class="sxs-lookup"><span data-stu-id="5744c-161">virtualCERCall</span></span>](../../../docs/framework/debug-trace-profile/virtualcercall-mda.md)|  
  
 <span data-ttu-id="5744c-162">既定では、.NET Framework はすべてのマネージ デバッガーに対して MDA のサブセットをアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="5744c-162">By default, the .NET Framework activates a subset of MDAs for all managed debuggers.</span></span> <span data-ttu-id="5744c-163">Visual Studio で既定のセットを表示するには、**[デバッグ]** メニューの **[例外]** をクリックし、**[マネージ デバッグ アシスタント]** の一覧を展開します。</span><span class="sxs-lookup"><span data-stu-id="5744c-163">You can view the default set in Visual Studio by clicking **Exceptions** on the **Debug** menu and expanding the **Managed Debugging Assistants** list.</span></span>  
  
## <a name="enabling-and-disabling-mdas"></a><span data-ttu-id="5744c-164">MDA の有効化と無効化</span><span class="sxs-lookup"><span data-stu-id="5744c-164">Enabling and Disabling MDAs</span></span>  
 <span data-ttu-id="5744c-165">MDA は、レジストリ キー、環境変数、およびアプリケーション構成設定を使用して有効または無効にできます。</span><span class="sxs-lookup"><span data-stu-id="5744c-165">You can enable and disable MDAs by using a registry key, an environment variable, and application configuration settings.</span></span> <span data-ttu-id="5744c-166">アプリケーション構成設定を使用するには、レジストリ キーまたは環境変数を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5744c-166">You must enable either the registry key or the environment variable to use the application configuration settings.</span></span>  
  
 <span data-ttu-id="5744c-167">Visual Studio 2005 以降のバージョンでは、ホスティング プロセスが有効な場合、既定のセットに含まれている MDA を無効にしたり、既定のセットに含まれていない MDA を有効にしたりはできません。</span><span class="sxs-lookup"><span data-stu-id="5744c-167">In Visual Studio 2005 and later versions, when the hosting process is enabled, you cannot disable MDAs that are in the default set or enable MDAs that are not in the default set.</span></span> <span data-ttu-id="5744c-168">ホスティング プロセスは既定で有効になるため、明示的に無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5744c-168">The hosting process is enabled by default, so it must be explicitly disabled.</span></span>  
  
 <span data-ttu-id="5744c-169">Visual Studio でホスティング プロセスを無効にするには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="5744c-169">To disable the hosting process in Visual Studio, do the following:</span></span>  
  
1.  <span data-ttu-id="5744c-170">**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="5744c-170">In **Solution Explorer**, select a project.</span></span>  
  
2.  <span data-ttu-id="5744c-171">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5744c-171">On the **Project** menu, click **Properties**.</span></span>  
  
     <span data-ttu-id="5744c-172">**[プロジェクト デザイナー]** ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5744c-172">The **Project Designer** window appears.</span></span>  
  
3.  <span data-ttu-id="5744c-173">**[デバッグ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5744c-173">Click the **Debug** tab.</span></span>  
  
4.  <span data-ttu-id="5744c-174">**[デバッガーを有効にする]** セクションで、**[Visual Studio ホスティング プロセスを有効にする]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="5744c-174">In the **Enable Debuggers** section, clear the **Enable the Visual Studio hosting process** check box.</span></span>  
  
 <span data-ttu-id="5744c-175">ただし、ホスティング プロセスを無効にすると、パフォーマンスに影響する場合があります。</span><span class="sxs-lookup"><span data-stu-id="5744c-175">However, disabling the hosting process can affect performance.</span></span> <span data-ttu-id="5744c-176">Visual Studio で、MDA 通知を受け取ったときに MDA ダイアログ ボックスが表示されないようにすると、MDA を無効にする必要がありません。</span><span class="sxs-lookup"><span data-stu-id="5744c-176">You can avoid the need to disable MDAs by preventing Visual Studio from displaying the MDA dialog box whenever an MDA notification is received.</span></span> <span data-ttu-id="5744c-177">そのためには、**[デバッグ]** メニューの **[例外]** をクリックし、**[マネージ デバッグ アシスタント]** の一覧を展開し、個々の MDA に対して **[スローされるとき]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="5744c-177">To do that, click **Exceptions** on the **Debug** menu, expand the **Managed Debugging Assistants** list, and then select or clear the **Thrown** check box for the individual MDA.</span></span>  
  
### <a name="enabling-and-disabling-mdas-by-using-a-registry-key"></a><span data-ttu-id="5744c-178">レジストリ キーを使用した MDA の有効化と無効化</span><span class="sxs-lookup"><span data-stu-id="5744c-178">Enabling and Disabling MDAs by Using a Registry Key</span></span>  
 <span data-ttu-id="5744c-179">MDA を有効にするには、Windows レジストリに HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\MDA サブキー (REG_SZ 型、値 1) を追加します。</span><span class="sxs-lookup"><span data-stu-id="5744c-179">You can enable MDAs by adding the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\MDA subkey (type REG_SZ, value 1) in the Windows registry.</span></span> <span data-ttu-id="5744c-180">MDAEnable.reg という名前のテキスト ファイルに次の例をコピーします。Windows レジストリ エディター (RegEdit.exe) を開き、**[ファイル]** メニューで **[インポート]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5744c-180">Copy the following example into a text file named MDAEnable.reg. Open the Windows Registry Editor (RegEdit.exe) and from the **File** menu choose **Import**.</span></span> <span data-ttu-id="5744c-181">MDAEnable.reg ファイルを選択します。そのコンピューターで MDA が有効になります。</span><span class="sxs-lookup"><span data-stu-id="5744c-181">Select the MDAEnable.reg  file to enable MDAs on that computer.</span></span> <span data-ttu-id="5744c-182">サブキーを (DWARD 値 1 ではなく) 文字列値 1 に設定すると、*ApplicationName.suffix*.mda.config ファイルから MDA の設定を読み取れるようになります。</span><span class="sxs-lookup"><span data-stu-id="5744c-182">Setting the subkey to string value of 1 (not DWORD value of 1) enables the reading of MDA settings from the *ApplicationName.suffix*.mda.config file.</span></span> <span data-ttu-id="5744c-183">(たとえばメモ帳の MDA 構成ファイルは notepad.exe.mda.config になります)</span><span class="sxs-lookup"><span data-stu-id="5744c-183">(For example the MDA configuration file for Notepad would be named notepad.exe.mda.config)</span></span>  
  
```  
Windows Registry Editor Version 5.00  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]  
"MDA"="1"  
```  
  
 <span data-ttu-id="5744c-184">64 ビット オペレーティング システム上で 32 ビット アプリケーションを実行しているコンピューターでは、MDA キーは次のように設定します。</span><span class="sxs-lookup"><span data-stu-id="5744c-184">If the computer is running a 32-bit application on a 64-bit operating system, then the MDA key should be set like the following:</span></span>  
  
```  
      Windows Registry Editor Version 5.00   
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]  
"MDA"="1"  
```  
  
 <span data-ttu-id="5744c-185">詳細については、「[アプリケーション固有の構成設定を使用した MDA の有効化と無効化](#appConfig)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5744c-185">See [Enabling and Disabling MDAs by Using Application-Specific Configuration Settings](#appConfig) for more information.</span></span> <span data-ttu-id="5744c-186">レジストリ設定は、COMPLUS_MDA 環境変数でオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="5744c-186">The registry setting can be overridden by the COMPLUS_MDA environment variable.</span></span> <span data-ttu-id="5744c-187">詳細については、「[環境変数を使用した MDA の有効化と無効化](#envVariable)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5744c-187">See [Enabling and Disabling MDAs by Using an Environment Variable](#envVariable) for more information.</span></span>  
  
 <span data-ttu-id="5744c-188">MDA を無効にするには、Windows レジストリ エディターを使用して MDA サブキーを 0 (ゼロ) に設定します。</span><span class="sxs-lookup"><span data-stu-id="5744c-188">To disable MDAs, set the MDA subkey to 0 (zero) using the Windows Registry Editor.</span></span>  
  
 <span data-ttu-id="5744c-189">MDA には、レジストリ キーを追加しなくても、デバッガーにアタッチされているアプリケーションを実行すると既定で有効になるものがあります。</span><span class="sxs-lookup"><span data-stu-id="5744c-189">By default, some MDAs are enabled when you run an application that is attached to a debugger, even without adding the registry key.</span></span> <span data-ttu-id="5744c-190">このようなアシスタントには、[pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) や [invalidApartmentStateChange](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md) などがあります。</span><span class="sxs-lookup"><span data-stu-id="5744c-190">Examples of such assistants are [pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) and [invalidApartmentStateChange](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md).</span></span> <span data-ttu-id="5744c-191">これらのアシスタントを無効にするには、このセクションの前述の説明に従って MDADisable.reg ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="5744c-191">You can disable these assistants by running the MDADisable.reg file as described earlier in this section.</span></span>  
  
<a name="envVariable"></a>   
### <a name="enabling-and-disabling-mdas-by-using-an-environment-variable"></a><span data-ttu-id="5744c-192">環境変数を使用した MDA の有効化と無効化</span><span class="sxs-lookup"><span data-stu-id="5744c-192">Enabling and Disabling MDAs by Using an Environment Variable</span></span>  
 <span data-ttu-id="5744c-193">MDA のアクティブ化は、COMPLUS_MDA 環境変数によって制御することもできます。この環境変数はレジストリ キーをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="5744c-193">MDA activation can also controlled by the environment variable COMPLUS_MDA, which overrides the registry key.</span></span> <span data-ttu-id="5744c-194">COMPLUS_MDA の文字列は、MDA 名やその他の特殊制御文字列の、セミコロンで区切られたリストで、大文字小文字の区別はありません。</span><span class="sxs-lookup"><span data-stu-id="5744c-194">The COMPLUS_MDA string is a case-insensitive, semicolon-delimited list of MDA names or other special control strings.</span></span> <span data-ttu-id="5744c-195">マネージ デバッガーやアンマネージ デバッガーの下で起動すると、MDA のセットが既定で有効になります。</span><span class="sxs-lookup"><span data-stu-id="5744c-195">Starting under a managed or unmanaged debugger enables a set of MDAs by default.</span></span> <span data-ttu-id="5744c-196">そのためには、デバッガーの下で既定で有効にする MDA のリスト (セミコロン区切り) を、環境変数またはレジストリ キーの値の前に暗黙的に付加します。</span><span class="sxs-lookup"><span data-stu-id="5744c-196">This is done by implicitly prepending the semicolon-delimited list of MDAs enabled by default under debuggers to the value of the environment variable or registry key.</span></span> <span data-ttu-id="5744c-197">特殊制御文字列は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5744c-197">The special control strings are the following:</span></span>  
  
-   <span data-ttu-id="5744c-198">`0` - すべての MDA を非アクティブにします。</span><span class="sxs-lookup"><span data-stu-id="5744c-198">`0` - Deactivates all MDAs.</span></span>  
  
-   <span data-ttu-id="5744c-199">`1` - *ApplicationName*.mda.config から MDA の設定を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="5744c-199">`1` - Reads MDA settings from *ApplicationName*.mda.config.</span></span>  
  
-   <span data-ttu-id="5744c-200">`managedDebugger` - デバッガーの下でマネージ実行可能ファイルを起動すると、暗黙的にアクティブ化されているすべての MDA が明示的にアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="5744c-200">`managedDebugger` - Explicitly activates all MDAs that are implicitly activated when a managed executable is started under a debugger.</span></span>  
  
-   <span data-ttu-id="5744c-201">`unmanagedDebugger` - デバッガーの下でアンマネージ実行可能ファイルを起動すると、暗黙的にアクティブ化されているすべての MDA が明示的にアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="5744c-201">`unmanagedDebugger` - Explicitly activates all MDAs that are implicitly activated when an unmanaged executable is started under a debugger.</span></span>  
  
 <span data-ttu-id="5744c-202">競合する設定がある場合は、最新の設定が以前の設定を次のようにオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="5744c-202">If there are conflicting settings, the most recent settings override previous settings:</span></span>  
  
-   <span data-ttu-id="5744c-203">`COMPLUS_MDA=0` は、デバッガーの下で暗黙的に有効化されている MDA を含め、すべての MDA を無効にします。</span><span class="sxs-lookup"><span data-stu-id="5744c-203">`COMPLUS_MDA=0` disables all MDAs, including those implicitly enabled under a debugger.</span></span>  
  
-   <span data-ttu-id="5744c-204">`COMPLUS_MDA=gcUnmanagedToManaged` は、デバッガーの下で暗黙的に有効化される MDA に加えて `gcUnmanagedToManaged` も有効にします。</span><span class="sxs-lookup"><span data-stu-id="5744c-204">`COMPLUS_MDA=gcUnmanagedToManaged` enables `gcUnmanagedToManaged` in addition to any MDAs that are implicitly enabled under a debugger.</span></span>  
  
-   <span data-ttu-id="5744c-205">`COMPLUS_MDA=0;gcUnmanagedToManaged` は `gcUnmanagedToManaged` を有効にしますが、デバッガーの下で別途暗黙的に有効化されている MDA を無効にします。</span><span class="sxs-lookup"><span data-stu-id="5744c-205">`COMPLUS_MDA=0;gcUnmanagedToManaged` enables `gcUnmanagedToManaged` but disables MDAs that would otherwise be implicitly enabled under a debugger.</span></span>  
  
<a name="appConfig"></a>   
### <a name="enabling-and-disabling-mdas-by-using-application-specific-configuration-settings"></a><span data-ttu-id="5744c-206">アプリケーション固有の構成設定を使用した MDA の有効化と無効化</span><span class="sxs-lookup"><span data-stu-id="5744c-206">Enabling and Disabling MDAs by Using Application-Specific Configuration Settings</span></span>  
 <span data-ttu-id="5744c-207">アプリケーションの MDA 構成ファイルでは、一部のアシスタントを個別に有効化、無効化、および構成できます。</span><span class="sxs-lookup"><span data-stu-id="5744c-207">You can enable, disable, and configure some assistants individually in the MDA configuration file for the application.</span></span> <span data-ttu-id="5744c-208">MDA を構成する目的でアプリケーション構成ファイルの使用を有効にするには、MDA レジストリ キーまたは COMPLUS_MDA 環境変数を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5744c-208">To enable the use of an application configuration file for configuring MDAs, either the MDA registry key or the COMPLUS_MDA environment variable must be set.</span></span> <span data-ttu-id="5744c-209">アプリケーション構成ファイルは、通常、アプリケーションの実行可能ファイル (.exe) と同じディレクトリに置かれます。</span><span class="sxs-lookup"><span data-stu-id="5744c-209">The application configuration file is typically located in the same directory as the application's executable (.exe) file.</span></span> <span data-ttu-id="5744c-210">このファイル名の形式は、*ApplicationName*.mda.config です (notepad.exe.mda.config など)。アプリケーション構成ファイルで有効にされたアシスタントには、そのアシスタントの動作を制御するために特別にデザインされた属性や要素が存在する場合があります。</span><span class="sxs-lookup"><span data-stu-id="5744c-210">The file name takes the form *ApplicationName*.mda.config; for example, notepad.exe.mda.config. Assistants that are enabled in the application configuration file may have attributes or elements specifically designed to control that assistant's behavior.</span></span> <span data-ttu-id="5744c-211">[marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md) を有効化して設定する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="5744c-211">The following example shows how to enable and configure the [marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md).</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshaling>  
      <methodFilter>  
        <match name="*"/>  
      </methodFilter>  
      <fieldFilter>  
        <match name="*"/>  
      </fieldFilter>  
    </marshaling>  
  </assistants>  
</mdaConfig>  
```  
  
 <span data-ttu-id="5744c-212">`Marshaling` MDA では、アプリケーションでのマネージ コードからアンマネージ コードへの遷移ごとに、アンマネージ型にマーシャリングされるマネージ型についての情報が出力されます。</span><span class="sxs-lookup"><span data-stu-id="5744c-212">The `Marshaling` MDA emits information about the managed type that is being marshaled to an unmanaged type for each managed-to-unmanaged transition in the application.</span></span> <span data-ttu-id="5744c-213">また、`Marshaling` MDA では、`<methodFilter>` 子要素と `<fieldFilter>` 子要素でそれぞれ指定されたメソッドと構造体フィールドの名前をフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="5744c-213">The `Marshaling` MDA can also filter the names of the method and structure fields supplied in the `<methodFilter>` and `<fieldFilter>` child elements, respectively.</span></span>  
  
 <span data-ttu-id="5744c-214">既定の設定を使用して複数の MDA を有効にする方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="5744c-214">The following example shows how to enable multiple MDAs by using their default settings.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion />  
    <invalidCERCall />  
    <openGenericCERCall />  
    <virtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="5744c-215">構成ファイルに複数のアシスタントを指定する場合は、アルファベット順に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5744c-215">When you specify more than one assistant in a configuration file, you must list them in alphabetical order.</span></span> <span data-ttu-id="5744c-216">たとえば、`virtualCERCall` MDA と `invalidCERCall` MDA の両方を有効にする場合は、`<invalidCERCall />` エントリ、`<virtualCERCall />` エントリの順に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5744c-216">For example, if you want to enable both the `virtualCERCall` and the `invalidCERCall` MDAs, you must add the `<invalidCERCall />` entry before the `<virtualCERCall />` entry.</span></span> <span data-ttu-id="5744c-217">エントリがアルファベット順になっていない場合、ハンドルされない無効な構成ファイルであることを示す例外メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5744c-217">If the entries are not in alphabetical order, an unhandled invalid configuration file exception message is displayed.</span></span>  
  
### <a name="mda-output"></a><span data-ttu-id="5744c-218">MDA の出力</span><span class="sxs-lookup"><span data-stu-id="5744c-218">MDA Output</span></span>  
 <span data-ttu-id="5744c-219">MDA の出力例を次に示します。この例は、`pInvokeStackImbalance` MDA の出力を示しています。</span><span class="sxs-lookup"><span data-stu-id="5744c-219">MDA output is similar to the following example, which shows the output from the `pInvokeStackImbalance` MDA.</span></span>  
  
 `A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.`  
  
## <a name="see-also"></a><span data-ttu-id="5744c-220">参照</span><span class="sxs-lookup"><span data-stu-id="5744c-220">See Also</span></span>  
 [<span data-ttu-id="5744c-221">デバッグ、トレース、およびプロファイリング</span><span class="sxs-lookup"><span data-stu-id="5744c-221">Debugging, Tracing, and Profiling</span></span>](../../../docs/framework/debug-trace-profile/index.md)

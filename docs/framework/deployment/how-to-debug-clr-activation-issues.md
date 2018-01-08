---
title: "方法: CLR のアクティブ化に関する問題をデバッグする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: CLR activation, debugging issues
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa8153fe680a8848ad19f32a2246d0f350c73c66
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-clr-activation-issues"></a><span data-ttu-id="f1352-102">方法: CLR のアクティブ化に関する問題をデバッグする</span><span class="sxs-lookup"><span data-stu-id="f1352-102">How to: Debug CLR Activation Issues</span></span>
<span data-ttu-id="f1352-103">正しいバージョンの共通言語ランタイム (CLR) でアプリケーションを実行して問題が発生した場合、CLR アクティベーション ログを表示し、デバッグできます。</span><span class="sxs-lookup"><span data-stu-id="f1352-103">If you encounter problems in getting your application to run with the correct version of the common language runtime (CLR), you can view and debug CLR activation logs.</span></span> <span data-ttu-id="f1352-104">アプリケーションで予想とは異なる CLR バージョンが読み込まれるときでも、CLR がまったく読み込まれないときでも、アクティベーション問題の根本原因を突き止めるときにこのログが大変役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f1352-104">These logs can be very useful in determining the root cause of an activation issue, when your application either loads a different CLR version than expected or doesn't load the CLR at all.</span></span> <span data-ttu-id="f1352-105">[.NET Framework 初期化エラー: ユーザー エクスペリエンスの管理](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md)では、アプリケーションに対して CLR が見つからない場合について説明されています。</span><span class="sxs-lookup"><span data-stu-id="f1352-105">The [.NET Framework Initialization Errors: Managing the User Experience](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) discusses the experience when no CLR is found for an application.</span></span>  
  
 <span data-ttu-id="f1352-106">HKEY_LOCAL_MACHINE レジストリ キーまたはシステム環境変数を利用すれば、CLR アクティベーション ログをシステム全体で有効にできます。</span><span class="sxs-lookup"><span data-stu-id="f1352-106">CLR activation logging can be enabled system-wide by using an HKEY_LOCAL_MACHINE registry key or a system environment variable.</span></span> <span data-ttu-id="f1352-107">このログは、レジストリ キーまたは環境変数が削除されるまで生成されます。</span><span class="sxs-lookup"><span data-stu-id="f1352-107">The log will be generated until the registry entry or the environment variable is removed.</span></span> <span data-ttu-id="f1352-108">あるいは、ユーザーまたはプロセスのローカル環境変数を利用し、別の範囲や期間でログを有効にできます。</span><span class="sxs-lookup"><span data-stu-id="f1352-108">Alternatively, you can use a user or process-local environment variable to enable logging with a different scope and duration.</span></span>  
  
 <span data-ttu-id="f1352-109">CLR アクティベーション ログと[アセンブリ バインド ログ](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md)は完全に異なりますので混同しないでください。</span><span class="sxs-lookup"><span data-stu-id="f1352-109">CLR activation logs shouldn't be confused with [assembly binding logs](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), which are entirely different.</span></span>  
  
## <a name="to-enable-clr-activation-logging"></a><span data-ttu-id="f1352-110">CLR アクティベーション ログを有効にするには</span><span class="sxs-lookup"><span data-stu-id="f1352-110">To enable CLR activation logging</span></span>  
  
#### <a name="using-the-registry"></a><span data-ttu-id="f1352-111">レジストリを利用する</span><span class="sxs-lookup"><span data-stu-id="f1352-111">Using the registry</span></span>  
  
1.  <span data-ttu-id="f1352-112">レジストリ エディターで、HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework (32 ビット コンピューターの場合) または HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework フォルダー (64 ビット コンピューターの場合) に移動します。</span><span class="sxs-lookup"><span data-stu-id="f1352-112">In the Registry Editor, navigate to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework (on a 32-bit computer) or HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework folder (on a 64-bit computer).</span></span>  
  
2.  <span data-ttu-id="f1352-113">`CLRLoadLogDir` という名前の文字列値を追加し、CLR アクティベーション ログを保存する既存ディレクトリの完全パスにそれを設定します。</span><span class="sxs-lookup"><span data-stu-id="f1352-113">Add a string value named `CLRLoadLogDir`, and set it to the full path of an existing directory where you'd like to store CLR activation logs.</span></span>  
  
 <span data-ttu-id="f1352-114">アクティベーション ログは、この文字列値を削除するまで有効です。</span><span class="sxs-lookup"><span data-stu-id="f1352-114">Activation logging remains enabled until you remove the string value.</span></span>  
  
#### <a name="using-an-environment-variable"></a><span data-ttu-id="f1352-115">環境変数を利用する</span><span class="sxs-lookup"><span data-stu-id="f1352-115">Using an environment variable</span></span>  
  
-   <span data-ttu-id="f1352-116">CLR アクティベーション ログを保存する既存ディレクトリの完全パスを表す文字列に `COMPLUS_CLRLoadLogDir` 環境変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="f1352-116">Set the `COMPLUS_CLRLoadLogDir` environment variable to a string that represents the full path of an existing directory where you'd like to store CLR activation logs.</span></span>  
  
     <span data-ttu-id="f1352-117">環境変数の設定方法でその範囲が決まります。</span><span class="sxs-lookup"><span data-stu-id="f1352-117">How you set the environment variable determines its scope:</span></span>  
  
    -   <span data-ttu-id="f1352-118">システム レベルで設定した場合、環境変数が削除されるまで、そのコンピューターのすべての .NET Framework アプリケーションに対してアクティベーション ログが有効になります。</span><span class="sxs-lookup"><span data-stu-id="f1352-118">If you set it at the system level, activation logging is enabled for all .NET Framework applications on that computer until the environment variable is removed.</span></span>  
  
    -   <span data-ttu-id="f1352-119">ユーザー レベルで設定した場合、現在のユーザー アカウントに対してのみ、アクティベーション ログが有効になります。</span><span class="sxs-lookup"><span data-stu-id="f1352-119">If you set it at the user level, activation logging is enabled only for the current user account.</span></span> <span data-ttu-id="f1352-120">環境変数が削除されるまでログが記録されます。</span><span class="sxs-lookup"><span data-stu-id="f1352-120">Logging continues until the environment variable is removed.</span></span>  
  
    -   <span data-ttu-id="f1352-121">CLR を読み込む前にプロセス内から設定した場合、プロセスが終了するまでアクティベーション ログが有効になります。</span><span class="sxs-lookup"><span data-stu-id="f1352-121">If you set it from within the process before loading the CLR, activation logging is enabled until the process terminates.</span></span>  
  
    -   <span data-ttu-id="f1352-122">アプリケーションを実行する前にコマンド プロンプトで設定した場合、そのコマンド プロンプトから実行されたあらゆるアプリケーションに対してアクティベーション ログが有効になります。</span><span class="sxs-lookup"><span data-stu-id="f1352-122">If you set it at a command prompt before you run an application, activation logging is enabled for any application that is run from that command prompt.</span></span>  
  
     <span data-ttu-id="f1352-123">たとえば、プロセスレベルの範囲で c:\clrloadlogs ディレクトリにアクティベーション ログを保存するには、アプリケーションを実行する前にコマンド プロンプト ウィンドウを開き、次を入力します。</span><span class="sxs-lookup"><span data-stu-id="f1352-123">For example, to store activation logs in the c:\clrloadlogs directory with process-level scope, open a Command Prompt window and type the following before you run the application:</span></span>  
  
    ```  
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs  
    ```  
  
## <a name="example"></a><span data-ttu-id="f1352-124">例</span><span class="sxs-lookup"><span data-stu-id="f1352-124">Example</span></span>  
 <span data-ttu-id="f1352-125">CLR アクティベーション ログは、CLR アクティベーションと API をホストする CLR の使用に関する大量のデータを提供します。</span><span class="sxs-lookup"><span data-stu-id="f1352-125">CLR activation logs provide a large amount of data about CLR activation and the use of the CLR hosting APIs.</span></span> <span data-ttu-id="f1352-126">そのデータの大半は Microsoft が社内で利用しますが、一部のデータは、この記事で説明するように、開発者にとっても役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f1352-126">Most of this data is used internally by Microsoft, but some of the data can also be useful to developers, as described in this article.</span></span>  
  
 <span data-ttu-id="f1352-127">このログには、API をホストする CLR が呼び出された順序が反映されます。</span><span class="sxs-lookup"><span data-stu-id="f1352-127">The log reflects the order in which the CLR hosting APIs were called.</span></span> <span data-ttu-id="f1352-128">コンピューターで検出された一連のインストール済みランタイムに関する有用な情報も含まれています。</span><span class="sxs-lookup"><span data-stu-id="f1352-128">It also includes useful data about the set of installed runtimes detected on the computer.</span></span> <span data-ttu-id="f1352-129">CLR アクティベーション ログの書式自体は記録されませんが、開発者が CLR アクティベーションの問題を解決するとき、この書式は役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="f1352-129">The CLR activation log format is not itself documented, but can be used to aid developers who need to resolve CLR activation issues.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1352-130">CLR を使用するプロセスが終了するまで、アクティベーション ログを開くことはできません。</span><span class="sxs-lookup"><span data-stu-id="f1352-130">You cannot open an activation log until the process that uses the CLR has terminated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1352-131">CLR アクティベーション ログはローカライズされません。常に英語で生成されます。</span><span class="sxs-lookup"><span data-stu-id="f1352-131">CLR activation logs are not localized; they are always generated in the English language.</span></span>  
  
 <span data-ttu-id="f1352-132">次のアクティベーション ログ例では、最も役に立つ情報が強調表示されており、ログの後に説明が付いています。</span><span class="sxs-lookup"><span data-stu-id="f1352-132">In the following example of an activation log, the most useful information is highlighted and described after the log.</span></span>  
  
```  
532,205950.367,CLR Loading log for C:\Tests\myapp.exe   
532,205950.367,Log started at 4:26:12 PM on 10/6/2011   
532,205950.367,-----------------------------------   
532,205950.382,FunctionCall: _CorExeMain   
532,205950.382,FunctionCall: ClrCreateInstance, Clsid: {2EBCD49A-1B47-4A61-B13A-4A03701E594B}, Iid: {E2190695-77B2-492E-8E14-C4B3A7FDD593}   
532,205950.382,MethodCall: ICLRMetaHostPolicy::GetRequestedRuntime. Version: (null), Metahost Policy Flags: 0x168, Binary: (null), Iid: {BD39D1D2-BA2F-486A-89B0-B4B0CB466891}   
532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0   
532,205950.382,Input values for ComputeVersionString follow this line   
532,205950.382,-----------------------------------   
532,205950.382,Default Application Name: C:\Tests\myapp.exe   
532,205950.382,IsLegacyBind is: 0   
532,205950.382,IsCapped is 0   
532,205950.382,SkuCheckFlags are 0   
532,205950.382,ShouldEmulateExeLaunch is 0   
532,205950.382,LegacyBindRequired is 0   
532,205950.382,-----------------------------------   
532,205950.382,Parsing config file: C:\Tests\myapp.exe   
532,205950.382,UseLegacyV2RuntimeActivationPolicy is set to 0   
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe   
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe   
532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727   
532,205950.382,ERROR: Version v2.0.50727 is not present on the machine.   
532,205950.398,SEM_FAILCRITICALERRORS is set to 0   
532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3   
532,205950.398,FunctionCall: RealDllMain. Reason: 0   
532,205950.398,FunctionCall: OnShimDllMainCalled. Reason: 0  
```  
  
-   <span data-ttu-id="f1352-133">**CLR Loading log** には、マネージ コードを読み込んだプロセスを開始した実行可能ファイルのパスがあります。</span><span class="sxs-lookup"><span data-stu-id="f1352-133">**CLR Loading log** provides the path to the executable that started the process that loaded managed code.</span></span> <span data-ttu-id="f1352-134">ネイティブ ホストの可能性があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f1352-134">Note that this could be a native host.</span></span>  
  
    ```  
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe  
    ```  
  
-   <span data-ttu-id="f1352-135">**Installed Runtime** は、コンピューターにインストールされている CLR の一連のバージョンであり、アクティベーション要求の候補となります。</span><span class="sxs-lookup"><span data-stu-id="f1352-135">**Installed Runtime** is the set of CLR versions installed on the computer that are candidates for the activation request.</span></span>  
  
    ```  
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0  
    ```  
  
-   <span data-ttu-id="f1352-136">**built with version** は、[ICLRMetaHostPolicy::GetRequestedRuntime](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) のようなメソッドに提供されたバイナリの構築に利用された CLR のバージョンです。</span><span class="sxs-lookup"><span data-stu-id="f1352-136">**built with version** is the version of the CLR that was used to build the binary that was provided to a method such as [ICLRMetaHostPolicy::GetRequestedRuntime](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).</span></span>  
  
    ```  
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727  
    ```  
  
-   <span data-ttu-id="f1352-137">**feature-on-demand installation** は Windows 8 で .NET Framework 3.5 を有効にすることを指します。</span><span class="sxs-lookup"><span data-stu-id="f1352-137">**feature-on-demand installation** refers to enabling the .NET Framework 3.5 on Windows 8.</span></span> <span data-ttu-id="f1352-138">このシナリオの詳細については、「[.NET Framework 初期化エラー: ユーザー エクスペリエンスの管理](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1352-138">See [.NET Framework Initialization Errors: Managing the User Experience](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) for more information about this scenario.</span></span>  
  
    ```  
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f1352-139">参照</span><span class="sxs-lookup"><span data-stu-id="f1352-139">See Also</span></span>  
 [<span data-ttu-id="f1352-140">配置</span><span class="sxs-lookup"><span data-stu-id="f1352-140">Deployment</span></span>](../../../docs/framework/deployment/index.md)  
 [<span data-ttu-id="f1352-141">方法: .NET Framework 4 または 4.5 をサポートするアプリを構成する</span><span class="sxs-lookup"><span data-stu-id="f1352-141">How to: Configure an App to Support .NET Framework 4 or 4.5</span></span>](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)

---
title: "Fuslogvw.exe (アセンブリ バインディング ログ ビューアー)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- failed assembly binds
- Fuslogvw.exe
- displaying failed assembly bind details
- assemblies [.NET Framework], failed assembly binds
- locating assemblies
- Assembly Binding Log Viewer
ms.assetid: e32fa443-0778-4cc3-bf36-5c8ea297d296
caps.latest.revision: 35
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 381464ecc911dedb0dd394ded7c29fe143423142
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="fuslogvwexe-assembly-binding-log-viewer"></a><span data-ttu-id="61fa5-102">Fuslogvw.exe (アセンブリ バインディング ログ ビューアー)</span><span class="sxs-lookup"><span data-stu-id="61fa5-102">Fuslogvw.exe (Assembly Binding Log Viewer)</span></span>
<span data-ttu-id="61fa5-103">アセンブリ バインディング ログ ビューアーは、アセンブリ バインドの詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="61fa5-103">The Assembly Binding Log Viewer displays details for assembly binds.</span></span> <span data-ttu-id="61fa5-104">この情報は、.NET Framework が実行時にアセンブリを見つけられない原因を診断する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="61fa5-104">This information helps you diagnose why the .NET Framework cannot locate an assembly at run time.</span></span> <span data-ttu-id="61fa5-105">通常、このようなエラーは、アセンブリが間違った位置に配置されているか、無効になったネイティブ イメージが存在するか、バージョン番号またはカルチャの不一致が存在する場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="61fa5-105">These failures are usually the result of an assembly deployed to the wrong location, a native image that is no longer valid, or a mismatch in version numbers or cultures.</span></span> <span data-ttu-id="61fa5-106">通常、共通言語ランタイムによるアセンブリ検出エラーは、アプリケーション内で <xref:System.TypeLoadException> として示されます。</span><span class="sxs-lookup"><span data-stu-id="61fa5-106">The common language runtime's failure to locate an assembly typically shows up as a <xref:System.TypeLoadException> in your application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="61fa5-107">fuslogvw.exe は、管理者特権で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61fa5-107">You must run fuslogvw.exe with administrator privileges.</span></span>  
  
 <span data-ttu-id="61fa5-108">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="61fa5-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="61fa5-109">このツールを実行するには、管理者の資格情報で開発者コマンド プロンプト (または、Windows 7 の Visual Studio コマンド プロンプト) を使用します。</span><span class="sxs-lookup"><span data-stu-id="61fa5-109">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7) with administrator credentials.</span></span> <span data-ttu-id="61fa5-110">詳細については、「[コマンド プロンプト](../../../docs/framework/tools/developer-command-prompt-for-vs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61fa5-110">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="61fa5-111">コマンド プロンプトに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="61fa5-111">At the command prompt, type the following:</span></span>  
  
```  
fuslogvw  
```  
  
 <span data-ttu-id="61fa5-112">ビューアーには、失敗したアセンブリ バインドごとに 1 つのエントリが表示されます。</span><span class="sxs-lookup"><span data-stu-id="61fa5-112">The viewer displays an entry for each failed assembly bind.</span></span> <span data-ttu-id="61fa5-113">バインドを開始したアプリケーション、バインドの対象となるアセンブリ (名前、バージョン、カルチャ、公開キーなど)、およびエラーの日時の情報が、エラーごとにビューアーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="61fa5-113">For each failure, the viewer describes the application that initiated the bind; the assembly the bind is for, including name, version, culture and public key; and the date and time of the failure.</span></span>  
  
### <a name="to-change-the-log-location-view"></a><span data-ttu-id="61fa5-114">ログ位置ビューを変更するには</span><span class="sxs-lookup"><span data-stu-id="61fa5-114">To change the log location view</span></span>  
  
1.  <span data-ttu-id="61fa5-115">[**Default**] を選択すると、すべてのアプリケーションの種類のバインド エラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="61fa5-115">Select the **Default** option button to view bind failures for all application types.</span></span> <span data-ttu-id="61fa5-116">既定では、ログ エントリは wininet キャッシュのディスクのユーザーごとのディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="61fa5-116">By default, log entries are stored in per-user directories on disk in the wininet cache.</span></span>  
  
2.  <span data-ttu-id="61fa5-117">[**Custom**] を選択すると、指定したカスタム ディレクトリのバインド エラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="61fa5-117">Select the **Custom** option button to view bind failures in a custom directory that you specify.</span></span> <span data-ttu-id="61fa5-118">[**ログ設定**] ダイアログの [カスタム ログのパス] を使用して、ランタイムがログを格納するカスタムの場所を有効なディレクトリ名に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61fa5-118">You must specify the custom location where you want the runtime to store the logs by setting the custom log location in the **Log Settings** dialog to a valid directory name.</span></span> <span data-ttu-id="61fa5-119">このディレクトリはクリーンで、ランタイムが生成するファイルだけが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="61fa5-119">This directory should be clean, and only contain files that the runtime generates.</span></span> <span data-ttu-id="61fa5-120">このディレクトリに、ログに記録するエラーを生成する実行可能ファイルが含まれている場合は、その実行可能ファイルと同じ名前でディレクトリの作成が試行されるため、そのエラーはログに記録されません。</span><span class="sxs-lookup"><span data-stu-id="61fa5-120">If it contains an executable that generates a failure to be logged, the failure will not be logged because the tool tries to create a directory with the same name as the executable.</span></span> <span data-ttu-id="61fa5-121">また、ログの位置から実行可能ファイルを実行しようとすると、失敗します。</span><span class="sxs-lookup"><span data-stu-id="61fa5-121">In addition, an attempt to run an executable from the log location will fail.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="61fa5-122">カスタム バインド位置ではなく、既定のバインド位置を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="61fa5-122">The default bind location is preferable to the custom bind location.</span></span> <span data-ttu-id="61fa5-123">ランタイムは wininet キャッシュに既定のバインド位置を格納するので、この位置は自動的に消去されます。</span><span class="sxs-lookup"><span data-stu-id="61fa5-123">The runtime stores the default bind location in the wininet cache, and therefore automatically cleans it out.</span></span> <span data-ttu-id="61fa5-124">カスタム バインド位置を指定する場合は、この位置を削除する手段を独自に組み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="61fa5-124">If you specify a custom bind location, you are responsible for cleaning it out.</span></span>  
  
### <a name="to-view-details-about-a-specific-failure"></a><span data-ttu-id="61fa5-125">特定のエラーの詳細を表示するには</span><span class="sxs-lookup"><span data-stu-id="61fa5-125">To view details about a specific failure</span></span>  
  
1.  <span data-ttu-id="61fa5-126">ビューアーにエントリを表示するアプリケーション名を選択します。</span><span class="sxs-lookup"><span data-stu-id="61fa5-126">Select the application name of the desired entry in the viewer.</span></span>  
  
2.  <span data-ttu-id="61fa5-127">[**View Log**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61fa5-127">Click the **View Log** button.</span></span> <span data-ttu-id="61fa5-128">また、選択したエントリをダブルクリックすることもできます。</span><span class="sxs-lookup"><span data-stu-id="61fa5-128">Alternately, you can double-click the selected entry.</span></span>  
  
     <span data-ttu-id="61fa5-129">選択したバインド エラーについて、次の詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="61fa5-129">The tool displays the following details about the selected bind failure:</span></span>  
  
    -   <span data-ttu-id="61fa5-130">"ファイルが見つからない" や "バージョンの不一致" など、バインド エラーの具体的な原因。</span><span class="sxs-lookup"><span data-stu-id="61fa5-130">The specific reason the bind failed, such as "file not found" or "version mismatch".</span></span>  
  
    -   <span data-ttu-id="61fa5-131">バインドを開始したアプリケーションについての情報 (アプリケーション名、アプリケーションのルート ディレクトリ (AppBase)、プライベート検索パスが存在する場合にはそのパスなど)。</span><span class="sxs-lookup"><span data-stu-id="61fa5-131">Information about the application that initiated the bind, including its name, the application's root directory (AppBase), and a description of the private search path, if there is one.</span></span>  
  
    -   <span data-ttu-id="61fa5-132">検索対象となるアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="61fa5-132">The identity of the assembly the tool is looking for.</span></span>  
  
    -   <span data-ttu-id="61fa5-133">Application、Publisher、または Administrator バージョンのポリシーが適用されている場合は、その説明。</span><span class="sxs-lookup"><span data-stu-id="61fa5-133">A description of any Application, Publisher, or Administrator version policies that have been applied.</span></span>  
  
    -   <span data-ttu-id="61fa5-134">[グローバル アセンブリ キャッシュ](../../../docs/framework/app-domains/gac.md)でのアセンブリの検出の有無。</span><span class="sxs-lookup"><span data-stu-id="61fa5-134">Whether the assembly was found in the [global assembly cache](../../../docs/framework/app-domains/gac.md).</span></span>  
  
    -   <span data-ttu-id="61fa5-135">すべてのプローブ URL の一覧。</span><span class="sxs-lookup"><span data-stu-id="61fa5-135">A list of all probing URLs.</span></span>  
  
 <span data-ttu-id="61fa5-136">失敗したアセンブリ バインドについての詳細情報を表示するサンプル ログ エントリを次に示します。</span><span class="sxs-lookup"><span data-stu-id="61fa5-136">The following sample log entry shows detailed information about a failed assembly bind.</span></span>  
  
```  
*** Assembly Binder Log Entry  (3/5/2007 @ 12:54:20 PM) ***  
  
The operation failed.  
Bind result: hr = 0x80070002. The system cannot find the file specified.  
  
Assembly manager loaded from:  C:\WINNT\Microsoft.NET\Framework\v2.0.50727\fusion.dll  
Running under executable  C:\Program Files\Microsoft.NET\FrameworkSDK\Samples\Tutorials\resourcesandlocalization\graphic\cs\graphicfailtest.exe  
--- A detailed error log follows.   
  
=== Pre-bind state information ===  
LOG: DisplayName = graphicfailtest.resources, Version=0.0.0.0, Culture=en-US, PublicKeyToken=null  
 (Fully-specified)  
LOG: Appbase = C:\Program Files\Microsoft.NET\FrameworkSDK\Samples\Tutorials\resourcesandlocalization\graphic\cs\  
LOG: Initial PrivatePath = NULL  
LOG: Dynamic Base = NULL  
LOG: Cache Base = NULL  
LOG: AppName = NULL  
Calling assembly : graphicfailtest, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
===  
  
LOG: Processing DEVPATH.  
LOG: DEVPATH is not set. Falling through to regular bind.  
LOG: Policy not being applied to reference at this time (private, custom, partial, or location-based assembly bind).  
LOG: Post-policy reference: graphicfailtest.resources, Version=0.0.0.0, Culture=en-US, PublicKeyToken=null  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources.DLL.  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources/graphicfailtest.resources.DLL.  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources.EXE.  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources/graphicfailtest.resources.EXE.  
LOG: All probing URLs attempted and failed.  
```  
  
### <a name="to-delete-a-single-entry-from-the-log"></a><span data-ttu-id="61fa5-137">ログから単一のエントリを削除するには</span><span class="sxs-lookup"><span data-stu-id="61fa5-137">To delete a single entry from the log</span></span>  
  
1.  <span data-ttu-id="61fa5-138">ビューアーでエントリを選択します。</span><span class="sxs-lookup"><span data-stu-id="61fa5-138">Select an entry in the viewer.</span></span>  
  
2.  <span data-ttu-id="61fa5-139">[**Delete Entry**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61fa5-139">Click the **Delete Entry** button.</span></span>  
  
### <a name="to-delete-all-entries-from-the-log"></a><span data-ttu-id="61fa5-140">ログからすべてのエントリを削除するには</span><span class="sxs-lookup"><span data-stu-id="61fa5-140">To delete all entries from the log</span></span>  
  
-   <span data-ttu-id="61fa5-141">[**Delete All**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61fa5-141">Click the **Delete All** button.</span></span>  
  
### <a name="to-refresh-the-user-interface"></a><span data-ttu-id="61fa5-142">ユーザー インターフェイスに最新の情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="61fa5-142">To refresh the user interface</span></span>  
  
-   <span data-ttu-id="61fa5-143">[**最新の情報に更新**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61fa5-143">Click the **Refresh** button.</span></span> <span data-ttu-id="61fa5-144">ビューアーの実行中に新しいログ エントリが自動的に検出されることはありません。</span><span class="sxs-lookup"><span data-stu-id="61fa5-144">The viewer does not automatically detect new log entries while it is running.</span></span> <span data-ttu-id="61fa5-145">新しいログ エントリを表示するには、[**Refresh**] を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61fa5-145">You must use the **Refresh** button to display them.</span></span>  
  
### <a name="to-change-the-log-settings"></a><span data-ttu-id="61fa5-146">ログ設定を変更するには、次の処理手順に従います。</span><span class="sxs-lookup"><span data-stu-id="61fa5-146">To change the log settings</span></span>  
  
-   <span data-ttu-id="61fa5-147">[**設定**] をクリックして [**ログ設定**] ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="61fa5-147">Click the **Settings** button to open the **Log Settings** dialog.</span></span>  
  
### <a name="to-view-the-about-dialog"></a><span data-ttu-id="61fa5-148">[バージョン情報] ダイアログを表示するには</span><span class="sxs-lookup"><span data-stu-id="61fa5-148">To view the About dialog</span></span>  
  
-   <span data-ttu-id="61fa5-149">[**バージョン情報**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61fa5-149">Click the **About** button.</span></span>  
  
## <a name="binding-logs-for-native-images"></a><span data-ttu-id="61fa5-150">ネイティブ イメージのバインディング ログ</span><span class="sxs-lookup"><span data-stu-id="61fa5-150">Binding Logs for Native Images</span></span>  
 <span data-ttu-id="61fa5-151">既定では、Fuslogvw.exe は通常のアセンブリ バインド要求をログに記録します。</span><span class="sxs-lookup"><span data-stu-id="61fa5-151">By default, Fuslogvw.exe logs normal assembly bind requests.</span></span> <span data-ttu-id="61fa5-152">代わりに、[ネイティブ イメージ ジェネレーター (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) を使用して作成されたネイティブ イメージのアセンブリ バインドをログに記録することもできます。</span><span class="sxs-lookup"><span data-stu-id="61fa5-152">Alternatively, you can log assembly binds for native images that were created using the [Ngen.exe (Native Image Generator)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>  
  
#### <a name="to-log-assembly-binds-for-native-images"></a><span data-ttu-id="61fa5-153">ネイティブ イメージのアセンブリ バインドをログに記録するには</span><span class="sxs-lookup"><span data-stu-id="61fa5-153">To log assembly binds for native images</span></span>  
  
-   <span data-ttu-id="61fa5-154">[**ログのカテゴリ**] グループで、[**ネイティブ イメージ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61fa5-154">In the **Log Categories** group, select the **Native Images** option button.</span></span>  
  
 <span data-ttu-id="61fa5-155">次のログは、アプリケーションのネイティブ イメージの作成時には存在しなかった依存関係が原因で発生したエラーを示しています。</span><span class="sxs-lookup"><span data-stu-id="61fa5-155">The following log shows a failure caused by a dependency that did not exist when the native image was created for the application.</span></span> <span data-ttu-id="61fa5-156">実行時の依存関係が Ngen.exe を実行したときの依存関係と異なる場合、ネイティブ イメージへのバインドはできません。</span><span class="sxs-lookup"><span data-stu-id="61fa5-156">If the dependencies at run time differ from the dependencies when Ngen.exe is run, binding to a native image is not allowed.</span></span>  
  
```  
*** Assembly Binder Log Entry  (12/8/2006 @ 5:22:07 PM) ***  
  
The operation failed.  
Bind result: hr = 0x80070002. The system cannot find the file specified.  
  
Assembly manager loaded from:  E:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll  
Running under executable  E:\test\App.exe  
--- A detailed error log follows.   
  
LOG: Start binding of native image App, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: IL assembly loaded from E:\test\App.exe.  
LOG: Start validating native image App, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: Start validating all the dependencies.  
LOG: [Level 1]Start validating native image dependency mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.  
LOG: Dependency evaluation succeeded.  
LOG: [Level 1]Start validating IL dependency b, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
WRN: Dependency assembly was not found at ngen time, but is found at binding time. Disallow using this native image.  
WRN: No matching native image found.  
LOG: Bind to native image assembly did not succeed. Use IL image.  
```  
  
 <span data-ttu-id="61fa5-157">次のログは、アプリケーションが実行されたときのコンピューターのセキュリティ設定が、ネイティブ イメージの作成時のセキュリティ設定と異なるために発生したネイティブ イメージのバインディング エラーを示しています。</span><span class="sxs-lookup"><span data-stu-id="61fa5-157">The following log shows a native image binding failure that occurred because the security settings on the computer when the application was run were different from the security settings at the time the native image was created.</span></span>  
  
```  
*** Assembly Binder Log Entry  (12/8/2006 @ 5:29:09 PM) ***  
  
The operation failed.  
Bind result: hr = 0x80004005. Unspecified error  
  
Assembly manager loaded from:  E:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll  
Running under executable  E:\test\Application101622.exe  
--- A detailed error log follows.   
  
LOG: Start binding of native image Application101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: IL assembly loaded from E:\test\Application101622.exe.  
LOG: Start validating native image Application101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: Start validating all the dependencies.  
LOG: [Level 1]Start validating native image dependency mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.  
LOG: Dependency evaluation succeeded.  
LOG: [Level 1]Start validating IL dependency Dependency101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: Dependency evaluation succeeded.  
LOG: Validation of dependencies succeeded.  
LOG: Start loading all the dependencies into load context.  
LOG: Loading of dependencies succeeded.  
LOG: Bind to native image succeeded.  
Native image has correct version information.  
Attempting to use native image E:\Windows\assembly\NativeImages_v2.0.50727_64\Application101622\1ac7fadabec4f72575d807501e9fdc72\Application101622.ni.exe.  
Rejecting native image because it failed the security check. The assembly's permissions must have changed since the time it was ngenned, or it is running with a different security context.  
Discarding native image.  
```  
  
## <a name="the-log-settings-dialog"></a><span data-ttu-id="61fa5-158">[ログ設定] ダイアログ</span><span class="sxs-lookup"><span data-stu-id="61fa5-158">The Log Settings Dialog</span></span>  
 <span data-ttu-id="61fa5-159">[**ログ設定**] ダイアログを使用すると、次のようなアクションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="61fa5-159">You can use the **Log Settings** dialog to perform the following actions.</span></span>  
  
#### <a name="to-disable-logging"></a><span data-ttu-id="61fa5-160">ログを無効にするには</span><span class="sxs-lookup"><span data-stu-id="61fa5-160">To disable logging</span></span>  
  
-   <span data-ttu-id="61fa5-161">[**ログを無効にする**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61fa5-161">Select the **Log disabled** option button.</span></span>  <span data-ttu-id="61fa5-162">このオプションの既定値はオンです。</span><span class="sxs-lookup"><span data-stu-id="61fa5-162">Note that this option is selected by default.</span></span>  
  
#### <a name="to-log-assembly-binds-in-exceptions"></a><span data-ttu-id="61fa5-163">アセンブリ バインドの例外をログに記録するには</span><span class="sxs-lookup"><span data-stu-id="61fa5-163">To log assembly binds in exceptions</span></span>  
  
-   <span data-ttu-id="61fa5-164">[**例外テキストに記録する**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61fa5-164">Select the **Log in exception text** option button.</span></span> <span data-ttu-id="61fa5-165">詳細度が最も低い fusion ログ情報だけが例外テキストに記録されます。</span><span class="sxs-lookup"><span data-stu-id="61fa5-165">Only the least detailed fusion log information is logged in exception text.</span></span> <span data-ttu-id="61fa5-166">完全な情報を表示するには、その他の設定のいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="61fa5-166">To view full information, use one of the other settings.</span></span>  
  
     <span data-ttu-id="61fa5-167">ドメインに中立的に読み込まれたアセンブリに関する「重要」メモを参照してください。</span><span class="sxs-lookup"><span data-stu-id="61fa5-167">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>  
  
#### <a name="to-log-assembly-bind-failures"></a><span data-ttu-id="61fa5-168">アセンブリ バインドの失敗をログに記録するには</span><span class="sxs-lookup"><span data-stu-id="61fa5-168">To log assembly bind failures</span></span>  
  
-   <span data-ttu-id="61fa5-169">[**バインドの失敗をディスクに記録する**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61fa5-169">Select the **Log bind failures to disk** option button.</span></span>  
  
     <span data-ttu-id="61fa5-170">ドメインに中立的に読み込まれたアセンブリに関する「重要」メモを参照してください。</span><span class="sxs-lookup"><span data-stu-id="61fa5-170">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>  
  
#### <a name="to-log-all-assembly-binds"></a><span data-ttu-id="61fa5-171">すべてのアセンブリ バインドをログに記録するには</span><span class="sxs-lookup"><span data-stu-id="61fa5-171">To log all assembly binds</span></span>  
  
-   <span data-ttu-id="61fa5-172">[**すべてのバインドをディスクに記録する**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61fa5-172">Select the **Log all binds to disk** option button.</span></span>  
  
     <span data-ttu-id="61fa5-173">ドメインに中立的に読み込まれたアセンブリに関する「重要」メモを参照してください。</span><span class="sxs-lookup"><span data-stu-id="61fa5-173">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="61fa5-174">アセンブリがドメインに中立的に読み込まれた場合 (<xref:System.AppDomainSetup.LoaderOptimization%2A> プロパティを <xref:System.LoaderOptimization.MultiDomain?displayProperty=fullName> または <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=fullName> に設定した場合など)、ログが有効になっているとメモリがリークすることがあります。</span><span class="sxs-lookup"><span data-stu-id="61fa5-174">When an assembly is loaded as domain neutral, for example by setting the <xref:System.AppDomainSetup.LoaderOptimization%2A> property to <xref:System.LoaderOptimization.MultiDomain?displayProperty=fullName> or <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=fullName>, turning on logging might leak memory in some cases.</span></span> <span data-ttu-id="61fa5-175">これが起こるのは、ドメインに中立的なモジュールがアプリケーション ドメインに読み込まれているときにログ エントリが作成され、その後でアプリケーション ドメインがアンロードされた場合です。</span><span class="sxs-lookup"><span data-stu-id="61fa5-175">This can happen if a log entry is made when a domain-neutral module is loaded into an application domain, and later the application domain is unloaded.</span></span> <span data-ttu-id="61fa5-176">このログ エントリは、プロセスが終了するまで解放されません。</span><span class="sxs-lookup"><span data-stu-id="61fa5-176">The log entry might not be released until the process ends.</span></span> <span data-ttu-id="61fa5-177">一部のデバッガーは、自動的にログを有効にします。</span><span class="sxs-lookup"><span data-stu-id="61fa5-177">Some debuggers automatically turn on logging.</span></span>  
  
#### <a name="to-enable-a-custom-log-path"></a><span data-ttu-id="61fa5-178">カスタムのログ パスを有効にするには</span><span class="sxs-lookup"><span data-stu-id="61fa5-178">To enable a custom log path</span></span>  
  
1.  <span data-ttu-id="61fa5-179">[**カスタム ログを有効にする**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="61fa5-179">Select the **Enable custom log path** option button.</span></span>  
  
2.  <span data-ttu-id="61fa5-180">[**カスタム ログのパス**] テキスト ボックスにパスを入力します。</span><span class="sxs-lookup"><span data-stu-id="61fa5-180">Enter the path into the **Custom log path** text box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61fa5-181">[アセンブリ バインディング ログ ビューアー (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) では、バインディング ログの格納に Internet Explorer (IE) のキャッシュを使用します。</span><span class="sxs-lookup"><span data-stu-id="61fa5-181">The [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) uses the Internet Explorer (IE) cache to store its binding log.</span></span> <span data-ttu-id="61fa5-182">IE キャッシュは時折破損することがあるため、[アセンブリ バインディング ログ ビューアー (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) の表示ウィンドウに新しいバインディング ログが表示されなくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="61fa5-182">Due to occasional corruption in the IE cache, the [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) can sometimes stop showing new binding logs in the viewing window.</span></span> <span data-ttu-id="61fa5-183">IE キャッシュが破損した場合、.NET バインディング インフラストラクチャ (fusion) ではバインディング ログの読み書きができなくなります</span><span class="sxs-lookup"><span data-stu-id="61fa5-183">As a result of this corruption, the .NET binding infrastructure (fusion) cannot write to or read from the binding log.</span></span> <span data-ttu-id="61fa5-184">(この問題はカスタム ログ パスを使用している場合は発生しません)。破損を修復し、fusion でバインディング ログが再度表示されるようにするには、IE の [インターネット オプション] ダイアログで一時インターネット ファイルを削除して IE キャッシュを消去します。</span><span class="sxs-lookup"><span data-stu-id="61fa5-184">(This issue is not encountered if you use a custom log path.)  To fix the corruption and allow fusion to show binding logs again, clear the IE cache by deleting temporary internet files from within the IE Internet Options dialog.</span></span>  
>   
>  <span data-ttu-id="61fa5-185">アンマネージ アプリケーションが、`IHostAssemblyManager` インターフェイスと `IHostAssemblyStore` インターフェイスを実装して共通言語ランタイムをホストしている場合、ログ エントリを wininet キャッシュに格納できません。</span><span class="sxs-lookup"><span data-stu-id="61fa5-185">If your unmanaged application hosts the common language runtime by implementing the `IHostAssemblyManager` and `IHostAssemblyStore` interfaces, log entries can't be stored in the wininet cache.</span></span>  <span data-ttu-id="61fa5-186">これらのインターフェイスを実装したカスタム ホストのログ エントリを表示するには、別のログ パスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61fa5-186">To view log entries for custom hosts that implement these interfaces, you must specify an alternate log path.</span></span>  
  
#### <a name="to-enable-logging-for-apps-running-in-the-windows-app-container"></a><span data-ttu-id="61fa5-187">Windows アプリ コンテナー内で実行するアプリに対してログを有効にするには</span><span class="sxs-lookup"><span data-stu-id="61fa5-187">To enable logging for apps running in the Windows app container</span></span>  
  
1.  <span data-ttu-id="61fa5-188">前の手順に従って、カスタム ログのパスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="61fa5-188">Enable a custom log path, as described in the previous procedure.</span></span> <span data-ttu-id="61fa5-189">既定では、Windows アプリ コンテナー内で実行しているアプリでは、ハード ディスクへのアクセスが制限されます。</span><span class="sxs-lookup"><span data-stu-id="61fa5-189">By default, apps that are running in the Windows app container have limited access to the hard disk.</span></span> <span data-ttu-id="61fa5-190">指定するディレクトリでは、アプリ コンテナー内のすべてのアプリに対する読み取り/書き込みアクセスが与えられます。</span><span class="sxs-lookup"><span data-stu-id="61fa5-190">The directory you specify will have read/write access for all apps in the app container.</span></span>  
  
2.  <span data-ttu-id="61fa5-191">[**没入型のログを有効にします**] チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="61fa5-191">Select the **Enable immersive logging** check box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="61fa5-192">このチェック ボックスは、Windows 8 以降でのみ有効になります。</span><span class="sxs-lookup"><span data-stu-id="61fa5-192">This box is enabled only on Windows 8 or later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61fa5-193">関連項目</span><span class="sxs-lookup"><span data-stu-id="61fa5-193">See Also</span></span>  
 <span data-ttu-id="61fa5-194"><xref:System.TypeLoadException></span><span class="sxs-lookup"><span data-stu-id="61fa5-194"><xref:System.TypeLoadException></span></span>   
 <span data-ttu-id="61fa5-195">[ツール](../../../docs/framework/tools/index.md) </span><span class="sxs-lookup"><span data-stu-id="61fa5-195">[Tools](../../../docs/framework/tools/index.md) </span></span>  
 <span data-ttu-id="61fa5-196">[グローバル アセンブリ キャッシュ](../../../docs/framework/app-domains/gac.md) </span><span class="sxs-lookup"><span data-stu-id="61fa5-196">[Global Assembly Cache](../../../docs/framework/app-domains/gac.md) </span></span>  
 <span data-ttu-id="61fa5-197">[ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="61fa5-197">[How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md) </span></span>  
 [<span data-ttu-id="61fa5-198">コマンド プロンプト</span><span class="sxs-lookup"><span data-stu-id="61fa5-198">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)


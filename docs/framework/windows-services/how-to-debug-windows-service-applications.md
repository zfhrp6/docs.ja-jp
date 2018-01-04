---
title: "方法 : Windows サービス アプリケーションをデバッグする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- Windows NT services, debugging
- Windows Service applications, debugging
- services, debugging
ms.assetid: 63ab0800-0f05-4f1e-88e6-94c73fd920a2
caps.latest.revision: "16"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 86d90e4129f089a77e51e6e58233a1087fe5d0f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-windows-service-applications"></a><span data-ttu-id="1bcf1-102">方法 : Windows サービス アプリケーションをデバッグする</span><span class="sxs-lookup"><span data-stu-id="1bcf1-102">How to: Debug Windows Service Applications</span></span>
<span data-ttu-id="1bcf1-103">サービスは、Visual Studio 内からではなく、サービス コントロール マネージャーのコンテキスト内から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-103">A service must be run from within the context of the Services Control Manager rather than from within Visual Studio.</span></span> <span data-ttu-id="1bcf1-104">そのため、サービスのデバッグは、その他の種類の Visual Studio アプリケーションをデバッグするように単純ではありません。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-104">For this reason, debugging a service is not as straightforward as debugging other Visual Studio application types.</span></span> <span data-ttu-id="1bcf1-105">サービスのデバッグを行うには、サービスを起動してから、サービスを実行しているプロセスにデバッガーをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-105">To debug a service, you must start the service and then attach a debugger to the process in which it is running.</span></span> <span data-ttu-id="1bcf1-106">これにより、Visual Studio のすべての標準デバッグ機能を使用して、アプリケーションをデバッグできるようになります。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-106">You can then debug your application by using all of the standard debugging functionality of Visual Studio.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="1bcf1-107">プロセスが強制終了される可能性もあるため、アタッチするプロセスの特性や、アタッチによる影響をよく理解している場合に限って、プロセスにデバッガーをアタッチしてください。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-107">You should not attach to a process unless you know what the process is and understand the consequences of attaching to and possibly killing that process.</span></span> <span data-ttu-id="1bcf1-108">たとえば、システムは WinLogon プロセスがないと動作しないため、WinLogon プロセスにデバッガーをアタッチした後でデバッグを中止すると、システムは停止します。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-108">For example, if you attach to the WinLogon process and then stop debugging, the system will halt because it can’t operate without WinLogon.</span></span>  
  
 <span data-ttu-id="1bcf1-109">デバッガーをアタッチできるのは、実行中のサービスだけです。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-109">You can attach the debugger only to a running service.</span></span> <span data-ttu-id="1bcf1-110">アタッチのプロセスは、サービスが現在実行している処理に割り込みます。実際にサービスの処理の停止や一時停止を行うのではありません。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-110">The attachment process interrupts the current functioning of your service; it doesn’t actually stop or pause the service's processing.</span></span> <span data-ttu-id="1bcf1-111">つまり、実行中のサービスに対してデバッグを開始すると、デバッグの間、サービスは技術的には起動状態のままですが、処理は中断されます。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-111">That is, if your service is running when you begin debugging, it is still technically in the Started state as you debug it, but its processing has been suspended.</span></span>  
  
 <span data-ttu-id="1bcf1-112">プロセスにデバッガーをアタッチした後で、ブレークポイントを設定し、設定したブレークポイントを使用してコードをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-112">After attaching to the process, you can set breakpoints and use these to debug your code.</span></span> <span data-ttu-id="1bcf1-113">プロセスへのアタッチに使用するダイアログ ボックスを閉じると、デバッグ モードが有効になります。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-113">Once you exit the dialog box you use to attach to the process, you are effectively in debug mode.</span></span> <span data-ttu-id="1bcf1-114">サービス コントロール マネージャーを使用して、サービスの開始、停止、一時停止、および再開を行うことができます。これによって、設定したブレークポイントにヒットします。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-114">You can use the Services Control Manager to start, stop, pause and continue your service, thus hitting the breakpoints you've set.</span></span> <span data-ttu-id="1bcf1-115">デバッグが正常に完了したら、このダミー サービスを削除できます。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-115">You can later remove this dummy service after debugging is successful.</span></span>  
  
 <span data-ttu-id="1bcf1-116">この記事ではローカル コンピューターで実行されているサービスのデバッグについて説明しますが、リモート コンピューターで実行されている Windows サービスをデバッグすることもできます。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-116">This article covers debugging a service that's running on the local computer, but you can also debug Windows Services that are running on a remote computer.</span></span> <span data-ttu-id="1bcf1-117">参照してください[リモート デバッグ](/visualstudio/debugger/debug-installed-app-package)です。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-117">See [Remote Debugging](/visualstudio/debugger/debug-installed-app-package).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1bcf1-118">サービス コントロール マネージャーではすべてのサービスの開始試行に対して 30 秒の制限が適用されるため、<xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドのデバッグが困難になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-118">Debugging the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method can be difficult because the Services Control Manager imposes a 30-second limit on all attempts to start a service.</span></span> <span data-ttu-id="1bcf1-119">詳細については、次を参照してください。[トラブルシューティング: Windows サービスのデバッグ](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-119">For more information, see [Troubleshooting: Debugging Windows Services](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="1bcf1-120">デバッグに有用な情報を取得するためには、Visual Studio デバッガーは、デバッグ対象のバイナリのシンボル ファイルを検索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-120">To get meaningful information for debugging, the Visual Studio debugger needs to find symbol files for the binaries that are being debugged.</span></span> <span data-ttu-id="1bcf1-121">Visual Studio に組み込まれているサービスをデバッグしている場合は、シンボル ファイル (.pdb ファイル) は実行可能ファイルまたはライブラリと同じフォルダーにあり、デバッガーはそれらを自動的に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-121">If you are debugging a service that you built in Visual Studio, the symbol files (.pdb files) are in the same folder as the executable or library, and the debugger loads them automatically.</span></span> <span data-ttu-id="1bcf1-122">構築していないサービスをデバッグしている場合は、最初にサービスのシンボルを検索し、デバッガーでこれらを検出できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-122">If you are debugging a service that you didn't build, you should first find symbols for the service and make sure they can be found by the debugger.</span></span> <span data-ttu-id="1bcf1-123">参照してください[シンボル (.pdb) を指定して、ソース ファイル](http://msdn.microsoft.com/library/1105e169-5272-4e7c-b3e7-cda1b7798a6b)です。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-123">See [Specify Symbol (.pdb) and Source Files](http://msdn.microsoft.com/library/1105e169-5272-4e7c-b3e7-cda1b7798a6b).</span></span> <span data-ttu-id="1bcf1-124">システム プロセスをデバッグしているか、サービスにシステム呼び出しのシンボルを含めたい場合は、Microsoft シンボル サーバーを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-124">If you're debugging a system process or want to have symbols for system calls in your services, you should add the Microsoft Symbol Servers.</span></span> <span data-ttu-id="1bcf1-125">参照してください[デバッグ シンボル](http://msdn.microsoft.com/windows/desktop/ee416588.aspx)です。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-125">See [Debugging Symbols](http://msdn.microsoft.com/windows/desktop/ee416588.aspx).</span></span>  
  
### <a name="to-debug-a-service"></a><span data-ttu-id="1bcf1-126">サービスをデバッグするには</span><span class="sxs-lookup"><span data-stu-id="1bcf1-126">To debug a service</span></span>  
  
1.  <span data-ttu-id="1bcf1-127">サービスをデバッグ構成で構築します。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-127">Build your service in the Debug configuration.</span></span>  
  
2.  <span data-ttu-id="1bcf1-128">サービスをインストールします。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-128">Install your service.</span></span> <span data-ttu-id="1bcf1-129">詳細については、「 [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-129">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
3.  <span data-ttu-id="1bcf1-130">いずれかから、サービスを起動**サービス コントロール マネージャー**、**サーバー エクスプ ローラー**コードとの間です。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-130">Start your service, either from **Services Control Manager**, **Server Explorer**, or from code.</span></span> <span data-ttu-id="1bcf1-131">詳細については、次を参照してください。[する方法: サービスを開始](../../../docs/framework/windows-services/how-to-start-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-131">For more information, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span>  
  
4.  <span data-ttu-id="1bcf1-132">システム プロセスにアタッチすることができるように、管理者資格情報を使用して Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-132">Start Visual Studio with administrative credentials so you can attach to system processes.</span></span>  
  
5.  <span data-ttu-id="1bcf1-133">(省略可能)Visual Studio メニュー バーで、**ツール**、**オプション**です。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-133">(Optional) On the Visual Studio menu bar, choose **Tools**, **Options**.</span></span> <span data-ttu-id="1bcf1-134">**オプション** ダイアログ ボックスで、選択**デバッグ**、**シンボル**、select、 **Microsoft シンボル サーバー**チェック ボックスをオンにして、**OK**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-134">In the **Options** dialog box, choose **Debugging**, **Symbols**, select the **Microsoft Symbol Servers** check box, and then choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="1bcf1-135">メニュー バーで、次のように選択します。**プロセスにアタッチする**から、**デバッグ**または**ツール**メニュー。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-135">On the menu bar, choose **Attach to Process** from the **Debug** or **Tools** menu.</span></span> <span data-ttu-id="1bcf1-136">(キーボード: Ctrl + Alt + P)</span><span class="sxs-lookup"><span data-stu-id="1bcf1-136">(Keyboard: Ctrl+Alt+P)</span></span>  
  
     <span data-ttu-id="1bcf1-137">**プロセス** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-137">The **Processes** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="1bcf1-138">選択、**プロセスのすべてのユーザーを表示する**チェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-138">Select the **Show processes from all users** check box.</span></span>  
  
8.  <span data-ttu-id="1bcf1-139">**選択可能なプロセス**セクションで、サービスのプロセスを選択し、**アタッチ**です。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-139">In the **Available Processes** section, choose the process for your service, and then choose **Attach**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="1bcf1-140">プロセスの名前は、サービスの実行可能ファイルの名前と同じになります。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-140">The process will have the same name as the executable file for your service.</span></span>  
  
     <span data-ttu-id="1bcf1-141">**[プロセスにアタッチ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-141">The **Attach to Process** dialog box appears.</span></span>  
  
9. <span data-ttu-id="1bcf1-142">適切なオプションを選択し、**[OK]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-142">Choose the appropriate options, and then choose **OK** to close the dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1bcf1-143">デバッグ モードになります。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-143">You are now in debug mode.</span></span>  
  
10. <span data-ttu-id="1bcf1-144">コード内で使用する任意のブレークポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-144">Set any breakpoints you want to use in your code.</span></span>  
  
11. <span data-ttu-id="1bcf1-145">サービス コントロール マネージャーを起動し、停止、一時停止、再開の各コマンドを送信してサービスを操作して、ブレークポイントをヒットします。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-145">Access the Services Control Manager and manipulate your service, sending stop, pause, and continue commands to hit your breakpoints.</span></span> <span data-ttu-id="1bcf1-146">詳細については、サービス コントロール マネージャーを実行して、次を参照してください。[する方法: サービスを開始](../../../docs/framework/windows-services/how-to-start-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-146">For more information about running the Services Control Manager, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span> <span data-ttu-id="1bcf1-147">またを参照してください[トラブルシューティング: Windows サービスのデバッグ](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-147">Also, see [Troubleshooting: Debugging Windows Services](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span></span>  
  
## <a name="debugging-tips-for-windows-services"></a><span data-ttu-id="1bcf1-148">Windows サービスのデバッグのヒント</span><span class="sxs-lookup"><span data-stu-id="1bcf1-148">Debugging Tips for Windows Services</span></span>  
 <span data-ttu-id="1bcf1-149">サービスのプロセスにアタッチすると、そのサービスのコードのほとんど (すべてではない) をデバッグすることができます。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-149">Attaching to the service's process allows you to debug most, but not all, the code for that service.</span></span> <span data-ttu-id="1bcf1-150">たとえば、サービスが既に開始されているため、そのサービスの <xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッド内のコード、またはサービスをこの方法で読み込むために使用されている `Main` メソッド内のコードは、デバッグすることができません。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-150">For example, because the service has already been started, you cannot debug the code in the service's <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method or the code in the `Main` method that is used to load the service this way.</span></span> <span data-ttu-id="1bcf1-151">この制限に対処する方法の 1 つは、デバッグ専用の一時的な "ダミー" サービスを作成し、サービス アプリケーションに追加することです。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-151">One way to work around this limitation is to create a temporary second service in your service application that exists only to aid in debugging.</span></span> <span data-ttu-id="1bcf1-152">サービスを両方ともインストールし、ダミー サービスを開始してサービス プロセスを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-152">You can install both services, and then start this dummy service to load the service process.</span></span> <span data-ttu-id="1bcf1-153">使用することができます、一時的なサービスのプロセスが開始されたら、**デバッグ**サービス プロセスにアタッチする Visual Studio のメニュー。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-153">Once the temporary service has started the process, you can use the **Debug** menu in Visual Studio to attach to the service process.</span></span>  
  
 <span data-ttu-id="1bcf1-154"><xref:System.Threading.Thread.Sleep%2A> メソッドに呼び出しを追加して、プロセスにアタッチできるようになるまで動作を遅延します。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-154">Try adding calls to the <xref:System.Threading.Thread.Sleep%2A> method to delay action until you’re able to attach to the process.</span></span>  
  
 <span data-ttu-id="1bcf1-155">プログラムを通常のコンソール アプリケーションに変更します。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-155">Try changing the program to a regular console application.</span></span> <span data-ttu-id="1bcf1-156">このためには、起動方法に応じて Windows サービスとコンソール アプリケーションの両方として実行することができるように、`Main` メソッドを次のように書き換えます。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-156">To do this, rewrite the `Main` method as follows so it can run both as a Windows Service and as a console application, depending on how it's started.</span></span>  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a><span data-ttu-id="1bcf1-157">方法: Windows サービスをコンソール アプリケーションとして実行する</span><span class="sxs-lookup"><span data-stu-id="1bcf1-157">How to: Run a Windows Service as a console application</span></span>  
  
1.  <span data-ttu-id="1bcf1-158"><xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドと <xref:System.ServiceProcess.ServiceBase.OnStop%2A> メソッドを実行するサービスにメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-158">Add a method to your service that runs the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods:</span></span>  
  
    ```  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2.  <span data-ttu-id="1bcf1-159">`Main` メソッドを次のように書き換えます。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-159">Rewrite the `Main` method as follows:</span></span>  
  
    ```  
    static void Main(string[] args)  
            {  
                if (Environment.UserInteractive)  
                {  
                    MyNewService service1 = new MyNewService(args);  
                    service1.TestStartupAndStop(args);  
                }  
                else  
                {  
                    // Put the body of your old Main method here.  
                }  
    ```  
  
3.  <span data-ttu-id="1bcf1-160">**アプリケーション**タブ、プロジェクトのプロパティの設定、**出力の種類**に**コンソール アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-160">In the **Application** tab of the project's properties, set the **Output type** to **Console Application**.</span></span>  
  
4.  <span data-ttu-id="1bcf1-161">選択**デバッグを開始**(F5) します。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-161">Choose **Start Debugging** (F5).</span></span>  
  
5.  <span data-ttu-id="1bcf1-162">プログラムを再度 Windows サービスとして実行するには、プログラムをインストールして、Windows サービスとして通常どおり起動します。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-162">To run the program as a Windows Service again, install it and start it as usual for a Windows Service.</span></span> <span data-ttu-id="1bcf1-163">これらの変更を反対にする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-163">It's not necessary to reverse these changes.</span></span>  
  
 <span data-ttu-id="1bcf1-164">システムの起動時にのみ発生する問題をデバッグするときなどのいくつかのケースでは、Windows デバッガーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-164">In some cases, such as when you want to debug an issue that occurs only on system startup, you have to use the Windows debugger.</span></span> <span data-ttu-id="1bcf1-165">インストール[Debugging Tools for Windows](http://msdn.microsoft.com/windows/hardware/hh852365)して[Windows サービスをデバッグする方法について](http://support.microsoft.com/kb/824344)です。</span><span class="sxs-lookup"><span data-stu-id="1bcf1-165">Install [Debugging Tools for Windows](http://msdn.microsoft.com/windows/hardware/hh852365) and see [How to debug Windows Services](http://support.microsoft.com/kb/824344).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bcf1-166">参照</span><span class="sxs-lookup"><span data-stu-id="1bcf1-166">See Also</span></span>  
 [<span data-ttu-id="1bcf1-167">Windows サービス アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="1bcf1-167">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="1bcf1-168">方法 : サービスをインストールおよびアンインストールする</span><span class="sxs-lookup"><span data-stu-id="1bcf1-168">How to: Install and Uninstall Services</span></span>](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [<span data-ttu-id="1bcf1-169">方法 : サービスを開始する</span><span class="sxs-lookup"><span data-stu-id="1bcf1-169">How to: Start Services</span></span>](../../../docs/framework/windows-services/how-to-start-services.md)  
 [<span data-ttu-id="1bcf1-170">サービスのデバッグ</span><span class="sxs-lookup"><span data-stu-id="1bcf1-170">Debugging a Service</span></span>](http://msdn.microsoft.com/library/windows/desktop/ms682546.aspx)

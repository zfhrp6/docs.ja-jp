---
title: '方法 : Windows サービス アプリケーションをデバッグする'
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- Windows NT services, debugging
- Windows Service applications, debugging
- services, debugging
ms.assetid: 63ab0800-0f05-4f1e-88e6-94c73fd920a2
author: ghogen
manager: douge
ms.openlocfilehash: 2c73ccd75bdbd1298371921bababa87ba4520495
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518051"
---
# <a name="how-to-debug-windows-service-applications"></a><span data-ttu-id="30cfc-102">方法 : Windows サービス アプリケーションをデバッグする</span><span class="sxs-lookup"><span data-stu-id="30cfc-102">How to: Debug Windows Service Applications</span></span>
<span data-ttu-id="30cfc-103">サービスは、Visual Studio 内からではなく、サービス コントロール マネージャーのコンテキスト内から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30cfc-103">A service must be run from within the context of the Services Control Manager rather than from within Visual Studio.</span></span> <span data-ttu-id="30cfc-104">そのため、サービスのデバッグは、その他の種類の Visual Studio アプリケーションをデバッグするように単純ではありません。</span><span class="sxs-lookup"><span data-stu-id="30cfc-104">For this reason, debugging a service is not as straightforward as debugging other Visual Studio application types.</span></span> <span data-ttu-id="30cfc-105">サービスのデバッグを行うには、サービスを起動してから、サービスを実行しているプロセスにデバッガーをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="30cfc-105">To debug a service, you must start the service and then attach a debugger to the process in which it is running.</span></span> <span data-ttu-id="30cfc-106">これにより、Visual Studio のすべての標準デバッグ機能を使用して、アプリケーションをデバッグできるようになります。</span><span class="sxs-lookup"><span data-stu-id="30cfc-106">You can then debug your application by using all of the standard debugging functionality of Visual Studio.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="30cfc-107">プロセスが強制終了される可能性もあるため、アタッチするプロセスの特性や、アタッチによる影響をよく理解している場合に限って、プロセスにデバッガーをアタッチしてください。</span><span class="sxs-lookup"><span data-stu-id="30cfc-107">You should not attach to a process unless you know what the process is and understand the consequences of attaching to and possibly killing that process.</span></span> <span data-ttu-id="30cfc-108">たとえば、システムは WinLogon プロセスがないと動作しないため、WinLogon プロセスにデバッガーをアタッチした後でデバッグを中止すると、システムは停止します。</span><span class="sxs-lookup"><span data-stu-id="30cfc-108">For example, if you attach to the WinLogon process and then stop debugging, the system will halt because it can’t operate without WinLogon.</span></span>  
  
 <span data-ttu-id="30cfc-109">デバッガーをアタッチできるのは、実行中のサービスだけです。</span><span class="sxs-lookup"><span data-stu-id="30cfc-109">You can attach the debugger only to a running service.</span></span> <span data-ttu-id="30cfc-110">アタッチのプロセスは、サービスが現在実行している処理に割り込みます。実際にサービスの処理の停止や一時停止を行うのではありません。</span><span class="sxs-lookup"><span data-stu-id="30cfc-110">The attachment process interrupts the current functioning of your service; it doesn’t actually stop or pause the service's processing.</span></span> <span data-ttu-id="30cfc-111">つまり、実行中のサービスに対してデバッグを開始すると、デバッグの間、サービスは技術的には起動状態のままですが、処理は中断されます。</span><span class="sxs-lookup"><span data-stu-id="30cfc-111">That is, if your service is running when you begin debugging, it is still technically in the Started state as you debug it, but its processing has been suspended.</span></span>  
  
 <span data-ttu-id="30cfc-112">プロセスにデバッガーをアタッチした後で、ブレークポイントを設定し、設定したブレークポイントを使用してコードをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="30cfc-112">After attaching to the process, you can set breakpoints and use these to debug your code.</span></span> <span data-ttu-id="30cfc-113">プロセスへのアタッチに使用するダイアログ ボックスを閉じると、デバッグ モードが有効になります。</span><span class="sxs-lookup"><span data-stu-id="30cfc-113">Once you exit the dialog box you use to attach to the process, you are effectively in debug mode.</span></span> <span data-ttu-id="30cfc-114">サービス コントロール マネージャーを使用して、サービスの開始、停止、一時停止、および再開を行うことができます。これによって、設定したブレークポイントにヒットします。</span><span class="sxs-lookup"><span data-stu-id="30cfc-114">You can use the Services Control Manager to start, stop, pause and continue your service, thus hitting the breakpoints you've set.</span></span> <span data-ttu-id="30cfc-115">デバッグが正常に完了したら、このダミー サービスを削除できます。</span><span class="sxs-lookup"><span data-stu-id="30cfc-115">You can later remove this dummy service after debugging is successful.</span></span>  
  
 <span data-ttu-id="30cfc-116">この記事ではローカル コンピューターで実行されているサービスのデバッグについて説明しますが、リモート コンピューターで実行されている Windows サービスをデバッグすることもできます。</span><span class="sxs-lookup"><span data-stu-id="30cfc-116">This article covers debugging a service that's running on the local computer, but you can also debug Windows Services that are running on a remote computer.</span></span> <span data-ttu-id="30cfc-117">「[リモート デバッグ](/visualstudio/debugger/debug-installed-app-package)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="30cfc-117">See [Remote Debugging](/visualstudio/debugger/debug-installed-app-package).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30cfc-118">サービス コントロール マネージャーではすべてのサービスの開始試行に対して 30 秒の制限が適用されるため、<xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドのデバッグが困難になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="30cfc-118">Debugging the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method can be difficult because the Services Control Manager imposes a 30-second limit on all attempts to start a service.</span></span> <span data-ttu-id="30cfc-119">詳しくは、「[Windows サービスをデバッグする場合](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="30cfc-119">For more information, see [Troubleshooting: Debugging Windows Services](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="30cfc-120">デバッグに有用な情報を取得するためには、Visual Studio デバッガーは、デバッグ対象のバイナリのシンボル ファイルを検索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30cfc-120">To get meaningful information for debugging, the Visual Studio debugger needs to find symbol files for the binaries that are being debugged.</span></span> <span data-ttu-id="30cfc-121">Visual Studio に組み込まれているサービスをデバッグしている場合は、シンボル ファイル (.pdb ファイル) は実行可能ファイルまたはライブラリと同じフォルダーにあり、デバッガーはそれらを自動的に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="30cfc-121">If you are debugging a service that you built in Visual Studio, the symbol files (.pdb files) are in the same folder as the executable or library, and the debugger loads them automatically.</span></span> <span data-ttu-id="30cfc-122">構築していないサービスをデバッグしている場合は、最初にサービスのシンボルを検索し、デバッガーでこれらを検出できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="30cfc-122">If you are debugging a service that you didn't build, you should first find symbols for the service and make sure they can be found by the debugger.</span></span> <span data-ttu-id="30cfc-123">[シンボル (.pdb) ファイルとソース ファイルの指定](http://msdn.microsoft.com/library/1105e169-5272-4e7c-b3e7-cda1b7798a6b)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="30cfc-123">See [Specify Symbol (.pdb) and Source Files](http://msdn.microsoft.com/library/1105e169-5272-4e7c-b3e7-cda1b7798a6b).</span></span> <span data-ttu-id="30cfc-124">システム プロセスをデバッグしているか、サービスにシステム呼び出しのシンボルを含めたい場合は、Microsoft シンボル サーバーを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30cfc-124">If you're debugging a system process or want to have symbols for system calls in your services, you should add the Microsoft Symbol Servers.</span></span> <span data-ttu-id="30cfc-125">[シンボルによるデバッグ](http://msdn.microsoft.com/windows/desktop/ee416588.aspx)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="30cfc-125">See [Debugging Symbols](http://msdn.microsoft.com/windows/desktop/ee416588.aspx).</span></span>  
  
### <a name="to-debug-a-service"></a><span data-ttu-id="30cfc-126">サービスをデバッグするには</span><span class="sxs-lookup"><span data-stu-id="30cfc-126">To debug a service</span></span>  
  
1.  <span data-ttu-id="30cfc-127">サービスをデバッグ構成で構築します。</span><span class="sxs-lookup"><span data-stu-id="30cfc-127">Build your service in the Debug configuration.</span></span>  
  
2.  <span data-ttu-id="30cfc-128">サービスをインストールします。</span><span class="sxs-lookup"><span data-stu-id="30cfc-128">Install your service.</span></span> <span data-ttu-id="30cfc-129">詳細については、「 [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30cfc-129">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
3.  <span data-ttu-id="30cfc-130">**サービス コントロール マネージャー**、**サーバー エクスプローラー**、またはコードで、サービスを起動します。</span><span class="sxs-lookup"><span data-stu-id="30cfc-130">Start your service, either from **Services Control Manager**, **Server Explorer**, or from code.</span></span> <span data-ttu-id="30cfc-131">詳しくは、「[方法: サービスを開始する](../../../docs/framework/windows-services/how-to-start-services.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="30cfc-131">For more information, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span>  
  
4.  <span data-ttu-id="30cfc-132">システム プロセスにアタッチすることができるように、管理者資格情報を使用して Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="30cfc-132">Start Visual Studio with administrative credentials so you can attach to system processes.</span></span>  
  
5.  <span data-ttu-id="30cfc-133">(省略可能) Visual Studio のメニュー バーで **[ツール]**、**[オプション]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="30cfc-133">(Optional) On the Visual Studio menu bar, choose **Tools**, **Options**.</span></span> <span data-ttu-id="30cfc-134">**[オプション]** ダイアログ ボックスで、**[デバッグ]**、**[シンボル]** の順に選択し、**[Microsoft シンボル サーバー]** チェック ボックスをオンにし、**[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="30cfc-134">In the **Options** dialog box, choose **Debugging**, **Symbols**, select the **Microsoft Symbol Servers** check box, and then choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="30cfc-135">メニュー バーの **[デバッグ]** または **[ツール]** メニューで、**[プロセスにアタッチ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="30cfc-135">On the menu bar, choose **Attach to Process** from the **Debug** or **Tools** menu.</span></span> <span data-ttu-id="30cfc-136">(キーボード: Ctrl + Alt + P)</span><span class="sxs-lookup"><span data-stu-id="30cfc-136">(Keyboard: Ctrl+Alt+P)</span></span>  
  
     <span data-ttu-id="30cfc-137">**[プロセス]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="30cfc-137">The **Processes** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="30cfc-138">**[全ユーザーのプロセスを表示する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="30cfc-138">Select the **Show processes from all users** check box.</span></span>  
  
8.  <span data-ttu-id="30cfc-139">**[選択可能なプロセス]** セクションでサービスのプロセスを選択し、**[アタッチ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="30cfc-139">In the **Available Processes** section, choose the process for your service, and then choose **Attach**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="30cfc-140">プロセスの名前は、サービスの実行可能ファイルの名前と同じになります。</span><span class="sxs-lookup"><span data-stu-id="30cfc-140">The process will have the same name as the executable file for your service.</span></span>  
  
     <span data-ttu-id="30cfc-141">**[プロセスにアタッチ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="30cfc-141">The **Attach to Process** dialog box appears.</span></span>  
  
9. <span data-ttu-id="30cfc-142">適切なオプションを選択し、**[OK]** を選択してダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="30cfc-142">Choose the appropriate options, and then choose **OK** to close the dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="30cfc-143">デバッグ モードになります。</span><span class="sxs-lookup"><span data-stu-id="30cfc-143">You are now in debug mode.</span></span>  
  
10. <span data-ttu-id="30cfc-144">コード内で使用する任意のブレークポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="30cfc-144">Set any breakpoints you want to use in your code.</span></span>  
  
11. <span data-ttu-id="30cfc-145">サービス コントロール マネージャーを起動し、停止、一時停止、再開の各コマンドを送信してサービスを操作して、ブレークポイントをヒットします。</span><span class="sxs-lookup"><span data-stu-id="30cfc-145">Access the Services Control Manager and manipulate your service, sending stop, pause, and continue commands to hit your breakpoints.</span></span> <span data-ttu-id="30cfc-146">サービス コントロール マネージャーの実行方法の詳細については、「[方法: サービスを開始する](../../../docs/framework/windows-services/how-to-start-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30cfc-146">For more information about running the Services Control Manager, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span> <span data-ttu-id="30cfc-147">さらに、「[Windows サービスをデバッグする場合](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30cfc-147">Also, see [Troubleshooting: Debugging Windows Services](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span></span>  
  
## <a name="debugging-tips-for-windows-services"></a><span data-ttu-id="30cfc-148">Windows サービスのデバッグのヒント</span><span class="sxs-lookup"><span data-stu-id="30cfc-148">Debugging Tips for Windows Services</span></span>  
 <span data-ttu-id="30cfc-149">サービスのプロセスにアタッチすると、そのサービスのコードのほとんど (すべてではない) をデバッグすることができます。</span><span class="sxs-lookup"><span data-stu-id="30cfc-149">Attaching to the service's process allows you to debug most, but not all, the code for that service.</span></span> <span data-ttu-id="30cfc-150">たとえば、サービスが既に開始されているため、そのサービスの <xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッド内のコード、またはサービスをこの方法で読み込むために使用されている `Main` メソッド内のコードは、デバッグすることができません。</span><span class="sxs-lookup"><span data-stu-id="30cfc-150">For example, because the service has already been started, you cannot debug the code in the service's <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method or the code in the `Main` method that is used to load the service this way.</span></span> <span data-ttu-id="30cfc-151">この制限に対処する方法の 1 つは、デバッグ専用の一時的な "ダミー" サービスを作成し、サービス アプリケーションに追加することです。</span><span class="sxs-lookup"><span data-stu-id="30cfc-151">One way to work around this limitation is to create a temporary second service in your service application that exists only to aid in debugging.</span></span> <span data-ttu-id="30cfc-152">サービスを両方ともインストールし、ダミー サービスを開始してサービス プロセスを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="30cfc-152">You can install both services, and then start this dummy service to load the service process.</span></span> <span data-ttu-id="30cfc-153">"ダミー" サービスがプロセスを起動した後は、Visual Studio の **[デバッグ]** メニューで、サービス プロセスへのアタッチを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="30cfc-153">Once the temporary service has started the process, you can use the **Debug** menu in Visual Studio to attach to the service process.</span></span>  
  
 <span data-ttu-id="30cfc-154"><xref:System.Threading.Thread.Sleep%2A> メソッドに呼び出しを追加して、プロセスにアタッチできるようになるまで動作を遅延します。</span><span class="sxs-lookup"><span data-stu-id="30cfc-154">Try adding calls to the <xref:System.Threading.Thread.Sleep%2A> method to delay action until you’re able to attach to the process.</span></span>  
  
 <span data-ttu-id="30cfc-155">プログラムを通常のコンソール アプリケーションに変更します。</span><span class="sxs-lookup"><span data-stu-id="30cfc-155">Try changing the program to a regular console application.</span></span> <span data-ttu-id="30cfc-156">このためには、起動方法に応じて Windows サービスとコンソール アプリケーションの両方として実行することができるように、`Main` メソッドを次のように書き換えます。</span><span class="sxs-lookup"><span data-stu-id="30cfc-156">To do this, rewrite the `Main` method as follows so it can run both as a Windows Service and as a console application, depending on how it's started.</span></span>  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a><span data-ttu-id="30cfc-157">方法: Windows サービスをコンソール アプリケーションとして実行する</span><span class="sxs-lookup"><span data-stu-id="30cfc-157">How to: Run a Windows Service as a console application</span></span>  
  
1.  <span data-ttu-id="30cfc-158"><xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドと <xref:System.ServiceProcess.ServiceBase.OnStop%2A> メソッドを実行するサービスにメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="30cfc-158">Add a method to your service that runs the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods:</span></span>  
  
    ```  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2.  <span data-ttu-id="30cfc-159">`Main` メソッドを次のように書き換えます。</span><span class="sxs-lookup"><span data-stu-id="30cfc-159">Rewrite the `Main` method as follows:</span></span>  
  
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
  
3.  <span data-ttu-id="30cfc-160">プロジェクトのプロパティの **[アプリケーション]** タブで、**[出力の種類]** を **[コンソール アプリケーション]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="30cfc-160">In the **Application** tab of the project's properties, set the **Output type** to **Console Application**.</span></span>  
  
4.  <span data-ttu-id="30cfc-161">**[デバッグの開始]** を選択します (F5)。</span><span class="sxs-lookup"><span data-stu-id="30cfc-161">Choose **Start Debugging** (F5).</span></span>  
  
5.  <span data-ttu-id="30cfc-162">プログラムを再度 Windows サービスとして実行するには、プログラムをインストールして、Windows サービスとして通常どおり起動します。</span><span class="sxs-lookup"><span data-stu-id="30cfc-162">To run the program as a Windows Service again, install it and start it as usual for a Windows Service.</span></span> <span data-ttu-id="30cfc-163">これらの変更を反対にする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="30cfc-163">It's not necessary to reverse these changes.</span></span>  
  
 <span data-ttu-id="30cfc-164">システムの起動時にのみ発生する問題をデバッグするときなどのいくつかのケースでは、Windows デバッガーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30cfc-164">In some cases, such as when you want to debug an issue that occurs only on system startup, you have to use the Windows debugger.</span></span> <span data-ttu-id="30cfc-165">[Windows 用デバッグ ツール](http://msdn.microsoft.com/windows/hardware/hh852365)をインストールし、「[Windows サービスをデバッグする方法](http://support.microsoft.com/kb/824344)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="30cfc-165">Install [Debugging Tools for Windows](http://msdn.microsoft.com/windows/hardware/hh852365) and see [How to debug Windows Services](http://support.microsoft.com/kb/824344).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30cfc-166">参照</span><span class="sxs-lookup"><span data-stu-id="30cfc-166">See Also</span></span>  
 [<span data-ttu-id="30cfc-167">Windows サービス アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="30cfc-167">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="30cfc-168">方法 : サービスをインストールおよびアンインストールする</span><span class="sxs-lookup"><span data-stu-id="30cfc-168">How to: Install and Uninstall Services</span></span>](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [<span data-ttu-id="30cfc-169">方法 : サービスを開始する</span><span class="sxs-lookup"><span data-stu-id="30cfc-169">How to: Start Services</span></span>](../../../docs/framework/windows-services/how-to-start-services.md)  
 [<span data-ttu-id="30cfc-170">サービスのデバッグ</span><span class="sxs-lookup"><span data-stu-id="30cfc-170">Debugging a Service</span></span>](http://msdn.microsoft.com/library/windows/desktop/ms682546.aspx)

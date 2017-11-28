---
title: "方法 : Windows サービスを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
caps.latest.revision: "18"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: c4d7f2f19c8d156f86513ac7138bccd59ae3b7fb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-windows-services"></a><span data-ttu-id="a7220-102">方法 : Windows サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="a7220-102">How to: Create Windows Services</span></span>
<span data-ttu-id="a7220-103">サービスを作成するときに、という名前の Visual Studio プロジェクト テンプレートを使用することができます**Windows サービス**です。</span><span class="sxs-lookup"><span data-stu-id="a7220-103">When you create a service, you can use a Visual Studio project template called **Windows Service**.</span></span> <span data-ttu-id="a7220-104">このテンプレートを使用すると、作業の多くを自動化できます。この自動化は、適切なクラスと名前空間を参照し、サービスの基底クラスからの継承を設定し、メソッドのいくつかをオーバーライドすることで実現されます。</span><span class="sxs-lookup"><span data-stu-id="a7220-104">This template automatically does much of the work for you by referencing the appropriate classes and namespaces, setting up the inheritance from the base class for services, and overriding several of the methods you're likely to want to override.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="a7220-105">Windows サービスのプロジェクト テンプレートは、Visual Studio の Express Edition では使用できません。</span><span class="sxs-lookup"><span data-stu-id="a7220-105">The Windows Services project template is not available in the Express edition of Visual Studio.</span></span>  
  
 <span data-ttu-id="a7220-106">実用的なサービスを作成するには、少なくとも以下の作業を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7220-106">At a minimum, to create a functional service you must:</span></span>  
  
-   <span data-ttu-id="a7220-107"><xref:System.ServiceProcess.ServiceBase.ServiceName%2A> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="a7220-107">Set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property.</span></span>  
  
-   <span data-ttu-id="a7220-108">サービス アプリケーションに必要なインストーラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="a7220-108">Create the necessary installers for your service application.</span></span>  
  
-   <span data-ttu-id="a7220-109"><xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドと <xref:System.ServiceProcess.ServiceBase.OnStop%2A> メソッドのオーバーライドとコーディングを行い、サービスの動作をカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="a7220-109">Override and specify code for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods to customize the ways in which your service behaves.</span></span>  
  
### <a name="to-create-a-windows-service-application"></a><span data-ttu-id="a7220-110">Windows サービス アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="a7220-110">To create a Windows Service application</span></span>  
  
1.  <span data-ttu-id="a7220-111">作成、 **Windows サービス**プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="a7220-111">Create a **Windows Service** project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a7220-112">テンプレートを使用せずにサービスを記述する方法については、次を参照してください。[する方法: プログラムによってサービスを書き込む](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)です。</span><span class="sxs-lookup"><span data-stu-id="a7220-112">For instructions on writing a service without using the template, see [How to: Write Services Programmatically](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).</span></span>  
  
2.  <span data-ttu-id="a7220-113">**プロパティ**ウィンドウで、設定、<xref:System.ServiceProcess.ServiceBase.ServiceName%2A>サービスのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="a7220-113">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for your service.</span></span>  
  
     <span data-ttu-id="a7220-114">![ServiceName プロパティを設定します。] (../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span><span class="sxs-lookup"><span data-stu-id="a7220-114">![Set the ServiceName property.](../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a7220-115"><xref:System.ServiceProcess.ServiceBase.ServiceName%2A> プロパティの値は、各インストーラー クラスに記録されている名前と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7220-115">The value of the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property must always match the name recorded in the installer classes.</span></span> <span data-ttu-id="a7220-116">このプロパティを変更した場合は、インストーラー クラスの <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> プロパティも変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7220-116">If you change this property, you must update the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property of installer classes as well.</span></span>  
  
3.  <span data-ttu-id="a7220-117">次のいずれかのプロパティを設定して、サービスの動作を決定します。</span><span class="sxs-lookup"><span data-stu-id="a7220-117">Set any of the following properties to determine how your service will function.</span></span>  
  
    |<span data-ttu-id="a7220-118">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a7220-118">Property</span></span>|<span data-ttu-id="a7220-119">設定</span><span class="sxs-lookup"><span data-stu-id="a7220-119">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|<span data-ttu-id="a7220-120">サービスが実行停止要求を受け付ける場合は `True` を設定します。サービスの実行を停止しない場合は `false` を設定します。</span><span class="sxs-lookup"><span data-stu-id="a7220-120">`True` to indicate that the service will accept requests to stop running; `false` to prevent the service from being stopped.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|<span data-ttu-id="a7220-121">サービスがコンピューターのシャットダウン時に通知を受けて `True` プロシージャを呼び出す場合は、<xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> を設定します。</span><span class="sxs-lookup"><span data-stu-id="a7220-121">`True` to indicate that the service wants to receive notification when the computer on which it lives shuts down, enabling it to call the <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedure.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|<span data-ttu-id="a7220-122">サービスが一時停止要求または再開要求を受け付ける場合は `True` を設定します。サービスを一時停止または再開しない場合は `false` を設定します。</span><span class="sxs-lookup"><span data-stu-id="a7220-122">`True` to indicate that the service will accept requests to pause or to resume running; `false` to prevent the service from being paused and resumed.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|<span data-ttu-id="a7220-123">`True`サービスがコンピューターの電源状態の変更の通知を処理できることを示すために`false`をサービスがしてこれらの変更通知を送信するを防ぐためにします。</span><span class="sxs-lookup"><span data-stu-id="a7220-123">`True` to indicate that the service can handle notification of changes to the computer's power status; `false` to prevent the service from being notified of these changes.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|<span data-ttu-id="a7220-124">サービスがアクションを実行したときにアプリケーション イベント ログに情報を入力する場合は `True` を設定します。この機能を無効にする場合は `false` を設定します。</span><span class="sxs-lookup"><span data-stu-id="a7220-124">`True` to write informational entries to the Application event log when your service performs an action; `false` to disable this functionality.</span></span> <span data-ttu-id="a7220-125">詳細については、次を参照してください。[する方法: サービスに関する情報のログ](../../../docs/framework/windows-services/how-to-log-information-about-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="a7220-125">For more information, see [How to: Log Information About Services](../../../docs/framework/windows-services/how-to-log-information-about-services.md).</span></span> <span data-ttu-id="a7220-126">**注:**既定では、<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>に設定されている`true`です。</span><span class="sxs-lookup"><span data-stu-id="a7220-126">**Note:**  By default, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> is set to `true`.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="a7220-127">ときに<xref:System.ServiceProcess.ServiceBase.CanStop%2A>または<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>に設定されている`false`、**サービス コントロール マネージャー**停止、一時停止、またはサービスを続行する、対応するメニュー オプションが無効になります。</span><span class="sxs-lookup"><span data-stu-id="a7220-127">When <xref:System.ServiceProcess.ServiceBase.CanStop%2A> or <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> are set to `false`, the **Service Control Manager** will disable the corresponding menu options to stop, pause, or continue the service.</span></span>  
  
4.  <span data-ttu-id="a7220-128">コード エディターを起動し、<xref:System.ServiceProcess.ServiceBase.OnStart%2A> プロシージャと <xref:System.ServiceProcess.ServiceBase.OnStop%2A> プロシージャの処理を記述します。</span><span class="sxs-lookup"><span data-stu-id="a7220-128">Access the Code Editor and fill in the processing you want for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures.</span></span>  
  
5.  <span data-ttu-id="a7220-129">ほかに動作を定義するメソッドがある場合は、それをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="a7220-129">Override any other methods for which you want to define functionality.</span></span>  
  
6.  <span data-ttu-id="a7220-130">サービス アプリケーションの必要なインストーラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="a7220-130">Add the necessary installers for your service application.</span></span> <span data-ttu-id="a7220-131">詳細については、次を参照してください。[する方法: サービス アプリケーションへのインストーラーの追加](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)です。</span><span class="sxs-lookup"><span data-stu-id="a7220-131">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
7.  <span data-ttu-id="a7220-132">選択して、プロジェクトをビルド**ソリューションのビルド**から、**ビルド**メニュー。</span><span class="sxs-lookup"><span data-stu-id="a7220-132">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a7220-133">F5 キーを押してプロジェクトを実行しないでください。この方法ではサービス プロジェクトを実行できません。</span><span class="sxs-lookup"><span data-stu-id="a7220-133">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
8.  <span data-ttu-id="a7220-134">サービスをインストールします。</span><span class="sxs-lookup"><span data-stu-id="a7220-134">Install the service.</span></span> <span data-ttu-id="a7220-135">詳細については、「 [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7220-135">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7220-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7220-136">See Also</span></span>  
 [<span data-ttu-id="a7220-137">Windows サービス アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="a7220-137">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="a7220-138">方法: プログラムによってサービスを作成</span><span class="sxs-lookup"><span data-stu-id="a7220-138">How to: Write Services Programmatically</span></span>](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)  
 [<span data-ttu-id="a7220-139">方法: サービス アプリケーションへのインストーラーの追加</span><span class="sxs-lookup"><span data-stu-id="a7220-139">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="a7220-140">方法: サービスに関する情報を記録</span><span class="sxs-lookup"><span data-stu-id="a7220-140">How to: Log Information About Services</span></span>](../../../docs/framework/windows-services/how-to-log-information-about-services.md)  
 [<span data-ttu-id="a7220-141">方法: サービスを開始します。</span><span class="sxs-lookup"><span data-stu-id="a7220-141">How to: Start Services</span></span>](../../../docs/framework/windows-services/how-to-start-services.md)  
 [<span data-ttu-id="a7220-142">方法: サービスのセキュリティ コンテキストを指定</span><span class="sxs-lookup"><span data-stu-id="a7220-142">How to: Specify the Security Context for Services</span></span>](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)  
 [<span data-ttu-id="a7220-143">方法: インストールし、サービスのアンインストール</span><span class="sxs-lookup"><span data-stu-id="a7220-143">How to: Install and Uninstall Services</span></span>](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [<span data-ttu-id="a7220-144">チュートリアル: コンポーネント デザイナーでの Windows サービス アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="a7220-144">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

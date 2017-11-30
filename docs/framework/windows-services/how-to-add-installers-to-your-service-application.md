---
title: "方法 : サービス アプリケーションにインストーラーを追加する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, deploying
- installation components, adding to services
- installers, adding to services
- Windows Service applications, adding installers
- services, adding installers
- ServiceInstaller class, adding installers to services
- ServiceProcessInstaller class, adding installers to services
ms.assetid: 8b698e9a-b88e-4f44-ae45-e0c5ea0ae5a8
caps.latest.revision: "14"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: 8137e41f92335849916dfc9e9ce72afeb186e73c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-installers-to-your-service-application"></a><span data-ttu-id="7451d-102">方法 : サービス アプリケーションにインストーラーを追加する</span><span class="sxs-lookup"><span data-stu-id="7451d-102">How to: Add Installers to Your Service Application</span></span>
<span data-ttu-id="7451d-103">Visual Studio では、サービス アプリケーションに関連付けられているリソースをインストールするインストール コンポーネントが同梱されています。</span><span class="sxs-lookup"><span data-stu-id="7451d-103">Visual Studio ships installation components that can install resources associated with your service applications.</span></span> <span data-ttu-id="7451d-104">インストール コンポーネントにインストールされていると、サービス コントロール マネージャー知らせます、サービスが存在するシステム上の個々 のサービスを登録します。</span><span class="sxs-lookup"><span data-stu-id="7451d-104">Installation components register an individual service on the system to which it is being installed and let the Services Control Manager know that the service exists.</span></span> <span data-ttu-id="7451d-105">サービス アプリケーションを操作するときに自動的に適切なインストーラーをプロジェクトに追加する [プロパティ] ウィンドウでリンクを選択することができます。</span><span class="sxs-lookup"><span data-stu-id="7451d-105">When you work with a service application, you can select a link in the Properties window to automatically add the appropriate installers to your project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7451d-106">サービスのプロパティの値は、インストーラー クラスに、サービス クラスからコピーされます。</span><span class="sxs-lookup"><span data-stu-id="7451d-106">Property values for your service are copied from the service class to the installer class.</span></span> <span data-ttu-id="7451d-107">サービス クラスのプロパティの値を更新する場合は自動的に更新されません installer で。</span><span class="sxs-lookup"><span data-stu-id="7451d-107">If you update the property values on the service class, they are not automatically updated in the installer.</span></span>  
  
 <span data-ttu-id="7451d-108">インストーラーをプロジェクトに新しいクラスに追加するとき (これは、既定では、名前は`ProjectInstaller`) プロジェクト、およびコンポーネントが内に作成した適切なインストールのインスタンスで作成されました。</span><span class="sxs-lookup"><span data-stu-id="7451d-108">When you add an installer to your project, a new class (which, by default, is named `ProjectInstaller`) is created in the project, and instances of the appropriate installation components are created within it.</span></span> <span data-ttu-id="7451d-109">このクラスは、すべてのインストール コンポーネントの中心点として機能しています。 プロジェクトの必要があります。</span><span class="sxs-lookup"><span data-stu-id="7451d-109">This class acts as a central point for all of the installation components your project needs.</span></span> <span data-ttu-id="7451d-110">など、2 番目のサービスをアプリケーションに追加するインストーラーの追加 をクリックすると、2 番目のインストーラー クラスは作成されません。代わりに、2 番目のサービスのために必要な追加のインストール コンポーネントは、既存のクラスに追加されます。</span><span class="sxs-lookup"><span data-stu-id="7451d-110">For example, if you add a second service to your application and click the Add Installer link, a second installer class is not created; instead, the necessary additional installation component for the second service is added to the existing class.</span></span>  
  
 <span data-ttu-id="7451d-111">サービスを正しくインストールするインストーラー内に特殊なコーディングを行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7451d-111">You do not need to do any special coding within the installers to make your services install correctly.</span></span> <span data-ttu-id="7451d-112">ただし、インストール プロセスに特別な機能を追加する必要がある場合、インストーラーの内容を変更する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="7451d-112">However, you may occasionally need to modify the contents of the installers if you need to add special functionality to the installation process.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7451d-113">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7451d-113">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7451d-114">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7451d-114">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7451d-115">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7451d-115">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-installers-to-your-service-application"></a><span data-ttu-id="7451d-116">サービス アプリケーションにインストーラーを追加するには</span><span class="sxs-lookup"><span data-stu-id="7451d-116">To add installers to your service application</span></span>  
  
1.  <span data-ttu-id="7451d-117">**ソリューション エクスプ ローラー**、アクセス**デザイン**インストール コンポーネントを追加するサービスを表示します。</span><span class="sxs-lookup"><span data-stu-id="7451d-117">In **Solution Explorer**, access **Design** view for the service for which you want to add an installation component.</span></span>  
  
2.  <span data-ttu-id="7451d-118">なく、それ自体の内容は、サービスを選択するデザイナーの背景をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7451d-118">Click the background of the designer to select the service itself, rather than any of its contents.</span></span>  
  
3.  <span data-ttu-id="7451d-119">デザイナーにフォーカスを右クリックし、クリック**インストーラーの追加**です。</span><span class="sxs-lookup"><span data-stu-id="7451d-119">With the designer in focus, right-click, and then click **Add Installer**.</span></span>  
  
     <span data-ttu-id="7451d-120">新しいクラスを`ProjectInstaller`、および 2 つのインストール コンポーネント<xref:System.ServiceProcess.ServiceProcessInstaller>と<xref:System.ServiceProcess.ServiceInstaller>サービスが、コンポーネントにコピーされるは、プロジェクト、およびプロパティの値に追加します。</span><span class="sxs-lookup"><span data-stu-id="7451d-120">A new class, `ProjectInstaller`, and two installation components, <xref:System.ServiceProcess.ServiceProcessInstaller> and <xref:System.ServiceProcess.ServiceInstaller>, are added to your project, and property values for the service are copied to the components.</span></span>  
  
4.  <span data-ttu-id="7451d-121">クリックして、<xref:System.ServiceProcess.ServiceInstaller>コンポーネントことを確認の値、<xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A>プロパティが同じ値に設定、<xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A>サービス自体のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="7451d-121">Click the <xref:System.ServiceProcess.ServiceInstaller> component and verify that the value of the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to the same value as the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property on the service itself.</span></span>  
  
5.  <span data-ttu-id="7451d-122">調べるには、サービスの開始方法をクリックして、<xref:System.ServiceProcess.ServiceInstaller>コンポーネントで、設定、<xref:System.ServiceProcess.ServiceInstaller.StartType%2A>プロパティを適切な値にします。</span><span class="sxs-lookup"><span data-stu-id="7451d-122">To determine how your service will be started, click the <xref:System.ServiceProcess.ServiceInstaller> component and set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to the appropriate value.</span></span>  
  
    |<span data-ttu-id="7451d-123">値</span><span class="sxs-lookup"><span data-stu-id="7451d-123">Value</span></span>|<span data-ttu-id="7451d-124">結果</span><span class="sxs-lookup"><span data-stu-id="7451d-124">Result</span></span>|  
    |-----------|------------|  
    |<xref:System.ServiceProcess.ServiceStartMode.Manual>|<span data-ttu-id="7451d-125">サービスは、インストール後に手動で開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7451d-125">The service must be manually started after installation.</span></span> <span data-ttu-id="7451d-126">詳細については、次を参照してください。[する方法: サービスを開始](../../../docs/framework/windows-services/how-to-start-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="7451d-126">For more information, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span>|  
    |<xref:System.ServiceProcess.ServiceStartMode.Automatic>|<span data-ttu-id="7451d-127">サービスは、コンピューターが再起動されるたびに、それ自体で起動されます。</span><span class="sxs-lookup"><span data-stu-id="7451d-127">The service will start by itself whenever the computer reboots.</span></span>|  
    |<xref:System.ServiceProcess.ServiceStartMode.Disabled>|<span data-ttu-id="7451d-128">サービスを開始することはできません。</span><span class="sxs-lookup"><span data-stu-id="7451d-128">The service cannot be started.</span></span>|  
  
6.  <span data-ttu-id="7451d-129">サービスを実行するセキュリティ コンテキストを決定するには、をクリックして、<xref:System.ServiceProcess.ServiceProcessInstaller>コンポーネントし、適切なプロパティの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="7451d-129">To determine the security context in which your service will run, click the <xref:System.ServiceProcess.ServiceProcessInstaller> component and set the appropriate property values.</span></span> <span data-ttu-id="7451d-130">詳細については、次を参照してください。[する方法: サービスのセキュリティ コンテキストを指定](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="7451d-130">For more information, see [How to: Specify the Security Context for Services](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md).</span></span>  
  
7.  <span data-ttu-id="7451d-131">対象のカスタム処理を実行する必要があります。 すべてのメソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="7451d-131">Override any methods for which you need to perform custom processing.</span></span>  
  
8.  <span data-ttu-id="7451d-132">プロジェクトのサービスごとに手順 1. ~ 7. を実行します。</span><span class="sxs-lookup"><span data-stu-id="7451d-132">Perform steps 1 through 7 for each additional service in your project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7451d-133">プロジェクト内の追加サービスごとに追加する必要があります<xref:System.ServiceProcess.ServiceInstaller>コンポーネントをプロジェクトの`ProjectInstaller`クラスです。</span><span class="sxs-lookup"><span data-stu-id="7451d-133">For each additional service in your project, you must add an additional <xref:System.ServiceProcess.ServiceInstaller> component to the project's `ProjectInstaller` class.</span></span> <span data-ttu-id="7451d-134"><xref:System.ServiceProcess.ServiceProcessInstaller>手順 3 で追加したコンポーネントがすべて、プロジェクト内の個々 のサービスのインストーラーの動作です。</span><span class="sxs-lookup"><span data-stu-id="7451d-134">The <xref:System.ServiceProcess.ServiceProcessInstaller> component added in step three works with all of the individual service installers in the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7451d-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="7451d-135">See Also</span></span>  
 [<span data-ttu-id="7451d-136">Windows サービス アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="7451d-136">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="7451d-137">方法: インストールし、サービスのアンインストール</span><span class="sxs-lookup"><span data-stu-id="7451d-137">How to: Install and Uninstall Services</span></span>](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [<span data-ttu-id="7451d-138">方法: サービスを開始します。</span><span class="sxs-lookup"><span data-stu-id="7451d-138">How to: Start Services</span></span>](../../../docs/framework/windows-services/how-to-start-services.md)  
 [<span data-ttu-id="7451d-139">方法: サービスのセキュリティ コンテキストを指定</span><span class="sxs-lookup"><span data-stu-id="7451d-139">How to: Specify the Security Context for Services</span></span>](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)

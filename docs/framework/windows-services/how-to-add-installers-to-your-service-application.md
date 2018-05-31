---
title: '方法 : サービス アプリケーションにインストーラーを追加する'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, deploying
- installation components, adding to services
- installers, adding to services
- Windows Service applications, adding installers
- services, adding installers
- ServiceInstaller class, adding installers to services
- ServiceProcessInstaller class, adding installers to services
ms.assetid: 8b698e9a-b88e-4f44-ae45-e0c5ea0ae5a8
author: ghogen
manager: douge
ms.openlocfilehash: faece1d7ee752e4c17f39027ff8a97fc95ed451b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514361"
---
# <a name="how-to-add-installers-to-your-service-application"></a><span data-ttu-id="caee8-102">方法 : サービス アプリケーションにインストーラーを追加する</span><span class="sxs-lookup"><span data-stu-id="caee8-102">How to: Add Installers to Your Service Application</span></span>
<span data-ttu-id="caee8-103">Visual Studio には、サービス アプリケーションに関連付けられているリソースをインストールできるインストール コンポーネントが付属しています。</span><span class="sxs-lookup"><span data-stu-id="caee8-103">Visual Studio ships installation components that can install resources associated with your service applications.</span></span> <span data-ttu-id="caee8-104">インストール コンポーネントは、個々のサービスをインストール先のシステムに登録し、サービス コントロール マネージャーにサービスが存在することを認識させます。</span><span class="sxs-lookup"><span data-stu-id="caee8-104">Installation components register an individual service on the system to which it is being installed and let the Services Control Manager know that the service exists.</span></span> <span data-ttu-id="caee8-105">サービス アプリケーションを操作するときは、[プロパティ] ウィンドウでリンクを選択して、適切なインストーラーをプロジェクトに自動的に追加することができます。</span><span class="sxs-lookup"><span data-stu-id="caee8-105">When you work with a service application, you can select a link in the Properties window to automatically add the appropriate installers to your project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="caee8-106">サービスに対するプロパティの値は、サービス クラスからインストーラー クラスにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="caee8-106">Property values for your service are copied from the service class to the installer class.</span></span> <span data-ttu-id="caee8-107">サービス クラスでプロパティの値を更新した場合、インストーラーでは自動的には更新されません。</span><span class="sxs-lookup"><span data-stu-id="caee8-107">If you update the property values on the service class, they are not automatically updated in the installer.</span></span>  
  
 <span data-ttu-id="caee8-108">インストーラーをプロジェクトに追加すると、新しいクラス (既定の名前は `ProjectInstaller`) がプロジェクトに作成され、その中に適切なインストール コンポーネントのインスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="caee8-108">When you add an installer to your project, a new class (which, by default, is named `ProjectInstaller`) is created in the project, and instances of the appropriate installation components are created within it.</span></span> <span data-ttu-id="caee8-109">このクラスは、プロジェクトで必要なすべてのインストール コンポーネントの中心的な場所として機能します。</span><span class="sxs-lookup"><span data-stu-id="caee8-109">This class acts as a central point for all of the installation components your project needs.</span></span> <span data-ttu-id="caee8-110">たとえば、2 番目のサービスをアプリケーションに追加し、[インストーラーの追加] リンクをクリックしても、2 番目のインストーラー クラスは作成されません。代わりに、2 番目のサービスに必要な追加のインストール コンポーネントは、既存のクラスに追加されます。</span><span class="sxs-lookup"><span data-stu-id="caee8-110">For example, if you add a second service to your application and click the Add Installer link, a second installer class is not created; instead, the necessary additional installation component for the second service is added to the existing class.</span></span>  
  
 <span data-ttu-id="caee8-111">サービスが正しくインストールされるようにするために、インストーラー内で特殊なコーディングを行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="caee8-111">You do not need to do any special coding within the installers to make your services install correctly.</span></span> <span data-ttu-id="caee8-112">ただし、インストール プロセスに特別な機能を追加する必要がある場合は、インストーラーの内容の変更が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="caee8-112">However, you may occasionally need to modify the contents of the installers if you need to add special functionality to the installation process.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="caee8-113">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="caee8-113">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="caee8-114">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="caee8-114">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="caee8-115">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="caee8-115">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-installers-to-your-service-application"></a><span data-ttu-id="caee8-116">サービス アプリケーションにインストーラーを追加するには</span><span class="sxs-lookup"><span data-stu-id="caee8-116">To add installers to your service application</span></span>  
  
1.  <span data-ttu-id="caee8-117">**ソリューション エクスプローラー**で、インストール コンポーネントを追加するサービスの **[デザイン]** ビューにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="caee8-117">In **Solution Explorer**, access **Design** view for the service for which you want to add an installation component.</span></span>  
  
2.  <span data-ttu-id="caee8-118">デザイナーの背景をクリックして、サービスの内容ではなくサービス自体を選択します。</span><span class="sxs-lookup"><span data-stu-id="caee8-118">Click the background of the designer to select the service itself, rather than any of its contents.</span></span>  
  
3.  <span data-ttu-id="caee8-119">デザイナーにフォーカスを置いた状態で右クリックし、**[インストーラーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="caee8-119">With the designer in focus, right-click, and then click **Add Installer**.</span></span>  
  
     <span data-ttu-id="caee8-120">新しいクラス `ProjectInstaller`、および 2 つのインストール コンポーネント <xref:System.ServiceProcess.ServiceProcessInstaller> と <xref:System.ServiceProcess.ServiceInstaller> がプロジェクトに追加され、サービスのプロパティ値がコンポーネントにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="caee8-120">A new class, `ProjectInstaller`, and two installation components, <xref:System.ServiceProcess.ServiceProcessInstaller> and <xref:System.ServiceProcess.ServiceInstaller>, are added to your project, and property values for the service are copied to the components.</span></span>  
  
4.  <span data-ttu-id="caee8-121"><xref:System.ServiceProcess.ServiceInstaller> コンポーネントをクリックし、<xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> プロパティが、サービス自体の <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> プロパティと同じ値に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="caee8-121">Click the <xref:System.ServiceProcess.ServiceInstaller> component and verify that the value of the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to the same value as the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property on the service itself.</span></span>  
  
5.  <span data-ttu-id="caee8-122">サービスの開始方法を決定するには、<xref:System.ServiceProcess.ServiceInstaller> コンポーネントをクリックし、<xref:System.ServiceProcess.ServiceInstaller.StartType%2A> プロパティを適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="caee8-122">To determine how your service will be started, click the <xref:System.ServiceProcess.ServiceInstaller> component and set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to the appropriate value.</span></span>  
  
    |<span data-ttu-id="caee8-123">[値]</span><span class="sxs-lookup"><span data-stu-id="caee8-123">Value</span></span>|<span data-ttu-id="caee8-124">結果</span><span class="sxs-lookup"><span data-stu-id="caee8-124">Result</span></span>|  
    |-----------|------------|  
    |<xref:System.ServiceProcess.ServiceStartMode.Manual>|<span data-ttu-id="caee8-125">インストールの後、サービスを手動で開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="caee8-125">The service must be manually started after installation.</span></span> <span data-ttu-id="caee8-126">詳しくは、「[方法: サービスを開始する](../../../docs/framework/windows-services/how-to-start-services.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="caee8-126">For more information, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span>|  
    |<xref:System.ServiceProcess.ServiceStartMode.Automatic>|<span data-ttu-id="caee8-127">サービスは、コンピューターが再起動されるたびに、自動的に開始します。</span><span class="sxs-lookup"><span data-stu-id="caee8-127">The service will start by itself whenever the computer reboots.</span></span>|  
    |<xref:System.ServiceProcess.ServiceStartMode.Disabled>|<span data-ttu-id="caee8-128">サービスは開始できません。</span><span class="sxs-lookup"><span data-stu-id="caee8-128">The service cannot be started.</span></span>|  
  
6.  <span data-ttu-id="caee8-129">サービスが実行するセキュリティ コンテキストを決定するには、<xref:System.ServiceProcess.ServiceProcessInstaller> コンポーネントをクリックし、適切なプロパティ値を設定します。</span><span class="sxs-lookup"><span data-stu-id="caee8-129">To determine the security context in which your service will run, click the <xref:System.ServiceProcess.ServiceProcessInstaller> component and set the appropriate property values.</span></span> <span data-ttu-id="caee8-130">詳しくは、「[方法: サービスのセキュリティ コンテキストを指定する](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="caee8-130">For more information, see [How to: Specify the Security Context for Services](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md).</span></span>  
  
7.  <span data-ttu-id="caee8-131">カスタム処理を実行する必要があるメソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="caee8-131">Override any methods for which you need to perform custom processing.</span></span>  
  
8.  <span data-ttu-id="caee8-132">プロジェクトの追加サービスごとに、手順 1 から 7 を実行します。</span><span class="sxs-lookup"><span data-stu-id="caee8-132">Perform steps 1 through 7 for each additional service in your project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="caee8-133">プロジェクトの追加サービスごとに、新しい <xref:System.ServiceProcess.ServiceInstaller> コンポーネントをプロジェクトの `ProjectInstaller` クラスに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="caee8-133">For each additional service in your project, you must add an additional <xref:System.ServiceProcess.ServiceInstaller> component to the project's `ProjectInstaller` class.</span></span> <span data-ttu-id="caee8-134">手順 3 で追加した <xref:System.ServiceProcess.ServiceProcessInstaller> コンポーネントは、プロジェクト内のすべての個別サービス インストーラーで動作します。</span><span class="sxs-lookup"><span data-stu-id="caee8-134">The <xref:System.ServiceProcess.ServiceProcessInstaller> component added in step three works with all of the individual service installers in the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caee8-135">参照</span><span class="sxs-lookup"><span data-stu-id="caee8-135">See Also</span></span>  
 [<span data-ttu-id="caee8-136">Windows サービス アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="caee8-136">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="caee8-137">方法 : サービスをインストールおよびアンインストールする</span><span class="sxs-lookup"><span data-stu-id="caee8-137">How to: Install and Uninstall Services</span></span>](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [<span data-ttu-id="caee8-138">方法 : サービスを開始する</span><span class="sxs-lookup"><span data-stu-id="caee8-138">How to: Start Services</span></span>](../../../docs/framework/windows-services/how-to-start-services.md)  
 [<span data-ttu-id="caee8-139">方法 : サービスのセキュリティ コンテキストを指定する</span><span class="sxs-lookup"><span data-stu-id="caee8-139">How to: Specify the Security Context for Services</span></span>](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)

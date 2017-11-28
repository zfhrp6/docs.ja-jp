---
title: "方法 : プログラムでサービスを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
caps.latest.revision: "21"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: 1721417b8d1fc799e6af5d09762ee852d9fbfb03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-services-programmatically"></a><span data-ttu-id="4076d-102">方法 : プログラムでサービスを作成する</span><span class="sxs-lookup"><span data-stu-id="4076d-102">How to: Write Services Programmatically</span></span>
<span data-ttu-id="4076d-103">Windows サービス プロジェクトのテンプレートを使用しない場合は、継承などの基本要素を設定して独自のサービスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="4076d-103">If you choose not to use the Windows Service project template, you can write your own services by setting up the inheritance and other infrastructure elements yourself.</span></span> <span data-ttu-id="4076d-104">プログラミングによってサービスを作成する場合は、テンプレートでは自動化される手順を手動で行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="4076d-104">When you create a service programmatically, you must perform several steps that the template would otherwise handle for you:</span></span>  
  
-   <span data-ttu-id="4076d-105">サービス クラスが <xref:System.ServiceProcess.ServiceBase> クラスから継承されるように設定します。</span><span class="sxs-lookup"><span data-stu-id="4076d-105">You must set up your service class to inherit from the <xref:System.ServiceProcess.ServiceBase> class.</span></span>  
  
-   <span data-ttu-id="4076d-106">サービス プロジェクトの `Main` メソッドを作成します。このメソッドは、実行するサービスを定義し、それに対して <xref:System.ServiceProcess.ServiceBase.Run%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4076d-106">You must create a `Main` method for your service project that defines the services to run and calls the <xref:System.ServiceProcess.ServiceBase.Run%2A> method on them.</span></span>  
  
-   <span data-ttu-id="4076d-107"><xref:System.ServiceProcess.ServiceBase.OnStart%2A> プロシージャと <xref:System.ServiceProcess.ServiceBase.OnStop%2A> プロシージャをオーバーライドし、任意の処理内容を記述します。</span><span class="sxs-lookup"><span data-stu-id="4076d-107">You must override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures and fill in any code you want them to run.</span></span>  
  
### <a name="to-write-a-service-programmatically"></a><span data-ttu-id="4076d-108">プログラミングによってサービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="4076d-108">To write a service programmatically</span></span>  
  
1.  <span data-ttu-id="4076d-109">空のプロジェクトを作成し、必要な名前空間への参照を作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="4076d-109">Create an empty project and create a reference to the necessary namespaces by following these steps:</span></span>  
  
    1.  <span data-ttu-id="4076d-110">**ソリューション エクスプ ローラー**を右クリックし、**参照**ノードとクリック**参照の追加**です。</span><span class="sxs-lookup"><span data-stu-id="4076d-110">In **Solution Explorer**, right-click the **References** node and click **Add Reference**.</span></span>  
  
    2.  <span data-ttu-id="4076d-111">**.NET Framework**  タブで、スクロールして**System.dll**  をクリック**選択**です。</span><span class="sxs-lookup"><span data-stu-id="4076d-111">On the **.NET Framework** tab, scroll to **System.dll** and click **Select**.</span></span>  
  
    3.  <span data-ttu-id="4076d-112">スクロール**System.ServiceProcess.dll**  をクリック**選択**です。</span><span class="sxs-lookup"><span data-stu-id="4076d-112">Scroll to **System.ServiceProcess.dll** and click **Select**.</span></span>  
  
    4.  <span data-ttu-id="4076d-113">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4076d-113">Click **OK**.</span></span>  
  
2.  <span data-ttu-id="4076d-114">クラスを追加し、<xref:System.ServiceProcess.ServiceBase> から継承されるように設定します。</span><span class="sxs-lookup"><span data-stu-id="4076d-114">Add a class and configure it to inherit from <xref:System.ServiceProcess.ServiceBase>:</span></span>  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3.  <span data-ttu-id="4076d-115">次のコードを追加してサービス クラスを設定します。</span><span class="sxs-lookup"><span data-stu-id="4076d-115">Add the following code to configure your service class:</span></span>  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4.  <span data-ttu-id="4076d-116">クラスの `Main` メソッドを作成し、それを使用してクラスに含まれるサービスを定義します。`userService1` がクラスの名前です。</span><span class="sxs-lookup"><span data-stu-id="4076d-116">Create a `Main` method for your class, and use it to define the service your class will contain; `userService1` is the name of the class:</span></span>  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5.  <span data-ttu-id="4076d-117"><xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドをオーバーライドし、サービスの開始時に実行する処理を定義します。</span><span class="sxs-lookup"><span data-stu-id="4076d-117">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and define any processing you want to occur when your service is started.</span></span>  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6.  <span data-ttu-id="4076d-118">他に独自の処理を定義するメソッドがあればそれをオーバーライドし、サービスが行うアクションを記述します。</span><span class="sxs-lookup"><span data-stu-id="4076d-118">Override any other methods you want to define custom processing for, and write code to determine the actions the service should take in each case.</span></span>  
  
7.  <span data-ttu-id="4076d-119">サービス アプリケーションの必要なインストーラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="4076d-119">Add the necessary installers for your service application.</span></span> <span data-ttu-id="4076d-120">詳細については、次を参照してください。[する方法: サービス アプリケーションへのインストーラーの追加](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)です。</span><span class="sxs-lookup"><span data-stu-id="4076d-120">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
8.  <span data-ttu-id="4076d-121">選択して、プロジェクトをビルド**ソリューションのビルド**から、**ビルド**メニュー。</span><span class="sxs-lookup"><span data-stu-id="4076d-121">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4076d-122">F5 キーを押してプロジェクトを実行しないでください。この方法ではサービス プロジェクトを実行できません。</span><span class="sxs-lookup"><span data-stu-id="4076d-122">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
9. <span data-ttu-id="4076d-123">セットアップ プロジェクトと、サービスをインストールするカスタム処理を作成します。</span><span class="sxs-lookup"><span data-stu-id="4076d-123">Create a setup project and the custom actions to install your service.</span></span> <span data-ttu-id="4076d-124">例については、次を参照してください。[チュートリアル: コンポーネント デザイナーでの Windows サービス アプリケーションを作成する](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)です。</span><span class="sxs-lookup"><span data-stu-id="4076d-124">For an example, see [Walkthrough: Creating a Windows Service Application in the Component Designer](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
10. <span data-ttu-id="4076d-125">サービスをインストールします。</span><span class="sxs-lookup"><span data-stu-id="4076d-125">Install the service.</span></span> <span data-ttu-id="4076d-126">詳細については、「 [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4076d-126">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4076d-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="4076d-127">See Also</span></span>  
 [<span data-ttu-id="4076d-128">Windows サービス アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="4076d-128">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="4076d-129">方法: Windows サービスの作成</span><span class="sxs-lookup"><span data-stu-id="4076d-129">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [<span data-ttu-id="4076d-130">方法: サービス アプリケーションへのインストーラーの追加</span><span class="sxs-lookup"><span data-stu-id="4076d-130">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="4076d-131">方法: サービスに関する情報を記録</span><span class="sxs-lookup"><span data-stu-id="4076d-131">How to: Log Information About Services</span></span>](../../../docs/framework/windows-services/how-to-log-information-about-services.md)  
 [<span data-ttu-id="4076d-132">チュートリアル: コンポーネント デザイナーでの Windows サービス アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="4076d-132">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

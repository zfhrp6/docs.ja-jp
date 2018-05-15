---
title: サービス アプリケーションのプログラミング アーキテクチャ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceController components, programming architecture
- ServiceBase class, service states
- Windows Service applications, code model
- services, programming architecture
- ServiceController class
- services, states
- ServiceProcessInstaller class, service application code model
- Windows Service applications, states
ms.assetid: 83230026-d068-4174-97ff-e264c896eb2f
author: ghogen
manager: douge
ms.openlocfilehash: f0c760d0f9b65fc9b612a8bee8abb68fa5b4ecae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="service-application-programming-architecture"></a><span data-ttu-id="5a29d-102">サービス アプリケーションのプログラミング アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="5a29d-102">Service Application Programming Architecture</span></span>
<span data-ttu-id="5a29d-103">継承するクラスに基づいて Windows サービス アプリケーション、<xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>クラスです。</span><span class="sxs-lookup"><span data-stu-id="5a29d-103">Windows Service applications are based on a class that inherits from the <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="5a29d-104">このクラスからメソッドをオーバーライドして、サービスの動作を決定するそれらの機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="5a29d-104">You override methods from this class and define functionality for them to determine how your service behaves.</span></span>  
  
 <span data-ttu-id="5a29d-105">サービスの作成に関連する主要なクラスは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5a29d-105">The main classes involved in service creation are:</span></span>  
  
-   <span data-ttu-id="5a29d-106"><xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> — メソッドをオーバーライドする、<xref:System.ServiceProcess.ServiceBase>クラスのサービスを作成するときに、このサービス関数がクラスを継承する方法を決定するコードを定義します。</span><span class="sxs-lookup"><span data-stu-id="5a29d-106"><xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> — You override methods from the <xref:System.ServiceProcess.ServiceBase> class when creating a service and define the code to determine how your service functions in this inherited class.</span></span>  
  
-   <span data-ttu-id="5a29d-107"><xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=nameWithType> <xref:System.ServiceProcess.ServiceInstaller?displayProperty=nameWithType> -これらのクラスを使用してインストールし、サービスをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="5a29d-107"><xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=nameWithType> and <xref:System.ServiceProcess.ServiceInstaller?displayProperty=nameWithType> —You use these classes to install and uninstall your service.</span></span>  
  
 <span data-ttu-id="5a29d-108">さらに、クラスの名前付き<xref:System.ServiceProcess.ServiceController>サービス自体を操作するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="5a29d-108">In addition, a class named <xref:System.ServiceProcess.ServiceController> can be used to manipulate the service itself.</span></span> <span data-ttu-id="5a29d-109">このクラスは、サービスの作成に関連するではありませんを開始し、サービスを停止し、コマンドを渡す、一連の列挙体を返すために使用できます。</span><span class="sxs-lookup"><span data-stu-id="5a29d-109">This class is not involved in the creation of a service, but can be used to start and stop the service, pass commands to it, and return a series of enumerations.</span></span>  
  
## <a name="defining-your-services-behavior"></a><span data-ttu-id="5a29d-110">サービスの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="5a29d-110">Defining Your Service's Behavior</span></span>  
 <span data-ttu-id="5a29d-111">サービス クラスでは、サービス コントロール マネージャーで、サービスの状態が変更されたときの動作を決定する基底クラスの関数をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="5a29d-111">In your service class, you override base class functions that determine what happens when the state of your service is changed in the Services Control Manager.</span></span> <span data-ttu-id="5a29d-112"><xref:System.ServiceProcess.ServiceBase>クラスは次のメソッドは、カスタム動作を追加するをオーバーライドすることができますを公開します。</span><span class="sxs-lookup"><span data-stu-id="5a29d-112">The <xref:System.ServiceProcess.ServiceBase> class exposes the following methods, which you can override to add custom behavior.</span></span>  
  
|<span data-ttu-id="5a29d-113">メソッド</span><span class="sxs-lookup"><span data-stu-id="5a29d-113">Method</span></span>|<span data-ttu-id="5a29d-114">する上書き</span><span class="sxs-lookup"><span data-stu-id="5a29d-114">Override to</span></span>|  
|------------|-----------------|  
|<xref:System.ServiceProcess.ServiceBase.OnStart%2A>|<span data-ttu-id="5a29d-115">サービスが実行を開始するときに、どのようなアクションを実行する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="5a29d-115">Indicate what actions should be taken when your service starts running.</span></span> <span data-ttu-id="5a29d-116">有効な作業を実行するようにサービスに対してこの手順でコードを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a29d-116">You must write code in this procedure for your service to perform useful work.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnPause%2A>|<span data-ttu-id="5a29d-117">サービスが一時停止したときの動作を示してください。</span><span class="sxs-lookup"><span data-stu-id="5a29d-117">Indicate what should happen when your service is paused.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnStop%2A>|<span data-ttu-id="5a29d-118">サービスの実行が停止したときの動作を示してください。</span><span class="sxs-lookup"><span data-stu-id="5a29d-118">Indicate what should happen when your service stops running.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>|<span data-ttu-id="5a29d-119">サービスが一時停止された後に正常な機能を再開したときの動作を示してください。</span><span class="sxs-lookup"><span data-stu-id="5a29d-119">Indicate what should happen when your service resumes normal functioning after being paused.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>|<span data-ttu-id="5a29d-120">その時点で、サービスが実行されている場合、システムがシャット ダウンする直前の動作を示します。</span><span class="sxs-lookup"><span data-stu-id="5a29d-120">Indicate what should happen just prior to your system shutting down, if your service is running at that time.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnCustomCommand%2A>|<span data-ttu-id="5a29d-121">サービスは、カスタム コマンドを受信したときの動作を示してください。</span><span class="sxs-lookup"><span data-stu-id="5a29d-121">Indicate what should happen when your service receives a custom command.</span></span> <span data-ttu-id="5a29d-122">カスタム コマンドの詳細については、オンライン MSDN 参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a29d-122">For more information on custom commands, see MSDN online.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnPowerEvent%2A>|<span data-ttu-id="5a29d-123">バッテリ低下や中断された操作など、電源管理イベントを受信したときに、サービスの応答方法を示してください。</span><span class="sxs-lookup"><span data-stu-id="5a29d-123">Indicate how the service should respond when a power management event is received, such as a low battery or suspended operation.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="5a29d-124">これらのメソッドは、サービスがその有効期間内に通過状態を表しています。サービスは、1 つの状態から、次に遷移します。</span><span class="sxs-lookup"><span data-stu-id="5a29d-124">These methods represent states that the service moves through in its lifetime; the service transitions from one state to the next.</span></span> <span data-ttu-id="5a29d-125">応答するサービスを決して取得するなど、<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>する前にコマンド<xref:System.ServiceProcess.ServiceBase.OnStart%2A>呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="5a29d-125">For example, you will never get the service to respond to an <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> command before <xref:System.ServiceProcess.ServiceBase.OnStart%2A> has been called.</span></span>  
  
 <span data-ttu-id="5a29d-126">その他のいくつかのプロパティと関心のあるメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="5a29d-126">There are several other properties and methods that are of interest.</span></span> <span data-ttu-id="5a29d-127">次の設定があります。</span><span class="sxs-lookup"><span data-stu-id="5a29d-127">These include:</span></span>  
  
-   <span data-ttu-id="5a29d-128"><xref:System.ServiceProcess.ServiceBase.Run%2A>メソッドを<xref:System.ServiceProcess.ServiceBase>クラスです。</span><span class="sxs-lookup"><span data-stu-id="5a29d-128">The <xref:System.ServiceProcess.ServiceBase.Run%2A> method on the <xref:System.ServiceProcess.ServiceBase> class.</span></span> <span data-ttu-id="5a29d-129">これは、サービスのメイン エントリ ポイントです。</span><span class="sxs-lookup"><span data-stu-id="5a29d-129">This is the main entry point for the service.</span></span> <span data-ttu-id="5a29d-130">アプリケーションのコードが挿入される Windows サービス テンプレートを使用してサービスを作成するときに`Main`メソッドをサービスを実行します。</span><span class="sxs-lookup"><span data-stu-id="5a29d-130">When you create a service using the Windows Service template, code is inserted in your application's `Main` method to run the service.</span></span> <span data-ttu-id="5a29d-131">このコードは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="5a29d-131">This code looks like this:</span></span>  
  
     [!code-csharp[VbRadconService#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#6)]
     [!code-vb[VbRadconService#6](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#6)]  
  
    > [!NOTE]
    >  <span data-ttu-id="5a29d-132">これらの例は、型の配列を使用して<xref:System.ServiceProcess.ServiceBase>をアプリケーションに含まれる各サービスを追加することができます、し、すべてのサービスで一緒に実行できます。</span><span class="sxs-lookup"><span data-stu-id="5a29d-132">These examples use an array of type <xref:System.ServiceProcess.ServiceBase>, into which each service your application contains can be added, and then all of the services can be run together.</span></span> <span data-ttu-id="5a29d-133">1 つのサービスのみを作成する場合は、ただし、こともできましていないを使用して、配列から継承する新しいオブジェクトを単に宣言<xref:System.ServiceProcess.ServiceBase>し、実行します。</span><span class="sxs-lookup"><span data-stu-id="5a29d-133">If you are only creating a single service, however, you might choose not to use the array and simply declare a new object inheriting from <xref:System.ServiceProcess.ServiceBase> and then run it.</span></span> <span data-ttu-id="5a29d-134">例については、次を参照してください。[する方法: プログラムによってサービスを書き込む](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)です。</span><span class="sxs-lookup"><span data-stu-id="5a29d-134">For an example, see [How to: Write Services Programmatically](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).</span></span>  
  
-   <span data-ttu-id="5a29d-135">一連のプロパティの<xref:System.ServiceProcess.ServiceBase>クラスです。</span><span class="sxs-lookup"><span data-stu-id="5a29d-135">A series of properties on the <xref:System.ServiceProcess.ServiceBase> class.</span></span> <span data-ttu-id="5a29d-136">これらは、どのような方法は、サービスを呼び出すことができますを決定します。</span><span class="sxs-lookup"><span data-stu-id="5a29d-136">These determine what methods can be called on your service.</span></span> <span data-ttu-id="5a29d-137">たとえばときに、<xref:System.ServiceProcess.ServiceBase.CanStop%2A>プロパティに設定されている`true`、<xref:System.ServiceProcess.ServiceBase.OnStop%2A>サービスでメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="5a29d-137">For example, when the <xref:System.ServiceProcess.ServiceBase.CanStop%2A> property is set to `true`, the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method on your service can be called.</span></span> <span data-ttu-id="5a29d-138">ときに、<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>プロパティに設定されている`true`、<xref:System.ServiceProcess.ServiceBase.OnPause%2A>と<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="5a29d-138">When the <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> property is set to `true`, the <xref:System.ServiceProcess.ServiceBase.OnPause%2A> and <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> methods can be called.</span></span> <span data-ttu-id="5a29d-139">これらのプロパティのいずれかを設定すると`true`、しをオーバーライドし、関連するメソッドの処理を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a29d-139">When you set one of these properties to `true`, you should then override and define processing for the associated methods.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5a29d-140">サービスをオーバーライドする必要がありますには、少なくとも<xref:System.ServiceProcess.ServiceBase.OnStart%2A>と<xref:System.ServiceProcess.ServiceBase.OnStop%2A>を有効にします。</span><span class="sxs-lookup"><span data-stu-id="5a29d-140">Your service must override at least <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> to be useful.</span></span>  
  
 <span data-ttu-id="5a29d-141">呼ばれるコンポーネントを使用することも、<xref:System.ServiceProcess.ServiceController>と通信して、既存のサービスの動作を制御します。</span><span class="sxs-lookup"><span data-stu-id="5a29d-141">You can also use a component called the <xref:System.ServiceProcess.ServiceController> to communicate with and control the behavior of an existing service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a29d-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a29d-142">See Also</span></span>  
 [<span data-ttu-id="5a29d-143">Windows サービス アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="5a29d-143">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="5a29d-144">方法 : Windows サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="5a29d-144">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)

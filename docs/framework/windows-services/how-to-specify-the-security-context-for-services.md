---
title: "方法 : サービスのセキュリティ コンテキストを指定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, security
- security [Visual Studio], contexts
- contexts, Visual Studio security
- security [Visual Studio], service applications
- ServiceProcessInstaller class, security context
- services, security
- ServiceInstaller class, security context
ms.assetid: 02187c7b-dbf2-45f2-96c2-e11010225a22
caps.latest.revision: "10"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 9ce65358f6d63414dbe6798d3cc2464ee2741980
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-security-context-for-services"></a><span data-ttu-id="6fd33-102">方法 : サービスのセキュリティ コンテキストを指定する</span><span class="sxs-lookup"><span data-stu-id="6fd33-102">How to: Specify the Security Context for Services</span></span>
<span data-ttu-id="6fd33-103">既定では、サービスは、ログイン ユーザーの場合よりも別のセキュリティ コンテキストで実行します。</span><span class="sxs-lookup"><span data-stu-id="6fd33-103">By default, services run in a different security context than that of the logged-in user.</span></span> <span data-ttu-id="6fd33-104">既定のシステム アカウントのコンテキストで実行するサービスと呼ばれる`LocalSystem`、与えるさまざまなアクセス特権ユーザーのシステム リソースにします。</span><span class="sxs-lookup"><span data-stu-id="6fd33-104">Services run in the context of the default system account, called `LocalSystem`, which gives them different access privileges to system resources than the user.</span></span> <span data-ttu-id="6fd33-105">サービスを実行する別のユーザー アカウントを指定するには、この動作を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="6fd33-105">You can change this behavior to specify a different user account under which your service should run.</span></span>  
  
 <span data-ttu-id="6fd33-106">操作することで、セキュリティ コンテキストを設定する、<xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A>サービスが実行されるプロセスのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="6fd33-106">You set the security context by manipulating the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property for the process within which the service runs.</span></span> <span data-ttu-id="6fd33-107">このプロパティでは、次の 4 つのアカウントの種類のいずれかにサービスを設定することができます。</span><span class="sxs-lookup"><span data-stu-id="6fd33-107">This property allows you to set the service to one of four account types:</span></span>  
  
-   <span data-ttu-id="6fd33-108">`User`、それが原因で、システム、サービスがインストールされているし、ネットワーク上の 1 人のユーザーによって指定されたアカウントのコンテキストで実行されるとき、有効なユーザー名とパスワードを要求するには</span><span class="sxs-lookup"><span data-stu-id="6fd33-108">`User`, which causes the system to prompt for a valid user name and password when the service is installed and runs in the context of an account specified by a single user on the network;</span></span>  
  
-   <span data-ttu-id="6fd33-109">`LocalService`、、ローカル コンピューターで非特権ユーザーとして機能し、すべてのリモート サーバーへの匿名の資格情報を表示するアカウントのコンテキストで実行します。</span><span class="sxs-lookup"><span data-stu-id="6fd33-109">`LocalService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents anonymous credentials to any remote server;</span></span>  
  
-   <span data-ttu-id="6fd33-110">`LocalSystem`、広範囲のローカル特権を提供し、すべてのリモート サーバーにコンピューターの資格情報を表示するアカウントのコンテキストで実行します。</span><span class="sxs-lookup"><span data-stu-id="6fd33-110">`LocalSystem`, which runs in the context of an account that provides extensive local privileges, and presents the computer's credentials to any remote server;</span></span>  
  
-   <span data-ttu-id="6fd33-111">`NetworkService`、、ローカル コンピューターで非特権ユーザーとしては機能し、リモート サーバーにコンピューターの資格情報を提示するアカウントのコンテキストで実行します。</span><span class="sxs-lookup"><span data-stu-id="6fd33-111">`NetworkService`, which runs in the context of an account that acts as a non-privileged user on the local computer, and presents the computer's credentials to any remote server.</span></span>  
  
 <span data-ttu-id="6fd33-112">詳細については、<xref:System.ServiceProcess.ServiceAccount> 列挙型のページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6fd33-112">For more information, see the <xref:System.ServiceProcess.ServiceAccount> enumeration.</span></span>  
  
### <a name="to-specify-the-security-context-for-a-service"></a><span data-ttu-id="6fd33-113">サービスのセキュリティ コンテキストを指定するには</span><span class="sxs-lookup"><span data-stu-id="6fd33-113">To specify the security context for a service</span></span>  
  
1.  <span data-ttu-id="6fd33-114">サービスの作成後、必要なインストーラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="6fd33-114">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="6fd33-115">詳細については、次を参照してください。[する方法: サービス アプリケーションへのインストーラーの追加](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)です。</span><span class="sxs-lookup"><span data-stu-id="6fd33-115">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
2.  <span data-ttu-id="6fd33-116">デザイナーで、アクセス、`ProjectInstaller`クラスを使用しているサービスのサービス プロセスのインストーラーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6fd33-116">In the designer, access the `ProjectInstaller` class and click the service process installer for the service you are working with.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6fd33-117">少なくとも 2 つのインストール コンポーネントがあるサービス アプリケーションごとに、`ProjectInstaller`クラス: いずれかのプロジェクト、およびアプリケーションを含むサービスごとに 1 つのインストーラーですべてのサービス プロセスをインストールします。</span><span class="sxs-lookup"><span data-stu-id="6fd33-117">For every service application, there are at least two installation components in the `ProjectInstaller` class — one that installs the processes for all services in the project, and one installer for each service the application contains.</span></span> <span data-ttu-id="6fd33-118">選択すると、このインスタンスで<xref:System.ServiceProcess.ServiceProcessInstaller>です。</span><span class="sxs-lookup"><span data-stu-id="6fd33-118">In this instance, you want to select <xref:System.ServiceProcess.ServiceProcessInstaller>.</span></span>  
  
3.  <span data-ttu-id="6fd33-119">**プロパティ**ウィンドウで、設定、<xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A>適切な値にします。</span><span class="sxs-lookup"><span data-stu-id="6fd33-119">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> to the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fd33-120">参照</span><span class="sxs-lookup"><span data-stu-id="6fd33-120">See Also</span></span>  
 [<span data-ttu-id="6fd33-121">Windows サービス アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="6fd33-121">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="6fd33-122">方法 : サービス アプリケーションにインストーラーを追加する</span><span class="sxs-lookup"><span data-stu-id="6fd33-122">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="6fd33-123">方法 : Windows サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="6fd33-123">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)

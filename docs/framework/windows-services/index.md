---
title: "Windows サービス アプリケーションの開発"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
caps.latest.revision: "18"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 325e43f4b1734bc6ab8753285e5069f36b0fda51
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="developing-windows-service-applications"></a><span data-ttu-id="0190a-102">Windows サービス アプリケーションの開発</span><span class="sxs-lookup"><span data-stu-id="0190a-102">Developing Windows Service Applications</span></span>
<span data-ttu-id="0190a-103">Microsoft[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]または Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK、簡単にサービスを作成できますが、サービスとしてインストールされているアプリケーションを作成しています。</span><span class="sxs-lookup"><span data-stu-id="0190a-103">Using Microsoft [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] or the Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="0190a-104">この種類のアプリケーションには、Windows サービスが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0190a-104">This type of application is called a Windows service.</span></span> <span data-ttu-id="0190a-105">フレームワーク機能を使用することができますサービスを作成、したり、インストールし、開始、停止、および動作を制御します。</span><span class="sxs-lookup"><span data-stu-id="0190a-105">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="0190a-106">C++ の Windows サービス テンプレートは、Visual Studio 2010 に組み込まれませんでした。</span><span class="sxs-lookup"><span data-stu-id="0190a-106">The Windows service template for C++ was not included in Visual Studio 2010.</span></span> <span data-ttu-id="0190a-107">Windows サービスを作成するには、Visual c# または Visual Basic は、必要な場合は、既存の C++ コードと相互運用する可能性があります、マネージ コードでサービスを作成することができますか、またはを使用して、ネイティブ C++ で Windows サービスを作成することができます、 [ATLプロジェクトウィザード](/cpp/atl/reference/atl-project-wizard).</span><span class="sxs-lookup"><span data-stu-id="0190a-107">To create a Windows service, you can either create a service in managed code in Visual C# or Visual Basic, which could interoperate with existing C++ code if required, or you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0190a-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="0190a-108">In This Section</span></span>  
 [<span data-ttu-id="0190a-109">Windows サービス アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="0190a-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 <span data-ttu-id="0190a-110">サービス、およびその他の一般的なプロジェクトの種類のサービス アプリケーションの違いの有効期間の Windows サービス アプリケーションの概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="0190a-110">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>  
  
 [<span data-ttu-id="0190a-111">チュートリアル: コンポーネント デザイナーによる Windows サービス アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="0190a-111">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 <span data-ttu-id="0190a-112">サービスを作成する例を示します[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]および Visual c# です。</span><span class="sxs-lookup"><span data-stu-id="0190a-112">Provides an example of creating a service in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] and Visual C#.</span></span>  
  
 [<span data-ttu-id="0190a-113">サービス アプリケーションのプログラミング アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="0190a-113">Service Application Programming Architecture</span></span>](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 <span data-ttu-id="0190a-114">サービスのプログラミングで使用される言語要素をについて説明します。</span><span class="sxs-lookup"><span data-stu-id="0190a-114">Explains the language elements used in service programming.</span></span>  
  
 [<span data-ttu-id="0190a-115">方法 : Windows サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="0190a-115">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 <span data-ttu-id="0190a-116">作成して、Windows サービス プロジェクトのテンプレートを使用して Windows サービスの構成のプロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="0190a-116">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0190a-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="0190a-117">Related Sections</span></span>  
 <xref:System.ServiceProcess.ServiceBase>  
 <span data-ttu-id="0190a-118">主要な機能について説明します、<xref:System.ServiceProcess.ServiceBase>クラスは、サービスを作成するために使用します。</span><span class="sxs-lookup"><span data-stu-id="0190a-118">Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 <span data-ttu-id="0190a-119">機能について説明します、<xref:System.ServiceProcess.ServiceProcessInstaller>と共に使用されるクラス、<xref:System.ServiceProcess.ServiceInstaller>クラスをインストールして、サービスをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="0190a-119">Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 <span data-ttu-id="0190a-120">機能について説明します、<xref:System.ServiceProcess.ServiceInstaller>と共に使用されるクラス、<xref:System.ServiceProcess.ServiceProcessInstaller>クラスをインストールおよびサービスをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="0190a-120">Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>  
  
 [<span data-ttu-id="0190a-121">NIB テンプレートからプロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="0190a-121">NIB Creating Projects from Templates</span></span>](http://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2)  
 <span data-ttu-id="0190a-122">プロジェクトをについて説明します。 この章でし、それらの間を選択する方法で使用される型。</span><span class="sxs-lookup"><span data-stu-id="0190a-122">Describes the projects types used in this chapter and how to choose between them.</span></span>

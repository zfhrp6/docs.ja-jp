---
title: Windows サービス アプリケーションの開発
ms.date: 03/30/2017
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
author: ghogen
manager: douge
ms.openlocfilehash: af6e4bf7697b3139f6809295737fdd0d90b7f013
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512269"
---
# <a name="developing-windows-service-applications"></a><span data-ttu-id="44a1d-102">Windows サービス アプリケーションの開発</span><span class="sxs-lookup"><span data-stu-id="44a1d-102">Developing Windows Service Applications</span></span>
<span data-ttu-id="44a1d-103">Microsoft Visual Studio または Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK を使用すると、サービスとしてインストールするアプリケーションを作成することで簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="44a1d-103">Using Microsoft Visual Studio or the Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="44a1d-104">この種類のアプリケーションは、Windows サービスと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="44a1d-104">This type of application is called a Windows service.</span></span> <span data-ttu-id="44a1d-105">フレームワーク機能を使用することで、サービスを作成、インストール、開始、停止したり、動作を制御したりできます。</span><span class="sxs-lookup"><span data-stu-id="44a1d-105">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="44a1d-106">C++ の Windows サービス テンプレートは、Visual Studio 2010 に含まれていませんでした。</span><span class="sxs-lookup"><span data-stu-id="44a1d-106">The Windows service template for C++ was not included in Visual Studio 2010.</span></span> <span data-ttu-id="44a1d-107">Windows サービスを作成するには、Visual C# または Visual Basic のマネージド コードでサービスを作成するか (必要に応じて、既存の C++ コードと相互運用できます)、[ATL プロジェクト ウィザード](/cpp/atl/reference/atl-project-wizard)を使用して、ネイティブ C++ で Windows サービスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="44a1d-107">To create a Windows service, you can either create a service in managed code in Visual C# or Visual Basic, which could interoperate with existing C++ code if required, or you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="44a1d-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="44a1d-108">In This Section</span></span>  
 [<span data-ttu-id="44a1d-109">Windows サービス アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="44a1d-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 <span data-ttu-id="44a1d-110">Windows サービス アプリケーションの概要、サービスの有効期間、およびサービスがその他の一般的な種類のプロジェクトどのように異なるかを説明します。</span><span class="sxs-lookup"><span data-stu-id="44a1d-110">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>  
  
 [<span data-ttu-id="44a1d-111">チュートリアル: コンポーネント デザイナーによる Windows サービス アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="44a1d-111">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 <span data-ttu-id="44a1d-112">Visual Basic および Visual C# でサービスを作成する例を提供します。</span><span class="sxs-lookup"><span data-stu-id="44a1d-112">Provides an example of creating a service in Visual Basic and Visual C#.</span></span>  
  
 [<span data-ttu-id="44a1d-113">サービス アプリケーションのプログラミング アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="44a1d-113">Service Application Programming Architecture</span></span>](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 <span data-ttu-id="44a1d-114">サービスのプログラミングで使用される言語要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="44a1d-114">Explains the language elements used in service programming.</span></span>  
  
 [<span data-ttu-id="44a1d-115">方法 : Windows サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="44a1d-115">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 <span data-ttu-id="44a1d-116">Windows サービス プロジェクトのテンプレートを使用して Windows サービスを作成、構成するプロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="44a1d-116">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="44a1d-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="44a1d-117">Related Sections</span></span>  
 <xref:System.ServiceProcess.ServiceBase>  
 <span data-ttu-id="44a1d-118">サービスの作成に使用される、<xref:System.ServiceProcess.ServiceBase> クラスの主要な機能を説明します。</span><span class="sxs-lookup"><span data-stu-id="44a1d-118">Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 <span data-ttu-id="44a1d-119"><xref:System.ServiceProcess.ServiceInstaller> クラスと共に使用して、サービスをインストール/アンインストールする <xref:System.ServiceProcess.ServiceProcessInstaller> クラスの機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="44a1d-119">Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 <span data-ttu-id="44a1d-120"><xref:System.ServiceProcess.ServiceProcessInstaller> クラスと共に使用して、サービスをインストール/アンインストールする <xref:System.ServiceProcess.ServiceInstaller> クラスの機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="44a1d-120">Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>  
  
 [<span data-ttu-id="44a1d-121">NIB テンプレートからのプロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="44a1d-121">NIB Creating Projects from Templates</span></span>](http://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2)  
 <span data-ttu-id="44a1d-122">この章で使用されるプロジェクトの種類と、それを選択する際に役立つガイドラインを説明します。</span><span class="sxs-lookup"><span data-stu-id="44a1d-122">Describes the projects types used in this chapter and how to choose between them.</span></span>

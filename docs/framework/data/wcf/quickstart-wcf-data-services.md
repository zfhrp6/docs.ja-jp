---
title: クイック スタート (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: 1a30f7e65efc65bf47abd61e5bfdfa85b58ae3a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365398"
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="19bf1-102">クイック スタート (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="19bf1-102">Quickstart (WCF Data Services)</span></span>
<span data-ttu-id="19bf1-103">このクイック スタートでは、理解できます。[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]と[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]一連のトピックでは、をサポートするタスクを[作業の開始](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="19bf1-103">This quickstart helps you become familiar with [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] and the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] through a series of tasks that support the topics in [Getting Started](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md).</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="19bf1-104">学習する内容</span><span class="sxs-lookup"><span data-stu-id="19bf1-104">What You Will Learn</span></span>  
 <span data-ttu-id="19bf1-105">このクイック スタートの最初のタスクでは、データ サービスを作成し、Northwind サンプル データベースの [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを公開する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="19bf1-105">The first task in this quickstart shows how to create a data service to expose an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed from the Northwind sample database.</span></span> <span data-ttu-id="19bf1-106">後半のトピックでは、Web ブラウザーを使用して [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードにアクセスします。また、クライアント ライブラリを使用して [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを使用する Windows Presentation Foundation (WPF) クライアント アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="19bf1-106">In later topics, you will access the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed by using client libraries.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="19bf1-107">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="19bf1-107">Prerequisites</span></span>  
 <span data-ttu-id="19bf1-108">このクイック スタートを最後まで行うには、次のコンポーネントがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="19bf1-108">To complete this quickstart, you must install the following components:</span></span>  
  
-   [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]<span data-ttu-id="19bf1-109">。</span><span class="sxs-lookup"><span data-stu-id="19bf1-109">.</span></span>  
  
-   <span data-ttu-id="19bf1-110">インスタンス[!INCLUDE[msCoName](../../../../includes/msconame-md.md)]SQL Server。</span><span class="sxs-lookup"><span data-stu-id="19bf1-110">An instance of [!INCLUDE[msCoName](../../../../includes/msconame-md.md)] SQL Server.</span></span> <span data-ttu-id="19bf1-111">これには、Visual Studio の既定のインストールに含まれる SQL Server Express が含まれます。</span><span class="sxs-lookup"><span data-stu-id="19bf1-111">This includes SQL Server Express, which is included in a default installation of Visual Studio.</span></span>  
  
-   <span data-ttu-id="19bf1-112">Northwind サンプル データベース。</span><span class="sxs-lookup"><span data-stu-id="19bf1-112">The Northwind sample database.</span></span> <span data-ttu-id="19bf1-113">このサンプル データベースをダウンロードするには、ダウンロード ページ「 [SQL Server 用サンプル データベース](http://go.microsoft.com/fwlink/?linkid=24758)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19bf1-113">To download this sample database, see the download page, [Sample Databases for SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).</span></span>  
  
## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="19bf1-114">WCF Data Services クイックスタートのタスク</span><span class="sxs-lookup"><span data-stu-id="19bf1-114">WCF Data Services Quickstart Tasks</span></span>  
 [<span data-ttu-id="19bf1-115">データ サービスの作成</span><span class="sxs-lookup"><span data-stu-id="19bf1-115">Creating the Data Service</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)  
 <span data-ttu-id="19bf1-116">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションの定義、データ モデルの定義、データ サービスの作成、およびリソースへのアクセスの有効化を行います。</span><span class="sxs-lookup"><span data-stu-id="19bf1-116">Define the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application, define the data model, create the data service, and enable access to resources.</span></span>  
  
 [<span data-ttu-id="19bf1-117">Web ブラウザーからサービスへのアクセス</span><span class="sxs-lookup"><span data-stu-id="19bf1-117">Accessing the Service from a Web Browser</span></span>](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)  
 <span data-ttu-id="19bf1-118">Visual Studio からサービスを開始し、公開されているフィードに対して Web ブラウザーから HTTP GET 要求を送信してサービスにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="19bf1-118">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>  
  
 [<span data-ttu-id="19bf1-119">.NET Framework クライアント アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="19bf1-119">Creating the .NET Framework Client Application</span></span>](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)  
 <span data-ttu-id="19bf1-120">[!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] クライアント アプリケーションを作成して、 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードの使用、Windows コントロールへのデータのバインド、バインドされたコントロールのデータの変更、およびデータ サービスへの変更内容の送信を行います。</span><span class="sxs-lookup"><span data-stu-id="19bf1-120">Create a [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] client application to consume the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19bf1-121">クイック スタートを完了したプロジェクト ファイルは、「 [WCF Data Services ドキュメントのサンプル](http://go.microsoft.com/fwlink/?LinkId=179994) 」ページからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="19bf1-121">Project files from a completed version of the quickstart can be downloaded from the [WCF Data Services Documentation Samples](http://go.microsoft.com/fwlink/?LinkId=179994) page.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="19bf1-122">次の手順</span><span class="sxs-lookup"><span data-stu-id="19bf1-122">Next Steps</span></span>  
 <span data-ttu-id="19bf1-123">[クイック スタートの開始](../../../../docs/framework/data/wcf/creating-the-data-service.md)</span><span class="sxs-lookup"><span data-stu-id="19bf1-123">[Start the Quickstart](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19bf1-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="19bf1-124">See Also</span></span>  
 [<span data-ttu-id="19bf1-125">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="19bf1-125">ADO.NET Entity Framework</span></span>](../../../../docs/framework/data/adonet/ef/index.md)

---
title: "Windows フォームの ClickOnce 配置"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ClickOnce deployment [Windows Forms]
- Windows Forms, ClickOnce deployment
- walkthroughs [Windows Forms], ClickOnce deployment
ms.assetid: 1451fce9-1965-4a03-b4d3-831b5fe4ad66
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f157ea4afcaccfffde548c26a440fa6686c87aa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="clickonce-deployment-for-windows-forms"></a><span data-ttu-id="ab6e2-102">Windows フォームの ClickOnce 配置</span><span class="sxs-lookup"><span data-stu-id="ab6e2-102">ClickOnce Deployment for Windows Forms</span></span>
<span data-ttu-id="ab6e2-103">次のトピックでは、Windows フォーム アプリケーションをクライアント コンピューターに簡単に配置するために使用されるテクノロジである [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] について説明します。</span><span class="sxs-lookup"><span data-stu-id="ab6e2-103">The following topics describe [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)], a technology used for easily deploying Windows Forms applications to client computers.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ab6e2-104">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab6e2-104">Related Sections</span></span>  
 [<span data-ttu-id="ab6e2-105">ClickOnce 配置ストラテジの選択</span><span class="sxs-lookup"><span data-stu-id="ab6e2-105">Choosing a ClickOnce Deployment Strategy</span></span>](/visualstudio/deployment/choosing-a-clickonce-deployment-strategy)  
 <span data-ttu-id="ab6e2-106">[!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] アプリケーションを配置するためのいくつかのオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ab6e2-106">Presents several options for deploying [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] applications.</span></span>  
  
 [<span data-ttu-id="ab6e2-107">ClickOnce の更新方法の選択</span><span class="sxs-lookup"><span data-stu-id="ab6e2-107">Choosing a ClickOnce Update Strategy</span></span>](/visualstudio/deployment/choosing-a-clickonce-update-strategy)  
 <span data-ttu-id="ab6e2-108">[!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] アプリケーションを更新するためのいくつかのオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ab6e2-108">Presents several options for updating [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] applications.</span></span>  
  
 [<span data-ttu-id="ab6e2-109">ClickOnce アプリケーションのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="ab6e2-109">Securing ClickOnce Applications</span></span>](/visualstudio/deployment/securing-clickonce-applications)  
 <span data-ttu-id="ab6e2-110">[!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 配置のセキュリティへの影響について説明します。</span><span class="sxs-lookup"><span data-stu-id="ab6e2-110">Explains the security implications of [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] deployment.</span></span>  
  
 [<span data-ttu-id="ab6e2-111">ClickOnce 配置のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="ab6e2-111">Troubleshooting ClickOnce Deployments</span></span>](/visualstudio/deployment/troubleshooting-clickonce-deployments)  
 <span data-ttu-id="ab6e2-112">[!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] アプリケーションを配置するときに発生する可能性のあるさまざまな問題について説明し、[!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] が生成する可能性のあるトップレベルのエラー メッセージを記載します。</span><span class="sxs-lookup"><span data-stu-id="ab6e2-112">Describes various problems that can occur when deploying [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] applications, and documents the top-level error messages that [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] might generate.</span></span>  
  
 [<span data-ttu-id="ab6e2-113">ClickOnce とアプリケーション設定</span><span class="sxs-lookup"><span data-stu-id="ab6e2-113">ClickOnce and Application Settings</span></span>](/visualstudio/deployment/clickonce-and-application-settings)  
 <span data-ttu-id="ab6e2-114">アプリケーション設定とユーザー設定を将来の取得に備えて保存するアプリケーション設定と、[!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 配置の連携方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ab6e2-114">Describes how [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] deployment works with application settings, which stores application and user settings for future retrieval.</span></span>  
  
 [<span data-ttu-id="ab6e2-115">信頼されたアプリケーションの配置の概要</span><span class="sxs-lookup"><span data-stu-id="ab6e2-115">Trusted Application Deployment Overview</span></span>](/visualstudio/deployment/trusted-application-deployment-overview)  
 <span data-ttu-id="ab6e2-116">クライアント コンピューターで、信頼されたアプリケーションが高いレベルのアクセス許可で実行できるようにする [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] の機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="ab6e2-116">Describes a [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] feature that allows trusted applications to run with a higher level of permission on client computers.</span></span>  
  
 [<span data-ttu-id="ab6e2-117">ClickOnce と Authenticode</span><span class="sxs-lookup"><span data-stu-id="ab6e2-117">ClickOnce and Authenticode</span></span>](/visualstudio/deployment/clickonce-and-authenticode)  
 <span data-ttu-id="ab6e2-118">Authenticode テクノロジが信頼されたアプリケーション配置で使用される方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ab6e2-118">Describes how Authenticode technology is used in trusted application deployment.</span></span>  
  
 [<span data-ttu-id="ab6e2-119">チュートリアル : ClickOnce アプリケーションを手動で配置する</span><span class="sxs-lookup"><span data-stu-id="ab6e2-119">Walkthrough: Manually Deploying a ClickOnce Application</span></span>](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)  
 <span data-ttu-id="ab6e2-120">コマンド ラインと SDK ツールを使用し、Visual Studio を使用せずに [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] アプリケーションを配置する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ab6e2-120">Demonstrates using command-line and SDK tools to deploy a [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] application without using Visual Studio.</span></span>  
  
 [<span data-ttu-id="ab6e2-121">方法: ClickOnce アプリケーション用の信頼された発行者をクライアント コンピューターに追加する</span><span class="sxs-lookup"><span data-stu-id="ab6e2-121">How to: Add a Trusted Publisher to a Client Computer for ClickOnce Applications</span></span>](/visualstudio/deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications)  
 <span data-ttu-id="ab6e2-122">信頼されたアプリケーションの配置に必要なクライアント コンピューターの 1 回限りの構成について説明します。</span><span class="sxs-lookup"><span data-stu-id="ab6e2-122">Demonstrates the one-time configuration of client computers required for trusted application deployment.</span></span>  
  
 [<span data-ttu-id="ab6e2-123">方法 : 配置の更新用に別の場所を指定する</span><span class="sxs-lookup"><span data-stu-id="ab6e2-123">How to: Specify an Alternate Location for Deployment Updates</span></span>](/visualstudio/deployment/how-to-specify-an-alternate-location-for-deployment-updates)  
 <span data-ttu-id="ab6e2-124">SDK ツールを使用して、[!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] アプリケーションを構成し、新しいバージョンのアプリケーションの別の場所を確認する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ab6e2-124">Demonstrates configuring a [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] application, using SDK tools, to check a different location for new versions of an application.</span></span>  
  
 [<span data-ttu-id="ab6e2-125">チュートリアル : ClickOnce 配置 API を使用して必要に応じてアセンブリをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="ab6e2-125">Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API</span></span>](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api)  
 <span data-ttu-id="ab6e2-126">API 呼び出しを使用して、アプリケーションが初めて読み込もうとしたときにアセンブリを取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ab6e2-126">Demonstrates using API calls to retrieve an assembly the first time your application attempts to load it.</span></span>  
  
 [<span data-ttu-id="ab6e2-127">方法 : オンライン ClickOnce アプリケーションでクエリ文字列を取得する</span><span class="sxs-lookup"><span data-stu-id="ab6e2-127">How to: Retrieve Query String Information in an Online ClickOnce Application</span></span>](/visualstudio/deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application)  
 <span data-ttu-id="ab6e2-128">[!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] アプリケーションの実行に使用する URL からパラメーターを取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ab6e2-128">Demonstrates retrieving parameters from the URL used to run a [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] application.</span></span>  
  
 [<span data-ttu-id="ab6e2-129">ClickOnce キャッシュの概要</span><span class="sxs-lookup"><span data-stu-id="ab6e2-129">ClickOnce Cache Overview</span></span>](/visualstudio/deployment/clickonce-cache-overview)  
 <span data-ttu-id="ab6e2-130">ローカル コンピューターに [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] アプリケーションを保存するために使用されるキャッシュについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ab6e2-130">Describes the cache used to store [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] applications on the local computer.</span></span>  
  
 [<span data-ttu-id="ab6e2-131">ClickOnce アプリケーションにおけるローカル データおよびリモート データへのアクセス</span><span class="sxs-lookup"><span data-stu-id="ab6e2-131">Accessing Local and Remote Data in ClickOnce Applications</span></span>](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications)  
 <span data-ttu-id="ab6e2-132">[!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] アプリケーションからローカル データ ファイルとリモート データ ソースにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ab6e2-132">Describes how to access local data files and remote data sources from a [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] application.</span></span>  
  
 [<span data-ttu-id="ab6e2-133">方法 : ClickOnce アプリケーションにデータ ファイルを含める</span><span class="sxs-lookup"><span data-stu-id="ab6e2-133">How to: Include a Data File in a ClickOnce Application</span></span>](/visualstudio/deployment/how-to-include-a-data-file-in-a-clickonce-application)  
 <span data-ttu-id="ab6e2-134">[!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] データ ディレクトリで利用できるファイルにマークする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ab6e2-134">Demonstrates how to mark a file so that it is available in the [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] data directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab6e2-135">参照</span><span class="sxs-lookup"><span data-stu-id="ab6e2-135">See Also</span></span>  
 [<span data-ttu-id="ab6e2-136">アプリケーション設定の概要</span><span class="sxs-lookup"><span data-stu-id="ab6e2-136">Application Settings Overview</span></span>](../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [<span data-ttu-id="ab6e2-137">ClickOnce アプリケーションの発行</span><span class="sxs-lookup"><span data-stu-id="ab6e2-137">Publishing ClickOnce Applications</span></span>](/visualstudio/deployment/publishing-clickonce-applications)  
 [<span data-ttu-id="ab6e2-138">ClickOnce アプリケーションのコマンド ラインからのビルド</span><span class="sxs-lookup"><span data-stu-id="ab6e2-138">Building ClickOnce Applications from the Command Line</span></span>](/visualstudio/deployment/building-clickonce-applications-from-the-command-line)  
 [<span data-ttu-id="ab6e2-139">System.Deployment.Application を使用する ClickOnce アプリケーションのデバッグ</span><span class="sxs-lookup"><span data-stu-id="ab6e2-139">Debugging ClickOnce Applications That Use System.Deployment.Application</span></span>](http://msdn.microsoft.com/library/86f31948-2ca8-47c0-8e8b-c2b817bbf79f)  
 [<span data-ttu-id="ab6e2-140">ClickOnce での COM コンポーネントの配置</span><span class="sxs-lookup"><span data-stu-id="ab6e2-140">Deploying COM Components with ClickOnce</span></span>](/visualstudio/deployment/deploying-com-components-with-clickonce)  
 [<span data-ttu-id="ab6e2-141">方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する</span><span class="sxs-lookup"><span data-stu-id="ab6e2-141">How to: Publish a ClickOnce Application using the Publish Wizard</span></span>](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)

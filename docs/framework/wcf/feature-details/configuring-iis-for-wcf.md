---
title: "Windows Communication Foundation での Internet Information Services 7.0 の構成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bd4bf1a97a544730714c46c1ba6f7f102166da35
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a><span data-ttu-id="1352f-102">Windows Communication Foundation での Internet Information Services 7.0 の構成</span><span class="sxs-lookup"><span data-stu-id="1352f-102">Configuring Internet Information Services 7.0 for Windows Communication Foundation</span></span>
<span data-ttu-id="1352f-103">Internet Information Services (IIS) 7.0 はモジュール設計になっており、必要なコンポーネントを選択してインストールできます。</span><span class="sxs-lookup"><span data-stu-id="1352f-103">Internet Information Services (IIS) 7.0 has a modular design that allows you to selectively install components that are required.</span></span> <span data-ttu-id="1352f-104">この設計は、[!INCLUDE[wv](../../../../includes/wv-md.md)] で新しく導入されたマニフェスト ドリブンのコンポーネント テクノロジに基づいています。</span><span class="sxs-lookup"><span data-stu-id="1352f-104">This design is based on the new manifest-driven componentization technology introduced in [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="1352f-105">[!INCLUDE[iisver](../../../../includes/iisver-md.md)] には、40 以上のスタンドアロン機能コンポーネントがあり、個別にインストールできます。</span><span class="sxs-lookup"><span data-stu-id="1352f-105">There are more than 40 standalone feature components of [!INCLUDE[iisver](../../../../includes/iisver-md.md)] that can be installed independently.</span></span> <span data-ttu-id="1352f-106">これにより、IT プロフェッショナルは必要に応じてインストールをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="1352f-106">This allows IT professionals to easily customize the installation as required.</span></span> <span data-ttu-id="1352f-107">このトピックでは、[!INCLUDE[iisver](../../../../includes/iisver-md.md)] で使用する [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を構成し、必要なコンポーネントを決定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1352f-107">This topic discusses how to configure [!INCLUDE[iisver](../../../../includes/iisver-md.md)] for use with [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and determine which components are required.</span></span>  
  
## <a name="minimal-installation-installing-was"></a><span data-ttu-id="1352f-108">最小インストール : WAS のインストール</span><span class="sxs-lookup"><span data-stu-id="1352f-108">Minimal Installation: Installing WAS</span></span>  
 <span data-ttu-id="1352f-109">完全な [!INCLUDE[iisver](../../../../includes/iisver-md.md)] パッケージの最小インストールでは、Windows プロセス アクティブ化サービス (WAS: Windows Process Activation Service) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="1352f-109">The minimal installation of the whole [!INCLUDE[iisver](../../../../includes/iisver-md.md)] package is to install the Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="1352f-110">WAS はスタンドアロン機能であり、すべての [!INCLUDE[iisver](../../../../includes/iisver-md.md)] オペレーティング システム (Home Basic、Home Premium、Business、Ultimate、および Enterprise) で利用できる唯一の [!INCLUDE[wv](../../../../includes/wv-md.md)] の機能です。</span><span class="sxs-lookup"><span data-stu-id="1352f-110">WAS is a standalone feature and it is the only feature from the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] that is available for all [!INCLUDE[wv](../../../../includes/wv-md.md)] operating systems (Home Basic, Home Premium, Business, and Ultimate and Enterprise).</span></span>  
  
 <span data-ttu-id="1352f-111">コントロール パネル からをクリックして**プログラム** をクリックし、 **Windows の機能のオンまたはオフ**の下に表示される**プログラムと機能**に WAS コンポーネントが表示、次の図のようにリストします。</span><span class="sxs-lookup"><span data-stu-id="1352f-111">From the Control Panel, click **Programs** and then click **Turn Windows features on or off** which is listed under **Programs and Features**, the WAS component is shown in the list as in the following illustration.</span></span>  
  
 <span data-ttu-id="1352f-112">![切り替える機能をオフ ダイアログ](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span><span class="sxs-lookup"><span data-stu-id="1352f-112">![Turn Features On or Off Dialog](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span></span>  
  
 <span data-ttu-id="1352f-113">この機能には、次のサブコンポーネントがあります。</span><span class="sxs-lookup"><span data-stu-id="1352f-113">This feature has the following sub-components:</span></span>  
  
-   <span data-ttu-id="1352f-114">.NET 環境</span><span class="sxs-lookup"><span data-stu-id="1352f-114">.NET Environment</span></span>  
  
-   <span data-ttu-id="1352f-115">構成 API</span><span class="sxs-lookup"><span data-stu-id="1352f-115">Configuration APIs</span></span>  
  
-   <span data-ttu-id="1352f-116">プロセス モデル</span><span class="sxs-lookup"><span data-stu-id="1352f-116">Process Model</span></span>  
  
 <span data-ttu-id="1352f-117">WAS のルート ノードのみを選択するかどうか、**プロセス モデル**サブ ノードは既定でオンにします。</span><span class="sxs-lookup"><span data-stu-id="1352f-117">If you select the root node of WAS, only the **Process Model** sub-node is checked by default.</span></span> <span data-ttu-id="1352f-118">このインストールでは Web サーバーをサポートしないため、WAS のみをインストールすることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1352f-118">Please note that with this installation you are only installing WAS, because there is no support for a Web server.</span></span>  
  
 <span data-ttu-id="1352f-119">させる[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]または any[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]するために、アプリケーションを確認して、 **.NET 環境**チェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="1352f-119">To make [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] or any [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application to work, check the **.NET Environment** checkbox.</span></span> <span data-ttu-id="1352f-120">つまり、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] および [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] を適切に機能させるには、すべての WAS コンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="1352f-120">This means that all of WAS components are required to make [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] to work well.</span></span> <span data-ttu-id="1352f-121">これらのコンポーネントのいずれかを一度インストールすると、チェック ボックスは自動的にオンになります。</span><span class="sxs-lookup"><span data-stu-id="1352f-121">These are automatically checked once you install any of those components.</span></span>  
  
## <a name="iis-70-default-installation"></a><span data-ttu-id="1352f-122">IIS 7.0 : 既定のインストール</span><span class="sxs-lookup"><span data-stu-id="1352f-122">IIS 7.0: Default Installation</span></span>  
 <span data-ttu-id="1352f-123">チェックして、**インターネット インフォメーション サービス**サブ ノードの一部の機能は、次の図に示すように自動的にチェックします。</span><span class="sxs-lookup"><span data-stu-id="1352f-123">By checking the **Internet Information Services** feature, some of the sub-nodes are automatically checked as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="1352f-124">![IIS 7.0 の機能の既定の設定](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span><span class="sxs-lookup"><span data-stu-id="1352f-124">![Default settings for IIS 7.0 features](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span></span>  
  
 <span data-ttu-id="1352f-125">これは [!INCLUDE[iisver](../../../../includes/iisver-md.md)] の既定のインストールです。</span><span class="sxs-lookup"><span data-stu-id="1352f-125">This is the default installation of [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span> <span data-ttu-id="1352f-126">このインストールにより、[!INCLUDE[iisver](../../../../includes/iisver-md.md)] を使用して静的コンテンツ (HTML ページなど) を提供できます。</span><span class="sxs-lookup"><span data-stu-id="1352f-126">With this installation, you can use [!INCLUDE[iisver](../../../../includes/iisver-md.md)] to service static content (such as HTML pages and other content).</span></span> <span data-ttu-id="1352f-127">ただし、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] や CGI アプリケーションを実行したり、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスをホストしたりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="1352f-127">However, you cannot run [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] or CGI applications or host [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services.</span></span>  
  
## <a name="iis-70-installation-with-aspnet-support"></a><span data-ttu-id="1352f-128">IIS 7.0 : ASP.NET サポートを行うインストール</span><span class="sxs-lookup"><span data-stu-id="1352f-128">IIS 7.0: Installation with ASP.NET Support</span></span>  
 <span data-ttu-id="1352f-129">IIS 7.0 で [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] を機能させるには [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1352f-129">You must install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] to make [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] work on IIS 7.0.</span></span> <span data-ttu-id="1352f-130">チェックした後**ASP.NET**画面に、次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="1352f-130">After checking **ASP.NET**, your screen should look like the following illustration.</span></span>  
  
 <span data-ttu-id="1352f-131">![Asp.NET の設定に必要な](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span><span class="sxs-lookup"><span data-stu-id="1352f-131">![Asp.NET required settings](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span></span>  
  
 <span data-ttu-id="1352f-132">これは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションと [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーションの両方が [!INCLUDE[iisver](../../../../includes/iisver-md.md)] で機能するための最小限の環境です。</span><span class="sxs-lookup"><span data-stu-id="1352f-132">This is the minimal environment for both [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] applications to work in [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span>  
  
## <a name="iis-70-installation-with-iis-60-compatibility-components"></a><span data-ttu-id="1352f-133">IIS 7.0 : IIS 6.0 互換コンポーネントを備えたインストール</span><span class="sxs-lookup"><span data-stu-id="1352f-133">IIS 7.0: Installation with IIS 6.0 Compatibility Components</span></span>  
 <span data-ttu-id="1352f-134">インストールするときに[!INCLUDE[iisver](../../../../includes/iisver-md.md)]Visual Studio 2005 または他の自動化スクリプトまたはを使用した仮想アプリケーションを構成する (Adsutil.vbs) などのツールがシステムの[!INCLUDE[iis601](../../../../includes/iis601-md.md)]メタベース API では、確認することを確認してください、 [!INCLUDE[iis601](../../../../includes/iis601-md.md)]  **。スクリプト ツール**です。</span><span class="sxs-lookup"><span data-stu-id="1352f-134">When installing [!INCLUDE[iisver](../../../../includes/iisver-md.md)] on a system with Visual Studio 2005 or some other automation scripts or tools (such as Adsutil.vbs) that configure virtual applications that use [!INCLUDE[iis601](../../../../includes/iis601-md.md)] Metabase API, ensure that you check the [!INCLUDE[iis601](../../../../includes/iis601-md.md)]**Scripting Tools**.</span></span> <span data-ttu-id="1352f-135">他のサブ ノードを自動的に確認[!INCLUDE[iis601](../../../../includes/iis601-md.md)]**互換性のある管理**です。</span><span class="sxs-lookup"><span data-stu-id="1352f-135">This automatically checks the other sub-nodes of [!INCLUDE[iis601](../../../../includes/iis601-md.md)]**Management Compatibility**.</span></span> <span data-ttu-id="1352f-136">実行後の画面を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="1352f-136">The following illustration shows the screen after this is done.</span></span>  
  
 <span data-ttu-id="1352f-137">![IIS 6.0 管理互換の設定](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span><span class="sxs-lookup"><span data-stu-id="1352f-137">![IIS 6.0 Management Compatibility Settings](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span></span>  
  
 <span data-ttu-id="1352f-138">このインストールにより、[!INCLUDE[iisver](../../../../includes/iisver-md.md)]、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]、および [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 機能を使用するために必要な準備ができ、Web でサンプルを利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1352f-138">With this installation, you have everything required to use [!INCLUDE[iisver](../../../../includes/iisver-md.md)], [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] features and samples available on the Web.</span></span>  
  
## <a name="request-limits"></a><span data-ttu-id="1352f-139">要求の制限</span><span class="sxs-lookup"><span data-stu-id="1352f-139">Request Limits</span></span>  
 <span data-ttu-id="1352f-140">IIS 7.0 がインストールされた [!INCLUDE[wv](../../../../includes/wv-md.md)] では、`maxUri` および `maxQueryStringSize` の設定の既定値が変更されています。</span><span class="sxs-lookup"><span data-stu-id="1352f-140">On [!INCLUDE[wv](../../../../includes/wv-md.md)] with IIS 7 the default value of the `maxUri` and `maxQueryStringSize` settings have been changed.</span></span> <span data-ttu-id="1352f-141">既定では、IIS 7.0 における要求のフィルター処理で使用できる文字数は、URL が 4096 文字、クエリ文字列が 2048 文字です。</span><span class="sxs-lookup"><span data-stu-id="1352f-141">By default, request filtering in IIS 7.0 allows a URL length of 4096 characters and a query string length of 2048 characters.</span></span> <span data-ttu-id="1352f-142">これらの既定値を変更するには、App.config ファイルに次の XML を追加します。</span><span class="sxs-lookup"><span data-stu-id="1352f-142">To change these defaults add the following XML to your App.config file.</span></span>  
  
 `<system.webServer>`  
  
 `<security>`  
  
 `<requestFiltering>`  
  
 `<requestLimits maxUrl="8192" maxQueryString="8192" />`  
  
 `</requestFiltering>`  
  
 `</security>`  
  
 `</system.webServer>`  
  
## <a name="see-also"></a><span data-ttu-id="1352f-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="1352f-143">See Also</span></span>  
 [<span data-ttu-id="1352f-144">WAS アクティベーション アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="1352f-144">WAS Activation Architecture</span></span>](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)  
 [<span data-ttu-id="1352f-145">WCF で使用するため、WAS を構成します。</span><span class="sxs-lookup"><span data-stu-id="1352f-145">Configuring WAS for Use with WCF</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)  
 [<span data-ttu-id="1352f-146">方法: インストールして WCF アクティブ化コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="1352f-146">How to: Install and Configure WCF Activation Components</span></span>](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)  
 [<span data-ttu-id="1352f-147">Windows Server App Fabric のホスティング機能</span><span class="sxs-lookup"><span data-stu-id="1352f-147">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)

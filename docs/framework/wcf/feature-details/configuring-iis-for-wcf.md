---
title: Windows Communication Foundation での Internet Information Services 7.0 の構成
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: 3e34f46fbf3ccf12c6a89a7cac96143965d958d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491717"
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a><span data-ttu-id="0b3b1-102">Windows Communication Foundation での Internet Information Services 7.0 の構成</span><span class="sxs-lookup"><span data-stu-id="0b3b1-102">Configuring Internet Information Services 7.0 for Windows Communication Foundation</span></span>
<span data-ttu-id="0b3b1-103">Internet Information Services (IIS) 7.0 はモジュール設計になっており、必要なコンポーネントを選択してインストールできます。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-103">Internet Information Services (IIS) 7.0 has a modular design that allows you to selectively install components that are required.</span></span> <span data-ttu-id="0b3b1-104">この設計は、[!INCLUDE[wv](../../../../includes/wv-md.md)] で新しく導入されたマニフェスト ドリブンのコンポーネント テクノロジに基づいています。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-104">This design is based on the new manifest-driven componentization technology introduced in [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="0b3b1-105">[!INCLUDE[iisver](../../../../includes/iisver-md.md)] には、40 以上のスタンドアロン機能コンポーネントがあり、個別にインストールできます。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-105">There are more than 40 standalone feature components of [!INCLUDE[iisver](../../../../includes/iisver-md.md)] that can be installed independently.</span></span> <span data-ttu-id="0b3b1-106">これにより、IT プロフェッショナルは必要に応じてインストールをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-106">This allows IT professionals to easily customize the installation as required.</span></span> <span data-ttu-id="0b3b1-107">このトピックで構成する方法について説明します[!INCLUDE[iisver](../../../../includes/iisver-md.md)]の Windows Communication Foundation (WCF) を使用し、必要なコンポーネントを決定します。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-107">This topic discusses how to configure [!INCLUDE[iisver](../../../../includes/iisver-md.md)] for use with Windows Communication Foundation (WCF) and determine which components are required.</span></span>  
  
## <a name="minimal-installation-installing-was"></a><span data-ttu-id="0b3b1-108">最小インストール : WAS のインストール</span><span class="sxs-lookup"><span data-stu-id="0b3b1-108">Minimal Installation: Installing WAS</span></span>  
 <span data-ttu-id="0b3b1-109">完全な [!INCLUDE[iisver](../../../../includes/iisver-md.md)] パッケージの最小インストールでは、Windows プロセス アクティブ化サービス (WAS: Windows Process Activation Service) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-109">The minimal installation of the whole [!INCLUDE[iisver](../../../../includes/iisver-md.md)] package is to install the Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="0b3b1-110">WAS はスタンドアロン機能であり、すべての [!INCLUDE[iisver](../../../../includes/iisver-md.md)] オペレーティング システム (Home Basic、Home Premium、Business、Ultimate、および Enterprise) で利用できる唯一の [!INCLUDE[wv](../../../../includes/wv-md.md)] の機能です。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-110">WAS is a standalone feature and it is the only feature from the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] that is available for all [!INCLUDE[wv](../../../../includes/wv-md.md)] operating systems (Home Basic, Home Premium, Business, and Ultimate and Enterprise).</span></span>  
  
 <span data-ttu-id="0b3b1-111">コントロール パネル からをクリックして**プログラム** をクリックし、 **Windows の機能のオンまたはオフ**の下に表示される**プログラムと機能**に WAS コンポーネントが表示、次の図のようにリストします。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-111">From the Control Panel, click **Programs** and then click **Turn Windows features on or off** which is listed under **Programs and Features**, the WAS component is shown in the list as in the following illustration.</span></span>  
  
 <span data-ttu-id="0b3b1-112">![切り替える機能をオフ ダイアログ](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span><span class="sxs-lookup"><span data-stu-id="0b3b1-112">![Turn Features On or Off Dialog](../../../../docs/framework/wcf/feature-details/media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span></span>  
  
 <span data-ttu-id="0b3b1-113">この機能には、次のサブコンポーネントがあります。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-113">This feature has the following sub-components:</span></span>  
  
-   <span data-ttu-id="0b3b1-114">.NET 環境</span><span class="sxs-lookup"><span data-stu-id="0b3b1-114">.NET Environment</span></span>  
  
-   <span data-ttu-id="0b3b1-115">構成 API</span><span class="sxs-lookup"><span data-stu-id="0b3b1-115">Configuration APIs</span></span>  
  
-   <span data-ttu-id="0b3b1-116">プロセス モデル</span><span class="sxs-lookup"><span data-stu-id="0b3b1-116">Process Model</span></span>  
  
 <span data-ttu-id="0b3b1-117">WAS のルート ノードのみを選択するかどうか、**プロセス モデル**サブ ノードは既定でオンにします。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-117">If you select the root node of WAS, only the **Process Model** sub-node is checked by default.</span></span> <span data-ttu-id="0b3b1-118">このインストールでは Web サーバーをサポートしないため、WAS のみをインストールすることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-118">Please note that with this installation you are only installing WAS, because there is no support for a Web server.</span></span>  
  
 <span data-ttu-id="0b3b1-119">WCF またはいずれかに[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]するために、アプリケーションを確認して、 **.NET 環境**チェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-119">To make WCF or any [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application to work, check the **.NET Environment** checkbox.</span></span> <span data-ttu-id="0b3b1-120">つまり、すべての WAS コンポーネントは WCF のために必要と[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]を適切に機能します。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-120">This means that all of WAS components are required to make WCF and [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] to work well.</span></span> <span data-ttu-id="0b3b1-121">これらのコンポーネントのいずれかを一度インストールすると、チェック ボックスは自動的にオンになります。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-121">These are automatically checked once you install any of those components.</span></span>  
  
## <a name="iis-70-default-installation"></a><span data-ttu-id="0b3b1-122">IIS 7.0 : 既定のインストール</span><span class="sxs-lookup"><span data-stu-id="0b3b1-122">IIS 7.0: Default Installation</span></span>  
 <span data-ttu-id="0b3b1-123">チェックして、**インターネット インフォメーション サービス**サブ ノードの一部の機能は、次の図に示すように自動的にチェックします。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-123">By checking the **Internet Information Services** feature, some of the sub-nodes are automatically checked as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="0b3b1-124">![IIS 7.0 の機能の既定の設定](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span><span class="sxs-lookup"><span data-stu-id="0b3b1-124">![Default settings for IIS 7.0 features](../../../../docs/framework/wcf/feature-details/media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span></span>  
  
 <span data-ttu-id="0b3b1-125">これは [!INCLUDE[iisver](../../../../includes/iisver-md.md)] の既定のインストールです。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-125">This is the default installation of [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span> <span data-ttu-id="0b3b1-126">このインストールにより、[!INCLUDE[iisver](../../../../includes/iisver-md.md)] を使用して静的コンテンツ (HTML ページなど) を提供できます。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-126">With this installation, you can use [!INCLUDE[iisver](../../../../includes/iisver-md.md)] to service static content (such as HTML pages and other content).</span></span> <span data-ttu-id="0b3b1-127">ただし、実行することはできません[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]または CGI アプリケーションまたは WCF サービスをホストします。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-127">However, you cannot run [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] or CGI applications or host WCF services.</span></span>  
  
## <a name="iis-70-installation-with-aspnet-support"></a><span data-ttu-id="0b3b1-128">IIS 7.0 : ASP.NET サポートを行うインストール</span><span class="sxs-lookup"><span data-stu-id="0b3b1-128">IIS 7.0: Installation with ASP.NET Support</span></span>  
 <span data-ttu-id="0b3b1-129">IIS 7.0 で [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] を機能させるには [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-129">You must install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] to make [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] work on IIS 7.0.</span></span> <span data-ttu-id="0b3b1-130">チェックした後**ASP.NET**画面に、次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-130">After checking **ASP.NET**, your screen should look like the following illustration.</span></span>  
  
 <span data-ttu-id="0b3b1-131">![Asp.NET の設定に必要な](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span><span class="sxs-lookup"><span data-stu-id="0b3b1-131">![Asp.NET required settings](../../../../docs/framework/wcf/feature-details/media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span></span>  
  
 <span data-ttu-id="0b3b1-132">これは、両方の WCF の最低限の環境と[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]で動作するアプリケーション[!INCLUDE[iisver](../../../../includes/iisver-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-132">This is the minimal environment for both WCF and [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] applications to work in [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span>  
  
## <a name="iis-70-installation-with-iis-60-compatibility-components"></a><span data-ttu-id="0b3b1-133">IIS 7.0 : IIS 6.0 互換コンポーネントを備えたインストール</span><span class="sxs-lookup"><span data-stu-id="0b3b1-133">IIS 7.0: Installation with IIS 6.0 Compatibility Components</span></span>  
 <span data-ttu-id="0b3b1-134">インストールするときに[!INCLUDE[iisver](../../../../includes/iisver-md.md)]Visual Studio 2005 または他の自動化スクリプトまたはを使用した仮想アプリケーションを構成する (Adsutil.vbs) などのツールがシステムの[!INCLUDE[iis601](../../../../includes/iis601-md.md)]メタベース API では、確認することを確認してください、 [!INCLUDE[iis601](../../../../includes/iis601-md.md)]  **。スクリプト ツール**です。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-134">When installing [!INCLUDE[iisver](../../../../includes/iisver-md.md)] on a system with Visual Studio 2005 or some other automation scripts or tools (such as Adsutil.vbs) that configure virtual applications that use [!INCLUDE[iis601](../../../../includes/iis601-md.md)] Metabase API, ensure that you check the [!INCLUDE[iis601](../../../../includes/iis601-md.md)]**Scripting Tools**.</span></span> <span data-ttu-id="0b3b1-135">他のサブ ノードを自動的に確認[!INCLUDE[iis601](../../../../includes/iis601-md.md)]**互換性のある管理**です。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-135">This automatically checks the other sub-nodes of [!INCLUDE[iis601](../../../../includes/iis601-md.md)]**Management Compatibility**.</span></span> <span data-ttu-id="0b3b1-136">実行後の画面を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-136">The following illustration shows the screen after this is done.</span></span>  
  
 <span data-ttu-id="0b3b1-137">![IIS 6.0 管理互換の設定](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span><span class="sxs-lookup"><span data-stu-id="0b3b1-137">![IIS 6.0 Management Compatibility Settings](../../../../docs/framework/wcf/feature-details/media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span></span>  
  
 <span data-ttu-id="0b3b1-138">このインストールがあるを使用するために必要なすべて[!INCLUDE[iisver](../../../../includes/iisver-md.md)]、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]および WCF の機能とサンプルは、Web でご確認いただけます。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-138">With this installation, you have everything required to use [!INCLUDE[iisver](../../../../includes/iisver-md.md)], [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] and WCF features and samples available on the Web.</span></span>  
  
## <a name="request-limits"></a><span data-ttu-id="0b3b1-139">要求の制限</span><span class="sxs-lookup"><span data-stu-id="0b3b1-139">Request Limits</span></span>  
 <span data-ttu-id="0b3b1-140">IIS 7.0 がインストールされた [!INCLUDE[wv](../../../../includes/wv-md.md)] では、`maxUri` および `maxQueryStringSize` の設定の既定値が変更されています。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-140">On [!INCLUDE[wv](../../../../includes/wv-md.md)] with IIS 7 the default value of the `maxUri` and `maxQueryStringSize` settings have been changed.</span></span> <span data-ttu-id="0b3b1-141">既定では、IIS 7.0 における要求のフィルター処理で使用できる文字数は、URL が 4096 文字、クエリ文字列が 2048 文字です。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-141">By default, request filtering in IIS 7.0 allows a URL length of 4096 characters and a query string length of 2048 characters.</span></span> <span data-ttu-id="0b3b1-142">これらの既定値を変更するには、App.config ファイルに次の XML を追加します。</span><span class="sxs-lookup"><span data-stu-id="0b3b1-142">To change these defaults add the following XML to your App.config file.</span></span>  
  
 `<system.webServer>`  
  
 `<security>`  
  
 `<requestFiltering>`  
  
 `<requestLimits maxUrl="8192" maxQueryString="8192" />`  
  
 `</requestFiltering>`  
  
 `</security>`  
  
 `</system.webServer>`  
  
## <a name="see-also"></a><span data-ttu-id="0b3b1-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b3b1-143">See Also</span></span>  
 [<span data-ttu-id="0b3b1-144">WAS アクティベーション アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="0b3b1-144">WAS Activation Architecture</span></span>](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)  
 [<span data-ttu-id="0b3b1-145">WCF で使用するための WAS を設定する</span><span class="sxs-lookup"><span data-stu-id="0b3b1-145">Configuring WAS for Use with WCF</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)  
 [<span data-ttu-id="0b3b1-146">方法 : WCF アクティブ化コンポーネントをインストールして設定する</span><span class="sxs-lookup"><span data-stu-id="0b3b1-146">How to: Install and Configure WCF Activation Components</span></span>](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)  
 [<span data-ttu-id="0b3b1-147">Windows Server App Fabric のホスティング機能</span><span class="sxs-lookup"><span data-stu-id="0b3b1-147">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)

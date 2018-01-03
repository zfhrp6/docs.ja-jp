---
title: "発行者名レジストリの検証パッケージのダウンロード"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
caps.latest.revision: "3"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bf6869de939ed7eda7cd3de868e712126f71751
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="downloading-the-validating-issuer-name-registry-package"></a><span data-ttu-id="46528-102">発行者名レジストリの検証パッケージのダウンロード</span><span class="sxs-lookup"><span data-stu-id="46528-102">Downloading the Validating Issuer Name Registry Package</span></span>
<span data-ttu-id="46528-103">このトピックでは、Validating Issuer Name Registry (VINR) をダウンロードしてプロジェクトで使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="46528-103">This topic discusses how to download and use the Validating Issuer Name Registry (VINR) in your project.</span></span>  
  
## <a name="downloading-the-validating-issuer-name-registry"></a><span data-ttu-id="46528-104">Validating Issuer Name Registry のダウンロード</span><span class="sxs-lookup"><span data-stu-id="46528-104">Downloading the Validating Issuer Name Registry</span></span>  
 <span data-ttu-id="46528-105">VINR は、プロジェクトに必要なアセンブリと参照を追加する NuGet パッケージとして入手できます。</span><span class="sxs-lookup"><span data-stu-id="46528-105">The VINR is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="46528-106">まだ NuGet がインストールされていない場合は、[nuget.org](http://nuget.org) にアクセスしてインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="46528-106">If you do not already have NuGet installed, go to [nuget.org](http://nuget.org) to install it.</span></span> <span data-ttu-id="46528-107">NuGet の「[Microsoft Validating Issuer Name Registry](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)」ページにアクセスすると、拡張機能のバージョン履歴を参照できます。</span><span class="sxs-lookup"><span data-stu-id="46528-107">You can see the versioning history for the extension by visiting its page on NuGet: [Microsoft Validating Issuer Name Registry on NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)</span></span>  
  
#### <a name="downloading-the-validating-issuer-name-registry-by-using-the-package-manager-gui"></a><span data-ttu-id="46528-108">パッケージ マネージャーの GUI を使用した Validating Issuer Name Registry のダウンロード</span><span class="sxs-lookup"><span data-stu-id="46528-108">Downloading the Validating Issuer Name Registry by using the Package Manager GUI</span></span>  
  
1.  <span data-ttu-id="46528-109">Visual Studio の**ソリューション エクスプローラー**でプロジェクトを右クリックし、**[NuGet パッケージの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="46528-109">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>  
  
2.  <span data-ttu-id="46528-110">**[NuGet パッケージの管理]** ウィンドウで、検索ボックスをクリックし、「`ValidatingIssuerNameRegistry`」と入力して **Enter** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="46528-110">In the **Manage NuGet Packages** window, click the search box and enter `ValidatingIssuerNameRegistry` and press **Enter**.</span></span>  
  
3.  <span data-ttu-id="46528-111">結果ペインから、最初の結果の **[インストール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46528-111">From the results pane, click the **Install** button for the first result.</span></span>  
  
4.  <span data-ttu-id="46528-112">パッケージのダウンロードが開始されます。</span><span class="sxs-lookup"><span data-stu-id="46528-112">The package will begin downloading.</span></span> <span data-ttu-id="46528-113">プロジェクトに追加される前に、[License Acceptance] ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="46528-113">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="46528-114">ライセンス条項に同意する場合は、**[I Accept]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46528-114">If you agree to the license terms, click **I Accept**.</span></span>  
  
5.  <span data-ttu-id="46528-115">最新の VINR アセンブリがダウンロードされ、プロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="46528-115">The latest VINR assemblies will be downloaded and added to your project.</span></span>  
  
#### <a name="downloading-the-validating-issuer-name-registry-by-using-the-package-manager-console"></a><span data-ttu-id="46528-116">パッケージ マネージャー コンソールを使用した Validating Issuer Name Registry のダウンロード</span><span class="sxs-lookup"><span data-stu-id="46528-116">Downloading the Validating Issuer Name Registry by using the Package Manager Console</span></span>  
  
1.  <span data-ttu-id="46528-117">Visual Studio で、**[ツール]**、**[ライブラリ パッケージ マネージャー]**、**[パッケージ マネージャー コンソール]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="46528-117">In Visual Studio, click **Tools**, **Library Package Manager**, and then **Package Manager Console**.</span></span>  
  
2.  <span data-ttu-id="46528-118">**[パッケージ マネージャー コンソール]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="46528-118">The **Package Manager Console** appears.</span></span> <span data-ttu-id="46528-119">次のテキストを入力し、**Enter** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="46528-119">Enter the following text and press **Enter**:</span></span>  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry  
    ```  
  
3.  <span data-ttu-id="46528-120">最新の VINR アセンブリがダウンロードされ、プロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="46528-120">The latest VINR assemblies will be downloaded and added to your project.</span></span>

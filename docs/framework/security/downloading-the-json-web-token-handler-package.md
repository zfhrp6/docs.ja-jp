---
title: JSON Web トークン ハンドラー パッケージのダウンロード
ms.date: 03/30/2017
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
ms.openlocfilehash: 5a4846a5ec92324105f41b320d0d77f8749c28f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404678"
---
# <a name="downloading-the-json-web-token-handler-package"></a><span data-ttu-id="d3c30-102">JSON Web トークン ハンドラー パッケージのダウンロード</span><span class="sxs-lookup"><span data-stu-id="d3c30-102">Downloading the JSON Web Token Handler Package</span></span>
<span data-ttu-id="d3c30-103">このトピックでは、JSON Web トークン ハンドラーをダウンロードしてプロジェクトで使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3c30-103">This topic discusses how to download and use the JSON Web Token Handler in your project.</span></span>  
  
## <a name="downloading-the-json-web-token-handler"></a><span data-ttu-id="d3c30-104">JSON Web トークン ハンドラーのダウンロード</span><span class="sxs-lookup"><span data-stu-id="d3c30-104">Downloading the JSON Web Token Handler</span></span>  
 <span data-ttu-id="d3c30-105">JSON Web トークン ハンドラー拡張機能は、プロジェクトに必要なアセンブリと参照を追加する NuGet パッケージとして入手できます。</span><span class="sxs-lookup"><span data-stu-id="d3c30-105">The JSON Web Token Handler extension is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="d3c30-106">まだ NuGet がインストールされていない場合は、[nuget.org](http://nuget.org) にアクセスしてインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="d3c30-106">If you do not already have NuGet installed, go to [nuget.org](http://nuget.org) to install it.</span></span> <span data-ttu-id="d3c30-107">NuGet の「[JSON Web Token Handler](http://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)」 (JSON Web トークン ハンドラー) ページにアクセスすると、拡張機能のバージョン履歴を参照できます。</span><span class="sxs-lookup"><span data-stu-id="d3c30-107">You can see the versioning history for the extension by visiting its page on NuGet: [JSON Web Token Handler on NuGet](http://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span></span>  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-gui"></a><span data-ttu-id="d3c30-108">パッケージ マネージャーの GUI を使用した JSON Web トークン ハンドラーのダウンロード</span><span class="sxs-lookup"><span data-stu-id="d3c30-108">Downloading the JSON Web Token Handler by using the Package Manager GUI</span></span>  
  
1.  <span data-ttu-id="d3c30-109">Visual Studio の**ソリューション エクスプローラー**でプロジェクトを右クリックし、**[NuGet パッケージの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d3c30-109">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>  
  
2.  <span data-ttu-id="d3c30-110">**[NuGet パッケージの管理]** ウィンドウで、検索ボックスをクリックし、「`JWT Token Handler`」と入力して **Enter** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="d3c30-110">In the **Manage NuGet Packages** window, click the search box and enter `JWT Token Handler` and press **Enter**.</span></span>  
  
3.  <span data-ttu-id="d3c30-111">結果ペインから、最初の結果の **[インストール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3c30-111">From the results pane, click the **Install** button for the first result.</span></span>  
  
4.  <span data-ttu-id="d3c30-112">パッケージのダウンロードが開始されます。</span><span class="sxs-lookup"><span data-stu-id="d3c30-112">The package will begin downloading.</span></span> <span data-ttu-id="d3c30-113">プロジェクトに追加される前に、[License Acceptance] ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3c30-113">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="d3c30-114">ライセンス条項に同意する場合は、**[I Accept]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3c30-114">If you agree to the license terms, click **I Accept**.</span></span>  
  
5.  <span data-ttu-id="d3c30-115">最新の JSON Web トークン ハンドラー アセンブリがダウンロードされ、プロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="d3c30-115">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-console"></a><span data-ttu-id="d3c30-116">パッケージ マネージャー コンソールを使用した JSON Web トークン ハンドラーのダウンロード</span><span class="sxs-lookup"><span data-stu-id="d3c30-116">Downloading the JSON Web Token Handler by using the Package Manager Console</span></span>  
  
1.  <span data-ttu-id="d3c30-117">Visual Studio で、**[ツール]**、**[ライブラリ パッケージ マネージャー]**、**[パッケージ マネージャー コンソール]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3c30-117">In Visual Studio, click **Tools**, **Library Package Manager**, and then **Package Manager Console**.</span></span>  
  
2.  <span data-ttu-id="d3c30-118">**[パッケージ マネージャー コンソール]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3c30-118">The **Package Manager Console** appears.</span></span> <span data-ttu-id="d3c30-119">次のテキストを入力し、**Enter** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="d3c30-119">Enter the following text and press **Enter**:</span></span>  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.Jwt  
    ```  
  
3.  <span data-ttu-id="d3c30-120">最新の JSON Web トークン ハンドラー アセンブリがダウンロードされ、プロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="d3c30-120">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>

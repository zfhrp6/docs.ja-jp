---
title: '方法 : COM+ 統合アプリケーションを展開する'
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: 872d0f0c84c1ac0ea96a87ed24a386bb9bedcf85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490140"
---
# <a name="how-to-deploy-a-com-integration-application"></a><span data-ttu-id="be2b6-102">方法 : COM+ 統合アプリケーションを展開する</span><span class="sxs-lookup"><span data-stu-id="be2b6-102">How to: Deploy a COM+ Integration Application</span></span>
<span data-ttu-id="be2b6-103">COM+ 統合アプリケーションを作成した後、これを別のコンピューターに展開する必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="be2b6-103">Once you have written a COM+ integration application, you may want to deploy it on another machine.</span></span> <span data-ttu-id="be2b6-104">ここでは、COM+ 統合アプリケーションをコンピューター間で移動する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="be2b6-104">This topic describes how to move a COM+ integration application from one machine to another.</span></span>  
  
### <a name="moving-a-com-hosted-integration-app"></a><span data-ttu-id="be2b6-105">COM+ ホスト統合アプリケーションの移動</span><span class="sxs-lookup"><span data-stu-id="be2b6-105">Moving a COM+ hosted Integration App</span></span>  
  
1.  <span data-ttu-id="be2b6-106">WCF が両方のコンピューターにインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="be2b6-106">Ensure that WCF is installed on both machines.</span></span>  
  
2.  <span data-ttu-id="be2b6-107">コンピューター A からアプリケーションをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="be2b6-107">Export the application from machine A.</span></span>  
  
3.  <span data-ttu-id="be2b6-108">コンピューター B にアプリケーションをインポートします。</span><span class="sxs-lookup"><span data-stu-id="be2b6-108">Import the application on machine B.</span></span>  
  
4.  <span data-ttu-id="be2b6-109">アプリケーション ルート ディレクトリを設定します。</span><span class="sxs-lookup"><span data-stu-id="be2b6-109">Set the Application Root Directory.</span></span> <span data-ttu-id="be2b6-110">通常これは %PROGRAMFILES%/ComPlus Applications/{AppGUID} になります。</span><span class="sxs-lookup"><span data-stu-id="be2b6-110">By convention, this is %PROGRAMFILES%/ComPlus Applications/{AppGUID}.</span></span>  
  
5.  <span data-ttu-id="be2b6-111">コンピューター A のアプリケーション ルート ディレクトリにある Application.config ファイルおよび Application.manifest ファイルを、コンピューター B のアプリケーション ルート ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="be2b6-111">Copy the Application.config and Application.manifest files from the application root directory on machine A to the application root directory on machine B.</span></span>  
  
6.  <span data-ttu-id="be2b6-112">コンピューター B の Application.config ファイルのサービス エンドポイント アドレスを編集して、コンピューター B が識別されるようにします。</span><span class="sxs-lookup"><span data-stu-id="be2b6-112">Edit the service endpoint addresses in the Application.config file on machine B to identify the appropriate machine.</span></span> <span data-ttu-id="be2b6-113">たとえば、http://machineA/MyService を http://machineB/MyService に変更します。</span><span class="sxs-lookup"><span data-stu-id="be2b6-113">For example, change http://machineA/MyService to http://machineB/MyService.</span></span>  
  
### <a name="moving-a-web-hosted-integration-application"></a><span data-ttu-id="be2b6-114">Web ホスト統合アプリケーションの移動</span><span class="sxs-lookup"><span data-stu-id="be2b6-114">Moving a Web-hosted integration application</span></span>  
  
1.  <span data-ttu-id="be2b6-115">WCF が両方のコンピューターにインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="be2b6-115">Ensure that WCF is installed on both machines.</span></span>  
  
2.  <span data-ttu-id="be2b6-116">コンピューター A からアプリケーションをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="be2b6-116">Export the application from machine A.</span></span>  
  
3.  <span data-ttu-id="be2b6-117">コンピューター B にアプリケーションをインポートします。</span><span class="sxs-lookup"><span data-stu-id="be2b6-117">Import the application on machine B.</span></span>  
  
4.  <span data-ttu-id="be2b6-118">コンピューター B で IIS vroot を作成します。</span><span class="sxs-lookup"><span data-stu-id="be2b6-118">Create an IIS vroot on machine B.</span></span>  
  
5.  <span data-ttu-id="be2b6-119">コンピューター A の vroot にある .svc ファイル (componentName.svc) と Web.config ファイルを、コンピューター B で新しく作成した vroot にコピーします。</span><span class="sxs-lookup"><span data-stu-id="be2b6-119">Copy the .svc file (componentName.svc) and the Web.config file from the vroot on machine A to the newly created vroot on machine B.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be2b6-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="be2b6-120">See Also</span></span>  
 [<span data-ttu-id="be2b6-121">COM+ アプリケーションとの統合の概要</span><span class="sxs-lookup"><span data-stu-id="be2b6-121">Integrating with COM+ Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)  
 [<span data-ttu-id="be2b6-122">方法 : COM+ サービス設定を構成する</span><span class="sxs-lookup"><span data-stu-id="be2b6-122">How to: Configure COM+ Service Settings</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)  
 [<span data-ttu-id="be2b6-123">方法 : COM+ サービス モデル構成ツールを使用する</span><span class="sxs-lookup"><span data-stu-id="be2b6-123">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)

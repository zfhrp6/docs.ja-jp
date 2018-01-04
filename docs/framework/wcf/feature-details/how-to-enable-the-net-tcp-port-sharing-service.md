---
title: "方法 : Net.TCP ポート共有サービスを有効にする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b9f1c57f067fa7c8bece3acaf0d51303b31d13bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a><span data-ttu-id="ec645-102">方法 : Net.TCP ポート共有サービスを有効にする</span><span class="sxs-lookup"><span data-stu-id="ec645-102">How to: Enable the Net.TCP Port Sharing Service</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="ec645-103"> は NET.TCP ポート共有サービスと呼ばれる Windows サービスを使用し、複数のプロセス間での TCP ポート共有を実現します。</span><span class="sxs-lookup"><span data-stu-id="ec645-103"> uses a Windows service called the Net.TCP Port Sharing Service to facilitate the sharing of TCP ports across multiple processes.</span></span> <span data-ttu-id="ec645-104">このサービスは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の一部としてインストールされますが、セキュリティ予防措置としてデフォルトでは有効になっていません。したがって、初めて使用する前に手動で有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec645-104">This service is installed as part of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], but the service is not enabled by default as a security precaution and so must be manually enabled prior to first use.</span></span> <span data-ttu-id="ec645-105">このトピックでは、Microsoft 管理コンソール (MMC) スナップインを使用して、Net TCP ポート共有サービスを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec645-105">This topic describes how to configure the Net TCP Port Sharing Service using the Microsoft Management Console (MMC) snap-In.</span></span>  
  
 <span data-ttu-id="ec645-106">Net.TCP ポート共有サービスを有効にするし、手動で起動するを参照してください。[する方法: ポート共有を使用する WCF サービスを構成する](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md)このサービスを使用するようにサービスを構成する方法についてはします。</span><span class="sxs-lookup"><span data-stu-id="ec645-106">After you enable the Net.TCP Port Sharing Service and start it manually, see [How to: Configure a WCF Service to Use Port Sharing](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) for information about how to configure your service to use this service.</span></span>  
  
 <span data-ttu-id="ec645-107">Net.tcp:// ポート共有を使用するサンプルについては、次を参照してください。、 [Net.TCP ポート共有のサンプル](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md)です。</span><span class="sxs-lookup"><span data-stu-id="ec645-107">For a sample that uses net.tcp:// port sharing, see the [Net.TCP Port Sharing Sample](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).</span></span>  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a><span data-ttu-id="ec645-108">MMC を使用して Net.TCP ポート共有サービスを有効にするには</span><span class="sxs-lookup"><span data-stu-id="ec645-108">To enable the Net.TCP Port Sharing Service using MMC</span></span>  
  
1.  <span data-ttu-id="ec645-109">[スタート] メニューから、コマンド プロンプト ウィンドウを開き、入力のいずれかのサービス管理コンソールを開きます`services.msc`または実行を開くと入力して`services.msc`ボックスにします。</span><span class="sxs-lookup"><span data-stu-id="ec645-109">From the Start menu, open the Services Management Console either by opening a Command Prompt window and typing `services.msc` or by opening Run and typing `services.msc` into the Open box.</span></span>  
  
2.  <span data-ttu-id="ec645-110">**名前**、サービスの一覧の列を右クリックし、 **Net.Tcp Port Sharing Service**を選択し、**プロパティ** メニューからです。</span><span class="sxs-lookup"><span data-stu-id="ec645-110">In the **Name** column of the list of services, right-click the **Net.Tcp Port Sharing Service**, and select **Properties** from the menu.</span></span>  
  
3.  <span data-ttu-id="ec645-111">サービスの手動起動を有効にする、**プロパティ**ウィンドウを選択、**全般** タブで、し、、**スタートアップの種類**ボックスの 手動、およびクリックして**適用**です。</span><span class="sxs-lookup"><span data-stu-id="ec645-111">To enable the manual start-up of the service, in the **Properties** window select the **General** tab, and in the **Startup type** box select Manual, and then click **Apply**.</span></span>  
  
4.  <span data-ttu-id="ec645-112">サービスの状態 領域で、サービスを開始するには、クリックして、**開始**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ec645-112">To start the service,  in the Service status area, click the **Start** button.</span></span> <span data-ttu-id="ec645-113">これで、サービスの状態には "開始" が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ec645-113">The service status should now display "Started".</span></span>  
  
5.  <span data-ttu-id="ec645-114">サービスの一覧に戻り、をクリックして、 **OK**、し、MMC コンソールを終了します。</span><span class="sxs-lookup"><span data-stu-id="ec645-114">To return to the list of services, click the **OK**, and exit the MMC Console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec645-115">例</span><span class="sxs-lookup"><span data-stu-id="ec645-115">Example</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec645-116">参照</span><span class="sxs-lookup"><span data-stu-id="ec645-116">See Also</span></span>  
 [<span data-ttu-id="ec645-117">Net.TCP ポート共有</span><span class="sxs-lookup"><span data-stu-id="ec645-117">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 [<span data-ttu-id="ec645-118">Net.TCP ポート共有サービスを構成する</span><span class="sxs-lookup"><span data-stu-id="ec645-118">Configuring the Net.TCP Port Sharing Service</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)

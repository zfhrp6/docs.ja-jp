---
title: "LINQ メッセージ クエリの関連付け"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3239d14ce8213b719305b5e32204569a8105997a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="linq-message-query-correlation"></a><span data-ttu-id="1e615-102">LINQ メッセージ クエリの関連付け</span><span class="sxs-lookup"><span data-stu-id="1e615-102">LINQ Message Query Correlation</span></span>
<span data-ttu-id="1e615-103">このサンプルでは、システム標準の <xref:System.ServiceModel.Dispatcher.MessageQuery> ではなく、カスタムの <xref:System.ServiceModel.XPathMessageQuery> 実装を使用して、コンテンツ ベースの関連付けを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1e615-103">This sample demonstrates how to do content-based correlation using a custom <xref:System.ServiceModel.Dispatcher.MessageQuery> implementation as opposed to the system-provided <xref:System.ServiceModel.XPathMessageQuery>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="1e615-104">使用例</span><span class="sxs-lookup"><span data-stu-id="1e615-104">Demonstrates</span></span>  
 <span data-ttu-id="1e615-105">カスタムの <xref:System.ServiceModel.Dispatcher.MessageQuery>、コンテンツ ベースの相関関係。</span><span class="sxs-lookup"><span data-stu-id="1e615-105">Custom <xref:System.ServiceModel.Dispatcher.MessageQuery>, Content-Based Correlation.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="1e615-106">説明</span><span class="sxs-lookup"><span data-stu-id="1e615-106">Discussion</span></span>  
 <span data-ttu-id="1e615-107">このサンプルでは、関連付けのために <xref:System.ServiceModel.Dispatcher.MessageQuery> 基本クラスから拡張する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1e615-107">This sample shows how to extend from the <xref:System.ServiceModel.Dispatcher.MessageQuery> base class for the purposes of correlation.</span></span> <span data-ttu-id="1e615-108">カスタム実装の `LinqMessageQuery` を使用すると、XLinq を使用してメッセージ内で検索する XName を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1e615-108">The custom implementation, `LinqMessageQuery`, allows users to provide an XName to find within the message using XLinq.</span></span> <span data-ttu-id="1e615-109">クエリによって取得されたデータを使用して、メッセージを適切なワークフロー インスタンスにディスパッチするための相関関係キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="1e615-109">The data retrieved by the query is used to form the correlation key to dispatch messages to the appropriate workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1e615-110">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="1e615-110">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1e615-111">このサンプルでは、HTTP エンドポイントを使用してワークフロー サービスを公開します。</span><span class="sxs-lookup"><span data-stu-id="1e615-111">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="1e615-112">このサンプルを適切な URL Acl を実行するを追加する必要があります (を参照してください[を構成する HTTP および HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353)詳細については)、管理者として Visual Studio を実行しているか、適切な Acl を追加する管理者特権のプロンプトで次のコマンドを実行することによってです。</span><span class="sxs-lookup"><span data-stu-id="1e615-112">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="1e615-113">ドメインとユーザー名は置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="1e615-113">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  <span data-ttu-id="1e615-114">URL ACL を追加したら、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="1e615-114">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1.  <span data-ttu-id="1e615-115">ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="1e615-115">Build the solution.</span></span>  
  
    2.  <span data-ttu-id="1e615-116">複数のスタートアップ プロジェクトを設定するには、ソリューションを右クリックしを選択すると**スタートアップ プロジェクトの**します。</span><span class="sxs-lookup"><span data-stu-id="1e615-116">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="1e615-117">追加**サービス**と**クライアント**(その順序で) 複数のスタートアップ プロジェクトとして。</span><span class="sxs-lookup"><span data-stu-id="1e615-117">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    3.  <span data-ttu-id="1e615-118">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="1e615-118">Run the application.</span></span> <span data-ttu-id="1e615-119">クライアント コンソールには、注文を送信し、発注書 ID を受信した後に、注文を確認するワークフローが示されます。</span><span class="sxs-lookup"><span data-stu-id="1e615-119">The client console shows a workflow  sending an order and receiving the purchase order id and then subsequently confirming the order.</span></span> <span data-ttu-id="1e615-120">Service のウィンドウには、処理されている要求が示されます。</span><span class="sxs-lookup"><span data-stu-id="1e615-120">The Service window will show the requests being processed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1e615-121">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="1e615-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1e615-122">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1e615-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1e615-123">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="1e615-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1e615-124">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="1e615-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`

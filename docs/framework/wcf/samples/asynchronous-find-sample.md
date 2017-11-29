---
title: "非同期検索のサンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a713a25-c1f4-42e1-8c4a-93d64ca45a3b
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a793945906bb1a106916d59ff07ea813f38469d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="asynchronous-find-sample"></a><span data-ttu-id="d3786-102">非同期検索のサンプル</span><span class="sxs-lookup"><span data-stu-id="d3786-102">Asynchronous Find Sample</span></span>
<span data-ttu-id="d3786-103">このサンプルでは、クライアント アプリケーションで非同期の検索操作を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d3786-103">This sample shows how to use the asynchronous find operation from a client application.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="d3786-104">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="d3786-104">Sample Details</span></span>  
 <span data-ttu-id="d3786-105">次のデザイン パターンの利点は、検索要求の結果として配置されたエンドポイントがクライアントに対して非同期に通知されることです。</span><span class="sxs-lookup"><span data-stu-id="d3786-105">The benefit of following this design pattern is that the client is notified asynchronously of the endpoints located as a result of the find request.</span></span> <span data-ttu-id="d3786-106">このしくみを確認するには、Client.cs ファイルを開いてください。</span><span class="sxs-lookup"><span data-stu-id="d3786-106">To see how this works, open the Client.cs file.</span></span> <span data-ttu-id="d3786-107"><xref:System.ServiceModel.Discovery.DiscoveryClient> オブジェクトには、そのイベント ハンドラーにアタッチされるデリゲートが 2 つあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d3786-107">Note the <xref:System.ServiceModel.Discovery.DiscoveryClient> object has two delegates attached to its event handlers.</span></span> <span data-ttu-id="d3786-108">1 つは <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> イベントの発生時に呼び出され、もう 1 つは <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> イベントが発生するたびに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d3786-108">One delegate is called when a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is raised and another is called each time a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> event is raised.</span></span> <span data-ttu-id="d3786-109">このサンプルでは、アプリケーションでこのパターンを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3786-109">The sample shows how you can utilize this pattern in your application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3786-110">このサンプルでは HTTP エンドポイントを使用します。サンプルを実行するには、適切な URL ACL を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3786-110">This sample uses HTTP endpoints and to run, proper URL ACLs must be added.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="d3786-111">[HTTP および HTTPS の構成](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)です。</span><span class="sxs-lookup"><span data-stu-id="d3786-111"> [Configuring HTTP and HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="d3786-112">管理特権で次のコマンドを実行すると、適切な ACL が追加されます。</span><span class="sxs-lookup"><span data-stu-id="d3786-112">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="d3786-113">そのままではコマンドが動作しない場合は、代わりに、ドメインとユーザー名を引数に指定して実行してみてください。</span><span class="sxs-lookup"><span data-stu-id="d3786-113">You may want to substitute your domain and username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d3786-114">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="d3786-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d3786-115">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] で、AsyncFind.sln を開きます。</span><span class="sxs-lookup"><span data-stu-id="d3786-115">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the AsyncFind.sln.</span></span>  
  
2.  <span data-ttu-id="d3786-116">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="d3786-116">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="d3786-117">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] コマンド プロンプトを開き、\WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug ディレクトリまたは \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug ディレクトリに移動して、Service.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="d3786-117">Open a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt and navigate to the \WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug or \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug directory and run Service.exe.</span></span>  
  
4.  <span data-ttu-id="d3786-118">サービスが開始したら、\WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug ディレクトリまたは WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug ディレクトリに移動して、Client.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="d3786-118">After the service has started, navigate to the \WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug or WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug directory and run Client.exe.</span></span>  
  
5.  <span data-ttu-id="d3786-119">クライアントでサービスを検索して呼び出せることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d3786-119">Observe the client is able to locate and call the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d3786-120">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="d3786-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d3786-121">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d3786-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d3786-122">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="d3786-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d3786-123">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="d3786-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\AsyncFind`  
  
## <a name="see-also"></a><span data-ttu-id="d3786-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3786-124">See Also</span></span>

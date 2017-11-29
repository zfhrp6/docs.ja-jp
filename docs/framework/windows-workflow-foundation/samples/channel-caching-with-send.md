---
title: "Send によるチャネル キャッシュ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e69a2502-25cb-43bf-b8d2-95fbdecb41cb
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3f78b22d1481e260535e4aeb9764d8ee349a7a2c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="channel-caching-with-send"></a><span data-ttu-id="d4458-102">Send によるチャネル キャッシュ</span><span class="sxs-lookup"><span data-stu-id="d4458-102">Channel Caching with Send</span></span>
<span data-ttu-id="d4458-103"><xref:System.ServiceModel.Activities.SendMessageChannelCache> を使用すると、ユーザーは <xref:System.ServiceModel.Activities.Send> および <xref:System.ServiceModel.Activities.SendParametersContent> アクティビティでさまざまなレベルのチャネル キャッシュを利用できます。</span><span class="sxs-lookup"><span data-stu-id="d4458-103">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> enables users to have different levels of channel caching with <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.SendParametersContent> activities.</span></span> <span data-ttu-id="d4458-104">既定では、インスタンス レベルのキャッシュが有効になっています。このサンプルでは、次の機能を示します。</span><span class="sxs-lookup"><span data-stu-id="d4458-104">Instance-level caching is enabled by default and this sample demonstrates the following features:</span></span>  
  
1.  <span data-ttu-id="d4458-105">アプリケーション ドメイン間での <xref:System.ServiceModel.Activities.SendMessageChannelCache> の共有。</span><span class="sxs-lookup"><span data-stu-id="d4458-105">Share a <xref:System.ServiceModel.Activities.SendMessageChannelCache> across an application domain.</span></span>  
  
2.  <span data-ttu-id="d4458-106">チャネル キャッシュの無効化。</span><span class="sxs-lookup"><span data-stu-id="d4458-106">Disable channel caching.</span></span>  
  
3.  <span data-ttu-id="d4458-107"><xref:System.ServiceModel.Activities.SendMessageChannelCache> 内のワークフロー インスタンス間での <xref:System.ServiceModel.Activities.WorkflowServiceHost> の共有。</span><span class="sxs-lookup"><span data-stu-id="d4458-107">Share a <xref:System.ServiceModel.Activities.SendMessageChannelCache> among workflow instances in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="d4458-108">使用例</span><span class="sxs-lookup"><span data-stu-id="d4458-108">Demonstrates</span></span>  
 <span data-ttu-id="d4458-109"><xref:System.ServiceModel.Activities.SendMessageChannelCache> 拡張、<xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.ReceiveContent>、および <xref:System.ServiceModel.Activities.SendReply> アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="d4458-109"><xref:System.ServiceModel.Activities.SendMessageChannelCache> extension, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d4458-110">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="d4458-110">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d4458-111">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] でプロジェクト ソリューションを読み込み、プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="d4458-111">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="d4458-112">\EchoWorkflowService\bin\debug に生成された EchoWorkflowService アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="d4458-112">Run the EchoWorkflowService application generated in \EchoWorkflowService\bin\debug.</span></span>  
  
3.  <span data-ttu-id="d4458-113">\EchoWorkflowClient\bin\debug に生成された EchoWorkflowClient アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="d4458-113">Run the EchoWorkflowClient application generated in .\EchoWorkflowClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="d4458-114">クライアントは、サービスで Echo 操作を呼び出し、結果を出力します。</span><span class="sxs-lookup"><span data-stu-id="d4458-114">The client calls the Echo operation on the service and prints the results.</span></span> <span data-ttu-id="d4458-115">結果が出力されたら、Enter キーを押してクライアントを終了し、サービスを終了します。</span><span class="sxs-lookup"><span data-stu-id="d4458-115">When the results have been printed, press ENTER to exit the client and the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d4458-116">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="d4458-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d4458-117">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d4458-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d4458-118">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="d4458-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d4458-119">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="d4458-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ChannelCache`

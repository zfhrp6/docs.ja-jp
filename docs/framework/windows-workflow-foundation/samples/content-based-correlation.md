---
title: "コンテンツ ベースの相関関係"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8638b5d6-1d59-456d-8acd-179a5b39b260
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 03c37fd66b8e03661d793b22a98c1816bf5042c9
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2017
---
# <a name="content-based-correlation"></a><span data-ttu-id="113b3-102">コンテンツ ベースの相関関係</span><span class="sxs-lookup"><span data-stu-id="113b3-102">Content-Based Correlation</span></span>
<span data-ttu-id="113b3-103">このサンプルでは、メッセージング アクティビティ (<xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.SendReply>、および <xref:System.ServiceModel.Activities.ReceiveReply>) を 1 つまたは複数のコンテンツ ベースの相関関係で使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="113b3-103">This sample demonstrates how the messaging activities (<xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>) can be used with multiple content-based correlations.and content-based correlation.</span></span> <span data-ttu-id="113b3-104">このシナリオでは、最初に発注書 ID に基づいて 1 つの相関関係を初期化し、後から顧客 ID に基づいて別の相関関係を作成します。</span><span class="sxs-lookup"><span data-stu-id="113b3-104">In this scenario, a correlation is first initialized based on a purchase order ID, and then another correlation is created later based on the customer ID.</span></span> <span data-ttu-id="113b3-105">ここでは、<xref:System.ServiceModel.Activities.Receive> アクティビティで、既存の相関関係を追跡し、なおかつ同じ受信メッセージに基づいて新しい相関関係を初期化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="113b3-105">This shows how a <xref:System.ServiceModel.Activities.Receive> activity can both follow an existing correlation and initialize a new correlation based on the same incoming message.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="113b3-106">使用例</span><span class="sxs-lookup"><span data-stu-id="113b3-106">Demonstrates</span></span>  
 <span data-ttu-id="113b3-107">メッセージング アクティビティとコンテンツ ベースの相関関係</span><span class="sxs-lookup"><span data-stu-id="113b3-107">Messaging activities and content-based correlation</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="113b3-108">説明</span><span class="sxs-lookup"><span data-stu-id="113b3-108">Discussion</span></span>  
 <span data-ttu-id="113b3-109">このサンプルでは、複数のコンテンツ ベースの相関関係を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="113b3-109">This sample shows how to use multiple content-based correlations.</span></span>  <span data-ttu-id="113b3-110">このシナリオでは、最初に発注書 ID に基づいて 1 つの相関関係を初期化し、後から顧客 ID に基づいて別の相関関係を作成します。</span><span class="sxs-lookup"><span data-stu-id="113b3-110">In this scenario, a correlation is first initialized based on a purchase order ID, and then another correlation is created later based on the customer ID.</span></span>  <span data-ttu-id="113b3-111">相関関係は、<xref:System.ServiceModel.Activities.Receive> アクティビティを使用してカスケード化されます。このアクティビティは、既存の相関関係 (PurchaseOrderId) を追跡し、なおかつ同じ受信メッセージに基づいて新しい相関関係 (CustomerId) も初期化します。</span><span class="sxs-lookup"><span data-stu-id="113b3-111">The correlations are cascaded using a <xref:System.ServiceModel.Activities.Receive> activity that both follows an existing correlation (PurchaseOrderId) and initializes a new correlation (CustomerId) based on the same incoming message.</span></span>  <span data-ttu-id="113b3-112">これを実現するために、<xref:System.ServiceModel.Activities.Receive> アクティビティで <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> プロパティ、<xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> プロパティ、および <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="113b3-112">To accomplish this, the <xref:System.ServiceModel.Activities.Receive> activity uses the <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>, <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> and <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> properties.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="113b3-113">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="113b3-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="113b3-114">開いている[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]を右クリックして、管理者特権での権限を持つ、[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]アイコンを選択して**管理者として実行**です。</span><span class="sxs-lookup"><span data-stu-id="113b3-114">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="113b3-115">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、CascadingCorrelation.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="113b3-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CascadingCorrelation.sln solution file.</span></span>  
  
3.  <span data-ttu-id="113b3-116">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="113b3-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="113b3-117">サーバーを実行するには、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="113b3-117">To run the server, press F5.</span></span>  
  
5.  <span data-ttu-id="113b3-118">サービスの準備ができ、メッセージのリッスンを開始したら、ソリューション エクスプローラーで、Client プロジェクトを右クリックして実行します。</span><span class="sxs-lookup"><span data-stu-id="113b3-118">Once the service is ready and listening for messages, in Solution Explorer, right-click the Client project and run it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="113b3-119">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="113b3-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="113b3-120">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="113b3-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="113b3-121">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="113b3-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="113b3-122">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="113b3-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ContentBasedCorrelation`
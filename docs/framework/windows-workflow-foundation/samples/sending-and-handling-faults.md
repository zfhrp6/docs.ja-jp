---
title: "エラーの送信と処理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98e8e04d-2ac9-4a33-ae08-462f757a7a14
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 57d522918d280c9a8a68fcd420b7216cc48216d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="sending-and-handling-faults"></a><span data-ttu-id="c17c2-102">エラーの送信と処理</span><span class="sxs-lookup"><span data-stu-id="c17c2-102">Sending and Handling Faults</span></span>
<span data-ttu-id="c17c2-103">このサンプルでは、<xref:System.ServiceModel.Activities.SendReply> および <xref:System.ServiceModel.Activities.ReceiveReply> メッセージング アクティビティを使用して、予期したエラーと予期しないエラーを送受信する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c17c2-103">This sample demonstrates how to use the <xref:System.ServiceModel.Activities.SendReply> and <xref:System.ServiceModel.Activities.ReceiveReply> messaging activities to send and receive expected and unexpected faults.</span></span> <span data-ttu-id="c17c2-104">このシナリオでは、最初のクライアント要求で、その <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> コレクションに含まれている予期したエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="c17c2-104">In this scenario, the first client request results in an expected fault that has been included in its <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> collection.</span></span> <span data-ttu-id="c17c2-105">次のいくつかのクライアント要求によって、予期しないエラーを受信してから、最後の要求が成功します。</span><span class="sxs-lookup"><span data-stu-id="c17c2-105">The next few client requests result in receiving unexpected faults, before the final request succeeds.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="c17c2-106">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="c17c2-106">To use this sample</span></span>  
  
1.  <span data-ttu-id="c17c2-107">開いている[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]を右クリックして、管理者特権での権限を持つ、[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]アイコンを選択して**管理者として実行**です。</span><span class="sxs-lookup"><span data-stu-id="c17c2-107">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="c17c2-108">Faults.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="c17c2-108">Open the Faults.sln solution file.</span></span>  
  
3.  <span data-ttu-id="c17c2-109">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="c17c2-109">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="c17c2-110">サービス プロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="c17c2-110">Run the service project.</span></span>  
  
    1.  <span data-ttu-id="c17c2-111">**ソリューション エクスプ ローラー**を右クリックし、`FaultService`プロジェクトし、選択**スタートアップ プロジェクトとして設定**です。</span><span class="sxs-lookup"><span data-stu-id="c17c2-111">In **Solution Explorer**, right-click the `FaultService` project and select **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="c17c2-112">Ctrl キーを押しながら、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="c17c2-112">Press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="c17c2-113">別のコピーを開く[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]を右クリックして、管理者特権での権限を持つ、[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]アイコンを選択して**管理者として実行**です。</span><span class="sxs-lookup"><span data-stu-id="c17c2-113">Open another copy of [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
6.  <span data-ttu-id="c17c2-114">Faults.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="c17c2-114">Open the Faults.sln solution file.</span></span>  
  
7.  <span data-ttu-id="c17c2-115">クライアント プロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="c17c2-115">Run the client project.</span></span>  
  
    1.  <span data-ttu-id="c17c2-116">**ソリューション エクスプ ローラー**を右クリックし、`FaultClient`プロジェクトし、選択**スタートアップ プロジェクトとして設定**です。</span><span class="sxs-lookup"><span data-stu-id="c17c2-116">In **Solution Explorer**, right-click the `FaultClient` project and select **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="c17c2-117">Ctrl キーを押しながら、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="c17c2-117">Press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c17c2-118">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="c17c2-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c17c2-119">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c17c2-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c17c2-120">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="c17c2-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c17c2-121">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c17c2-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Faults`  
  
## <a name="see-also"></a><span data-ttu-id="c17c2-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="c17c2-122">See Also</span></span>

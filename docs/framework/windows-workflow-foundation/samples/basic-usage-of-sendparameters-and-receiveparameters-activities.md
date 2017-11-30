---
title: "SendParameters および ReceiveParameters アクティビティの基本的な使用方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b6b1681-3d41-403f-bfe2-3f600f24aa8c
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a45e04c4368406255736312503e19de95ed12150
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2017
---
# <a name="basic-usage-of-sendparameters-and-receiveparameters-activities"></a><span data-ttu-id="9749b-102">SendParameters および ReceiveParameters アクティビティの基本的な使用方法</span><span class="sxs-lookup"><span data-stu-id="9749b-102">Basic Usage of SendParameters and ReceiveParameters Activities</span></span>
<span data-ttu-id="9749b-103">このサンプルでは、<xref:System.ServiceModel.Activities.SendParametersContent> アクティビティと <xref:System.ServiceModel.Activities.ReceiveParametersContent> アクティビティの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9749b-103">This sample shows the use of <xref:System.ServiceModel.Activities.SendParametersContent> and <xref:System.ServiceModel.Activities.ReceiveParametersContent> activities.</span></span> <span data-ttu-id="9749b-104">このサービスは、文字列引数を取得して、クライアントに入力を再度エコーするという 1 つの操作を公開します。</span><span class="sxs-lookup"><span data-stu-id="9749b-104">The service exposes one operation that takes a string argument and echoes the input back to the client.</span></span> <span data-ttu-id="9749b-105">このサンプルで示すのは、これらのメッセージング アクティビティのパラメーターを設定する方法です。</span><span class="sxs-lookup"><span data-stu-id="9749b-105">The sample shows how to set up the parameters for these messaging activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9749b-106">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="9749b-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9749b-107">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="9749b-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9749b-108">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="9749b-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9749b-109">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="9749b-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\SendReceiveParameters`  
  
#### <a name="using-this-sample"></a><span data-ttu-id="9749b-110">このサンプルの使用</span><span class="sxs-lookup"><span data-stu-id="9749b-110">Using this sample</span></span>  
  
1.  <span data-ttu-id="9749b-111">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] でプロジェクト ソリューションを読み込み、プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="9749b-111">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="9749b-112">最初に、[ソリューションの基本ディレクトリ]\EchoWorkflowService\bin\debug に生成された EchoWorkflowService アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="9749b-112">First run the EchoWorkflowService application generated in [solution base directory]\EchoWorkflowService\bin\debug.</span></span>  
  
3.  <span data-ttu-id="9749b-113">2 番目に、[ソリューションの基本ディレクトリ]\EchoWorkflowClient\bin\debug に生成された EchoWorkflowClient アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="9749b-113">Second, run the EchoWorkflowClient application generated in [solution base directory]\EchoWorkflowClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="9749b-114">クライアントは、サービスで Echo 操作を呼び出し、結果を出力します。</span><span class="sxs-lookup"><span data-stu-id="9749b-114">The client calls Echo operation on the service and prints the results.</span></span> <span data-ttu-id="9749b-115">完了したら、Enter キーを押してクライアントを終了し、サービスを終了します。</span><span class="sxs-lookup"><span data-stu-id="9749b-115">When complete, press ENTER to exit the client and then the service.</span></span>
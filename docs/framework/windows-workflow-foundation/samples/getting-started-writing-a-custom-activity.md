---
title: "カスタム アクティビティの記述について"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3902f5fa-8a43-4048-8a6a-6b15472f90f0
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 568c25574fa5c3536f1c7678f2705c19719c62d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-writing-a-custom-activity"></a><span data-ttu-id="09b55-102">カスタム アクティビティの記述について</span><span class="sxs-lookup"><span data-stu-id="09b55-102">Getting Started Writing a Custom Activity</span></span>
<span data-ttu-id="09b55-103">このサンプルでは、XAML で単純なカスタム アクティビティを定義する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="09b55-103">This sample demonstrates how to define a simple custom activity in XAML.</span></span> <span data-ttu-id="09b55-104">このアクティビティの名前は `Rhyme` で、ロジックは 3 つの連続する <xref:System.Activities.Statements.WriteLine> アクティビティです。</span><span class="sxs-lookup"><span data-stu-id="09b55-104">The activity is given the name `Rhyme`, and its logic is a sequence of three <xref:System.Activities.Statements.WriteLine> activities.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="09b55-105">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="09b55-105">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="09b55-106">開く、 **Simple.sln**サンプルのソリューション[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="09b55-106">Open the **Simple.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="09b55-107">ソリューションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="09b55-107">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="09b55-108">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="09b55-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="09b55-109">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="09b55-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="09b55-110">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="09b55-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="09b55-111">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="09b55-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\GettingStarted`
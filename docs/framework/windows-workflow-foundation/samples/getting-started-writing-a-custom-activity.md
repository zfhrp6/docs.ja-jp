---
title: カスタム アクティビティの記述について
ms.date: 03/30/2017
ms.assetid: 3902f5fa-8a43-4048-8a6a-6b15472f90f0
ms.openlocfilehash: 1c455009a0c658429c13da5e93d07c744402dd61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="getting-started-writing-a-custom-activity"></a><span data-ttu-id="523f7-102">カスタム アクティビティの記述について</span><span class="sxs-lookup"><span data-stu-id="523f7-102">Getting Started Writing a Custom Activity</span></span>
<span data-ttu-id="523f7-103">このサンプルでは、XAML で単純なカスタム アクティビティを定義する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="523f7-103">This sample demonstrates how to define a simple custom activity in XAML.</span></span> <span data-ttu-id="523f7-104">このアクティビティの名前は `Rhyme` で、ロジックは 3 つの連続する <xref:System.Activities.Statements.WriteLine> アクティビティです。</span><span class="sxs-lookup"><span data-stu-id="523f7-104">The activity is given the name `Rhyme`, and its logic is a sequence of three <xref:System.Activities.Statements.WriteLine> activities.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="523f7-105">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="523f7-105">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="523f7-106">開く、 **Simple.sln**サンプルのソリューション[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="523f7-106">Open the **Simple.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="523f7-107">ソリューションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="523f7-107">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="523f7-108">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="523f7-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="523f7-109">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="523f7-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="523f7-110">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="523f7-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="523f7-111">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="523f7-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\GettingStarted`
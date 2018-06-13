---
title: 実行プロパティ
ms.date: 03/30/2017
ms.assetid: 31c009db-397c-4653-87e2-32dc77fa4b13
ms.openlocfilehash: 201fe222de1cb2029696a1694ae97815db5f913d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513023"
---
# <a name="execution-properties"></a><span data-ttu-id="07601-102">実行プロパティ</span><span class="sxs-lookup"><span data-stu-id="07601-102">Execution Properties</span></span>
<span data-ttu-id="07601-103">このサンプルでは、カスタム アクティビティで実行プロパティを定義および使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="07601-103">This sample shows how to define and use an execution property in a custom activity.</span></span> <span data-ttu-id="07601-104">この例では、実行プロパティによってコンソールの前景色が決定されます。</span><span class="sxs-lookup"><span data-stu-id="07601-104">In this example, the execution property determines the console's foreground color.</span></span> <span data-ttu-id="07601-105">例のワークフローでは、実行のさまざまな論理パス (<xref:System.Activities.Statements.Parallel> アクティビティの分岐) が、アクティビティの逐次的実行にもかかわらず、<xref:System.Activities.Statements.Parallel> アクティビティの分岐全体にわたってさまざまなコンソール色をどのように保持するかを示します。</span><span class="sxs-lookup"><span data-stu-id="07601-105">An example workflow shows how different logical paths of execution (branches of a <xref:System.Activities.Statements.Parallel> activity) can maintain different console colors despite interleaved execution of activities (across the branches of the <xref:System.Activities.Statements.Parallel> activity).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="07601-106">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="07601-106">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="07601-107">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で ExecutionProperties.sln サンプル ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="07601-107">Open the ExecutionProperties.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="07601-108">使用されるカスタム アクティビティはソリューションと同時にビルドする必要があるため、ソリューションをビルドする前に ThreeColors.xaml を表示するとエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="07601-108">Viewing ThreeColors.xaml before building the solution displays an error, because the custom activities used must be built at the same time as the solution.</span></span>  
  
2.  <span data-ttu-id="07601-109">ソリューションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="07601-109">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="07601-110">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="07601-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="07601-111">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="07601-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="07601-112">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="07601-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="07601-113">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="07601-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ExecutionProperties`
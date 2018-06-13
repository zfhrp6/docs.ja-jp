---
title: 補正可能なアクティビティのサンプル
ms.date: 03/30/2017
ms.assetid: 58f4898c-b2b8-44a4-9a73-3bef4da6d5ba
ms.openlocfilehash: 8008eaaca062723cab1efabfb1b25018353c73b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514007"
---
# <a name="compensable-activity-sample"></a><span data-ttu-id="38260-102">補正可能なアクティビティのサンプル</span><span class="sxs-lookup"><span data-stu-id="38260-102">Compensable Activity Sample</span></span>
<span data-ttu-id="38260-103">このサンプルでは、`CompensableActivity` アクティビティを使用して、通常の実行中に特定のアクションに対して実行される作業、および必要に応じて後からアクションを補正するために実行する必要がある作業を定義する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="38260-103">This sample demonstrates how to use the `CompensableActivity` activity to define the work to be done for a given action during normal execution and the work that is necessary to be done to compensate that action, if necessary at a later time.</span></span>  <span data-ttu-id="38260-104">このサンプルの最初の部分は、補正可能な作業単位を定義できる方法では、Windows Workflow Foundation (WF) を示しています。 を使用して、`CompensableActivity`アクティビティおよびを正常に実行の実行方法。</span><span class="sxs-lookup"><span data-stu-id="38260-104">The first part of the sample shows how units of compensable work can be defined in Windows Workflow Foundation (WF) using a `CompensableActivity` activity and how they are executed in a successful run.</span></span>  <span data-ttu-id="38260-105">サンプルの 2 つ目の部分では、予期しないイベントが発生してワークフロー インスタンスがキャンセルされたときに、同じ単位の補正可能な作業が自動的に補正を引き継ぐ方法を示します。</span><span class="sxs-lookup"><span data-stu-id="38260-105">The second part of the sample shows how the same units of compensable work automatically take care of compensation when an unexpected event is hit and the workflow instance is canceled.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="38260-106">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="38260-106">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="38260-107">Visual Studio 2010 を使用して、CompensableActivity.sln を開きます。</span><span class="sxs-lookup"><span data-stu-id="38260-107">Using Visual Studio 2010, open the CompensableActivity.sln.</span></span>  
  
2.  <span data-ttu-id="38260-108">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="38260-108">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="38260-109">F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="38260-109">Run the application by pressing F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="38260-110">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="38260-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="38260-111">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="38260-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="38260-112">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="38260-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="38260-113">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="38260-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\BasicCompensableActivity`
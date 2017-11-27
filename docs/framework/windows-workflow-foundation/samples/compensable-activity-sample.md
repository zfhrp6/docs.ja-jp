---
title: "補正可能なアクティビティのサンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58f4898c-b2b8-44a4-9a73-3bef4da6d5ba
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b8d7fb5650a8927016e0deebc07a68a8145496db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="compensable-activity-sample"></a><span data-ttu-id="b1be0-102">補正可能なアクティビティのサンプル</span><span class="sxs-lookup"><span data-stu-id="b1be0-102">Compensable Activity Sample</span></span>
<span data-ttu-id="b1be0-103">このサンプルでは、`CompensableActivity` アクティビティを使用して、通常の実行中に特定のアクションに対して実行される作業、および必要に応じて後からアクションを補正するために実行する必要がある作業を定義する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b1be0-103">This sample demonstrates how to use the `CompensableActivity` activity to define the work to be done for a given action during normal execution and the work that is necessary to be done to compensate that action, if necessary at a later time.</span></span>  <span data-ttu-id="b1be0-104">サンプルの最初の部分では、[!INCLUDE[wf](../../../../includes/wf-md.md)] アクティビティを使用して `CompensableActivity` で補正可能な作業の単位を定義する方法と、これらの作業を正常に実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b1be0-104">The first part of the sample shows how units of compensable work can be defined in [!INCLUDE[wf](../../../../includes/wf-md.md)] using a `CompensableActivity` activity and how they are executed in a successful run.</span></span>  <span data-ttu-id="b1be0-105">サンプルの 2 つ目の部分では、予期しないイベントが発生してワークフロー インスタンスがキャンセルされたときに、同じ単位の補正可能な作業が自動的に補正を引き継ぐ方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b1be0-105">The second part of the sample shows how the same units of compensable work automatically take care of compensation when an unexpected event is hit and the workflow instance is canceled.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b1be0-106">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="b1be0-106">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b1be0-107">Visual Studio 2010 を使用して、CompensableActivity.sln を開きます。</span><span class="sxs-lookup"><span data-stu-id="b1be0-107">Using Visual Studio 2010, open the CompensableActivity.sln.</span></span>  
  
2.  <span data-ttu-id="b1be0-108">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="b1be0-108">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="b1be0-109">F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="b1be0-109">Run the application by pressing F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b1be0-110">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="b1be0-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b1be0-111">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b1be0-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b1be0-112">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="b1be0-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b1be0-113">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="b1be0-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\BasicCompensableActivity`  
  
## <a name="see-also"></a><span data-ttu-id="b1be0-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="b1be0-114">See Also</span></span>

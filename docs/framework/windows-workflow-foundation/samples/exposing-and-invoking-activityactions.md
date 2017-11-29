---
title: "ActivityAction の公開と呼び出し"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8a87e4463689e9301045a55b16af46cb037c1fa5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="exposing-and-invoking-activityactions"></a><span data-ttu-id="6bad5-102">ActivityAction の公開と呼び出し</span><span class="sxs-lookup"><span data-stu-id="6bad5-102">Exposing and Invoking ActivityActions</span></span>
<span data-ttu-id="6bad5-103">このサンプルでは、<xref:System.Activities.ActivityAction> を含むカスタム アクティビティを開発する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6bad5-103">This sample demonstrates how to develop a custom activity that has an <xref:System.Activities.ActivityAction>.</span></span> <span data-ttu-id="6bad5-104">また、<xref:System.Activities.ActivityAction> の実装を提供して、このアクティビティを使用する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="6bad5-104">It also demonstrates how to use this activity by providing an implementation of the <xref:System.Activities.ActivityAction>.</span></span>  
  
 <span data-ttu-id="6bad5-105"><xref:System.Activities.ActivityAction>により、アクティビティ作成者は、「口」を公開特定のシグネチャを持つアクティビティのユーザーがカスタム動作に接続できます。</span><span class="sxs-lookup"><span data-stu-id="6bad5-105">An <xref:System.Activities.ActivityAction> allows an activity author to expose "holes" with specific signatures where the activity user can plug in a custom behavior.</span></span> <span data-ttu-id="6bad5-106">たとえば、 <!--zz <xref:System.Activities.Statements.ForEach>--> `System.Activities.Statements.ForEach`アクティビティが (で動作します項目のコレクション)、<xref:System.Activities.ActivityAction>アクティビティのユーザーの現在の反復処理項目で機能する動作をプラグインすることができます。</span><span class="sxs-lookup"><span data-stu-id="6bad5-106">For example, the <!--zz <xref:System.Activities.Statements.ForEach>--> `System.Activities.Statements.ForEach` activity, (which operates over a collection of items), has an <xref:System.Activities.ActivityAction> that allows the activity user to plug in behavior that operates on the current iteration item.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6bad5-107">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="6bad5-107">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="6bad5-108">開く、 **ActivityAction.sln**サンプルのソリューション[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="6bad5-108">Open the **ActivityAction.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="6bad5-109">ソリューションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="6bad5-109">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6bad5-110">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="6bad5-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6bad5-111">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="6bad5-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6bad5-112">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="6bad5-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6bad5-113">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="6bad5-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`  
  
## <a name="see-also"></a><span data-ttu-id="6bad5-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="6bad5-114">See Also</span></span>

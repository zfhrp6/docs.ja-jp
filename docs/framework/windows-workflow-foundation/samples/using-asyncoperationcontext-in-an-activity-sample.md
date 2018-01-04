---
title: "アクティビティ サンプルでの AsyncOperationContext の使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5aa36c3173e4e20d063f93b3583d063057b9bac7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="using-asyncoperationcontext-in-an-activity-sample"></a><span data-ttu-id="33afb-102">アクティビティ サンプルでの AsyncOperationContext の使用</span><span class="sxs-lookup"><span data-stu-id="33afb-102">Using AsyncOperationContext in an Activity Sample</span></span>
<span data-ttu-id="33afb-103">このサンプルでは、<xref:System.Activities.CodeActivity> を使用してワークフロー外で非同期に作業を実行するカスタムの <xref:System.Activities.AsyncCodeActivityContext> を開発する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="33afb-103">This sample demonstrates how to develop a custom <xref:System.Activities.CodeActivity> that uses <xref:System.Activities.AsyncCodeActivityContext> to perform work asynchronously outside of the workflow.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="33afb-104">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="33afb-104">Sample Details</span></span>  
 <span data-ttu-id="33afb-105">サンプルのアクティビティでは、<xref:System.IO.FileStream.BeginWrite%2A> クラスの <xref:System.IO.FileStream.EndWrite%2A> メソッドおよび <xref:System.IO.FileStream> メソッドを使用して、非同期にデータをファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="33afb-105">The sample activity uses the <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.EndWrite%2A> methods on the <xref:System.IO.FileStream> class to asynchronously write data to a file.</span></span> <span data-ttu-id="33afb-106">ここで示すパターンは、他の非同期メソッドでの使用に合わせて変更できます。</span><span class="sxs-lookup"><span data-stu-id="33afb-106">The pattern introduced here can be adapted for use with other asynchronous methods.</span></span> <span data-ttu-id="33afb-107">非同期操作の実行中、ワークフローの他のアクティビティを実行できますが、ワークフローを永続化することはできません。</span><span class="sxs-lookup"><span data-stu-id="33afb-107">While the asynchronous operation is executing, other activities in the workflow can execute, but the workflow cannot be persisted.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="33afb-108">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="33afb-108">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="33afb-109">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で Async.sln サンプル ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="33afb-109">Open the Async.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="33afb-110">ソリューションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="33afb-110">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="33afb-111">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="33afb-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="33afb-112">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="33afb-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="33afb-113">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="33afb-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="33afb-114">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="33afb-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`
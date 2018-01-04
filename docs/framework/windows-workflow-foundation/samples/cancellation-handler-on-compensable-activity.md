---
title: "補正可能なアクティビティでのキャンセル ハンドラー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: afd98bee-eccf-47e9-99c9-27cea84ce5ce
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f0f8e05d9a43b02412e7445480f7204fd2e7e13
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cancellation-handler-on-compensable-activity"></a><span data-ttu-id="218fb-102">補正可能なアクティビティでのキャンセル ハンドラー</span><span class="sxs-lookup"><span data-stu-id="218fb-102">Cancellation Handler on Compensable Activity</span></span>
<span data-ttu-id="218fb-103">このサンプルでは、<xref:System.Activities.Statements.CompensableActivity> でキャンセル ハンドラーを使用する例を示します。</span><span class="sxs-lookup"><span data-stu-id="218fb-103">This sample demonstrates the use of a cancellation handler on a <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 <span data-ttu-id="218fb-104">このサンプルには、<xref:System.Activities.Statements.CompensableActivity> キャンセルの使用法を示す 2 つのシナリオが含まれています。最初のシナリオには、3 つの補正可能な子アクティビティを含む補正可能なルート アクティビティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="218fb-104">This sample contains two scenarios that demonstrate the use of <xref:System.Activities.Statements.CompensableActivity> cancellation.The first scenario contains a root compensable activity that contains three child compensable activities.</span></span> <span data-ttu-id="218fb-105">2 つの子アクティビティは、アクティビティ本体の実行を正常に終了します。</span><span class="sxs-lookup"><span data-stu-id="218fb-105">Two child activities finish running their activity bodies successfully.</span></span> <span data-ttu-id="218fb-106">3 つ目の子アクティビティ本体が実行されると、3 つ目のアクティビティ処理をキャンセルすることで処理される例外が発生し、その後ルート アクティビティのキャンセルがトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="218fb-106">When the third child activity body runs, it encounters an exception that is handled by canceling the third activity processing, after which the cancellation of the root activity is triggered.</span></span> <span data-ttu-id="218fb-107">この例のルート アクティビティのロジックでは、先に完了している他の 2 つの子アクティビティが補正されます。</span><span class="sxs-lookup"><span data-stu-id="218fb-107">The logic in the root activity in this example is to compensate the other two child activities that completed earlier.</span></span>  
  
```  
Try  
{  
    CA   
    {  
        CA1   
        {  
        }  
        CA2  
        {  
        }  
        CA3  
        {  
            //Exception here  
            // Then this will get cancelled  
        }  
  
       // Cancellation for the root activity automatically gets called, which, in turn, adds some logic to revert what was done (Or can decide to actually confirm CA1 & CA2 if the user so desires).  
    }  
}  
Catches {  
// Can do more stuff...  
}  
```  
  
 <span data-ttu-id="218fb-108">2 つ目のシナリオでは、<xref:System.Activities.Statements.TryCatch> 分岐の前に終了する <xref:System.Activities.Statements.Delay> と平行して、<xref:System.Activities.Statements.TryCatch> を実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="218fb-108">The second scenario demonstrates executing a <xref:System.Activities.Statements.TryCatch> in parallel with a <xref:System.Activities.Statements.Delay>, which finishes before the <xref:System.Activities.Statements.TryCatch> branch.</span></span> <span data-ttu-id="218fb-109">最初の分岐が終了したときに完了条件が `true` に設定されて、他の分岐がキャンセルされます。</span><span class="sxs-lookup"><span data-stu-id="218fb-109">The completion condition is set to `true` once the first branch finishes, causing the other branch to be canceled.</span></span>  
  
```  
Parallel   
{  
    Branch1   
    {  
        // Small Delay that times out (timeout1) before branch2.  
    }  
    Branch2   
    {  
        CA   
        {  
            CA1   
            {  
            }  
            CA2   
            {  
            }  
            CA3   
            {  
            }  
            If (timeout1)    
            {  
                call Cancel CA  
            }  
        }  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="218fb-110">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="218fb-110">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="218fb-111">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して CompensationCancellation.sln を開きます。</span><span class="sxs-lookup"><span data-stu-id="218fb-111">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open CompensationCancellation.sln.</span></span>  
  
2.  <span data-ttu-id="218fb-112">Ctrl キーと Shift キーを押しながら B キーを押すか、[ビルド] メニューの [ソリューションのビルド] をクリックして、サンプルをビルドします。</span><span class="sxs-lookup"><span data-stu-id="218fb-112">Build the sample by pressing CTRL+SHIFT+B or select "Build Solution" from the Build menu..</span></span>  
  
3.  <span data-ttu-id="218fb-113">F5 キーを押すか、[デバッグ] メニューの [デバッグ開始] をクリックしてサンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="218fb-113">Run the sample by pressing F5 or select "Start Debugging" from the Debug menu.</span></span> <span data-ttu-id="218fb-114">または、Ctrl キーを押しながら F5 キーを押すか、[デバッグ] メニューの [デバッグなしで開始] をクリックすることもできます。</span><span class="sxs-lookup"><span data-stu-id="218fb-114">Alternately you may press Ctrl+F5 or select "Start without Debugging" from the Debug menu.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="218fb-115">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="218fb-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="218fb-116">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="218fb-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="218fb-117">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="218fb-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="218fb-118">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="218fb-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CompensationCancellation`
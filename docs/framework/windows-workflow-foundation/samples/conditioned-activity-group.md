---
title: "条件付きアクティビティ グループ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f76ef924-34ce-48ae-8c8d-48faf9697754
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7049f0ab787264893f334b8fe6aa0036e240a73f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="conditioned-activity-group"></a><span data-ttu-id="c3d6c-102">条件付きアクティビティ グループ</span><span class="sxs-lookup"><span data-stu-id="c3d6c-102">Conditioned Activity Group</span></span>
<span data-ttu-id="c3d6c-103">このサンプルは、旅行の予約アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="c3d6c-103">The sample demonstrates a travel booking application.</span></span> <span data-ttu-id="c3d6c-104"><xref:System.Workflow.Activities.ConditionedActivityGroup> (CAG) には、コード アクティビティである Car アクティビティと Airline アクティビティの 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="c3d6c-104">The <xref:System.Workflow.Activities.ConditionedActivityGroup> (CAG) has two code activities: a Car activity and an Airline activity.</span></span> <span data-ttu-id="c3d6c-105">`SimpleCAGWorkflow` コンストラクタ内の ArrayList オブジェクト "travelNeedType" には、必要とされる旅行の予約の種類が設定されています。</span><span class="sxs-lookup"><span data-stu-id="c3d6c-105">In the `SimpleCAGWorkflow` constructor, a "travelNeedType" ArrayList object is populated with the types of travel bookings that are required.</span></span> <span data-ttu-id="c3d6c-106">`travelNeeds.Add` ステートメントの 1 つまたは両方をコメント化することで、CAG の動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="c3d6c-106">By commenting out one or both of the `travelNeeds.Add` statements, you modify the CAG behavior accordingly.</span></span> <span data-ttu-id="c3d6c-107">Car アクティビティと Airline アクティビティには、<xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> の設定された <xref:System.Workflow.Activities.CodeCondition> 条件がそれぞれ含まれています。</span><span class="sxs-lookup"><span data-stu-id="c3d6c-107">Both the Car and Airline activities have their <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> condition populated with a <xref:System.Workflow.Activities.CodeCondition>.</span></span> <span data-ttu-id="c3d6c-108">Car アクティビティは、`travelNeeds` コレクションに `TravelNeeds.Car` のエントリがある場合にだけ実行され、Airline アクティビティは、`travelNeeds` コレクションに `TravelNeeds.Airline` のエントリがある場合にだけ実行されます。</span><span class="sxs-lookup"><span data-stu-id="c3d6c-108">The Car activity executes only if the `travelNeeds` collection has a `TravelNeeds.Car` entry, and the Airline activity executes only if the `travelNeeds` collection has a `TravelNeeds.Airline` entry.</span></span>  
  
 <span data-ttu-id="c3d6c-109">各アクティビティが実行されると、コレクションから対応するエントリが削除されます。</span><span class="sxs-lookup"><span data-stu-id="c3d6c-109">The execution of each activity removes the corresponding entry from the collection.</span></span> <span data-ttu-id="c3d6c-110">既定の条件 <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> では、実行中または実行する準備の整った子がない場合に (それぞれの <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> 条件による)、CAG が終了するように指定されています。</span><span class="sxs-lookup"><span data-stu-id="c3d6c-110">The default <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> condition specifies that the CAG should exit when no children are executing or are ready for execution (based on their <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> conditions).</span></span> <span data-ttu-id="c3d6c-111">このサンプルでは、CAG は `travelNeeds` コレクションが空になったときに終了します。</span><span class="sxs-lookup"><span data-stu-id="c3d6c-111">In this sample, this means that the CAG exits when the `travelNeeds` collection is empty.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="c3d6c-112">サンプルをビルドするには</span><span class="sxs-lookup"><span data-stu-id="c3d6c-112">To build the sample</span></span>  
  
1.  <span data-ttu-id="c3d6c-113">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で、ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="c3d6c-113">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="c3d6c-114">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="c3d6c-114">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="c3d6c-115">Ctrl キーを押しながら F5 キーを押して、ソリューションをデバッグなしで実行します。</span><span class="sxs-lookup"><span data-stu-id="c3d6c-115">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="c3d6c-116">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="c3d6c-116">To run the sample</span></span>  
  
-   <span data-ttu-id="c3d6c-117">[SDK コマンド プロンプト] ウィンドウで、SimpleCAG\bin\debug フォルダー (Visual Basic バージョンのサンプルの場合は SimpleCAG\bin フォルダー) にある .exe ファイルを実行します。このフォルダーは、サンプルのメイン フォルダーの下に作成されます。</span><span class="sxs-lookup"><span data-stu-id="c3d6c-117">In the SDK Command Prompt window, run the .exe file in the SimpleCAG\bin\debug folder (or the SimpleCAG\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c3d6c-118">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="c3d6c-118">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c3d6c-119">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c3d6c-119">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c3d6c-120">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="c3d6c-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c3d6c-121">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c3d6c-121">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\SimpleCAG`  
  
## <a name="see-also"></a><span data-ttu-id="c3d6c-122">参照</span><span class="sxs-lookup"><span data-stu-id="c3d6c-122">See Also</span></span>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty>  
 <xref:System.Workflow.Activities.CodeCondition>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A>

---
title: "外部アクティビティの検証"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49619f59-9819-484a-bcd8-5596308e8551
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e3fdc37e22bf06cdfdad3141af5657a1b20911a2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="external-activity-validation"></a><span data-ttu-id="d4218-102">外部アクティビティの検証</span><span class="sxs-lookup"><span data-stu-id="d4218-102">External Activity Validation</span></span>
<span data-ttu-id="d4218-103">このサンプルでは、ユーザーが作成するものではないビルトイン アクティビティに検証ロジックを追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d4218-103">This sample shows how to add validation logic to a built-in activity that you are not the author of.</span></span> <span data-ttu-id="d4218-104">検証ロジックでは、ワークフロー内に存在するすべての <xref:System.Activities.Statements.If> アクティビティに <xref:System.Activities.Statements.If.Then%2A> または <xref:System.Activities.Statements.If.Else%2A> のいずれかのプロパティが強制的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="d4218-104">The validation logic consists of enforcing that all <xref:System.Activities.Statements.If> activities present in the workflow either have their <xref:System.Activities.Statements.If.Then%2A> property set or their <xref:System.Activities.Statements.If.Else%2A> property set.</span></span> <span data-ttu-id="d4218-105">また、ワークフロー内に存在するすべての <xref:System.Activities.Statements.Pick> アクティビティに複数の分岐が含まれているかどうかが確認され、分岐が含まれていない場合は警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d4218-105">Also, the validation logic includes checking that all <xref:System.Activities.Statements.Pick> activities present in the workflow have more than one branch, and if that is not the case, a warning is generated.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="d4218-106">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="d4218-106">Sample details</span></span>  
 <span data-ttu-id="d4218-107">このサンプルでは、検証する各アクティビティ (<xref:System.Activities.Statements.If> アクティビティと <xref:System.Activities.Statements.Pick> アクティビティ) のインスタンスを含むワークフローを作成します。</span><span class="sxs-lookup"><span data-stu-id="d4218-107">This sample creates a workflow with an instance of each activity to validate: the <xref:System.Activities.Statements.If> activity and the <xref:System.Activities.Statements.Pick> activity.</span></span> <span data-ttu-id="d4218-108">検証動作ごとに <xref:System.Activities.Validation.Constraint> を作成します。</span><span class="sxs-lookup"><span data-stu-id="d4218-108">A <xref:System.Activities.Validation.Constraint> is created for each validation behavior.</span></span> <span data-ttu-id="d4218-109">このサンプルで作成される制約は `ConstraintError_IfShouldHaveThenOrElse` と `ConstraintWarning_PickHasOneBranch` です。</span><span class="sxs-lookup"><span data-stu-id="d4218-109">The constraints created in this sample are `ConstraintError_IfShouldHaveThenOrElse` and `ConstraintWarning_PickHasOneBranch`.</span></span> <span data-ttu-id="d4218-110">次に、これらの制約を `AdditionalConstraints` インスタンスの <xref:System.Activities.Validation.ValidationSettings> コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="d4218-110">Next, these constraints are added to the `AdditionalConstraints` collection of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="d4218-111">最後に、`static` の <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A><xref:System.Activities.Validation.ActivityValidationServices> メソッドを呼び出してワークフロー内のアクティビティを検証し、検証結果をコンソールに出力します。</span><span class="sxs-lookup"><span data-stu-id="d4218-111">Finally, the `static`<xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> method of <xref:System.Activities.Validation.ActivityValidationServices> is called to validate the activities in the workflow and the validation results are printed out to the console.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4218-112">ポリシー制約は、任意のアクティビティに追加できます。</span><span class="sxs-lookup"><span data-stu-id="d4218-112">You can add policy constraints to any activity.</span></span> <span data-ttu-id="d4218-113">たとえば、<xref:System.Activities.Statements.Sequence> または <xref:System.Activities.Statements.Parallel> アクティビティにポリシー制約を追加できます。</span><span class="sxs-lookup"><span data-stu-id="d4218-113">For example, you can add a policy constraint to a <xref:System.Activities.Statements.Sequence> or <xref:System.Activities.Statements.Parallel> activity.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="d4218-114">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="d4218-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="d4218-115">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、ExternalActivityValidation.sln ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="d4218-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ExternalActivityValidation.sln file.</span></span>  
  
2.  <span data-ttu-id="d4218-116">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="d4218-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="d4218-117">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="d4218-117">To run the solution, press Ctrl+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d4218-118">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="d4218-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d4218-119">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d4218-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d4218-120">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="d4218-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d4218-121">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="d4218-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ExternalActivityValidation`  
  
## <a name="see-also"></a><span data-ttu-id="d4218-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4218-122">See Also</span></span>

---
title: OverloadGroups
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1d547d2-f5fb-4de3-a959-ee6139a4f1ad
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 36807ce154ab70e54d211405e0cea5ead56e9b88
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="overloadgroups"></a><span data-ttu-id="64ec0-102">OverloadGroups</span><span class="sxs-lookup"><span data-stu-id="64ec0-102">OverloadGroups</span></span>
<span data-ttu-id="64ec0-103">このサンプルは、次の 2 つの興味深い特性を持つアクティビティ (`CreateLocation`) で構成されます。</span><span class="sxs-lookup"><span data-stu-id="64ec0-103">This sample consists of an activity (`CreateLocation`), which has two interesting characteristics:</span></span>  
  
1.  <span data-ttu-id="64ec0-104">いくつかの必須の引数といくつかの省略可能な引数があります。</span><span class="sxs-lookup"><span data-stu-id="64ec0-104">It has some required arguments and some optional ones.</span></span>  
  
2.  <span data-ttu-id="64ec0-105">ユーザーは、2 つの異なる引数セットのうちのどちらを指定するかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="64ec0-105">It allows the user to choose to provide one of two different sets of arguments.</span></span>  
  
 <span data-ttu-id="64ec0-106">これらの動作は、次の 2 つの機能によって実現されます。</span><span class="sxs-lookup"><span data-stu-id="64ec0-106">These behaviors are accomplished by using these two features:</span></span>  
  
-   <span data-ttu-id="64ec0-107">`[isRequired]` : 特定のアクティビティのプロパティが割り当てられているかどうかを検証し、割り当てられていない場合は例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="64ec0-107">`[isRequired]` validates that a property of a specific activity is assign, and if not, it throws an exception.</span></span>  
  
-   <span data-ttu-id="64ec0-108">`[OverloadGroup]` : 一連の引数をまとめて、アクティビティのユーザーが 2 つのセットのうちのどちらを使用するかを選択できるようにします。</span><span class="sxs-lookup"><span data-stu-id="64ec0-108">`[OverloadGroup]` puts together a set of arguments, so that the user of the activity can choose between using one set or another.</span></span> <span data-ttu-id="64ec0-109">ユーザーは、同じインスタンス内の異なるオーバーロード グループの引数を使用できません。</span><span class="sxs-lookup"><span data-stu-id="64ec0-109">The user cannot use arguments from different Overload Groups in the same instance.</span></span>  
  
 <span data-ttu-id="64ec0-110">さまざまなワークフローを設定したら、<xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> の <xref:System.Activities.Validation.ValidationResults> コレクションを返す <xref:System.Activities.Validation.Constraint> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="64ec0-110">After setting up different workflows, call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.Constraint>.</span></span> <span data-ttu-id="64ec0-111"><xref:System.Activities.Validation.Constraint> オブジェクトをコンソールに出力します。</span><span class="sxs-lookup"><span data-stu-id="64ec0-111">Print the <xref:System.Activities.Validation.Constraint> objects to the console.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="64ec0-112">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="64ec0-112">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="64ec0-113">開く、 **OverloadGroups.sln**サンプルのソリューション[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="64ec0-113">Open the **OverloadGroups.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="64ec0-114">ソリューションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="64ec0-114">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="64ec0-115">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="64ec0-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="64ec0-116">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="64ec0-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="64ec0-117">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="64ec0-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="64ec0-118">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="64ec0-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\OverloadGroups`

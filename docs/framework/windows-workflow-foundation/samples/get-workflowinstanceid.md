---
title: WorkflowInstanceId の取得
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: fbfaf52931345571e5125200fe467dcc098b9dc3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513907"
---
# <a name="get-workflowinstanceid"></a><span data-ttu-id="f9491-102">WorkflowInstanceId の取得</span><span class="sxs-lookup"><span data-stu-id="f9491-102">Get WorkflowInstanceId</span></span>
<span data-ttu-id="f9491-103">このサンプルでは、カスタム アクティビティ `GetWorkflowInstanceId` を使用して、ワークフロー インスタンス ID を返す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f9491-103">This sample demonstrates how to use the custom activity, `GetWorkflowInstanceId` to return the workflow instance ID.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="f9491-104">使用例</span><span class="sxs-lookup"><span data-stu-id="f9491-104">Demonstrates</span></span>  
 <span data-ttu-id="f9491-105">カスタム アクティビティの開発、ワークフロー インスタンスにアクセスする方法。</span><span class="sxs-lookup"><span data-stu-id="f9491-105">Custom activity development, how to access the workflow instance.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="f9491-106">説明</span><span class="sxs-lookup"><span data-stu-id="f9491-106">Discussion</span></span>  
 <span data-ttu-id="f9491-107">実行中のワークフローのインスタンス ID を取得するには、コードを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9491-107">Getting the instance ID of a running workflow requires writing code.</span></span> <span data-ttu-id="f9491-108">完全な宣言型のワークフローを記述する場合は、ワークフロー インスタンス ID を返すことができるアクティビティが必要です。そのアクティビティをワークフローで参照することで、完全な宣言型のワークフローを作成できるようになります。</span><span class="sxs-lookup"><span data-stu-id="f9491-108">If you want to write a fully-declarative workflow, then you need an activity that can return the workflow instance ID so that the activity can be referenced in the workflow to provide a fully-declarative workflow authoring experience.</span></span> <span data-ttu-id="f9491-109">多くのシナリオで、インスタンス ID へのアクセスが必要になります。例としては、ログ記録または監査のためや、後で連携できるようにインスタンス ID をクライアントに返送する (たとえば、SendReply アクティビティ内でこのアクティビティを使用する) ことでアプリケーション レベルの関連付けを行うためなどが挙げられます。</span><span class="sxs-lookup"><span data-stu-id="f9491-109">Many scenarios require access to the instance ID: a few examples are for logging or auditing purposes or for doing application-level correlation by providing the instance ID back to a client for future association (for example, by using this activity inside a SendReply activity).</span></span>  
  
 <span data-ttu-id="f9491-110">`GetWorkflowInstanceId` は、<xref:System.Activities.CodeActivity%601> 型の値を返す必要があり、ワークフローのインスタンス ID を取得するために <xref:System.Guid> にアクセスできる必要があるので、<xref:System.Activities.CodeActivityContext> として実装されます。</span><span class="sxs-lookup"><span data-stu-id="f9491-110">`GetWorkflowInstanceId` is implemented as a <xref:System.Activities.CodeActivity%601> because it must return a value of type <xref:System.Guid>, and it must have access to the <xref:System.Activities.CodeActivityContext> for getting the workflow’s instance ID.</span></span> <span data-ttu-id="f9491-111">この実装は非常に基本的なものです。</span><span class="sxs-lookup"><span data-stu-id="f9491-111">Its implementation is fairly basic.</span></span>  
  
```  
public sealed class GetWorkflowInstanceId : CodeActivity<Guid>  
{  
protected override Guid Execute(CodeActivityContext context)  
        {  
            return context.WorkflowInstanceId;  
        }  
}  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="f9491-112">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="f9491-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f9491-113">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f9491-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f9491-114">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="f9491-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f9491-115">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="f9491-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`

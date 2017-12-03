---
title: "ワークフローの一時停止と再開"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11f38339-79c7-4295-b610-24a7223bbf6d
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0d7637a9d49100d3a46ceb3c49769cacae14b5e8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="pausing-and-resuming-a-workflow"></a><span data-ttu-id="2b661-102">ワークフローの一時停止と再開</span><span class="sxs-lookup"><span data-stu-id="2b661-102">Pausing and Resuming a Workflow</span></span>
<span data-ttu-id="2b661-103">ワークフローはブックマークや <xref:System.Activities.Statements.Delay> などのブロッキング アクティビティへの応答として一時停止および再開をしますが、永続化を使用して、明示的に一時停止、アンロード、再開することもできます。</span><span class="sxs-lookup"><span data-stu-id="2b661-103">Workflows will pause and resume in response to bookmarks and blocking activities such as <xref:System.Activities.Statements.Delay>, but a workflow can also be explicitly paused, unloaded, and resumed by using persistence.</span></span>  
  
## <a name="pausing-a-workflow"></a><span data-ttu-id="2b661-104">ワークフローの一時停止</span><span class="sxs-lookup"><span data-stu-id="2b661-104">Pausing a Workflow</span></span>  
 <span data-ttu-id="2b661-105">ワークフローを一時停止するには、<xref:System.Activities.WorkflowApplication.Unload%2A> を使用します。</span><span class="sxs-lookup"><span data-stu-id="2b661-105">To pause a workflow, use <xref:System.Activities.WorkflowApplication.Unload%2A>.</span></span>  <span data-ttu-id="2b661-106">このメソッドはワークフローの永続化とアンロードを要求し、ワークフローが 30 秒以内にアンロードしないと <xref:System.TimeoutException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="2b661-106">This method requests that the workflow persist and unload, and will throw a <xref:System.TimeoutException> if the workflow does not unload in 30 seconds.</span></span>  
  
```csharp  
try  
{  
    // attempt to unload will fail if the workflow is idle within a NoPersistZone  
    application.Unload(TimeSpan.FromSeconds(5));  
}  
catch (TimeoutException e)  
{  
    Console.WriteLine(e.Message);  
}  
```  
  
## <a name="resuming-a-workflow"></a><span data-ttu-id="2b661-107">ワークフローの再開</span><span class="sxs-lookup"><span data-stu-id="2b661-107">Resuming a Workflow</span></span>  
 <span data-ttu-id="2b661-108">以前に一時停止およびアンロードされているワークフローを再開するには、<xref:System.Activities.WorkflowApplication.Load%2A> を使用します。</span><span class="sxs-lookup"><span data-stu-id="2b661-108">To resume a previously paused and unloaded workflow, use <xref:System.Activities.WorkflowApplication.Load%2A>.</span></span> <span data-ttu-id="2b661-109">このメソッドは、ワークフローを永続化ストアからメモリに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="2b661-109">This method loads a workflow from a persistence store into memory.</span></span>  
  
```csharp  
WorkflowApplication application = new WorkflowApplication(activity);  
application.InstanceStore = instanceStore;  
application.Load(id);  
```  
  
## <a name="example"></a><span data-ttu-id="2b661-110">例</span><span class="sxs-lookup"><span data-stu-id="2b661-110">Example</span></span>  
 <span data-ttu-id="2b661-111">次のコード例は、永続化を使用してワークフローを一時停止および再開する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="2b661-111">The following code sample demonstrates how to pause and resume a workflow by using persistence.</span></span>  
  
```csharp  
static string bkName = "bkName";  
static void Main(string[] args)   
{  
    StartAndUnloadInstance();  
}  
  
static void StartAndUnloadInstance()   
{  
    AutoResetEvent waitHandler = new AutoResetEvent(false);  
    WorkflowApplication wfApp = new WorkflowApplication(GetDelayedWF());  
    SqlWorkflowInstanceStore instanceStore = SetupSqlpersistenceStore();  
    wfApp.InstanceStore = instanceStore;  
    wfApp.Extensions.Add(SetupMyFileTrackingParticipant);  
    wfApp.PersistableIdle = (e) => {          ///persists application state and remove it from memory   
    return PersistableIdleAction.Unload;  
    };  
    wfApp.Unloaded = (e) => {  
        waitHandler.Set();  
    };  
    Guid id = wfApp.Id;  
    wfApp.Run();  
    waitHandler.WaitOne();  
    LoadAndCompleteInstance(id);  
}  
  
static void LoadAndCompleteInstance(Guid id)   
{            
    Console.WriteLine("Press <enter> to load the persisted workflow");  
    Console.ReadLine();  
    AutoResetEvent waitHandler = new AutoResetEvent(false);  
    WorkflowApplication wfApp = new WorkflowApplication(new Workflow1());  
    wfApp.InstanceStore =  
        new SqlWorkflowInstanceStore(ConfigurationManager.AppSettings["SqlWF4PersistenceConnectionString"].ToString());  
    wfApp.Completed = (workflowApplicationCompletedEventArgs) => {  
        Console.WriteLine("\nWorkflowApplication has Completed in the {0} state.",  
            workflowApplicationCompletedEventArgs.CompletionState);  
    };  
    wfApp.Unloaded = (workflowApplicationEventArgs) => {  
        Console.WriteLine("WorkflowApplication has Unloaded\n");  
        waitHandler.Set();  
    };  
    wfApp.Load(id);  
    wfApp.Run();  
    waitHandler.WaitOne();  
}  
  
public static Activity GetDelayedWF()   
{  
    return new Sequence {  
        Activities ={  
            new WriteLine{Text="Workflow Started"},  
            new Delay{Duration=TimeSpan.FromSeconds(10)},  
            new WriteLine{Text="Workflow Ended"}  
        }  
    };  
}  
  
private static SqlWorkflowInstanceStore SetupSqlpersistenceStore()   
{   
     string connectionString = ConfigurationManager.AppSettings["SqlWF4PersistenceConnectionString"].ToString();  
    SqlWorkflowInstanceStore sqlWFInstanceStore = new SqlWorkflowInstanceStore(connectionString);  
    sqlWFInstanceStore.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;  
    InstanceHandle handle = sqlWFInstanceStore.CreateInstanceHandle();  
    InstanceView view = sqlWFInstanceStore.Execute(handle, new CreateWorkflowOwnerCommand(), TimeSpan.FromSeconds(5));  
    handle.Free();  
    sqlWFInstanceStore.DefaultInstanceOwner = view.InstanceOwner;  
    return sqlWFInstanceStore;  
}  
```

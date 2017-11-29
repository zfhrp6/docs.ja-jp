---
title: "ワークフロー インスタンスの作成と実行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d53becfc126f1acee4759ddff956b4435c9aa769
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="creating-and-running-a-workflow-instance"></a>ワークフロー インスタンスの作成と実行
このサンプルでは、ワークフロー インスタンスを実行する方法を示します。 ここでは、ワークフロー インスタンスを同期的または非同期的に実行する方法を示します。  
  
## <a name="demonstrates"></a>使用例  
 <xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.  
  
## <a name="discussion"></a>説明  
 サンプルの最初の部分では <xref:System.Activities.WorkflowInvoker.Invoke%2A> を使用します。 これはワークフローを実行する最も基本的な方法です。 <xref:System.Activities.WorkflowInvoker.Invoke%2A> を使用して実行するワークフローは同期的に実行されます。  
  
 サンプルの 2 番目の部分は <xref:System.Activities.WorkflowApplication> クラスを使用します。 <xref:System.Activities.WorkflowApplication> を使用すると、各インスタンスをより細かく制御できるようになり、実行中のワークフローと対話したり、ワークフローを非同期的に実行したりできます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`  
  
## <a name="see-also"></a>関連項目  
 [WorkflowInvoker と WorkflowApplication の使用](../../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md)

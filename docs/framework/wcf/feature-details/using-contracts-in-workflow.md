---
title: "ワークフロー内でのコントラクトの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1c84483b2ca18d63f20e64a62bb757e244db9b24
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="using-contracts-in-workflow"></a><span data-ttu-id="1e3df-102">ワークフロー内でのコントラクトの使用</span><span class="sxs-lookup"><span data-stu-id="1e3df-102">Using Contracts in Workflow</span></span>
<span data-ttu-id="1e3df-103">サービスを実装するときは、サービスおよびサービスが送受信するデータを説明する一連のコントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="1e3df-103">When implementing a service, you define a number of contracts that describe the service and the data that it sends and receives.</span></span> <span data-ttu-id="1e3df-104">データは、データ コントラクトとメッセージ コントラクトで表されます。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスもワークフロー サービスも、サービスの説明の一環として、データ コントラクトとメッセージ コントラクトの定義を使用します。</span><span class="sxs-lookup"><span data-stu-id="1e3df-104">The data is represented as data contracts and message contracts; both [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and workflow services use data contract and message contract definitions as part of service descriptions.</span></span> <span data-ttu-id="1e3df-105">サービス自体は、(WSDL の形で) メタデータを公開して、サービスの操作を説明します。</span><span class="sxs-lookup"><span data-stu-id="1e3df-105">The service itself exposes metadata (in the form of WSDL) in order to describe the operations of the service.</span></span> <span data-ttu-id="1e3df-106">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、サービス コントラクトと操作コントラクトによって、サービスとサービスがサポートする操作を定義します。</span><span class="sxs-lookup"><span data-stu-id="1e3df-106">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], service contracts and operation contracts define the service and the operations it supports.</span></span> <span data-ttu-id="1e3df-107">ただし、ワークフロー サービスでは、これらのコントラクトはビジネス プロセス自体の一部になり、コントラクト推論と呼ばれるプロセスによってメタデータとして公開されます。</span><span class="sxs-lookup"><span data-stu-id="1e3df-107">However, in a workflow service, these contracts are part of the business process itself; they are exposed in metadata by a process called contract inference.</span></span>  
  
## <a name="contract-inference"></a><span data-ttu-id="1e3df-108">コントラクト推論</span><span class="sxs-lookup"><span data-stu-id="1e3df-108">Contract Inference</span></span>  
 <span data-ttu-id="1e3df-109">ワークフロー サービスが <xref:System.ServiceModel.Activities.WorkflowServiceHost> を使用してホストされている場合は、ワークフローで見つかった一連のメッセージ アクティビティに基づいて、ワークフロー定義が確認され、コントラクトが生成されます。</span><span class="sxs-lookup"><span data-stu-id="1e3df-109">When a workflow service is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, the workflow definition is examined and a contract is generated based on the set of messaging activities found in the workflow.</span></span> <span data-ttu-id="1e3df-110">具体的には、次のアクティビティとプロパティが、コントラクトの生成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="1e3df-110">In particular the following activities and properties are used to generate the contract:</span></span>  
  
 <span data-ttu-id="1e3df-111"><xref:System.ServiceModel.Activities.Receive> アクティビティ</span><span class="sxs-lookup"><span data-stu-id="1e3df-111"><xref:System.ServiceModel.Activities.Receive> Activity</span></span>  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.Receive.OperationContractName%2A>  --> `System.ServiceModel.Activities.Receive.OperationContractName`
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.Receive.ValueType%2A> --> `System.ServiceModel.Activities.Receive.ValueType`
  
 <span data-ttu-id="1e3df-112"><xref:System.ServiceModel.Activities.SendReply> アクティビティ</span><span class="sxs-lookup"><span data-stu-id="1e3df-112"><xref:System.ServiceModel.Activities.SendReply> Activity</span></span>  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.SendReply.ValueType%2A>-->  `System.ServiceModel.Activities.SendReply.ValueType`
  
 <span data-ttu-id="1e3df-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティ</span><span class="sxs-lookup"><span data-stu-id="1e3df-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Activity</span></span>  
  
 <span data-ttu-id="1e3df-114">コントラクト推論の結果は、WCF サービスと操作コントラクトと同じデータ構造を使用するサービスの説明になります。</span><span class="sxs-lookup"><span data-stu-id="1e3df-114">The end result of contract inference is a description of the service using the same data structures as WCF service and operation contracts.</span></span> <span data-ttu-id="1e3df-115">この情報を使用して、ワークフロー サービス用に WSDL が公開されます。</span><span class="sxs-lookup"><span data-stu-id="1e3df-115">This information is then used to expose WSDL for the workflow service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e3df-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e3df-116">See Also</span></span>  
 [<span data-ttu-id="1e3df-117">ワークフロー サービス</span><span class="sxs-lookup"><span data-stu-id="1e3df-117">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="1e3df-118">メッセージング アクティビティ</span><span class="sxs-lookup"><span data-stu-id="1e3df-118">Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/messaging-activities.md)  
 [<span data-ttu-id="1e3df-119">方法: メッセージング アクティビティでワークフロー サービスを作成</span><span class="sxs-lookup"><span data-stu-id="1e3df-119">How to: Create a Workflow Service with Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)  
 [<span data-ttu-id="1e3df-120">既存のサービス コントラクトを使用するワークフロー サービスを作成する方法</span><span class="sxs-lookup"><span data-stu-id="1e3df-120">How to: Create a workflow service that consumes an existing service contract</span></span>](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)

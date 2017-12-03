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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c13da32e304e54d1826c6dd4ad83d5fbb17702a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="using-contracts-in-workflow"></a>ワークフロー内でのコントラクトの使用
サービスを実装するときは、サービスおよびサービスが送受信するデータを説明する一連のコントラクトを定義します。 データは、データ コントラクトとメッセージ コントラクトで表されます。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスもワークフロー サービスも、サービスの説明の一環として、データ コントラクトとメッセージ コントラクトの定義を使用します。 サービス自体は、(WSDL の形で) メタデータを公開して、サービスの操作を説明します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、サービス コントラクトと操作コントラクトによって、サービスとサービスがサポートする操作を定義します。 ただし、ワークフロー サービスでは、これらのコントラクトはビジネス プロセス自体の一部になり、コントラクト推論と呼ばれるプロセスによってメタデータとして公開されます。  
  
## <a name="contract-inference"></a>コントラクト推論  
 ワークフロー サービスが <xref:System.ServiceModel.Activities.WorkflowServiceHost> を使用してホストされている場合は、ワークフローで見つかった一連のメッセージ アクティビティに基づいて、ワークフロー定義が確認され、コントラクトが生成されます。 具体的には、次のアクティビティとプロパティが、コントラクトの生成に使用されます。  
  
 <xref:System.ServiceModel.Activities.Receive> アクティビティ  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>   
 
 <xref:System.ServiceModel.Activities.SendReply> アクティビティ  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティ  
  
 コントラクト推論の結果は、WCF サービスと操作コントラクトと同じデータ構造を使用するサービスの説明になります。 この情報を使用して、ワークフロー サービス用に WSDL が公開されます。  
  
## <a name="see-also"></a>関連項目  
 [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [メッセージング アクティビティ](../../../../docs/framework/wcf/feature-details/messaging-activities.md)  
 [方法: メッセージング アクティビティでワークフロー サービスを作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)  
 [既存のサービス コントラクトを使用するワークフロー サービスを作成する方法](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)

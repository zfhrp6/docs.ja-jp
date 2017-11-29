---
title: "ワークフロー サービスの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e536dda3-e286-441e-99a7-49ddc004b646
caps.latest.revision: "30"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f33920dbad701d803b9cb062cdd2b11aa1346df4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="workflow-services-overview"></a>ワークフロー サービスの概要
ワークフロー サービスは、ワークフローを使用して実装される [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ベースのサービスです。 ワーク フロー サービスは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] メッセージを送受信するメッセージ アクティビティを使用するワークフローです。 .NET Framework 4.5 では、ワークフロー内からメッセージを送受信できるようにする多数のメッセージ アクティビティが導入されています。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]メッセージング アクティビティ、およびそれらを使用して異なるメッセージ交換パターンを実装する方法を参照してください。[メッセージング アクティビティ](../../../../docs/framework/wcf/feature-details/messaging-activities.md)です。  
  
## <a name="benefits-of-using-workflow-services"></a>ワークフロー サービスを使用する利点  
 アプリケーションが分散型になるにつれ、負荷を軽減させるために、個々のサービスが他のサービスを呼び出す役割を果たすようになっています。 これらの呼び出しを非同期操作として実装すると、コードがやや複雑になります。 エラー処理によって、例外処理と詳細な追跡情報の形式がさらに複雑になります。 一部のサービスには、長時間実行されることが多く、入力を待機する間に貴重なシステム リソースを占有するものがあります。 このような問題があるため、分散アプリケーションは、非常に複雑で、作成と保守が困難であることがよくあります。 ワークフローは、特に外部サービスへの呼び出しなど、非同期操作の連携を表す方法として最適です。 また、実行時間が長いビジネス プロセスを表す場合にも効率的です。 ワークフローが、分散環境でのサービス構築に役立つ資産となるのは、これらの特性があるためです。  
  
## <a name="implementing-a-workflow-service"></a>ワークフロー サービスの実装  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを実装するときは、サービスおよびサービスが送受信するデータを説明する一連のコントラクトを定義します。 データは、データ コントラクトとメッセージ コントラクトで表されます。 WCF サービスもワークフロー サービスも、サービスの説明の一環として、データ コントラクトとメッセージ コントラクトの定義を使用します。 サービス自体は、(WSDL の形で) メタデータを公開して、サービスの操作を説明します。 WCF では、サービス コントラクトと操作コントラクトによって、サービス、およびサービスがサポートする操作を定義します。 ただし、ワークフロー サービスでは、これらのコントラクトはビジネス プロセス自体の一部です。 これらは、コントラクト推論と呼ばれるプロセスによってメタデータとして公開されます。 ワークフロー サービスが <xref:System.ServiceModel.Activities.WorkflowServiceHost> を使用してホストされている場合は、ワークフローで見つかった一連のメッセージ アクティビティに基づいて、ワークフロー定義が確認され、コントラクトが生成されます。 具体的には、次のアクティビティとプロパティが、コントラクトの生成に使用されます。  
  
 <xref:System.ServiceModel.Activities.Receive> アクティビティ  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.Receive.OperationContractName%2A>  --> `System.ServiceModel.Activities.Receive.OperationContractName`
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.Receive.ValueType%2A>  --> `System.ServiceModel.Activities.Receive.ValueType`
  
 <xref:System.ServiceModel.Activities.SendReply> アクティビティ  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.SendReply.ValueType%2A> -->
`xref:System.ServiceModel.Activities.SendReply.ValueType`
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティ  
  
 コントラクト推論の結果は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスと操作コントラクトと同じデータ構造を使用するサービスの説明になります。 この情報を使用して、ワークフロー サービス用に WSDL が公開されます。  
  
> [!NOTE]
>  [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] では、ツール サポートを追加せずに、既存のコントラクト定義を使用してワークフロー サービスを記述することはできません。 ワークフロー サービスのコントラクトは、前述のコントラクト推論プロセスによって作成されます。 ただし、メッセージ コントラクトおよびデータ コントラクトは完全にサポートされます。  
  
## <a name="workflow-services-and-msmq-based-bindings"></a>ワークフロー サービスと MSMQ ベースのバインディング  
 WCF は、2 つの MSMQ ベースのバインディングである <xref:System.ServiceModel.NetMsmqBinding> と <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> を定義します。  MSMQ ベースのバインディングは、多くの場合、ワークフロー サービスと共に使用されます。これは、これらのサービスに、実行時間が長いという性質があるためです。 MSMQ ベースのバインディングには、MSMQ メッセージが有効と見なされる時間を指定する `ValidityDuration` プロパティがあります。 ワークフロー サービスは本質的に実行時間が長いため、ワークフロー サービスによるメッセージの処理が可能になる前に、MSMQ メッセージの有効期間が切れることがあります。 そのため、MSMQ バインディングの有効期間を適切な値に設定することが重要です。 この値は、ワークフローとそのメッセージの処理方法に基づいて選択する必要があります。 たとえば、<xref:System.ServiceModel.Activities.Receive> アクティビティがあり、これに続いて 10 分間実行されるカスタム アクティビティがあり、その後に別の <xref:System.ServiceModel.Activities.Receive> アクティビティがある場合、`ValidityDuration` の適切な値は 10 分を超えることになります。  
  
## <a name="hosting-a-workflow-service"></a>ワークフロー サービスのホスティング  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスと同様、ワークフロー サービスがホストされている必要があります。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは、<xref:System.ServiceModel.ServiceHost> クラスを使用してサービスをホストし、ワークフロー サービスは、<xref:System.ServiceModel.Activities.WorkflowServiceHost> を使用してサービスをホストします。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスと同様に、ワークフロー サービスはさまざまな方法でホストできます。次に例を示します。  
  
-   マネージ [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アプリケーション。  
  
-   インターネット インフォメーション サービス (IIS)。  
  
-   Windows プロセス アクティブ化サービス (WAS)。  
  
-   マネージ Windows サービス。  
  
 マネージ [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アプリケーションまたはマネージ Windows サービスでホストされるワークフロー サービスは、<xref:System.ServiceModel.Activities.WorkflowServiceHost> クラスのインスタンスを作成し、このインスタンスに、<xref:System.ServiceModel.Activities.WorkflowService> プロパティ内のワークフロー定義を含む <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> のインスタンスを渡します。 メッセージ アクティビティを格納するワークフロー定義は、ワークフロー サービスとして公開されます。  
  
 ワークフロー サービスを IIS または WAS でホストするには、ワークフロー サービス定義を格納する .xamlx ファイルを仮想ディレクトリに配置します。 既定のエンドポイント (を使用して<xref:System.ServiceModel.BasicHttpBinding>) が自動的に作成[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][簡略化された構成](../../../../docs/framework/wcf/simplified-configuration.md)です。 また、Web.config ファイルを仮想ディレクトリに配置し、独自のエンドポイントを指定することもできます。 ワークフロー定義がアセンブリ内にある場合は、.svc ファイルを仮想ディレクトリに配置し、ワークフロー アセンブリを App_Code ディレクトリに配置できます。 この .svc ファイルには、サービス ホスト ファクトリと、ワークフロー サービスを実装するクラスを指定する必要があります。 次の例に、サービス ホスト ファクトリを指定し、ワークフロー サービスを実装するクラスを指定する方法を示します。  
  
```  
<%@ServiceHost Factory=" System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory  
Service="EchoService"%>  
```

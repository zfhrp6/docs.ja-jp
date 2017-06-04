---
title: "ワークフロー サービスのホスティング | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2d55217e-8697-4113-94ce-10b60863342e
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# ワークフロー サービスのホスティング
ワークフロー サービスが受信メッセージに応答するには、ワークフロー サービスがホストされている必要があります。ワークフロー サービスは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] メッセージング インフラストラクチャを使用するため、これと似た方法でホストされます。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスと同様に、ワークフロー サービスは、インターネット インフォメーション サービス \(IIS\) または Windows プロセス アクティブ化サービス \(WAS\) の下で、任意のマネージ アプリケーションでホストできます。また、ワークフロー サービスは Windows Server AppFabric でホストできます。Windows Server App Fabric [!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[Windows Server App Fabric のドキュメント](http://go.microsoft.com/fwlink/?LinkId=193037)」、「[AppFabric のホスティング機能](http://go.microsoft.com/fwlink/?LinkId=196494)」、および「[AppFabric ホスティングの概念](http://go.microsoft.com/fwlink/?LinkId=196495)」を参照してください。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスをホストするためのさまざまな方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[ホスティング サービス](../../../../docs/framework/wcf/hosting-services.md)」を参照してください。  
  
## マネージ アプリケーションでのホスト  
 マネージ アプリケーションでワークフロー サービスをホストするには、<xref:System.ServiceModel.Activities.WorkflowServiceHost> クラスを使用します。<xref:System.ServiceModel.Activities.WorkflowServiceHost> コンストラクターにより、シングルトン ワークフロー サービス インスタンス、ワークフロー サービス定義、またはワークフロー メッセージング アクティビティを使用するアクティビティを指定できます。<xref:System.ServiceModel.Activities.WorkflowServiceHost.Open%2A> の呼び出しによって、サービスが受信メッセージのリッスンを開始します。  
  
## IIS または WAS の下でのホスト  
 IIS または WAS の下でワークフロー サービスをホストする場合は、仮想ディレクトリを作成し、サービスとその動作を定義するファイルをその仮想ディレクトリ内に配置します。IIS または WAS の下でワークフローをホストする場合は、いくつかの方法が考えられます。  
  
-   ワークフロー サービスを定義する .xamlx ファイルを、サービス動作、エンドポイント、およびその他の構成要素を指定する Web.config ファイルと共に、IIS\/WAS 仮想ディレクトリに配置します。  
  
-   ワークフロー サービスを定義する .xamlx ファイルを IIS\/WAS 仮想ディレクトリに配置します。この .xamlx ファイルで、公開するエンドポイントが指定されます。エンドポイントは、次の例に示すように、`WorkflowService.Endpoints` 要素で指定されます。  
  
    ```  
    <WorkflowService xmlns="http://schemas.microsoft.com/netfx/2009/xaml/servicemodel"  xmlns:p1="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:sad="clr-namespace:System.Activities.Debugger;assembly=System.Activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
      <WorkflowService.Endpoints>  
        <Endpoint ServiceContractName="IWorkFlowEchoService" AddressUri="">  
          <Endpoint.Binding>  
            <BasicHttpBinding />  
          </Endpoint.Binding>  
        </Endpoint>  
      </WorkflowService.Endpoints>  
    <!-- ... -->  
    </WorkflowService>  
  
    ```  
  
    > [!NOTE]
    >  動作は .xamlx ファイルで指定できないため、動作設定を指定するには Web.config を使用する必要があります。  
  
-   ワークフロー サービスを定義する .xamlx ファイルを IIS\/WAS 仮想ディレクトリに配置します。さらに、.svc ファイルを仮想ディレクトリに配置します。.svc ファイルでは、カスタム Web サービス ホスト ファクトリの指定、カスタム動作の適用、またはカスタムの場所からの構成の読み込みが可能です。  
  
-   WCF メッセージング アクティビティを使用するアクティビティを含むアセンブリを IIS\/WAS 仮想ディレクトリに配置します。  
  
 ワークフロー サービスを定義する .xamlx ファイルには、\<`Service`\> ルート要素、または <xref:System.Workflow.ComponentModel.Activity> から派生する型を含むルート要素が含まれている必要があります。[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] アクティビティ テンプレートを使用する場合は、.xamlx ファイルが作成されます。WCF ワークフロー サービス テンプレートを使用する場合は、.xamlx ファイルが作成されます。  
  
## Windows Server AppFabric でのワークフロー サービスのホスティング  
 Windows Server AppFabric でのワークフロー サービスのホスティングは IIS\/WAS でのホスティングと同じ方法で行われます。唯一の違いは、Windows Server AppFabric がインストールされるということです。Windows Server AppFabric には、PowerShell コマンドと同様に、インターネット インフォメーション サービス マネージャーに追加されるツールが用意されています。これらのツールによって、ワークフロー サービスおよび WCF サービスの配置、管理、および追跡を簡略化することができます。.Windows Server AppFabric [!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=193037)」を参照してください。  
  
## カスタム アクティビティの参照  
 カスタム アクティビティの参照は、\<`System.Web.Compilation`\> の下の \<`Assemblies`\> セクションに追加する必要があります。これにより、この参照がアプリケーション ドメインに読み込まれ、XAML デシリアライザーが型を見つけることができます。これらの設定をコンピューター上のすべてのアプリケーションに適用する必要がある場合は、アプリケーション レベルまたはルートの Web.config で設定できます。  
  
## 配置  
 配置作業を容易にするために、Web 配置ツールが作成されています。このツールを使用すると、アプリケーションの IIS 6.0 および IIS 7.0 間での移行や、サーバー ファームの同期のほか、Web アプリケーションのパッケージ化、アーカイブ、および配置を実行できます。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][、MS 配置ツールを参照してください。](http://go.microsoft.com/fwlink/?LinkId=178690)  
  
## 参照  
 [ワークフロー サービス ホストの内部](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)   
 [WorkflowServiceHost の構成](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)
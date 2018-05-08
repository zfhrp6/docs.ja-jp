---
title: ワークフロー サービスのホスティング
ms.date: 03/30/2017
ms.assetid: 2d55217e-8697-4113-94ce-10b60863342e
ms.openlocfilehash: 02d77b851dcd35108668ee6a42022e9721b84bd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="hosting-workflow-services"></a>ワークフロー サービスのホスティング
ワークフロー サービスが受信メッセージに応答するには、ワークフロー サービスがホストされている必要があります。 ワークフロー サービスは WCF メッセージング インフラストラクチャを使用するため、これと似た方法でホストされます。 WCF サービスと同様に、インターネット インフォメーション サービス (IIS)、または Windows プロセス アクティブ化サービス (WAS) の下で、すべての管理対象のアプリケーションでワークフロー サービスをホストできます。 また、ワークフロー サービスは Windows Server AppFabric でホストできます。 Windows Server App Fabric の詳細については、次を参照してください。 [Windows Server App Fabric ドキュメント](http://go.microsoft.com/fwlink/?LinkId=193037)、 [AppFabric のホスティング機能](http://go.microsoft.com/fwlink/?LinkId=196494)、および[AppFabric ホスティングの概念](http://go.microsoft.com/fwlink/?LinkId=196495)です。 WCF をホストするさまざまな方法の詳細については、「」を参照をサービスの[ホスティング サービス](../../../../docs/framework/wcf/hosting-services.md)です。  
  
## <a name="hosting-in-a-managed-application"></a>マネージ アプリケーションでのホスト  
 マネージ アプリケーションでワークフロー サービスをホストするには、<xref:System.ServiceModel.Activities.WorkflowServiceHost> クラスを使用します。 <xref:System.ServiceModel.Activities.WorkflowServiceHost> コンストラクターにより、シングルトン ワークフロー サービス インスタンス、ワークフロー サービス定義、またはワークフロー メッセージング アクティビティを使用するアクティビティを指定できます。 呼び出す <<!--zz xref:System.ServiceModel.Activities.WorkflowServiceHost.Open%2A--> `System.ServiceModel.Activities.WorkflowServiceHost.Open`> サービスが受信メッセージのリッスンを開始します。  
  
## <a name="hosting-under-iis-or-was"></a>IIS または WAS の下でのホスト  
 IIS または WAS の下でワークフロー サービスをホストする場合は、仮想ディレクトリを作成し、サービスとその動作を定義するファイルをその仮想ディレクトリ内に配置します。 IIS または WAS の下でワークフローをホストする場合は、いくつかの方法が考えられます。  
  
-   ワークフロー サービスを定義する .xamlx ファイルを、サービス動作、エンドポイント、およびその他の構成要素を指定する Web.config ファイルと共に、IIS/WAS 仮想ディレクトリに配置します。  
  
-   ワークフロー サービスを定義する .xamlx ファイルを IIS/WAS 仮想ディレクトリに配置します。 この .xamlx ファイルで、公開するエンドポイントが指定されます。 エンドポイントは、次の例に示すように、`WorkflowService.Endpoints` 要素で指定されます。  
  
    ```xml  
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
  
-   ワークフロー サービスを定義する .xamlx ファイルを IIS/WAS 仮想ディレクトリに配置します。 さらに、.svc ファイルを仮想ディレクトリに配置します。 .svc ファイルでは、カスタム Web サービス ホスト ファクトリの指定、カスタム動作の適用、またはカスタムの場所からの構成の読み込みが可能です。  
  
-   WCF メッセージング アクティビティを使用するアクティビティを含むアセンブリを IIS/WAS 仮想ディレクトリに配置します。  
  
 ワークフロー サービスを定義する .xamlx ファイルを含める必要があります、<`Service`> ルート要素またはから派生した任意の型を含むルート要素<xref:System.Workflow.ComponentModel.Activity>です。 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] アクティビティ テンプレートを使用する場合は、.xamlx ファイルが作成されます。 WCF ワークフロー サービス テンプレートを使用する場合は、.xamlx ファイルが作成されます。  
  
## <a name="hosting-workflow-services-under-windows-server-app-fabric"></a>Windows Server AppFabric でのワークフロー サービスのホスティング  
 Windows Server AppFabric でのワークフロー サービスのホスティングは IIS/WAS でのホスティングと同じ方法で行われます。 唯一の違いは、Windows Server AppFabric がインストールされるということです。 Windows Server AppFabric には、PowerShell コマンドと同様に、インターネット インフォメーション サービス マネージャーに追加されるツールが用意されています。 これらのツールによって、ワークフロー サービスおよび WCF サービスの配置、管理、および追跡を簡略化することができます。 である必要があります。 Windows Server App Fabric の詳細については、次を参照してください[Windows Server App Fabric。](http://go.microsoft.com/fwlink/?LinkId=193037)  
  
## <a name="referencing-custom-activities"></a>カスタム アクティビティの参照  
 カスタム活動項目への参照を追加する必要があります、<`Assemblies`> セクションの下にある <`System.Web.Compilation`> アプリケーション ドメインに読み込まれ、XAML デシリアライザーは、型を検索できるようにします。 これらの設定をコンピューター上のすべてのアプリケーションに適用する必要がある場合は、アプリケーション レベルまたはルートの Web.config で設定できます。  
  
## <a name="deployment"></a>配置  
 配置作業を容易にするために、Web 配置ツールが作成されています。 このツールを使用すると、アプリケーションの IIS 6.0 および IIS 7.0 間での移行や、サーバー ファームの同期のほか、Web アプリケーションのパッケージ化、アーカイブ、および配置を実行できます。 詳細については、次を参照してください[MS 配置ツール。](http://go.microsoft.com/fwlink/?LinkId=178690)  
  
## <a name="see-also"></a>関連項目  
 [ワークフロー サービス ホストの内部](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 [WorkflowServiceHost の構成](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)

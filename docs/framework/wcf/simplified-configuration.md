---
title: 簡略化された構成
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 9f35a5f4fa4ae6be63bd75a24f58b56dd236ee9c
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="simplified-configuration"></a>簡略化された構成
Windows Communication Foundation (WCF) サービスを構成すると、複雑なタスクを指定できます。 さまざまなオプションがあり、どの設定が必要であるかをいつでも簡単に判断できるとは限りません。 構成ファイルは、WCF サービスの柔軟性を向上させ、それらもは発見しにくい問題の多くのソースです。 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] では、このような問題に対応し、サービス構成の規模と複雑さを軽減する手段を提供しています。  
  
## <a name="simplified-configuration"></a>簡略化された構成  
 WCF サービス構成ファイルで、<`system.serviceModel`> セクションが含まれています、<`service`> ホストされているサービスごとの要素。 <`service`> 要素には、各サービスに対して公開されるエンドポイントと、必要に応じて一連のサービス動作を指定する <`endpoint`> 要素が含まれます。 <`endpoint`> 要素は、エンドポイントが公開するアドレス、バインド、およびコントラクトと、必要に応じてバインド構成およびエンドポイントの動作を指定します。 <`system.serviceModel`> セクションには、サービスまたはエンドポイントの動作を指定できる <`behaviors`> 要素も含まれます。 構成ファイルの <`system.serviceModel`> セクションの例を次に示します。  
  
```  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true">  
        <serviceDebug includeExceptionDetailInFaults="false">  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <bindings>  
   <basicHttpBinding>  
      <binding name=MyBindingConfig"  
               maxBufferSize="100"  
               maxReceiveBufferSize="100" />  
   </basicHttpBinding>  
   </bindings>   <services>  
    <service behaviorConfiguration="MyServiceBehavior"  
             name="MyService">  
      <endpoint address=""  
                binding="basicHttpBinding"  
                contract="ICalculator"  
                bindingConfiguration="MyBindingConfig" />  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange"/>  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 要件を削除することで簡単に WCF サービスを構成できるように、<`service`> 要素。 <`service`> セクションを追加したり、<`service`> セクションにエンドポイントを追加したりせず、サービスがプログラムを使用してエンドポイントを定義しない場合は、一連の既定のエンドポイントが自動的にサービスに追加されます。この場合、各サービスのベース アドレスに対して 1 つ、サービスによって実装される各コントラクトに対して 1 つのエンドポイントが追加されます。 これらの各エンドポイントでは、エンドポイント アドレスがベース アドレスに対応し、バインドがベース アドレス スキームで決定されます。また、コントラクトは、サービスによって実装されるコントラクトになります。 エンドポイントまたはサービスの動作を指定する必要も、バインド設定を変更する必要もない場合、サービス構成ファイルを指定する必要はありません。 サービスが 2 つのコントラクトを実装し、ホストが HTTP トランスポートと TCP トランスポートの両方を有効にしている場合、サービス ホストは、それぞれのトランスポートを使用する各コントラクトに対して 1 つずつ、合計 4 つの既定のエンドポイントを作成します。 既定のエンドポイントを作成するには、使用するバインドをサービス ホストに伝える必要があります。 これらの設定は、<`protocolMappings`> セクション内の <`system.serviceModel`> セクションに指定します。 <`protocolMappings`> セクションには、バインドの型にマップされたトランスポート プロトコル スキームの一覧が設定されます。 サービス ホストは、渡されたベース アドレスを使用して、使用するバインドを決定します。 次の例では、<`protocolMappings`> 要素を使用しています。  
  
> [!WARNING]
>  バインディングまたは動作のような既定の構成要素を変更すると、構成階層の下のレベルで定義されたサービスはこれらの既定のバインディングおよび動作を使用している可能性があるため、影響を受けることがあります。 したがって、既定のバインディングおよび動作を変更する場合は、これらの変更が階層の他のサービスに影響を与える可能性があることに注意する必要があります。  
  
> [!NOTE]
>  インターネット インフォメーション サービス (IIS) または Windows プロセス アクティブ化サービス (WAS) にホストされるサービスは、仮想ディレクトリをベース アドレスとして使用します。  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 前の例では、"http" スキームで始まるベース アドレスのエンドポイントは、<xref:System.ServiceModel.BasicHttpBinding> を使用します。 "net.tcp" スキームで始まるベース アドレスのエンドポイントは、<xref:System.ServiceModel.NetTcpBinding> を使用します。 ローカルの App.config または Web.config ファイルの設定はオーバーライドできます。  
  
 <`protocolMappings`> セクション内の各要素は、スキームとバインドを指定する必要があります。 必要に応じて、構成ファイルの <`bindingConfiguration`> セクション内で、バインド構成を指定する `bindings` 属性を指定できます。 `bindingConfiguration` が指定されていない場合は、適切なバインド型の匿名バインド構成が使用されます。  
  
 既定のエンドポイントでは、<`behavior`> セクション内の匿名の <`serviceBehaviors`> セクションを使用して、サービスの動作が構成されます。 サービスの動作の構成には、<`behavior`> 内の、名前が付けられていない <`serviceBehaviors`> 要素が使用されます。 たとえば、次の構成ファイルでは、ホスト内のすべてのサービスで、サービス メタデータの公開が有効になります。  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <!-- No <service> tag is necessary. Default endpoints are added to the service -->  
    <!-- The service behavior with name="" is picked up by the service -->  
 </system.serviceModel>  
```  
  
 エンドポイントの動作は、<`behavior`> セクション内の匿名の <`serviceBehaviors`> セクションを使用して構成されます。  
  
 以下は、このトピックの最初にある例と同じ内容ですが、簡略化された構成モデルを使用している構成ファイルの例です。  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="false"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <bindings>  
       <basicHttpBinding>  
          <binding maxBufferSize="100"  
                   maxReceiveBufferSize="100" />  
       </basicHttpBinding>  
    </bindings>    <!-- No <service> tag is necessary. Default endpoints will be added to the service -->  
    <!-- The service behavior with name="" will be picked up by the service -->  
    <protocolMapping>  
      <add scheme="http"     binding="basicHttpBinding" / </protocolMapping>  
  </system.serviceModel>  
```  
  
> [!IMPORTANT]
>  この機能は、WCF サービス構成にのみ適用され、クライアント構成には適用されません。 ほとんどの場合、WCF クライアント構成は、svcutil.exe などのツールを使用したり、Visual Studio からサービス参照を追加したりすることで生成されます。 WCF クライアントを手動で構成している場合は、追加する必要があります、\<クライアント > 要素を構成し、呼び出すエンドポイントを指定します。  
  
## <a name="see-also"></a>関連項目  
 [構成ファイルを使用してサービスを構成する方法](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [サービスのバインディングの構成](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)  
 [システムが提供するバインディングの構成](../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [サービスの構成](../../../docs/framework/wcf/configuring-services.md)  
 [Windows Communication Foundation アプリケーションの構成](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 [コード内での WCF サービスの構成](../../../docs/framework/wcf/configuring-wcf-services-in-code.md)

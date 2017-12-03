---
title: "コード内での WCF サービスの構成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c05cc5947a36bbe8573c5308cdfbbe3f6c990815
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-wcf-services-in-code"></a>コード内での WCF サービスの構成
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] では、開発者が構成ファイルまたはコードを使用してサービスを構成できます。  構成ファイルは、サービスを配置した後に構成する必要がある場合に便利です。 構成ファイルを使用する場合、IT 専門家は構成ファイルを更新するだけで、再コンパイルの必要はありません。 ただし、構成ファイルの管理は複雑で難しくなる場合があります。 構成ファイルのデバッグはサポートされていません。また、構成要素は名前で参照されるため、構成ファイルの作成時にエラーが発生しやすく、構成ファイルの作成が困難になります。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] では、コードでサービスを構成することもできます。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] の以前のバージョン (4.0 以前) では、自己ホスト型のシナリオであれば、コードで簡単にサービスを構成できました。また、<xref:System.ServiceModel.ServiceHost> クラスを使用すると、ServiceHost.Open を呼び出す前にエンドポイントと動作を構成できました。 ただし、Web ホストのシナリオでは、<xref:System.ServiceModel.ServiceHost> クラスに直接アクセスできません。 Web ホスト サービスを構成するには、`System.ServiceModel.ServiceHostFactory` を作成して必要な構成を実行する <xref:System.ServiceModel.Activation.ServiceHostFactory> を作成する必要がありました。 .NET 4.5 以降では、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] を使用すると、自己ホスト型サービスと Web ホスト サービスの両方をコードで簡単に構成できます。  
  
## <a name="the-configure-method"></a>Configure メソッド  
 サービス実装クラスで、次のシグネチャを持つ `Configure` という名前のパブリックな静的メソッドを定義します。  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 Configure メソッドは、開発者がエンドポイントおよび動作を追加できるようにする <xref:System.ServiceModel.ServiceConfiguration> インスタンスを受け取ります。 このメソッドは、サービス ホストが開かれる前に、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] によって呼び出されます。 app.config ファイルまたは web.config ファイルで指定されたすべてのサービスの構成設定は、定義されている場合、無視されます。  
  
 次のコード スニペットは、`Configure` メソッドを定義し、サービス エンドポイント、エンドポイントの動作、およびサービスの動作を追加する方法を示しています。  
  
```csharp  
public class Service1 : IService1  
    {  
        public static void Configure(ServiceConfiguration config)  
        {  
            ServiceEndpoint se = new ServiceEndpoint(new ContractDescription("IService1"), new BasicHttpBinding(), new EndpointAddress("basic"));  
            se.Behaviors.Add(new MyEndpointBehavior());  
            config.AddServiceEndpoint(se);  
  
            config.Description.Behaviors.Add(new ServiceMetadataBehavior { HttpGetEnabled = true });  
            config.Description.Behaviors.Add(new ServiceDebugBehavior { IncludeExceptionDetailInFaults = true });  
        }  
  
        public string GetData(int value)  
        {  
            return string.Format("You entered: {0}", value);  
        }  
  
        public CompositeType GetDataUsingDataContract(CompositeType composite)  
        {  
            if (composite == null)  
            {  
                throw new ArgumentNullException("composite");  
            }  
            if (composite.BoolValue)  
            {  
                composite.StringValue += "Suffix";  
            }  
            return composite;  
        }  
    }  
```  
  
 サービスで https などのプロトコルを有効にするには、プロトコルを使用するエンドポイントを明示的に追加するか、ServiceConfiguration.EnableProtocol(Binding) を呼び出すことによって自動的にエンドポイントを追加します。このメソッドは、プロトコルおよび定義された各サービス コントラクトと互換性がある各ベース アドレスのエンドポイントを追加します。 次のコードは、ServiceConfiguration.EnableProtocol メソッドを使用する方法を示しています。  
  
```csharp  
public class Service1 : IService1   
{   
    public string GetData(int value);   
    public static void Configure(ServiceConfiguration config)   
    {   
        // Enable "Add Service Reference" support   
       config.Description.Behaviors.Add( new ServiceMetadataBehavior { HttpGetEnabled = true });   
       // set up support for http, https, net.tcp, net.pipe   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new NetTcpBinding());   
       config.EnableProtocol(new NetNamedPipeBinding());   
       // add an extra BasicHttpBinding endpoint at http:///basic   
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");   
    }   
}   
```  
  
 設定、<`protocolMappings`> セクションをアプリケーション エンドポイントが追加されていない場合にのみ使用が、<xref:System.ServiceModel.ServiceConfiguration>プログラムでします。呼び出すことによって、既定のアプリケーション構成ファイルからサービスの構成を読み込むことができます必要に応じて<xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A>し、設定を変更します。 <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> クラスを使って、集中化された構成から構成を読み込むこともできます。 これを実装する方法を次のコードに示します。  
  
```  
public class Service1 : IService1   
{   
    public void DoWork();   
    public static void Configure(ServiceConfiguration config)   
    {   
          config.LoadFromConfiguration(ConfigurationManager.OpenMappedExeConfiguration(new ExeConfigurationFileMap { ExeConfigFilename = @"c:\sharedConfig\MyConfig.config" }, ConfigurationUserLevel.None));   
    }   
}  
```  
  
> [!IMPORTANT]
>  なお<xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A>を無視 <`host`> 内の設定、<`service`> のタグ <`system.serviceModel`>。 概念的には、<`host`> は、ホストの構成、いないサービス構成、およびそのについて構成するメソッドが実行される前に読み込まれたを取得します。  
  
## <a name="see-also"></a>関連項目  
 [構成ファイルを使用してサービスを構成する方法](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [クライアントの動作の構成](../../../docs/framework/wcf/configuring-client-behaviors.md)  
 [簡略化された構成](../../../docs/framework/wcf/simplified-configuration.md)  
 [構成ベースのアクティブ化](../../../docs/framework/wcf/samples/configuration-based-activation.md)  
 [構成](../../../docs/framework/wcf/samples/configuration-sample.md)  
 [IIS と WAS における構成ベースのアクティブ化](../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)  
 [構成とメタデータのサポート](../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)  
 [構成](../../../docs/framework/wcf/diagnostics/exceptions-reference/configuration.md)  
 [方法: 構成でサービス バインディングを指定する](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
 [方法: 構成でサービス エンドポイントの作成](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 [方法: 構成ファイルを使用して、サービスのメタデータを公開](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [方法: 構成でクライアント バインディングを指定する](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)

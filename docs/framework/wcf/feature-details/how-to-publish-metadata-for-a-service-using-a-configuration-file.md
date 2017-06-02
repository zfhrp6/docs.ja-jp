---
title: "方法: 構成ファイルを使用してサービスのメタデータを公開する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
caps.latest.revision: 24
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 24
---
# 方法: 構成ファイルを使用してサービスのメタデータを公開する
このトピックは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスのメタデータを公開する手段を示す&2; つの「方法」トピックのうちの&1; つです。 構成ファイルとコードを使用して、サービスがメタデータを公開する手段を指定する方法は&2; つあります。 このトピックでは、構成ファイルを使用してサービスのメタデータを公開する方法について説明します。  
  
> [!CAUTION]
>  このトピックでは、セキュリティで保護されていない方法でメタデータを公開する方法について説明します。 クライアントは、サービスからメタデータを取得できます。 安全な方法でメタデータを公開するサービスを必要とする場合は、次を参照してください。[カスタム セキュリティで保護されたメタデータ エンドポイント](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)します。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]コードでは、メタデータの公開を参照してください[方法: サービスを使用してコードのメタデータを公開](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)します。 メタデータを公開すると、クライアントが `?wsdl` クエリ文字列を使用した WS-Transfer GET 要求または HTTP/GET 要求によりメタデータを取得できるようになります。 コードが機能するかどうかを確認するために、基本的な [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを作成します。 簡略化のため、次のコードに基本的な自己ホスト型サービスが用意されています。  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));   
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
 これは、構成ファイルを使用して構成された自己ホスト型サービスです。 以下の構成ファイルをベースとして使用します。  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Metadata.Example.SimpleService">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
      </service>  
    </services>  
    <behaviors>  
  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
  
```  
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a>アプリケーション構成ファイルを使用して WCF サービスのメタデータを公開するには  
  
1.  
          `</services>` 要素を閉じた後、App.config ファイル内に `<behaviors>` 要素を作成します。  
  
  
  
2.  
          `<behaviors>` 要素内に `<serviceBehaviors>` 要素を追加します。  
  
  
  
3.  
          `<behavior>`要素に `<serviceBehaviors>` 要素を追加し、`name` 要素の `<behavior>` 属性に値を指定します。  
  
  
  
4.  
          `<serviceMetadata>` 要素を `<behavior>` 要素に追加します。 `httpGetEnabled` 属性を `true` に設定し、`policyVersion` 属性を Policy15 に設定します。 `httpGetEnabled` により、サービスは HTTP GET 要求からのメタデータ要求に応答できるようになります。 `policyVersion` は、サービスに対して、WS-Policy 1.5 準拠でメタデータを生成するように指示します。  
  
  
  
5.  次のコード例に示すように、`behaviorConfiguration` 要素に `<service>` 属性を追加し、手順 1. で追加した `name` 要素の `<behavior>` 属性を指定します。  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
        ...  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy15" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
6.  1 つ以上の `<endpoint>` 要素を追加して、コントラクトを `IMetadataExchange` に設定します。コード例を次に示します。  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    ```  
  
7.  前の手順で追加したメタデータ エンドポイントについて、`binding` 属性に次のいずれかの値を設定します。  
  
    -   HTTP 公開の場合、`mexHttpBinding`  
  
    -   HTTPS 公開の場合、`mexHttpsBinding`  
  
    -   名前付きパイプ公開の場合、`mexNamedPipeBinding`  
  
    -   TCP 公開の場合、`mexTcpBinding`  
  
8.  前の手順で追加したメタデータ エンドポイントについて、次のいずれかに等しいアドレスを設定します。  
  
    -   ベース アドレスがメタデータ バインディングと同じ場合に、公開ポイントとしてホスト アプリケーションのベース アドレスを使用するための空の文字列  
  
    -   ホスト アプリケーションにベース アドレスがある場合、相対アドレス  
  
    -   絶対アドレス  
  
9. コンソール アプリケーションのビルドと実行  
  
10. Internet Explorer を使用してサービスのベース アドレス (この例では、http://localhost:8001/MetadataSample) を参照し、メタデータの公開が有効になっていることを確認します。 有効になっていない場合は、"このサービスのメタデータ公開は現在は無効になっています。" というメッセージが結果ページの上部に表示されます。  
  
### <a name="to-use-default-endpoints"></a>既定のエンドポイントを使用するには  
  
1.  既定のエンドポイントを使用するサービスのメタデータを構成するには、指定、 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>の構成ファイルの前の例のように、任意のエンドポイントを指定しません。 構成ファイルは、次のようになります。  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="SimpleServiceBehavior">  
              <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     サービスがあるため、 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>で、`httpGetEnabled`に設定`true`サービスが有効な場合、メタデータの公開、およびエンドポイントが明示的に追加されていないため、ランタイムは既定のエンドポイントを追加します。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]既定のエンドポイント、バインディング、および動作を参照してください[簡略化された構成](../../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)します。  
  
## <a name="example"></a>例  
 次のコード例は、基本的な [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの実装と、このサービスのメタデータを公開する構成ファイルを示しています。  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));   
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>   
 [方法: マネージ アプリケーションで WCF サービスをホスト](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)   
 [自己ホストします。](../../../../docs/framework/wcf/samples/self-host.md)   
 [メタデータ アーキテクチャの概要](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)   
 [メタデータを使用します。](../../../../docs/framework/wcf/feature-details/using-metadata.md)   
 [方法: コードを使用して、サービスのメタデータを公開](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
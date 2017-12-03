---
title: "方法: 構成ファイルを使用してサービスのメタデータを公開する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 16e278fd0eb227ddd382157d38c7370e604c35d3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a><span data-ttu-id="72411-102">方法: 構成ファイルを使用してサービスのメタデータを公開する</span><span class="sxs-lookup"><span data-stu-id="72411-102">How to: Publish Metadata for a Service Using a Configuration File</span></span>
<span data-ttu-id="72411-103">このトピックは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスのメタデータを公開する手段を示す 2 つの「方法」トピックのうちの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="72411-103">This is one of two how-to topics that demonstrate publishing metadata for a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span></span> <span data-ttu-id="72411-104">構成ファイルとコードを使用して、サービスがメタデータを公開する手段を指定する方法は 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="72411-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="72411-105">このトピックでは、構成ファイルを使用してサービスのメタデータを公開する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="72411-105">This topic shows how to publish metadata for a service using a configuration file.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="72411-106">このトピックでは、セキュリティで保護されていない方法でメタデータを公開する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="72411-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="72411-107">クライアントは、サービスからメタデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="72411-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="72411-108">安全な方法でメタデータを公開するようにサービスを必要とする場合は、次を参照してください。[カスタム セキュリティで保護されたメタデータ エンドポイント](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)です。</span><span class="sxs-lookup"><span data-stu-id="72411-108">If you require your service to publish metadata in a secure manner, see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="72411-109">コードでは、メタデータの公開を参照してください[する方法: サービスを使用してコードのメタデータを公開](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)です。</span><span class="sxs-lookup"><span data-stu-id="72411-109"> publishing metadata in code, see [How to: Publish Metadata for a Service Using Code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span></span> <span data-ttu-id="72411-110">メタデータを公開すると、クライアントが `?wsdl` クエリ文字列を使用した WS-Transfer GET 要求または HTTP/GET 要求によりメタデータを取得できるようになります。</span><span class="sxs-lookup"><span data-stu-id="72411-110">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="72411-111">コードが機能するかどうかを確認するために、基本的な [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="72411-111">To be sure that the code is working, create a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="72411-112">簡略化のため、次のコードに基本的な自己ホスト型サービスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="72411-112">For simplicity, a basic self-hosted service is provided in the following code.</span></span>  
  
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
  
 <span data-ttu-id="72411-113">これは、構成ファイルを使用して構成された自己ホスト型サービスです。</span><span class="sxs-lookup"><span data-stu-id="72411-113">This service is a self-hosted service, which is configured using a configuration file.</span></span> <span data-ttu-id="72411-114">以下の構成ファイルをベースとして使用します。</span><span class="sxs-lookup"><span data-stu-id="72411-114">The following configuration file serves as a starting point.</span></span>  
  
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
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a><span data-ttu-id="72411-115">アプリケーション構成ファイルを使用して WCF サービスのメタデータを公開するには</span><span class="sxs-lookup"><span data-stu-id="72411-115">To publish metadata for a WCF service using an application configuration file</span></span>  
  
1.  <span data-ttu-id="72411-116">`</services>` 要素を閉じた後、App.config ファイル内に `<behaviors>` 要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="72411-116">Within the App.config file, after the closing `</services>` element, create a `<behaviors>` element.</span></span>  
  
  
  
2.  <span data-ttu-id="72411-117">`<behaviors>` 要素内に `<serviceBehaviors>` 要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="72411-117">Within the `<behaviors>` element, add a `<serviceBehaviors>` element.</span></span>  
  
  
  
3.  <span data-ttu-id="72411-118">`<behavior>`要素に `<serviceBehaviors>` 要素を追加し、`name` 要素の `<behavior>` 属性に値を指定します。</span><span class="sxs-lookup"><span data-stu-id="72411-118">Add a `<behavior>` element to the `<serviceBehaviors>` element and specify a value for the `name` attribute of the `<behavior>` element.</span></span>  
  
  
  
4.  <span data-ttu-id="72411-119">`<serviceMetadata>` 要素を `<behavior>` 要素に追加します。</span><span class="sxs-lookup"><span data-stu-id="72411-119">Add a `<serviceMetadata>` element to the `<behavior>` element.</span></span> <span data-ttu-id="72411-120">`httpGetEnabled` 属性を `true` に設定し、`policyVersion` 属性を Policy15 に設定します。</span><span class="sxs-lookup"><span data-stu-id="72411-120">Set the `httpGetEnabled` attribute to `true` and the `policyVersion` attribute to Policy15.</span></span> <span data-ttu-id="72411-121">`httpGetEnabled` により、サービスは HTTP GET 要求からのメタデータ要求に応答できるようになります。</span><span class="sxs-lookup"><span data-stu-id="72411-121">`httpGetEnabled` allows the service to respond to metadata requests made by an HTTP GET request.</span></span> <span data-ttu-id="72411-122">`policyVersion` は、サービスに対して、WS-Policy 1.5 準拠でメタデータを生成するように指示します。</span><span class="sxs-lookup"><span data-stu-id="72411-122">`policyVersion` tells the service to conform to WS-Policy 1.5 when generating metadata.</span></span>  
  
  
  
5.  <span data-ttu-id="72411-123">次のコード例に示すように、`behaviorConfiguration` 要素に `<service>` 属性を追加し、手順 1. で追加した `name` 要素の `<behavior>` 属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="72411-123">Add a `behaviorConfiguration` attribute to the `<service>` element and specify the `name` attribute of the `<behavior>` element added in step 1, as shown in the following code example.</span></span>  
  
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
  
6.  <span data-ttu-id="72411-124">1 つ以上の `<endpoint>` 要素を追加して、コントラクトを `IMetadataExchange` に設定します。コード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="72411-124">Add one or more `<endpoint>` elements with the contract set to `IMetadataExchange`, as shown in the following code example.</span></span>  
  
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
  
7.  <span data-ttu-id="72411-125">前の手順で追加したメタデータ エンドポイントについて、`binding` 属性に次のいずれかの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="72411-125">For the metadata endpoints added in the previous step, set the `binding` attribute to one of the following:</span></span>  
  
    -   <span data-ttu-id="72411-126">HTTP 公開の場合、`mexHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="72411-126">`mexHttpBinding` for HTTP publication.</span></span>  
  
    -   <span data-ttu-id="72411-127">HTTPS 公開の場合、`mexHttpsBinding`</span><span class="sxs-lookup"><span data-stu-id="72411-127">`mexHttpsBinding` for HTTPS publication.</span></span>  
  
    -   <span data-ttu-id="72411-128">名前付きパイプ公開の場合、`mexNamedPipeBinding`</span><span class="sxs-lookup"><span data-stu-id="72411-128">`mexNamedPipeBinding` for named pipe publication.</span></span>  
  
    -   <span data-ttu-id="72411-129">TCP 公開の場合、`mexTcpBinding`</span><span class="sxs-lookup"><span data-stu-id="72411-129">`mexTcpBinding` for TCP publication.</span></span>  
  
8.  <span data-ttu-id="72411-130">前の手順で追加したメタデータ エンドポイントについて、次のいずれかに等しいアドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="72411-130">For the metadata endpoints added in a previous step, set the address equal to:</span></span>  
  
    -   <span data-ttu-id="72411-131">ベース アドレスがメタデータ バインディングと同じ場合に、公開ポイントとしてホスト アプリケーションのベース アドレスを使用するための空の文字列</span><span class="sxs-lookup"><span data-stu-id="72411-131">An empty string to use the host application's base address as the publication point if the base address is the same as the metadata binding.</span></span>  
  
    -   <span data-ttu-id="72411-132">ホスト アプリケーションにベース アドレスがある場合、相対アドレス</span><span class="sxs-lookup"><span data-stu-id="72411-132">A relative address if the host application has a base address.</span></span>  
  
    -   <span data-ttu-id="72411-133">絶対アドレス</span><span class="sxs-lookup"><span data-stu-id="72411-133">An absolute address.</span></span>  
  
9. <span data-ttu-id="72411-134">コンソール アプリケーションのビルドと実行</span><span class="sxs-lookup"><span data-stu-id="72411-134">Build and run the console application.</span></span>  
  
10. <span data-ttu-id="72411-135">Internet Explorer を使用してサービスのベース アドレス (この例では、http://localhost:8001/MetadataSample) を参照し、メタデータの公開が有効になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="72411-135">Use Internet Explorer to browse to the base address of the service (http://localhost:8001/MetadataSample in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="72411-136">有効になっていない場合は、"このサービスのメタデータ公開は現在は無効になっています。" というメッセージが結果ページの上部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="72411-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
### <a name="to-use-default-endpoints"></a><span data-ttu-id="72411-137">既定のエンドポイントを使用するには</span><span class="sxs-lookup"><span data-stu-id="72411-137">To use default endpoints</span></span>  
  
1.  <span data-ttu-id="72411-138">既定のエンドポイントを使用するサービスでメタデータを構成するには、前の例のように、構成ファイルで <xref:System.ServiceModel.Description.ServiceMetadataBehavior> を指定します。ただし、エンドポイントは指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="72411-138">To configure metadata on a service that uses default endpoints, specify the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> in the configuration file as in the previous example, but do not specify any endpoints.</span></span> <span data-ttu-id="72411-139">構成ファイルは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="72411-139">The configuration file would then look like this.</span></span>  
  
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
  
     <span data-ttu-id="72411-140">サービスの <xref:System.ServiceModel.Description.ServiceMetadataBehavior> では `httpGetEnabled` が `true` に設定されているため、サービスではメタデータの公開が有効になっています。また、エンドポイントが明示的に追加されていないため、ランタイムは既定のエンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="72411-140">Because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> with the `httpGetEnabled` set to `true`, the service has publishing metadata enabled, and because no endpoints were explicitly added, the runtime adds the default endpoints.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="72411-141">既定のエンドポイント、バインディング、および動作を参照してください[簡略化された構成](../../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="72411-141"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="72411-142">例</span><span class="sxs-lookup"><span data-stu-id="72411-142">Example</span></span>  
 <span data-ttu-id="72411-143">次のコード例は、基本的な [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの実装と、このサービスのメタデータを公開する構成ファイルを示しています。</span><span class="sxs-lookup"><span data-stu-id="72411-143">The following code example shows the implementation of a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service and the configuration file that publishes metadata for the service.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="72411-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="72411-144">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 [<span data-ttu-id="72411-145">方法: マネージ アプリケーションで WCF サービスをホストする</span><span class="sxs-lookup"><span data-stu-id="72411-145">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [<span data-ttu-id="72411-146">自己ホストします。</span><span class="sxs-lookup"><span data-stu-id="72411-146">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)  
 [<span data-ttu-id="72411-147">メタデータ アーキテクチャの概要</span><span class="sxs-lookup"><span data-stu-id="72411-147">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)  
 [<span data-ttu-id="72411-148">メタデータを使用します。</span><span class="sxs-lookup"><span data-stu-id="72411-148">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [<span data-ttu-id="72411-149">方法: コードを使用して、サービスのメタデータを公開</span><span class="sxs-lookup"><span data-stu-id="72411-149">How to: Publish Metadata for a Service Using Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)

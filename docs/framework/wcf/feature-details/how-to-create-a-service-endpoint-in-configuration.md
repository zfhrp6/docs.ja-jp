---
title: '方法 : 構成にサービス エンドポイントを作成する'
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: f1a2696e2aeb8d0c704d008b064a8f8c8b0745d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490228"
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a><span data-ttu-id="61677-102">方法 : 構成にサービス エンドポイントを作成する</span><span class="sxs-lookup"><span data-stu-id="61677-102">How to: Create a Service Endpoint in Configuration</span></span>
<span data-ttu-id="61677-103">エンドポイントは、Windows Communication Foundation (WCF) サービスを提供する機能へのアクセスを持つクライアントを提供します。</span><span class="sxs-lookup"><span data-stu-id="61677-103">Endpoints provide clients with access to the functionality a Windows Communication Foundation (WCF) service offers.</span></span> <span data-ttu-id="61677-104">エンドポイントの相対アドレスと絶対アドレスを組み合わせてサービスのエンドポイントを 1 つ以上定義できます。または、サービス エンドポイントを定義しない場合、ランタイムは既定で一部を提供します。</span><span class="sxs-lookup"><span data-stu-id="61677-104">You can define one or more endpoints for a service by using a combination of relative and absolute endpoint addresses, or if you do not define any service endpoints, the runtime provides some by default for you.</span></span> <span data-ttu-id="61677-105">このトピックでは、相対アドレスと絶対アドレスの両方を含んでいる構成ファイルを使用したエンドポイントの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="61677-105">This topic shows how to add endpoints using a configuration file that contain both relative and absolute addresses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61677-106">例</span><span class="sxs-lookup"><span data-stu-id="61677-106">Example</span></span>  
 <span data-ttu-id="61677-107">次のサービス構成では、1 つのベース アドレスと 5 つのエンドポイントを指定します。</span><span class="sxs-lookup"><span data-stu-id="61677-107">The following service configuration specifies a base address and five endpoints.</span></span>  
  
```xml  
<configuration>  
  
  <appSettings>  
    <!-- use appSetting to configure base address provided by host -->  
    <add key="baseAddress" value="http://localhost:8000/servicemodelsamples/service" />  
  </appSettings>  
  
  <system.serviceModel>  
    <services>  
    <!-- This section is optional with the default configuration introduced  
         in .NET Framework 4. -->  
      <service  
          name="Microsoft.ServiceModel.Samples.CalculatorService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="/test"  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="http://localhost:8001/hello/servicemodelsamples"  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
                  binding="netTcpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is another relative address exposed at   
             http://localhost:8000/ServiceModelSamples/service/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="61677-108">例</span><span class="sxs-lookup"><span data-stu-id="61677-108">Example</span></span>  
 <span data-ttu-id="61677-109">ベース アドレスは、次のサンプルのように `add` 要素を使用して service/host/baseAddresses の下に指定します。</span><span class="sxs-lookup"><span data-stu-id="61677-109">The base address is specified using the `add` element, under service/host/baseAddresses, as shown in the following sample.</span></span>  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a><span data-ttu-id="61677-110">例</span><span class="sxs-lookup"><span data-stu-id="61677-110">Example</span></span>  
 <span data-ttu-id="61677-111">次のサンプルの最初のエンドポイント定義では、相対アドレスを指定します。つまり、エンドポイント アドレスは、ベース アドレスと URI (Uniform Resource Identifier) 構造の規則に従った相対アドレスの組み合わせということを意味します。</span><span class="sxs-lookup"><span data-stu-id="61677-111">The first endpoint definition shown in the following sample specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of Uniform Resource Identifier (URI) composition.</span></span> <span data-ttu-id="61677-112">相対アドレスが空 ("") のため、エンドポイント アドレスはベース アドレスと同じになります。</span><span class="sxs-lookup"><span data-stu-id="61677-112">The relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="61677-113">実際のエンドポイント アドレスがhttp://localhost:8000/servicemodelsamples/serviceです。</span><span class="sxs-lookup"><span data-stu-id="61677-113">The actual endpoint address is http://localhost:8000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address=""   
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="61677-114">例</span><span class="sxs-lookup"><span data-stu-id="61677-114">Example</span></span>  
 <span data-ttu-id="61677-115">2 番目のエンドポイント定義でも、相対アドレスを指定します。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61677-115">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span> <span data-ttu-id="61677-116">相対アドレス "test" がベース アドレスの末尾に追加されています。</span><span class="sxs-lookup"><span data-stu-id="61677-116">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="61677-117">実際のエンドポイント アドレスがhttp://localhost:8000/servicemodelsamples/service/testです。</span><span class="sxs-lookup"><span data-stu-id="61677-117">The actual endpoint address is http://localhost:8000/servicemodelsamples/service/test.</span></span>  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="61677-118">例</span><span class="sxs-lookup"><span data-stu-id="61677-118">Example</span></span>  
 <span data-ttu-id="61677-119">3 番目のエンドポイント定義では、絶対アドレスを指定します。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61677-119">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span> <span data-ttu-id="61677-120">このアドレスでは、ベース アドレスは使用されていません。</span><span class="sxs-lookup"><span data-stu-id="61677-120">The base address plays no role in the address.</span></span> <span data-ttu-id="61677-121">実際のエンドポイント アドレスがhttp://localhost:8001/hello/servicemodelsamplesです。</span><span class="sxs-lookup"><span data-stu-id="61677-121">The actual endpoint address is http://localhost:8001/hello/servicemodelsamples.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="61677-122">例</span><span class="sxs-lookup"><span data-stu-id="61677-122">Example</span></span>  
 <span data-ttu-id="61677-123">4 番目のエンドポイント アドレスは、絶対アドレスと別のトランスポート (ここでは TCP) を指定しています。</span><span class="sxs-lookup"><span data-stu-id="61677-123">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="61677-124">このアドレスでは、ベース アドレスは使用されていません。</span><span class="sxs-lookup"><span data-stu-id="61677-124">The base address plays no role in the address.</span></span> <span data-ttu-id="61677-125">具体的には net.tcp://localhost:9000/servicemodelsamples/service です。</span><span class="sxs-lookup"><span data-stu-id="61677-125">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="61677-126">例</span><span class="sxs-lookup"><span data-stu-id="61677-126">Example</span></span>  
 <span data-ttu-id="61677-127">ランタイムによって提供された既定のエンドポイントを使用するには、コードまたは構成ファイルでサービス エンドポイントを指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="61677-127">To use the default endpoints provided by the runtime, do not specify any service endpoints in either the code or the configuration file.</span></span> <span data-ttu-id="61677-128">次の例では、サービスを開くときに、ランタイムは既定のエンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="61677-128">In this example, the runtime creates the default endpoints when the service is opened.</span></span> <span data-ttu-id="61677-129">既定のエンドポイント、バインディング、および動作の詳細については、次を参照してください。[簡略化された構成](../../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="61677-129">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
```xml  
<configuration>  
  
  <appSettings>  
    <!-- use appSetting to configure base address provided by host -->  
    <add key="baseAddress" value="http://localhost:8000/servicemodelsamples/service" />  
  </appSettings>  
  
  <system.serviceModel>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```

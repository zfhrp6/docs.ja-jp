---
title: '方法: マネージ コード DCOM を WCF に移行する'
ms.date: 03/30/2017
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 187bff7c75ba2a0887e3c5728a484a9231936511
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a><span data-ttu-id="1b6f1-102">方法: マネージ コード DCOM を WCF に移行する</span><span class="sxs-lookup"><span data-stu-id="1b6f1-102">How to: Migrate Managed-Code DCOM to WCF</span></span>
<span data-ttu-id="1b6f1-103">Windows Communication Foundation (WCF) は、分散コンポーネント オブジェクト モデル (DCOM) と比較して、分散環境でサーバーとクライアントの間でマネージ コードを呼び出すための、推奨されているセキュリティで保護された選択肢です。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-103">Windows Communication Foundation (WCF) is the recommended and secure choice over Distributed Component Object Model (DCOM) for managed code calls between servers and clients in a distributed environment.</span></span> <span data-ttu-id="1b6f1-104">この記事では、以下のシナリオで、DCOM から WCF にコードを移行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-104">This article shows how you to migrate code from DCOM to WCF for the following scenarios.</span></span>  
  
-   <span data-ttu-id="1b6f1-105">リモート サービスからクライアントに値渡しでオブジェクトを返す</span><span class="sxs-lookup"><span data-stu-id="1b6f1-105">The remote service returns an object by-value to the client</span></span>  
  
-   <span data-ttu-id="1b6f1-106">クライアントからリモート サービスに値渡しでオブジェクトを送信する</span><span class="sxs-lookup"><span data-stu-id="1b6f1-106">The client sends an object by-value to the remote service</span></span>  
  
-   <span data-ttu-id="1b6f1-107">リモート サービスからクライアントに参照渡しでオブジェクトを返す</span><span class="sxs-lookup"><span data-stu-id="1b6f1-107">The remote service returns an object by-reference to the client</span></span>  
  
 <span data-ttu-id="1b6f1-108">セキュリティ上の理由で、WCF では、クライアントからサービスに参照渡しでオブジェクトを送信することはできません。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-108">For security reasons, sending an object by-reference from the client to the service is not allowed in WCF.</span></span> <span data-ttu-id="1b6f1-109">クライアントとサーバーの間で対話を必要とするシナリオは、WCF で双方向サービスを使用することによって実現できます。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-109">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span>  <span data-ttu-id="1b6f1-110">双方向サービスの詳細については、「[双方向サービス](../../../docs/framework/wcf/feature-details/duplex-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-110">For more information about duplex services, see [Duplex Services](../../../docs/framework/wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="1b6f1-111">WCF サービスの作成方法、およびそれらのサービスのクライアントの作成方法について詳しくは、「[基本的な WCF プログラミング](../../../docs/framework/wcf/basic-wcf-programming.md)」、「[サービスの設計と実装](../../../docs/framework/wcf/designing-and-implementing-services.md)」および「[クライアントを構築する](../../../docs/framework/wcf/building-clients.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-111">For more details about creating WCF services and clients for those services, see [Basic WCF Programming](../../../docs/framework/wcf/basic-wcf-programming.md), [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md), and [Building Clients](../../../docs/framework/wcf/building-clients.md).</span></span>  
  
## <a name="dcom-example-code"></a><span data-ttu-id="1b6f1-112">DCOM コード例</span><span class="sxs-lookup"><span data-stu-id="1b6f1-112">DCOM example code</span></span>  
 <span data-ttu-id="1b6f1-113">これらのシナリオでは、WCF を使用して示されている DCOM インターフェイスに、以下の構造があります。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-113">For these scenarios, the DCOM interfaces that are illustrated using WCF have the following structure:</span></span>  
  
```  
[ComVisible(true)]  
[Guid("AA9C4CDB-55EA-4413-90D2-843F1A49E6E6")]  
public interface IRemoteService  
{  
   Customer GetObjectByValue();  
   IRemoteObject GetObjectByReference();  
   void SendObjectByValue(Customer customer);  
}  
  
[ComVisible(true)]  
[Guid("A12C98DE-B6A1-463D-8C24-81E4BBC4351B")]  
public interface IRemoteObject  
{  
}  
  
public class Customer  
{  
}  
```  
  
## <a name="the-service-returns-an-object-by-value"></a><span data-ttu-id="1b6f1-114">サービスから値渡しでオブジェクトを返す</span><span class="sxs-lookup"><span data-stu-id="1b6f1-114">The service returns an object by-value</span></span>  
 <span data-ttu-id="1b6f1-115">このシナリオでは、サービスを呼び出し、そのメソッドがオブジェクトを返します。オブジェクトはサーバーからクライアントに値で渡されます。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-115">For this scenario, you make a call to a service and it method returns an object, which is passed by-value from the server to the client.</span></span> <span data-ttu-id="1b6f1-116">このシナリオは、次の COM 呼び出しを表しています。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-116">This scenario represents the following COM call:</span></span>  
  
```  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 <span data-ttu-id="1b6f1-117">このシナリオでは、クライアントは、リモート サービスからオブジェクトの逆シリアル化されたコピーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-117">In this scenario, the client receives a deserialized copy of an object from the remote service.</span></span> <span data-ttu-id="1b6f1-118">クライアントは、サービスにコールバックしなくても、このローカル コピーと対話できます。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-118">The client can interact with this local copy without calling back to the service.</span></span>  <span data-ttu-id="1b6f1-119">つまり、ローカル コピーのメソッドが呼び出されるときに、サービスはまったく関与しないことがクライアントに保証されています。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-119">In other words, the client is guaranteed the service will not be involved in any way when methods on the local copy are called.</span></span> <span data-ttu-id="1b6f1-120">WCF は常にサービスから値渡しでオブジェクトを返すため、次の各手順では、通常の WCF サービスを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-120">WCF always returns objects from the service by value, so the following steps describe creating a regular WCF service.</span></span>  
  
### <a name="step-1-define-the-wcf-service-interface"></a><span data-ttu-id="1b6f1-121">手順 1: WCF サービスのインターフェイスを定義する</span><span class="sxs-lookup"><span data-stu-id="1b6f1-121">Step 1: Define the WCF service interface</span></span>  
 <span data-ttu-id="1b6f1-122">WCF サービスのパブリック インターフェイスを定義し、[<xref:System.ServiceModel.ServiceContractAttribute>] 属性でマークします。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-122">Define a public interface for the WCF service and mark it with the [<xref:System.ServiceModel.ServiceContractAttribute>] attribute.</span></span>  <span data-ttu-id="1b6f1-123">クライアントに公開するメソッドを [<xref:System.ServiceModel.OperationContractAttribute>] 属性でマークします。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-123">Mark the methods you want to expose to clients with the [<xref:System.ServiceModel.OperationContractAttribute>] attribute.</span></span> <span data-ttu-id="1b6f1-124">次の例は、これらの属性を使用して、サーバー側のインターフェイスと、クライアントが呼び出すことのできるインターフェイス メソッドとを識別する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-124">The following example shows using these attributes to identify the server-side interface and interface methods a client can call.</span></span> <span data-ttu-id="1b6f1-125">このシナリオで使用されるメソッドは、太字で示します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-125">The method used for this scenario is shown in bold.</span></span>  
  
```  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Web;   
. . .  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]  
    void StoreCustomer(Customer customer);  
  
    [OperationContract]     Customer GetCustomer(string firstName, string lastName);   
  
}  
```  
  
### <a name="step-2-define-the-data-contract"></a><span data-ttu-id="1b6f1-126">手順 2: データ コントラクトを定義する</span><span class="sxs-lookup"><span data-stu-id="1b6f1-126">Step 2: Define the data contract</span></span>  
 <span data-ttu-id="1b6f1-127">次に、サービスとクライアントの間でデータが交換される方法を説明する、サービスのデータ コントラクトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-127">Next you should create a data contract for the service, which will describe how the data will be exchanged between the service and its clients.</span></span>  <span data-ttu-id="1b6f1-128">データ コントラクトで説明されたクラスは、[<xref:System.Runtime.Serialization.DataContractAttribute>] 属性でマークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-128">Classes described in the data contract should be marked with the [<xref:System.Runtime.Serialization.DataContractAttribute>] attribute.</span></span> <span data-ttu-id="1b6f1-129">クライアントとサーバーの両方に表示する個々のプロパティやフィールドは、[<xref:System.Runtime.Serialization.DataMemberAttribute>] 属性でマークする必要があります。データ コントラクト内のクラスから派生した型を許可する場合は、[<xref:System.Runtime.Serialization.KnownTypeAttribute>] 属性でそれらを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-129">The individual properties or fields you want visible to both client and server should be marked with the [<xref:System.Runtime.Serialization.DataMemberAttribute>] attribute.If you want types derived from a class in the data contract to be allowed, you must identify them with the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute.</span></span> <span data-ttu-id="1b6f1-130">WCF は、サービス インターフェイス内の型と既知の型として識別される型だけを、シリアル化または逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-130">WCF will only serialize or deserialize types in the service interface and types identified as known types.</span></span> <span data-ttu-id="1b6f1-131">既知の型ではない型を使用しようとすると、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-131">If you attempt to use a type that is not a known type, an exception will occur.</span></span>  
  
 <span data-ttu-id="1b6f1-132">データ コントラクトの詳細については、「[データ コントラクト](../../../docs/framework/wcf/samples/data-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-132">For more information about data contracts, see [Data Contracts](../../../docs/framework/wcf/samples/data-contracts.md).</span></span>  
  
```  
[DataContract]  
[KnownType(typeof(PremiumCustomer))]  
public class Customer  
{  
    [DataMember]  
    public string Firstname;  
    [DataMember]  
    public string Lastname;  
    [DataMember]  
    public Address DefaultDeliveryAddress;  
    [DataMember]  
    public Address DefaultBillingAddress;  
}  
 [DataContract]  
public class PremiumCustomer : Customer  
{  
    [DataMember]  
    public int AccountID;  
}  
  
 [DataContract]  
public class Address  
{  
    [DataMember]  
    public string Street;  
    [DataMember]  
    public string Zipcode;  
    [DataMember]  
    public string City;  
    [DataMember]  
    public string State;  
    [DataMember]  
    public string Country;  
}  
```  
  
### <a name="step-3-implement-the-wcf-service"></a><span data-ttu-id="1b6f1-133">手順 3: WCF サービスを実装する</span><span class="sxs-lookup"><span data-stu-id="1b6f1-133">Step 3: Implement the WCF service</span></span>  
 <span data-ttu-id="1b6f1-134">次に、前の手順で定義したインターフェイスを実装する、WCF サービス クラスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-134">Next, you should implement the WCF service class that implements the interface you defined in the previous step.</span></span>  
  
```  
public class CustomerService: ICustomerManager    
{  
    public void StoreCustomer(Customer customer)  
    {  
        // write to a database  
    }  
    public Customer GetCustomer(string firstName, string lastName)  
    {  
        // read from a database  
    }  
}  
```  
  
### <a name="step-4-configure-the-service-and-the-client"></a><span data-ttu-id="1b6f1-135">手順 4: サービスとクライアントを構成する</span><span class="sxs-lookup"><span data-stu-id="1b6f1-135">Step 4: Configure the service and the client</span></span>  
 <span data-ttu-id="1b6f1-136">WCF サービスを実行するには、特定の WCF バインドを使用して特定の URL で上記のサービス インターフェイスを公開するエンドポイントを宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-136">To run a WCF service, you need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="1b6f1-137">バインディングは、クライアントとサーバーが通信するための、トランスポート、エンコード、およびプロトコルの詳細を指定します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-137">A binding specifies the transport, encoding and protocol details for the clients and server to communicate.</span></span> <span data-ttu-id="1b6f1-138">通常、サービス プロジェクトの構成ファイル (web.config) にバインドを追加します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-138">You typically add bindings to the service project’s configuration file (web.config).</span></span> <span data-ttu-id="1b6f1-139">サービス例のためのバインド エントリを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-139">The following shows a binding entry for the example service:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Server.CustomerService">  
        <endpoint address="http://localhost:8083/CustomerManager"   
                  binding="basicHttpBinding"  
                  contract="Shared.ICustomerManager" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="1b6f1-140">次に、サービスによって指定されたバインド情報と一致するように、クライアントを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-140">Next, you need to configure the client to match the binding information specified by the service.</span></span> <span data-ttu-id="1b6f1-141">そのためには、クライアントのアプリケーション構成 (app.config) ファイルに以下を追加します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-141">To do so, add the following to the client’s application configuration (app.config) file.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="customermanager"   
                address="http://localhost:8083/CustomerManager"   
                binding="basicHttpBinding"   
                contract="Shared.ICustomerManager"/>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="step-5-run-the-service"></a><span data-ttu-id="1b6f1-142">手順 5: サービスを実行する</span><span class="sxs-lookup"><span data-stu-id="1b6f1-142">Step 5: Run the service</span></span>  
 <span data-ttu-id="1b6f1-143">最後に、サービス アプリに次の行を追加して、アプリを起動することにより、コンソール アプリケーション内で自己ホストすることができます。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-143">Finally, you can self-host it in a console application by adding the following lines to the service app, and starting the app.</span></span> <span data-ttu-id="1b6f1-144">WCF サービス アプリケーションをホストするその他の方法について詳しくは、「[ホスティング サービス](../../../docs/framework/wcf/hosting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-144">For more information about other ways to host a WCF service application, [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
```  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a><span data-ttu-id="1b6f1-145">手順 6: クライアントからサービスを呼び出す</span><span class="sxs-lookup"><span data-stu-id="1b6f1-145">Step 6: Call the service from the client</span></span>  
 <span data-ttu-id="1b6f1-146">クライアントからのサービスを呼び出すには、サービスのチャネル ファクトリを作成し、チャネルを要求する必要があります。これにより、クライアントから `GetCustomer` メソッドを直接呼び出すことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-146">To call the service from the client, you need to create a channel factory for the service, and request a channel, which will enable you to directly call the `GetCustomer` method directly from the client.</span></span> <span data-ttu-id="1b6f1-147">チャネルはサービスのインターフェイスを実装し、基になる要求/応答のロジックを処理します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-147">The channel implements the service’s interface and handles the underlying request/reply logic for you.</span></span>  <span data-ttu-id="1b6f1-148">このメソッドの呼び出しからの戻り値は、サービス応答の逆シリアル化されたコピーです。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-148">The return value from that method call is the deserialized copy of the service response.</span></span>  
  
```  
ChannelFactory<ICustomerManager> factory =   
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a><span data-ttu-id="1b6f1-149">クライアントからサーバーに値渡しのオブジェクトを送信する</span><span class="sxs-lookup"><span data-stu-id="1b6f1-149">The client sends a by-value object to the server</span></span>  
 <span data-ttu-id="1b6f1-150">このシナリオでは、クライアントがサーバーに値渡しでオブジェクトを送信します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-150">In this scenario, the client sends an object to the server, by-value.</span></span> <span data-ttu-id="1b6f1-151">つまり、サーバーは、オブジェクトの逆シリアル化されたコピーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-151">This means that the server will receive a deserialized copy of the object.</span></span>  <span data-ttu-id="1b6f1-152">サーバーは、そのコピーのメソッドを呼び出すことができ、クライアント コードにコールバックがないことが保証されます。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-152">The server can call methods on that copy and be guaranteed there is no callback into client code.</span></span> <span data-ttu-id="1b6f1-153">前述のとおり、WCF での通常のデータ交換は、値渡しでなされます。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-153">As mentioned previously, normal WCF exchanges of data are by-value.</span></span>  <span data-ttu-id="1b6f1-154">これにより、これらのいずれかのオブジェクトのメソッドの呼び出しはローカルでのみ実行され、クライアントではコードは呼び出されないことが保証されます。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-154">This guarantees that calling methods on one of these objects executes locally only – it will not invoke code on the client.</span></span>  
  
 <span data-ttu-id="1b6f1-155">このシナリオは、次の COM メソッドの呼び出しを表しています。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-155">This scenario represents the following COM method call:</span></span>  
  
```  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 <span data-ttu-id="1b6f1-156">このシナリオでは、最初の例で示すものと同じサービス インターフェイスおよびデータ コントラクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-156">This scenario uses the same service interface and data contract as shown in the first example.</span></span> <span data-ttu-id="1b6f1-157">さらに、クライアントとサービスが同じ方法で構成されます。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-157">In addition, the client and service will be configured in the same way.</span></span> <span data-ttu-id="1b6f1-158">この例では、オブジェクトを送信するためにチャネルが作成されて、同じ方法で実行されます。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-158">In this example, a channel is created to send the object and run the same way.</span></span> <span data-ttu-id="1b6f1-159">ただし、この例では、値渡しでオブジェクトを送信して、サービスを呼び出すクライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-159">However, for this example, you will create a client that calls the service, passing an object by-value.</span></span> <span data-ttu-id="1b6f1-160">クライアントがサービス コントラクトで呼び出すサービス メソッドは、太字で示されます。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-160">The service method the client will call in the service contract is shown in bold:</span></span>  
  
```  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a><span data-ttu-id="1b6f1-161">値渡しのオブジェクトを送信するクライアントにコードを追加する</span><span class="sxs-lookup"><span data-stu-id="1b6f1-161">Add code to the client that sends a by-value object</span></span>  
 <span data-ttu-id="1b6f1-162">次のコードは、クライアントが値渡しの customer オブジェクトを新規に作成する方法、`ICustomerManager` サービスと通信するチャネルを作成する方法、およびそこに customer オブジェクトを送信する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-162">The following code shows how the client creates a new by-value customer object, creates a channel to communicate with the `ICustomerManager` service, and sends the customer object to it.</span></span>  
  
 <span data-ttu-id="1b6f1-163">Customer オブジェクトはシリアル化され、サービスに送信されて、サービスによりそのオブジェクトの新しいコピーへと逆シリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-163">The customer object will be serialized, and sent to the service, where it is deserialized by the service into a new copy of that object.</span></span>  <span data-ttu-id="1b6f1-164">サービスがこのオブジェクトで呼び出すメソッドは、サーバーにおいてローカルでのみ実行します。このコードは、派生型 (`PremiumCustomer`) の送信を例示していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-164">Any methods the service calls on this object will execute only locally on the server.It’s important to note that this code illustrates sending a derived type (`PremiumCustomer`).</span></span>  <span data-ttu-id="1b6f1-165">サービス コントラクトは `Customer` オブジェクトを想定していますが、サービス データ コントラクトは [<xref:System.Runtime.Serialization.KnownTypeAttribute>] 属性を使用して `PremiumCustomer` も許可されることを示しています。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-165">The service contract expects a `Customer` object, but the service data contract uses the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute to indicate that `PremiumCustomer` is also allowed.</span></span>  <span data-ttu-id="1b6f1-166">このサービス インターフェイスを介して他の型をシリアル化または逆シリアル化しようとしても、WCF は失敗します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-166">WCF will fail attempts to serialize or deserialize any other type via this service interface.</span></span>  
  
```  
PremiumCustomer customer = new PremiumCustomer();  
customer.Firstname = "John";  
customer.Lastname = "Doe";  
customer.DefaultBillingAddress = new Address();  
customer.DefaultBillingAddress.Street = "One Microsoft Way";  
customer.DefaultDeliveryAddress = customer.DefaultBillingAddress;  
customer.AccountID = 42;  
  
ChannelFactory<ICustomerManager> factory =  
   new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager customerManager = factory.CreateChannel();  
customerManager.StoreCustomer(customer);  
```  
  
## <a name="the-service-returns-an-object-by-reference"></a><span data-ttu-id="1b6f1-167">サービスから参照渡しでオブジェクトを返す</span><span class="sxs-lookup"><span data-stu-id="1b6f1-167">The service returns an object by reference</span></span>  
 <span data-ttu-id="1b6f1-168">このシナリオでは、クライアント アプリがリモート サービスを呼び出し、メソッドがオブジェクトを返します。オブジェクトはサービスからクライアントに参照によって渡されます。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-168">For this scenario, the client app makes a call to the remote service and the method returns an object, which is passed by reference from the service to the client.</span></span>  
  
 <span data-ttu-id="1b6f1-169">前述のとおり、WCF サービスは常に値でオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-169">As mentioned previously, WCF services always return object by value.</span></span>  <span data-ttu-id="1b6f1-170">ただし、<xref:System.ServiceModel.EndpointAddress10> クラスを使用して同様の結果を得ることもできます。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-170">However, you can achieve a similar result by using the <xref:System.ServiceModel.EndpointAddress10> class.</span></span>  <span data-ttu-id="1b6f1-171"><xref:System.ServiceModel.EndpointAddress10> は、サーバー上のセッションフルな参照渡しのオブジェクトを取得するためにクライアントが使用できる、シリアル化可能な値渡しのオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-171">The <xref:System.ServiceModel.EndpointAddress10> is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span>  
  
 <span data-ttu-id="1b6f1-172">このシナリオで示される WCF の参照渡しのオブジェクトの動作は、DCOM とは異なります。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-172">The behavior of the by-reference object in WCF shown in this scenario is different than DCOM.</span></span>  <span data-ttu-id="1b6f1-173">DCOM では、サーバーが参照渡しのオブジェクトをクライアントに直接返すことができ、クライアントはそのオブジェクトのメソッドを呼び出して、サーバーで実行することができます。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-173">In DCOM, the server can return a by-reference object to the client directly, and the client can call that object’s methods, which execute on the server.</span></span>  <span data-ttu-id="1b6f1-174">しかし WCF では、オブジェクトが常に値渡しで返されます。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-174">In WCF, however, the object returned is always by-value.</span></span>  <span data-ttu-id="1b6f1-175">クライアントは、<xref:System.ServiceModel.EndpointAddress10> によって表されるその値渡しのオブジェクトを取得し、それを使用して独自の参照渡しのセッションフル オブジェクトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-175">The client must take that by-value object, represented by <xref:System.ServiceModel.EndpointAddress10> and use it to create its own sessionful by-reference object.</span></span>  <span data-ttu-id="1b6f1-176">セッションフル オブジェクトのクライアント メソッド呼び出しは、サーバーで実行されます。つまり、WCF でのこの参照渡しのオブジェクトは、セッションフルとなるように構成された通常の WCF サービスです。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-176">The client method calls on the sessionful object execute on the server.In other words, this by-reference object in WCF is a normal WCF service that is configured to be sessionful.</span></span>  
  
 <span data-ttu-id="1b6f1-177">WCF では、セッションは 2 つのエンドポイント間で送信される複数のメッセージを関連付ける方法です。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-177">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span>  <span data-ttu-id="1b6f1-178">つまり、クライアントがこのサービスへの接続を確保すると、クライアントとサーバーの間でセッションが確立されます。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-178">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span>  <span data-ttu-id="1b6f1-179">クライアントは、サーバー側オブジェクトの単一で一意のインスタンスを、この 1 つのセッション内でのすべてのやり取りに使用することになります。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-179">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span> <span data-ttu-id="1b6f1-180">セッションフル WCF コントラクトは、接続指向ネットワークの要求/応答パターンに似ています。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-180">Sessionful WCF contracts are similar to connection-oriented network request/response patterns.</span></span>  
  
 <span data-ttu-id="1b6f1-181">このシナリオは、以下の DCOM メソッドによって表されます。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-181">This scenario is represented by the following DCOM method.</span></span>  
  
```  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a><span data-ttu-id="1b6f1-182">手順 1: セッションフル WCF サービスのインターフェイスと実装を定義する</span><span class="sxs-lookup"><span data-stu-id="1b6f1-182">Step 1: Define the Sessionful WCF service interface and implementation</span></span>  
 <span data-ttu-id="1b6f1-183">最初に、セッションフル オブジェクトを含む WCF サービスのインターフェイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-183">First, define a WCF service interface that contains the sessionful object.</span></span>  
  
 <span data-ttu-id="1b6f1-184">このコードでは、セッションフル オブジェクトが `ServiceContract` 属性でマークされ、通常の WCF サービスのインターフェイスとして示されています。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-184">In this code, the sessionful object is marked with the `ServiceContract` attribute, which identifies it as a regular WCF service interface.</span></span>  <span data-ttu-id="1b6f1-185">さらに、<xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> プロパティが設定されて、セッションフル サービスとなることが示されています。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-185">In addition, the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> property is set to indicate it will be a sessionful service.</span></span>  
  
```  
[ServiceContract(SessionMode = SessionMode.Allowed)]  
public interface ISessionBoundObject  
{  
    [OperationContract]  
    string GetCurrentValue();  
  
    [OperationContract]  
    void SetCurrentValue(string value);  
}  
```  
  
 <span data-ttu-id="1b6f1-186">サービスの実装を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-186">The following code shows the service implementation.</span></span>  
  
 <span data-ttu-id="1b6f1-187">サービスは [ServiceBehavior] 属性でマークされ、InstanceContextMode プロパティが InstanceContextMode.PerSessions に設定されて、セッションごとにこの型の一意のインスタンスを作成する必要があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-187">The service is marked with the [ServiceBehavior] attribute, and its InstanceContextMode property set to InstanceContextMode.PerSessions to indicate that a unique instance of this type should be created for each session.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
    public class MySessionBoundObject : ISessionBoundObject  
    {  
        private string _value;  
  
        public string GetCurrentValue()  
        {  
            return _value;  
        }  
  
        public void SetCurrentValue(string val)  
        {  
            _value = val;  
        }  
  
    }  
```  
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a><span data-ttu-id="1b6f1-188">手順 2: セッションフル オブジェクトの WCF ファクトリ サービスを定義する</span><span class="sxs-lookup"><span data-stu-id="1b6f1-188">Step 2: Define the WCF factory service for the sessionful object</span></span>  
 <span data-ttu-id="1b6f1-189">セッションフル オブジェクトを作成するサービスを定義して実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-189">The service that creates the sessionful object must be defined and implemented.</span></span> <span data-ttu-id="1b6f1-190">この方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-190">The following code shows how to do this.</span></span> <span data-ttu-id="1b6f1-191">このコードは、<xref:System.ServiceModel.EndpointAddress10> オブジェクトとして返される別の WCF サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-191">This code creates another WCF service that returns an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  <span data-ttu-id="1b6f1-192">これはセッションフル オブジェクトの作成に使用できる、エンドポイントのシリアル化可能な形式です。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-192">This is a serializable form of an endpoint the can use to create the session-full object.</span></span>  
  
```  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 <span data-ttu-id="1b6f1-193">このサービスの実装を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-193">Following is the implementation of this service.</span></span> <span data-ttu-id="1b6f1-194">この実装では、セッションフル オブジェクトを作成するためにシングルトン チャネル ファクトリを保持しています。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-194">This implementation maintains a singleton channel factory to create sessionful objects.</span></span>  <span data-ttu-id="1b6f1-195">チャネル ファクトリは、`GetInstanceAddress` が呼び出されるとチャネルを作成し、このチャネルに関連付けられているリモート アドレスをポイントする <xref:System.ServiceModel.EndpointAddress10> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-195">When `GetInstanceAddress` is called, it creates a channel and creates an <xref:System.ServiceModel.EndpointAddress10> object that points to the remote address associated with this channel.</span></span>   <span data-ttu-id="1b6f1-196"><xref:System.ServiceModel.EndpointAddress10> は、値渡しでクライアントに返すことのできるデータ型です。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-196"><xref:System.ServiceModel.EndpointAddress10> is a data type that can be returned to the client by-value.</span></span>  
  
```  
public class SessionBoundFactory : ISessionBoundFactory  
    {  
        public static ChannelFactory<ISessionBoundObject> _factory =   
            new ChannelFactory<ISessionBoundObject>("sessionbound");  
  
        public SessionBoundFactory()  
        {  
        }  
  
        public EndpointAddress10 GetInstanceAddress()  
        {  
            IClientChannel channel = (IClientChannel)_factory.CreateChannel();  
            return EndpointAddress10.FromEndpointAddress(channel.RemoteAddress);  
        }  
    }  
```  
  
### <a name="step-3-configure-and-start-the-wcf-services"></a><span data-ttu-id="1b6f1-197">手順 3: WCF サービスを構成して開始する</span><span class="sxs-lookup"><span data-stu-id="1b6f1-197">Step 3: Configure and start the WCF services</span></span>  
 <span data-ttu-id="1b6f1-198">これらのサービスをホストするには、サーバーの構成ファイル (web.config) に以下を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-198">To host these services, you will need to make the following additions to the server’s configuration file (web.config).</span></span>  
  
1.  <span data-ttu-id="1b6f1-199">セッションフル オブジェクトのエンドポイントを示す `<client>` セクションを追加します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-199">Add a `<client>` section that describes the endpoint for the sessionful object.</span></span>  <span data-ttu-id="1b6f1-200">このシナリオでは、サーバーもクライアントとして機能するので、それが有効となるように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-200">In this scenario, the server also acts as a client and must be configured to enable this.</span></span>  
  
2.  <span data-ttu-id="1b6f1-201">`<services>` セクションで、ファクトリおよびセッションフル オブジェクトのサービス エンドポイントを宣言します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-201">In the `<services>` section, declare service endpoints for the factory and sessionful object.</span></span>  <span data-ttu-id="1b6f1-202">これにより、クライアントは、サービス エンドポイントと通信すること、<xref:System.ServiceModel.EndpointAddress10> を取得すること、およびセッションフル チャネルを作成することが可能になります。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-202">This enables the client to communicate with the service endpoints, acquire the <xref:System.ServiceModel.EndpointAddress10> and create the sessionful channel.</span></span>  
  
 <span data-ttu-id="1b6f1-203">これらの設定のある構成ファイルの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-203">Following is an example configuration file with these settings:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="sessionbound"  
                address="net.tcp://localhost:8081/SessionBoundObject"  
                binding="netTcpBinding"  
                contract="Shared.ISessionBoundObject"/>  
    </client>  
  
    <services>  
      <service name="Server.MySessionBoundObject">  
        <endpoint address="net.tcp://localhost:8081/SessionBoundObject"  
                  binding="netTcpBinding"   
                  contract="Shared.ISessionBoundObject" />  
      </service>  
      <service name="Server.SessionBoundFactory">  
        <endpoint address="net.tcp://localhost:8081/SessionBoundFactory"  
                  binding="netTcpBinding"   
                  contract="Shared.ISessionBoundFactory" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="1b6f1-204">以下の行をコンソール アプリケーションに追加し、サービスを自己ホストして、アプリを開始します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-204">Add the following lines to a console application, to self-host the service, and start the app.</span></span>  
  
```  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a><span data-ttu-id="1b6f1-205">手順 4: クライアントを構成してサービスを呼び出す</span><span class="sxs-lookup"><span data-stu-id="1b6f1-205">Step 4: Configure the client and call the service</span></span>  
 <span data-ttu-id="1b6f1-206">プロジェクトのアプリケーション構成ファイル (app.config) に以下のエントリを作成して、クライアントが WCF サービスと通信するように構成します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-206">Configure the client to communicate with the WCF services by making the following entries in the project’s application configuration file (app.config).</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="sessionbound"   
                address="net.tcp://localhost:8081/SessionBoundObject"   
                binding="netTcpBinding"   
                contract="Shared.ISessionBoundObject"/>  
      <endpoint name="factory"   
                address="net.tcp://localhost:8081/SessionBoundFactory"   
                binding="netTcpBinding"   
                contract="Shared.ISessionBoundFactory"/>  
    </client>    
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="1b6f1-207">サービスを呼び出すには、クライアントにコードを追加して、以下を実行するようにします。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-207">To call the service, add the code to the client to do the following:</span></span>  
  
1.  <span data-ttu-id="1b6f1-208">`ISessionBoundFactory` サービスへのチャネルを作成します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-208">Create a channel to the `ISessionBoundFactory` service.</span></span>  
  
2.  <span data-ttu-id="1b6f1-209">チャネルを使用して `ISessionBoundFactory` サービスを呼び出し、<xref:System.ServiceModel.EndpointAddress10> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-209">Use the channel to invoke the `ISessionBoundFactory` service an obtain an <xref:System.ServiceModel.EndpointAddress10> bbject.</span></span>  
  
3.  <span data-ttu-id="1b6f1-210"><xref:System.ServiceModel.EndpointAddress10> を使用してチャネルを作成し、セッションフル オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-210">Use the <xref:System.ServiceModel.EndpointAddress10> to create a channel to obtain a sessionful object.</span></span>  
  
4.  <span data-ttu-id="1b6f1-211">`SetCurrentValue` および `GetCurrentValue` メソッドを呼び出して、複数の呼び出しの間で同じオブジェクト インスタンスが使用されることを示します。</span><span class="sxs-lookup"><span data-stu-id="1b6f1-211">Call the `SetCurrentValue` and `GetCurrentValue` methods to demonstrate it remains the same object instance is used across multiple calls.</span></span>  
  
```  
ChannelFactory<ISessionBoundFactory> factory =  
        new ChannelFactory<ISessionBoundFactory>("factory");  
  
ISessionBoundFactory sessionBoundFactory = factory.CreateChannel();  
  
EndpointAddress10 address = sessionBoundFactory.GetInstanceAddress();  
  
ChannelFactory<ISessionBoundObject> sessionBoundObjectFactory =  
    new ChannelFactory<ISessionBoundObject>(  
        new NetTcpBinding(),  
        address.ToEndpointAddress());  
  
ISessionBoundObject sessionBoundObject =  
        sessionBoundObjectFactory.CreateChannel();  
  
sessionBoundObject.SetCurrentValue("Hello");  
if (sessionBoundObject.GetCurrentValue() == "Hello")  
{  
    Console.WriteLine("Session-full instance management works as expected");  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="1b6f1-212">参照</span><span class="sxs-lookup"><span data-stu-id="1b6f1-212">See Also</span></span>  
 [<span data-ttu-id="1b6f1-213">基本的な WCF プログラミング</span><span class="sxs-lookup"><span data-stu-id="1b6f1-213">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="1b6f1-214">サービスの設計と実装</span><span class="sxs-lookup"><span data-stu-id="1b6f1-214">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [<span data-ttu-id="1b6f1-215">クライアントを構築する</span><span class="sxs-lookup"><span data-stu-id="1b6f1-215">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)  
 [<span data-ttu-id="1b6f1-216">双方向サービス</span><span class="sxs-lookup"><span data-stu-id="1b6f1-216">Duplex Services</span></span>](../../../docs/framework/wcf/feature-details/duplex-services.md)

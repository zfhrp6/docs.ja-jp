---
title: カスタム サービス ホスト
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: c02ceb114a5346ea2a851f711f1ab9b50373cb75
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806797"
---
# <a name="custom-service-host"></a><span data-ttu-id="51c67-102">カスタム サービス ホスト</span><span class="sxs-lookup"><span data-stu-id="51c67-102">Custom Service Host</span></span>
<span data-ttu-id="51c67-103">このサンプルでは、<xref:System.ServiceModel.ServiceHost> クラスから派生したカスタムのサービス ホストを使用して、サービスの実行時動作を変更する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="51c67-103">This sample demonstrates how to use a custom derivative of the <xref:System.ServiceModel.ServiceHost> class to alter the run-time behavior of a service.</span></span> <span data-ttu-id="51c67-104">この方法は、多数のサービスを共通方式で構成するという方法の代わりに使用でき、再利用可能です。</span><span class="sxs-lookup"><span data-stu-id="51c67-104">This approach provides a reusable alternative to configuring a large number of services in a common way.</span></span> <span data-ttu-id="51c67-105">このサンプルでは、<xref:System.ServiceModel.Activation.ServiceHostFactory> クラスを使用して、カスタムの ServiceHost を、インターネット インフォメーション サービス (IIS) または Windows プロセス アクティブ化サービス (WAS) でホストされる環境で使用する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="51c67-105">The sample also demonstrates how to use the <xref:System.ServiceModel.Activation.ServiceHostFactory> class to use a custom ServiceHost in the Internet Information Services (IIS) or Windows Process Activation Service (WAS) hosting environment.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="51c67-106">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="51c67-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="51c67-107">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="51c67-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="51c67-108">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="51c67-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="51c67-109">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="51c67-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a><span data-ttu-id="51c67-110">シナリオについて</span><span class="sxs-lookup"><span data-stu-id="51c67-110">About the Scenario</span></span>  
 <span data-ttu-id="51c67-111">機密性の高いサービス メタデータが誤って漏洩を防ぐためには、Windows Communication Foundation (WCF) サービスの既定の構成はメタデータの公開を無効にします。</span><span class="sxs-lookup"><span data-stu-id="51c67-111">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="51c67-112">この動作は、既定の設定ではセキュリティで保護されますが、同時に、サービスの構成の中でメタデータ発行の動作が明示的に有効化されない限り、サービスの呼び出しに必要なクライアント コードをメタデータ インポート ツール (Svcutil.exe など) を使用して生成できないことも意味します。</span><span class="sxs-lookup"><span data-stu-id="51c67-112">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
 <span data-ttu-id="51c67-113">多数のサービスのメタデータ公開を有効にすると、同一の構成要素が各サービスに追加されます。この結果、本質的に同じ構成情報が大量に発生することになります。</span><span class="sxs-lookup"><span data-stu-id="51c67-113">Enabling metadata publishing for a large number of services involves adding the same configuration elements to each individual service, which results in a large amount of configuration information that is essentially the same.</span></span> <span data-ttu-id="51c67-114">各サービスを個別に構成する代わりに、メタデータ公開を有効化する命令型コードを一度だけプログラミングして、そのコードを複数のサービスで再利用するという方法もあります。</span><span class="sxs-lookup"><span data-stu-id="51c67-114">As an alternative to configuring each service individually, it is possible to write the imperative code that enables metadata publishing once and then reuse that code across several different services.</span></span> <span data-ttu-id="51c67-115">この方法を使用するには、<xref:System.ServiceModel.ServiceHost> から派生する新しいクラスを作成し、`ApplyConfiguration`() メソッドをオーバーライドして命令型コードでメタデータ公開動作を追加します。</span><span class="sxs-lookup"><span data-stu-id="51c67-115">This is accomplished by creating a new class that derives from <xref:System.ServiceModel.ServiceHost> and overrides the `ApplyConfiguration`() method to imperatively add the metadata publishing behavior.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="51c67-116">このサンプルでは、わかりやすくするために、セキュリティで保護されていないメタデータ公開エンドポイントを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="51c67-116">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="51c67-117">このようなエンドポイントを利用するコンシューマーは、匿名で、認証を受けていない可能性もあります。したがって、エンドポイントを配置する前には注意を払い、サービスのメタデータをパブリックに開示することが適切であることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="51c67-117">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span>  
  
## <a name="implementing-a-custom-servicehost"></a><span data-ttu-id="51c67-118">カスタム ServiceHost の実装</span><span class="sxs-lookup"><span data-stu-id="51c67-118">Implementing a Custom ServiceHost</span></span>  
 <span data-ttu-id="51c67-119"><xref:System.ServiceModel.ServiceHost> クラスは、便利な仮想メソッドを多数公開しています。継承側でこの仮想メソッドをオーバーライドして、サービスの実行時動作を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="51c67-119">The <xref:System.ServiceModel.ServiceHost> class exposes several useful virtual methods that inheritors can override to alter the run-time behavior of a service.</span></span> <span data-ttu-id="51c67-120">たとえば、`ApplyConfiguration`() メソッドはサービスの構成情報を構成ストアから読み取り、それに応じてホストの <xref:System.ServiceModel.Description.ServiceDescription> を変更します。</span><span class="sxs-lookup"><span data-stu-id="51c67-120">For example, the `ApplyConfiguration`() method reads service configuration information from the configuration store and alters the host's <xref:System.ServiceModel.Description.ServiceDescription> accordingly.</span></span> <span data-ttu-id="51c67-121">既定の実装は構成をアプリケーションの構成ファイルから読み取りますが、</span><span class="sxs-lookup"><span data-stu-id="51c67-121">The default implementation reads configuration from the application’s configuration file.</span></span> <span data-ttu-id="51c67-122">カスタム実装では、`ApplyConfiguration`() をオーバーライドすれば、命令型コードを使用して <xref:System.ServiceModel.Description.ServiceDescription> にさらに変更を加えることや、既定の構成ストア全体を置き換えることも可能です (</span><span class="sxs-lookup"><span data-stu-id="51c67-122">Custom implementations can override `ApplyConfiguration`() to further alter the <xref:System.ServiceModel.Description.ServiceDescription> using imperative code or even replace the default configuration store entirely.</span></span> <span data-ttu-id="51c67-123">たとえば、サービスのエンドポイント構成を、アプリケーションの構成ファイルではなくデータベースから読み取るようにする場合)。</span><span class="sxs-lookup"><span data-stu-id="51c67-123">For example, to read a service’s endpoint configuration from a database instead of the application’s configuration file.</span></span>  
  
 <span data-ttu-id="51c67-124">このサンプルでは、ServiceMetadataBehavior (メタデータ公開を有効にする動作) がサービスの構成ファイルに明示的に追加されていない場合でもこの動作を追加する、カスタムの ServiceHost を構築します。</span><span class="sxs-lookup"><span data-stu-id="51c67-124">In this sample, we want to build a custom ServiceHost that adds the ServiceMetadataBehavior, (which enables metadata publishing), even if this behavior is not explicitly added in the service’s configuration file.</span></span> <span data-ttu-id="51c67-125">これを実現するには、<xref:System.ServiceModel.ServiceHost> から継承する新しいクラスを作成して `ApplyConfiguration`() をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="51c67-125">To accomplish this, we create a new class that inherits from <xref:System.ServiceModel.ServiceHost> and overrides `ApplyConfiguration`().</span></span>  
  
```  
class SelfDescribingServiceHost : ServiceHost  
{  
    public SelfDescribingServiceHost(Type serviceType, params Uri[] baseAddresses)  
        : base(serviceType, baseAddresses) { }  
  
    //Overriding ApplyConfiguration() allows us to   
    //alter the ServiceDescription prior to opening  
    //the service host.   
    protected override void ApplyConfiguration()  
    {  
        //First, we call base.ApplyConfiguration()  
        //to read any configuration that was provided for  
        //the service we're hosting. After this call,  
        //this.Description describes the service  
        //as it was configured.  
        base.ApplyConfiguration();       
  
        //(rest of implementation elided for clarity)  
    }  
}  
```  
  
 <span data-ttu-id="51c67-126">アプリケーションの構成ファイルで指定されている構成が無視されないようにしたいので、`ApplyConfiguration`() のオーバーライドで最初に行うことは、基本実装の呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="51c67-126">Because we do not want to ignore any configuration that has been provided in the application’s configuration file, the first thing our override of `ApplyConfiguration`() does is call the base implementation.</span></span> <span data-ttu-id="51c67-127">このメソッドが完了した後で、次の命令型コードを使用して、サービス記述に <xref:System.ServiceModel.Description.ServiceMetadataBehavior> を追加します。</span><span class="sxs-lookup"><span data-stu-id="51c67-127">Once this method completes, we can imperatively add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> to the description using the following imperative code.</span></span>  
  
```  
ServiceMetadataBehavior mexBehavior = this.Description.Behaviors.Find<ServiceMetadataBehavior>();  
if (mexBehavior == null)  
{  
    mexBehavior = new ServiceMetadataBehavior();  
    this.Description.Behaviors.Add(mexBehavior);  
}  
else  
{  
    //Metadata behavior has already been configured,   
    //so we do not have any work to do.  
    return;  
}  
```  
  
 <span data-ttu-id="51c67-128">`ApplyConfiguration`() のオーバーライドでの最後の処理は、既定のメタデータ エンドポイントの追加です。</span><span class="sxs-lookup"><span data-stu-id="51c67-128">The last thing our `ApplyConfiguration`() override must do is add the default metadata endpoint.</span></span> <span data-ttu-id="51c67-129">通常は、サービス ホストの BaseAddresses コレクション内の各 URI に対して 1 つずつメタデータ エンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="51c67-129">By convention, one metadata endpoint is created for each URI in the service host’s BaseAddresses collection.</span></span>  
  
```  
//Add a metadata endpoint at each base address  
//using the "/mex" addressing convention  
foreach (Uri baseAddress in this.BaseAddresses)  
{  
    if (baseAddress.Scheme == Uri.UriSchemeHttp)  
    {  
        mexBehavior.HttpGetEnabled = true;  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexHttpBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeHttps)  
    {  
        mexBehavior.HttpsGetEnabled = true;  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexHttpsBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeNetPipe)  
    {  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexNamedPipeBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeNetTcp)  
    {  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexTcpBinding(),  
                                "mex");  
    }  
}  
```  
  
## <a name="using-a-custom-servicehost-in-self-host"></a><span data-ttu-id="51c67-130">自己ホストでのカスタム ServiceHost の使用</span><span class="sxs-lookup"><span data-stu-id="51c67-130">Using a custom ServiceHost in self-host</span></span>  
 <span data-ttu-id="51c67-131">カスタム ServiceHost の実装が完成したので、これを使用して任意のサービスにメタデータ公開動作を追加できるようになりました。追加するには、`SelfDescribingServiceHost` のインスタンス内でサービスをホストします。</span><span class="sxs-lookup"><span data-stu-id="51c67-131">Now that we have completed our custom ServiceHost implementation, we can use it to add metadata publishing behavior to any service by hosting that service inside of an instance of our `SelfDescribingServiceHost`.</span></span> <span data-ttu-id="51c67-132">カスタム ServiceHost を自己ホストのシナリオで使用する方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="51c67-132">The following code shows how to use it in the self-host scenario.</span></span>  
  
```  
SelfDescribingServiceHost host =   
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 <span data-ttu-id="51c67-133">既定の <xref:System.ServiceModel.ServiceHost> クラスを使用してサービスをホストする場合と同様に、このカスタム ServiceHost も、サービスのエンドポイント構成をアプリケーションの構成ファイルから読み取ります。</span><span class="sxs-lookup"><span data-stu-id="51c67-133">Our custom host still reads the service’s endpoint configuration from the application’s configuration file, just as if we had used the default <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="51c67-134">ただし、カスタム ホストの内部でメタデータ公開を有効にするというロジックを追加したので、構成の中でメタデータ公開動作を明示的に有効化することは不要になりました。</span><span class="sxs-lookup"><span data-stu-id="51c67-134">However, because we added the logic to enable metadata publishing inside of our custom host, we no longer must explicitly enable the metadata publishing behavior in configuration.</span></span> <span data-ttu-id="51c67-135">この方法のメリットがはっきりと現れるのは、開発するアプリケーションに複数のサービスがあり、同じ構成要素を繰り返し記述することなく各サービスでメタデータ公開を有効化できるようにする場合です。</span><span class="sxs-lookup"><span data-stu-id="51c67-135">This approach has a distinct advantage when you are building an application that contains several services and you want to enable metadata publishing on each of them without writing the same configuration elements over and over.</span></span>  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a><span data-ttu-id="51c67-136">IIS または WAS でのカスタム ServiceHost の使用</span><span class="sxs-lookup"><span data-stu-id="51c67-136">Using a Custom ServiceHost in IIS or WAS</span></span>  
 <span data-ttu-id="51c67-137">カスタム サービス ホストを自己ホストのシナリオで使用することは簡単です。サービス ホストのインスタンスを作成して開くことは、アプリケーションのコードで行うからです。</span><span class="sxs-lookup"><span data-stu-id="51c67-137">Using a custom service host in self-host scenarios is straightforward, because it is your application code that is ultimately responsible for creating and opening the service host instance.</span></span> <span data-ttu-id="51c67-138">IIS または WAS がホストする環境で、ただし、WCF インフラストラクチャが動的にインスタンス化する受信メッセージに応答してサービスのホスト。</span><span class="sxs-lookup"><span data-stu-id="51c67-138">In the IIS or WAS hosting environment, however, the WCF infrastructure is dynamically instantiating your service’s host in response to incoming messages.</span></span> <span data-ttu-id="51c67-139">このホスト環境でもカスタム サービス ホストを使用できますが、ServiceHostFactory の形式でコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="51c67-139">Custom service hosts can also be used in this hosting environment, but they require some additional code in the form of a ServiceHostFactory.</span></span> <span data-ttu-id="51c67-140">次に示すコードは、カスタム <xref:System.ServiceModel.Activation.ServiceHostFactory> のインスタンスを返す、`SelfDescribingServiceHost` の派生クラスの例です。</span><span class="sxs-lookup"><span data-stu-id="51c67-140">The following code shows a derivative of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns instances of our custom `SelfDescribingServiceHost`.</span></span>  
  
```  
public class SelfDescribingServiceHostFactory : ServiceHostFactory  
{  
    protected override ServiceHost CreateServiceHost(Type serviceType,   
     Uri[] baseAddresses)  
    {  
        //All the custom factory does is return a new instance  
        //of our custom host class. The bulk of the custom logic should  
        //live in the custom host (as opposed to the factory)   
        //for maximum  
        //reuse value outside of the IIS/WAS hosting environment.  
        return new SelfDescribingServiceHost(serviceType,     
                                             baseAddresses);  
    }  
}  
```  
  
 <span data-ttu-id="51c67-141">上のコードでわかるように、カスタム ServiceHostFactory の実装は非常に簡単です。</span><span class="sxs-lookup"><span data-stu-id="51c67-141">As you can see, implementing a custom ServiceHostFactory is very straightforward.</span></span> <span data-ttu-id="51c67-142">すべてのカスタム ロジックは ServiceHost 実装内部にあり、このファクトリによって派生クラスのインスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="51c67-142">All of the custom logic resides inside of the ServiceHost implementation; the factory returns an instance of the derived class.</span></span>  
  
 <span data-ttu-id="51c67-143">サービス実装と共にカスタム ファクトリを使用するには、いくつかのメタデータをサービスの .svc ファイルに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="51c67-143">To use a custom factory with a service implementation, we must add some additional metadata to the service’s .svc file.</span></span>  
  
```  
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"  
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"  
               language=c# Debug="true" %>  
```  
  
 <span data-ttu-id="51c67-144">ここでは、`Factory` 属性を `@ServiceHost` ディレクティブに追加し、カスタム ファクトリの CLR 型の名前を属性値として渡しました。</span><span class="sxs-lookup"><span data-stu-id="51c67-144">Here we have added an additional `Factory` attribute to the `@ServiceHost` directive, and passed the CLR type name of our custom factory as the attribute’s value.</span></span> <span data-ttu-id="51c67-145">WCF ホスティング インフラストラクチャが最初に ServiceHostFactory のインスタンスを作成し、サービス ホスト自体を呼び出すことによってインスタンス化し IIS または WAS は、このサービスのメッセージを受信したときに`ServiceHostFactory.CreateServiceHost()`です。</span><span class="sxs-lookup"><span data-stu-id="51c67-145">When IIS or WAS receives a message for this service, the WCF hosting infrastructure first creates an instance of the ServiceHostFactory and then instantiate the service host itself by calling `ServiceHostFactory.CreateServiceHost()`.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="51c67-146">サンプルの実行</span><span class="sxs-lookup"><span data-stu-id="51c67-146">Running the Sample</span></span>  
 <span data-ttu-id="51c67-147">このサンプルには完全な機能を持つクライアントとサービスの実装が用意されていますが、ここでの目的は、カスタム ホストを使用してサービスのランタイム動作を変更する方法を示すことです。次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="51c67-147">Although this sample does provide a fully-functional client and service implementation, the point of the sample is to illustrate how to alter a service’s run-time behavior by means of a custom host., do the following steps:</span></span>  
  
#### <a name="to-observe-the-effect-of-the-custom-host"></a><span data-ttu-id="51c67-148">カスタム ホストの影響を確認するには</span><span class="sxs-lookup"><span data-stu-id="51c67-148">To observe the effect of the custom host</span></span>  
  
1.  <span data-ttu-id="51c67-149">サービスの Web.config ファイルを開き、その構成ではサービスのメタデータが明示的には有効にされていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="51c67-149">Open the service’s Web.config file and observe that there is no configuration explicitly enabling metadata for the service.</span></span>  
  
2.  <span data-ttu-id="51c67-150">サービスの .svc ファイルを開き、されることを確認、@ServiceHostディレクティブには、カスタム ServiceHostFactory の名前を示す Factory 属性が含まれています。</span><span class="sxs-lookup"><span data-stu-id="51c67-150">Open the service’s .svc file and observe that its @ServiceHost directive contains a Factory attribute that specifies the name of a custom ServiceHostFactory.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="51c67-151">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="51c67-151">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="51c67-152">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="51c67-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="51c67-153">指示に従って、ソリューションをビルドする[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="51c67-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="51c67-154">ソリューションがビルドされたら、Setup.bat を実行し、[!INCLUDE[iisver](../../../../includes/iisver-md.md)] で ServiceModelSamples アプリケーションを設定します。</span><span class="sxs-lookup"><span data-stu-id="51c67-154">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span> <span data-ttu-id="51c67-155">ServiceModelSamples ディレクトリは、[!INCLUDE[iisver](../../../../includes/iisver-md.md)] アプリケーションとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="51c67-155">The ServiceModelSamples directory should now appear as an [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Application.</span></span>  
  
4.  <span data-ttu-id="51c67-156">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="51c67-156">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="51c67-157">[!INCLUDE[iisver](../../../../includes/iisver-md.md)] アプリケーションを削除するには、Cleanup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="51c67-157">To remove the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] application, run Cleanup.bat.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51c67-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="51c67-158">See Also</span></span>  
 [<span data-ttu-id="51c67-159">方法 : IIS で WCF サービスをホストする</span><span class="sxs-lookup"><span data-stu-id="51c67-159">How to: Host a WCF Service in IIS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)

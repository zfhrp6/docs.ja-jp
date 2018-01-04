---
title: "方法 : 構成を使用せずに ASP.NET AJAX エンドポイントを追加する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7b90ecd94f439472c89d0c075c8b7486abeacf38
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a><span data-ttu-id="99966-102">方法 : 構成を使用せずに ASP.NET AJAX エンドポイントを追加する</span><span class="sxs-lookup"><span data-stu-id="99966-102">How to: Add an ASP.NET AJAX Endpoint Without Using Configuration</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="99966-103"> では、クライアント Web サイトの JavaScript から呼び出される ASP.NET AJAX 対応のエンドポイントを公開するサービスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="99966-103"> allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="99966-104">このようなエンドポイントを作成するには、他のすべての WCF エンドポイントと同様に、構成ファイルを使用するか、または構成要素を必要としないメソッドを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="99966-104">To create such an endpoint, you can either use a configuration file, as with all other WCF endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="99966-105">ここでは、2 番目の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="99966-105">This topic demonstrates the second approach.</span></span>  
  
 <span data-ttu-id="99966-106">構成を使用せずに ASP.NET AJAX エンドポイントを持つサービスを作成するには、サービスがインターネット インフォメーション サービス (IIS) でホストされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="99966-106">To create services with ASP.NET AJAX endpoints without configuration, the services must be hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="99966-107">このアプローチを使用する ASP.NET AJAX エンドポイントをアクティブ化するには指定、<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>工場出荷時のパラメーターとして、 [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) .svc ファイルでディレクティブです。</span><span class="sxs-lookup"><span data-stu-id="99966-107">To activate an ASP.NET AJAX endpoint using this approach, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> as the Factory parameter in the [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive in the .svc file.</span></span> <span data-ttu-id="99966-108">このカスタム ファクトリは自動的に ASP.NET AJAX エンドポイントを構成するコンポーネントであるため、クライアント Web サイトの JavaScript から呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="99966-108">This custom factory is the component that automatically configures an ASP.NET AJAX endpoint so that it can be called from JavaScript on a client Web site.</span></span>  
  
 <span data-ttu-id="99966-109">実際の例では、次を参照してください。、 [AJAX サービスのない構成](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md)です。</span><span class="sxs-lookup"><span data-stu-id="99966-109">For a working example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
 <span data-ttu-id="99966-110">構成要素を使用して ASP.NET AJAX エンドポイントを構成する方法の概要については、次を参照してください。[する方法: ASP.NET AJAX エンドポイントを追加する構成を使用する](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)です。</span><span class="sxs-lookup"><span data-stu-id="99966-110">For an outline of how to configure an ASP.NET AJAX endpoint using configuration elements, see [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="99966-111">基本的な WCF サービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="99966-111">To create a basic WCF service</span></span>  
  
1.  <span data-ttu-id="99966-112">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 属性でマークされたインターフェイスを使用して、基本的な <xref:System.ServiceModel.ServiceContractAttribute> サービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="99966-112">Define a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="99966-113">各操作を <xref:System.ServiceModel.OperationContractAttribute> でマークします。</span><span class="sxs-lookup"><span data-stu-id="99966-113">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="99966-114"><xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> プロパティが設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="99966-114">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
    ```csharp  
    [ServiceContract(Namespace = "MyService")]]  
    public interface ICalculator  
    {  
        [OperationContract]  
        // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2.  <span data-ttu-id="99966-115">`ICalculator` を使用して、`CalculatorService` サービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="99966-115">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  <span data-ttu-id="99966-116">名前空間ブロック内にラップすることにより、`ICalculator` と `CalculatorService` の実装の名前空間を定義します。</span><span class="sxs-lookup"><span data-stu-id="99966-116">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a><span data-ttu-id="99966-117">構成を使用せずにインターネット インフォメーション サービスでサービスをホストするには</span><span class="sxs-lookup"><span data-stu-id="99966-117">To host the service in Internet Information Services without configuration</span></span>  
  
1.  <span data-ttu-id="99966-118">アプリケーションで、.svc という拡張子を付けて新しい service ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="99966-118">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="99966-119">適切なを追加してこのファイルを編集[ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)ディレクティブ、サービスの情報です。</span><span class="sxs-lookup"><span data-stu-id="99966-119">Edit this file by adding the appropriate [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="99966-120">指定する、<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>で使用するのには、 [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)ディレクティブを自動的に ASP.NET AJAX エンドポイントを構成します。</span><span class="sxs-lookup"><span data-stu-id="99966-120">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2.  <span data-ttu-id="99966-121">サービスをビルドしてクライアントから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="99966-121">Build the service and call it from the client.</span></span> <span data-ttu-id="99966-122">呼び出されたサービスがインターネット インフォメーション サービス (IIS) によってアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="99966-122">Internet Information Services (IIS) activates the service when called.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="99966-123">IIS では、ホストを参照してください[する方法: IIS で WCF サービスをホスト](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)です。</span><span class="sxs-lookup"><span data-stu-id="99966-123"> hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="99966-124">サービスを呼び出すには</span><span class="sxs-lookup"><span data-stu-id="99966-124">To call the service</span></span>  
  
1.  <span data-ttu-id="99966-125">.Svc ファイルに相対する空のアドレスでエンドポイントが構成されているサービスが利用できるようになりましたされ、に対してに要求を送信することによって呼び出すことができますので\<操作 > たとえば、service.svc/Add の`Add`操作します。</span><span class="sxs-lookup"><span data-stu-id="99966-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="99966-126">これは、ASP.NET AJAX Script Manager コントロールのスクリプト コレクションにサービス URL を入力することで使用できます。</span><span class="sxs-lookup"><span data-stu-id="99966-126">You can use it by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="99966-127">例については、次を参照してください。、 [AJAX サービスのない構成](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md)です。</span><span class="sxs-lookup"><span data-stu-id="99966-127">For an example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="99966-128">例</span><span class="sxs-lookup"><span data-stu-id="99966-128">Example</span></span>  
  
 <span data-ttu-id="99966-129">自動的に構成されたエンドポイントは、ベース URL に対して相対的に空のアドレスの位置に作成されます。</span><span class="sxs-lookup"><span data-stu-id="99966-129">The automatically-configured endpoint is created at an empty address relative to the base URL.</span></span> <span data-ttu-id="99966-130">この方法では、構成ファイルを追加して使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="99966-130">A configuration file can also be added and used with this approach.</span></span> <span data-ttu-id="99966-131">構成ファイルにエンドポイントの定義がある場合、これらのエンドポイントは自動的に構成されたエンドポイントに追加されます。</span><span class="sxs-lookup"><span data-stu-id="99966-131">If the configuration file contains endpoint definitions, these endpoints are added to the automatically-configured endpoint.</span></span>  
  
 <span data-ttu-id="99966-132">たとえば、service.svc が <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> を使用していて、そのサービス ディレクトリには、<xref:System.ServiceModel.BasicHttpBinding> を使用して "soap" という相対アドレスで同じサービスのエンドポイントを定義する Web.config ファイルが含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="99966-132">For example, service.svc uses the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> and the service directory contains a Web.config file that defines an endpoint for the same service using the <xref:System.ServiceModel.BasicHttpBinding> at the "soap" relative address.</span></span> <span data-ttu-id="99966-133">この場合、サービスには、service.svc に含まれるエンドポイント (ASP.NET AJAX 要求に応答) と、service.svc/soap にあるもう 1 つのエンドポイント (SOAP 要求に応答) の 2 つのエンドポイントが含まれることになります。</span><span class="sxs-lookup"><span data-stu-id="99966-133">In this case, the service contains two endpoints: one at service.svc (which responds to ASP.NET AJAX requests) and another at service.svc/soap (which responds to SOAP requests).</span></span>  
  
 <span data-ttu-id="99966-134">構成ファイルで空の相対アドレスにエンドポイントを定義した場合は、<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> が使用されると例外がスローされ、サービスの開始に失敗します。</span><span class="sxs-lookup"><span data-stu-id="99966-134">If the configuration file defines an endpoint at an empty relative address and the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used, an exception is thrown and the service fails to start.</span></span>  
  
 <span data-ttu-id="99966-135">自動的に構成されるエンドポイントの設定を変更するために構成を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="99966-135">You cannot use configuration to modify settings on the automatically-configured endpoint.</span></span> <span data-ttu-id="99966-136">リーダーのクォータなど、設定の変更が必要な場合は、.svc ファイルから <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> を削除し、エンドポイントの構成エントリを作成することで、構成を使用しない方法の採用を中止します。</span><span class="sxs-lookup"><span data-stu-id="99966-136">If any setting (such as a reader quota) must be modified, you must not use the configuration-free approach by removing the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> from the .svc file and creating a configuration entry for the endpoint.</span></span>  
  
 <span data-ttu-id="99966-137"><xref:System.Web.HttpContext> クラスや ASP.NET 承認機構を使用するなど、サービスで ASP.NET 互換モードが必要な場合は、このモードを有効にするために引き続き構成ファイルが必要です。</span><span class="sxs-lookup"><span data-stu-id="99966-137">If your service requires ASP.NET Compatibility Mode - for example, if it uses the <xref:System.Web.HttpContext> class or ASP.NET authorization mechanisms - a configuration file is still required to turn on this mode.</span></span> <span data-ttu-id="99966-138">必要な構成要素は、 [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)要素は、次のように追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99966-138">The configuration element required is the [\<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, which must be added as follows.</span></span>  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="99966-139">[WCF サービスと ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="99966-139"> the [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) topic.</span></span>  
  
 <span data-ttu-id="99966-140"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> クラスは、<xref:System.ServiceModel.Activation.ServiceHostFactory> の派生クラスです。</span><span class="sxs-lookup"><span data-stu-id="99966-140">The <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> class is a derived class of <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span></span> <span data-ttu-id="99966-141">サービス ホスト ファクトリ メカニズムの詳細については、次を参照してください。、[ホストを使用して ServiceHostFactory の拡張](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="99966-141">For a detailed explanation of the service host factory mechanism, see the [Extending Hosting Using ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99966-142">参照</span><span class="sxs-lookup"><span data-stu-id="99966-142">See Also</span></span>  
 [<span data-ttu-id="99966-143">ASP.NET AJAX 用の WCF サービスの作成</span><span class="sxs-lookup"><span data-stu-id="99966-143">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [<span data-ttu-id="99966-144">方法 : AJAX 対応 ASP.NET Web サービスを WCF に移行する</span><span class="sxs-lookup"><span data-stu-id="99966-144">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)

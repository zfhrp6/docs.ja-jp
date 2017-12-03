---
title: "方法 : ASP.NET Web サービス コードを Windows Communication Foundation に移行する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e528c64f-c027-4f2e-ada6-d8f3994cf8d6
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1d6ed443d2b645687d59a3d795c706f303616cfb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-migrate-aspnet-web-service-code-to-the-windows-communication-foundation"></a><span data-ttu-id="ceab6-102">方法 : ASP.NET Web サービス コードを Windows Communication Foundation に移行する</span><span class="sxs-lookup"><span data-stu-id="ceab6-102">How to: Migrate ASP.NET Web Service Code to the Windows Communication Foundation</span></span>
<span data-ttu-id="ceab6-103">ASP.NET Web サービスを [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] に移行する手順を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ceab6-103">The following procedure describes how to migrate an ASP.NET Web Service to [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="ceab6-104">手順</span><span class="sxs-lookup"><span data-stu-id="ceab6-104">Procedure</span></span>  
  
#### <a name="to-migrate-aspnet-web-service-code-to-wcf"></a><span data-ttu-id="ceab6-105">ASP.NET Web サービス コードを WCF に移行するには</span><span class="sxs-lookup"><span data-stu-id="ceab6-105">To migrate ASP.NET Web service code to WCF</span></span>  
  
1.  <span data-ttu-id="ceab6-106">サービスの包括的なテスト セットが存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="ceab6-106">Ensure that a comprehensive set of tests exist for the service.</span></span>  
  
2.  <span data-ttu-id="ceab6-107">サービスの WSDL を生成し、サービスの .asmx ファイルと同じフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="ceab6-107">Generate the WSDL for the service and save a copy in the same folder as the service’s .asmx file.</span></span>  
  
3.  <span data-ttu-id="ceab6-108">ASP.NET Web サービスをアップグレードして、.NET 2.0 を基盤として動作するようにします。</span><span class="sxs-lookup"><span data-stu-id="ceab6-108">Upgrade the ASP.NET Web service to use .NET 2.0.</span></span> <span data-ttu-id="ceab6-109">最初、.NET Framework 2.0 を IIS では、アプリケーションを展開してに記載されているように、コードの変換プロセスを自動化する Visual Studio 2005 を使用[から Visual Studio .NET 2002年/2003 を Visual Studio Web プロジェクト変換ステップバイ ステップ ガイド2005](http://go.microsoft.com/fwlink/?LinkId=96492)です。</span><span class="sxs-lookup"><span data-stu-id="ceab6-109">First deploy the .NET Framework 2.0 to the application in IIS, and then use Visual Studio 2005 to automate the code conversion process, as documented in [Step-By-Step Guide to Converting Web Projects from Visual Studio .NET 2002/2003 to Visual Studio 2005](http://go.microsoft.com/fwlink/?LinkId=96492).</span></span> <span data-ttu-id="ceab6-110">テスト セットを実行します。</span><span class="sxs-lookup"><span data-stu-id="ceab6-110">Run the set of tests.</span></span>  
  
4.  <span data-ttu-id="ceab6-111">`Namespace` 属性の `Name` および <xref:System.Web.Services.WebService> パラメーターにまだ値を指定していない場合は、ここで明示的に指定します。</span><span class="sxs-lookup"><span data-stu-id="ceab6-111">Provide explicit values for the `Namespace` and `Name` parameters of the <xref:System.Web.Services.WebService> attributes if they are not provided already.</span></span> <span data-ttu-id="ceab6-112">`MessageName` の <xref:System.Web.Services.WebMethodAttribute> パラメーターについても同様に値を指定してください。</span><span class="sxs-lookup"><span data-stu-id="ceab6-112">Do the same for the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span> <span data-ttu-id="ceab6-113">メソッドに要求が送られるように SOAPAction HTTP ヘッダーに値を明示的に指定していない場合は、`Action` で <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> パラメーターの既定値を明示的に指定します。</span><span class="sxs-lookup"><span data-stu-id="ceab6-113">If explicit values are not already provided for the SOAPAction HTTP headers by which requests are routed to methods, then explicitly specify the default value of the `Action` parameter with a <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span></span>  
  
    ```  
    [WebService(Namespace = "http://tempuri.org/", Name = "Adder")]  
    public class Adder  
    {  
         [WebMethod(MessageName = "Add")]  
         [SoapDocumentMethod(Action = "http://tempuri.org/Add")]  
         public double Add(SumInput input)  
         {  
              double sum = 0.00;  
              foreach (double inputValue in input.Input)  
              {  
                  sum += inputValue;  
              }  
          return sum;  
         }  
    }  
    ```  
  
5.  <span data-ttu-id="ceab6-114">変更点をテストします。</span><span class="sxs-lookup"><span data-stu-id="ceab6-114">Test the change.</span></span>  
  
6.  <span data-ttu-id="ceab6-115">クラスのメソッド本体にある実質的なコードを、独立した別のクラスに移動し、これを元のクラスで使用します。</span><span class="sxs-lookup"><span data-stu-id="ceab6-115">Move any substantive code in the bodies of the methods of the class to a separate class that the original class is made to use.</span></span>  
  
    ```  
    [WebService(Namespace = "http://tempuri.org/", Name = "Adder")]  
    public class Adder  
    {  
         [WebMethod(MessageName = "Add")]  
         [SoapDocumentMethod(Action = "http://tempuri.org/Add")]  
         public double Add(SumInput input)  
         {  
              return new ActualAdder().Add(input);  
         }  
    }  
  
    internal class ActualAdder  
    {  
         internal double Add(SumInput input)  
         {  
              double sum = 0.00;  
              foreach (double inputValue in input.Input)  
              {  
                  sum += inputValue;  
              }  
          return sum;  
         }  
    }  
    ```  
  
7.  <span data-ttu-id="ceab6-116">変更点をテストします。</span><span class="sxs-lookup"><span data-stu-id="ceab6-116">Test the change.</span></span>  
  
8.  <span data-ttu-id="ceab6-117">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のアセンブリである System.ServiceModel および System.Runtime.Serialization の参照を ASP.NET Web サービス プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="ceab6-117">Add references to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] assemblies System.ServiceModel and System.Runtime.Serialization to the ASP.NET Web service project.</span></span>  
  
9. <span data-ttu-id="ceab6-118">実行[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)を生成する、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSDL からクライアント クラスです。</span><span class="sxs-lookup"><span data-stu-id="ceab6-118">Run [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class from the WSDL.</span></span> <span data-ttu-id="ceab6-119">生成されたクラス モジュールをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="ceab6-119">Add the generated class module to the solution.</span></span>  
  
10. <span data-ttu-id="ceab6-120">前の手順で生成したクラス モジュールには、インターフェイスの定義が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ceab6-120">The class module generated in the preceding step contains the definition of an interface.</span></span>  
  
    ```  
    [System.ServiceModel.ServiceContractAttribute()]  
    public interface AdderSoap  
    {  
         [System.ServiceModel.OperationContractAttribute(  
          Action="http://tempuri.org/Add",   
          ReplyAction="http://tempuri.org/Add")]  
         AddResponse Add(AddRequest request);  
    }  
    ```  
  
     <span data-ttu-id="ceab6-121">ASP.NET Web サービス クラスの定義を変更して、次のコード例のように、このインターフェイスを実装するようにします。</span><span class="sxs-lookup"><span data-stu-id="ceab6-121">Modify the definition of the ASP.NET Web service class so that the class is defined as implementing that interface, as shown in the following sample code.</span></span>  
  
    ```  
    [WebService(Namespace = "http://tempuri.org/", Name = "Adder")]  
    public class Adder: AdderSoap  
    {  
         [WebMethod(MessageName = "Add")]  
         [SoapDocumentMethod(Action = "http://tempuri.org/Add")]  
         public double Add(SumInput input)  
         {  
              return new ActualAdder().Add(input);  
         }  
  
         public AddResponse Add(AddRequest request)  
         {  
            return new AddResponse(  
            new AddResponseBody(  
            this.Add(request.Body.input)));  
         }  
    }  
    ```  
  
11. <span data-ttu-id="ceab6-122">プロジェクトをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="ceab6-122">Compile the project.</span></span> <span data-ttu-id="ceab6-123">手順 9. で生成したコードには型定義の重複があるため、エラーが何件か発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ceab6-123">There may be some errors due to the code generated in step nine that duplicated some type definitions.</span></span> <span data-ttu-id="ceab6-124">発生したエラーは、通常は、元からあった方の型定義を削除することで修正できます。</span><span class="sxs-lookup"><span data-stu-id="ceab6-124">Repair those errors, usually by deleting the pre-existing definitions of the types.</span></span> <span data-ttu-id="ceab6-125">変更点をテストします。</span><span class="sxs-lookup"><span data-stu-id="ceab6-125">Test the change.</span></span>  
  
12. <span data-ttu-id="ceab6-126"><xref:System.Web.Services.WebService>、<xref:System.Web.Services.WebMethodAttribute>、<xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> など、ASP.NET 固有の属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="ceab6-126">Remove the ASP.NET-specific attributes, such as the <xref:System.Web.Services.WebService>, <xref:System.Web.Services.WebMethodAttribute> and <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>.</span></span>  
  
    ```  
    public class Adder: AdderSoap  
    {  
         public double Add(SumInput input)  
         {  
              return new ActualAdder().Add(input);  
         }  
  
         public AddResponse Add(AddRequest request)  
         {  
              return new AddResponse(  
             new AddResponseBody(  
            this.Add(request.Body.input)));  
         }  
    }  
    ```  
  
13. <span data-ttu-id="ceab6-127">以上の手順により、クラスは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス型になりました。ASP.NET Web サービスが次のいずれかに依存する場合は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET 互換モードであることを要求するよう、クラスのモードを設定します。</span><span class="sxs-lookup"><span data-stu-id="ceab6-127">Configure the class, which is now a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service type, to require [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET compatibility mode if the ASP.NET Web service relied on any of the following:</span></span>  
  
    -   <span data-ttu-id="ceab6-128"><xref:System.Web.HttpContext> クラス</span><span class="sxs-lookup"><span data-stu-id="ceab6-128">The <xref:System.Web.HttpContext> class.</span></span>  
  
    -   <span data-ttu-id="ceab6-129">ASP.NET プロファイル</span><span class="sxs-lookup"><span data-stu-id="ceab6-129">The ASP.NET Profiles.</span></span>  
  
    -   <span data-ttu-id="ceab6-130">.asmx ファイルの ACL</span><span class="sxs-lookup"><span data-stu-id="ceab6-130">ACLs on .asmx files.</span></span>  
  
    -   <span data-ttu-id="ceab6-131">IIS 認証オプション</span><span class="sxs-lookup"><span data-stu-id="ceab6-131">IIS authentication options.</span></span>  
  
    -   <span data-ttu-id="ceab6-132">ASP.NET の偽装オプション</span><span class="sxs-lookup"><span data-stu-id="ceab6-132">ASP.NET impersonation options.</span></span>  
  
    -   <span data-ttu-id="ceab6-133">ASP.NET のグローバリゼーション</span><span class="sxs-lookup"><span data-stu-id="ceab6-133">ASP.NET globalization.</span></span>  
  
    ```  
    [System.ServiceModel.AspNetCompatibilityRequirements(  
      RequirementsMode=AspNetCompatbilityRequirementsMode.Required)]  
    public class Adder: AdderSoap  
    ```  
  
14. <span data-ttu-id="ceab6-134">元の .asmx ファイルを .asmx.old と改名します。</span><span class="sxs-lookup"><span data-stu-id="ceab6-134">Rename the original .asmx file to .asmx.old.</span></span>  
  
15. <span data-ttu-id="ceab6-135">サービスの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス ファイルを作成し、その拡張子を .asmx として、IIS のアプリケーション ルートに保存します。</span><span class="sxs-lookup"><span data-stu-id="ceab6-135">Create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service file for the service, give it the extension, .asmx, and save it into the application root in IIS.</span></span>  
  
    ```xml  
    <%@Service Class="MyOrganization.Adder" %>  
    <%@Assembly Name="MyServiceAssembly" %>   
    ```  
  
16. <span data-ttu-id="ceab6-136">サービスの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 構成を Web.config ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="ceab6-136">Add a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuration for the service to its Web.config file.</span></span> <span data-ttu-id="ceab6-137">使用するサービスを構成、 [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)、上記の手順で作成された .asmx 拡張子を持つサービス ファイルを使用して、自身の WSDL を生成しないことが手順 2 からの WSDL を使用します。</span><span class="sxs-lookup"><span data-stu-id="ceab6-137">Configure the service to use the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), to use the service file with the .asmx extension created in the preceding steps, and to not generate WSDL for itself, but to use the WSDL from step two.</span></span> <span data-ttu-id="ceab6-138">さらに、必要に応じて、ASP.NET 互換モードを使用するように設定します。</span><span class="sxs-lookup"><span data-stu-id="ceab6-138">Also configure it to use ASP.NET compatibility mode if necessary.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
     <system.web>  
      <compilation>  
      <buildProviders>  
       <remove extension=".asmx" />  
       <add extension=".asmx"   
        type=  
        "System.ServiceModel.Activation.ServiceBuildProvider,  
        T:System.ServiceModel, Version=2.0.0.0,   
       Culture=neutral,   
       PublicKeyToken=b77a5c561934e089" />  
      </buildProviders>  
      </compilation>  
     </system.web>  
     <system.serviceModel>  
      <services>  
      <service name="MyOrganization.Adder "  
        behaviorConfiguration="AdderBehavior">  
       <endpoint   
        address=""  
        binding="basicHttpBinding"  
        contract="AdderSoap "/>  
       </service>  
      </services>  
      <behaviors>  
      <behavior name="AdderBehavior">  
       <metadataPublishing   
        enableMetadataExchange="true"   
        enableGetWsdl="true"   
        enableHelpPage="true"   
        metadataLocation=  
        "http://MyHost.com/AdderService/Service.WSDL"/>  
      </behavior>  
      </behaviors>  
      <serviceHostingEnvironment   
       aspNetCompatibilityEnabled ="true"/>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
17. <span data-ttu-id="ceab6-139">構成を保存します。</span><span class="sxs-lookup"><span data-stu-id="ceab6-139">Save the configuration.</span></span>  
  
18. <span data-ttu-id="ceab6-140">プロジェクトをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="ceab6-140">Compile the project.</span></span>  
  
19. <span data-ttu-id="ceab6-141">テスト セットを実行して、想定どおりに変更されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="ceab6-141">Run the set of tests to make sure all the changes work.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceab6-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="ceab6-142">See Also</span></span>  
 [<span data-ttu-id="ceab6-143">方法: ASP.NET Web サービス クライアント コードを Windows Communication Foundation に移行</span><span class="sxs-lookup"><span data-stu-id="ceab6-143">How to: Migrate ASP.NET Web Service Client Code to the Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)

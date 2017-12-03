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
# <a name="how-to-migrate-aspnet-web-service-code-to-the-windows-communication-foundation"></a>方法 : ASP.NET Web サービス コードを Windows Communication Foundation に移行する
ASP.NET Web サービスを [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] に移行する手順を次に示します。  
  
## <a name="procedure"></a>手順  
  
#### <a name="to-migrate-aspnet-web-service-code-to-wcf"></a>ASP.NET Web サービス コードを WCF に移行するには  
  
1.  サービスの包括的なテスト セットが存在することを確認します。  
  
2.  サービスの WSDL を生成し、サービスの .asmx ファイルと同じフォルダーに保存します。  
  
3.  ASP.NET Web サービスをアップグレードして、.NET 2.0 を基盤として動作するようにします。 最初、.NET Framework 2.0 を IIS では、アプリケーションを展開してに記載されているように、コードの変換プロセスを自動化する Visual Studio 2005 を使用[から Visual Studio .NET 2002年/2003 を Visual Studio Web プロジェクト変換ステップバイ ステップ ガイド2005](http://go.microsoft.com/fwlink/?LinkId=96492)です。 テスト セットを実行します。  
  
4.  `Namespace` 属性の `Name` および <xref:System.Web.Services.WebService> パラメーターにまだ値を指定していない場合は、ここで明示的に指定します。 `MessageName` の <xref:System.Web.Services.WebMethodAttribute> パラメーターについても同様に値を指定してください。 メソッドに要求が送られるように SOAPAction HTTP ヘッダーに値を明示的に指定していない場合は、`Action` で <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> パラメーターの既定値を明示的に指定します。  
  
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
  
5.  変更点をテストします。  
  
6.  クラスのメソッド本体にある実質的なコードを、独立した別のクラスに移動し、これを元のクラスで使用します。  
  
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
  
7.  変更点をテストします。  
  
8.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のアセンブリである System.ServiceModel および System.Runtime.Serialization の参照を ASP.NET Web サービス プロジェクトに追加します。  
  
9. 実行[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)を生成する、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSDL からクライアント クラスです。 生成されたクラス モジュールをソリューションに追加します。  
  
10. 前の手順で生成したクラス モジュールには、インターフェイスの定義が含まれます。  
  
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
  
     ASP.NET Web サービス クラスの定義を変更して、次のコード例のように、このインターフェイスを実装するようにします。  
  
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
  
11. プロジェクトをコンパイルします。 手順 9. で生成したコードには型定義の重複があるため、エラーが何件か発生する可能性があります。 発生したエラーは、通常は、元からあった方の型定義を削除することで修正できます。 変更点をテストします。  
  
12. <xref:System.Web.Services.WebService>、<xref:System.Web.Services.WebMethodAttribute>、<xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> など、ASP.NET 固有の属性を削除します。  
  
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
  
13. 以上の手順により、クラスは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス型になりました。ASP.NET Web サービスが次のいずれかに依存する場合は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET 互換モードであることを要求するよう、クラスのモードを設定します。  
  
    -   <xref:System.Web.HttpContext> クラス  
  
    -   ASP.NET プロファイル  
  
    -   .asmx ファイルの ACL  
  
    -   IIS 認証オプション  
  
    -   ASP.NET の偽装オプション  
  
    -   ASP.NET のグローバリゼーション  
  
    ```  
    [System.ServiceModel.AspNetCompatibilityRequirements(  
      RequirementsMode=AspNetCompatbilityRequirementsMode.Required)]  
    public class Adder: AdderSoap  
    ```  
  
14. 元の .asmx ファイルを .asmx.old と改名します。  
  
15. サービスの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス ファイルを作成し、その拡張子を .asmx として、IIS のアプリケーション ルートに保存します。  
  
    ```xml  
    <%@Service Class="MyOrganization.Adder" %>  
    <%@Assembly Name="MyServiceAssembly" %>   
    ```  
  
16. サービスの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 構成を Web.config ファイルに追加します。 使用するサービスを構成、 [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)、上記の手順で作成された .asmx 拡張子を持つサービス ファイルを使用して、自身の WSDL を生成しないことが手順 2 からの WSDL を使用します。 さらに、必要に応じて、ASP.NET 互換モードを使用するように設定します。  
  
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
  
17. 構成を保存します。  
  
18. プロジェクトをコンパイルします。  
  
19. テスト セットを実行して、想定どおりに変更されていることを確認してください。  
  
## <a name="see-also"></a>関連項目  
 [方法: ASP.NET Web サービス クライアント コードを Windows Communication Foundation に移行](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)

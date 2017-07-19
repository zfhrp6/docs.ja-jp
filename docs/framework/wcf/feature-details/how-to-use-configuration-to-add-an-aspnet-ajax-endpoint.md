---
title: "方法 : 構成を使用して ASP.NET AJAX エンドポイントを追加する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# 方法 : 構成を使用して ASP.NET AJAX エンドポイントを追加する
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、クライアント Web サイトの JavaScript から呼び出される ASP.NET AJAX 対応のエンドポイントを使用できるようにするサービスを作成できます。このようなエンドポイントを作成するには、他のすべての [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] エンドポイントと同様に、構成ファイルを使用するか、または構成要素を必要としないメソッドを使用できます。ここでは、構成を使用する方法について説明します。  
  
 サービス エンドポイントを ASP.NET AJAX 対応にする手順には、<xref:System.ServiceModel.WebHttpBinding> を使用するようにエンドポイントを構成し、[\<enableWebScript\>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) エンドポイント動作を追加することが含まれます。エンドポイントの構成後、サービスを実装してホストする手順は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスで使用される手順に似ています。実施例については、「[HTTP POST を使用する AJAX サービス](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)」を参照してください。  
  
 構成を使用せずに ASP.NET AJAX エンドポイントを構成する方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : 構成を使用せずに ASP.NET AJAX エンドポイントを追加する](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)」を参照してください。  
  
### 基本的な WCF サービスを作成するには  
  
1.  <xref:System.ServiceModel.ServiceContractAttribute> 属性でマークされたインターフェイスを使用して、基本的な [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス コントラクトを定義します。各操作を <xref:System.ServiceModel.OperationContractAttribute> でマークします。<xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> プロパティが設定されていることを確認します。  
  
    ```  
    [ServiceContract(Namespace = "MyService")]  
    public interface ICalculator  
    {  
        [OperationContract]  
         // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2.  `CalculatorService` を使用して、`ICalculator` サービス コントラクトを実装します。  
  
    ```  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  名前空間ブロック内にラップすることにより、`ICalculator` と `CalculatorService` の実装の名前空間を定義します。  
  
    ```  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### サービスに ASP.NET AJAX エンドポイントを作成するには  
  
1.  動作の構成を作成し、サービスの ASP.NET AJAX 対応のエンドポイント用に [\<enableWebScript\>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) 動作を指定します。  
  
    ```  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="AspNetAjaxBehavior">  
                    <enableWebScript />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
    </system.serviceModel>  
    ```  
  
2.  <xref:System.ServiceModel.WebHttpBinding> と、前の手順で定義した ASP.NET AJAX 動作を使用するサービスのエンドポイントを作成します。  
  
    ```  
    <system.serviceModel>  
        <services>  
            <service name="Microsoft.Ajax.Samples.CalculatorService">  
                <endpoint address=""  
                    behaviorConfiguration="AspNetAjaxBehavior"   
                    binding="webHttpBinding"  
                    contract="Microsoft.Ajax.Samples.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>   
    ```  
  
### IIS でサービスをホストするには  
  
1.  IIS でサービスをホストするには、アプリケーションで .svc 拡張子の新しいサービス ファイルを作成します。サービスに該当する [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) ディレクティブ情報を追加して、このファイルを編集します。たとえば、`CalculatorService` サンプルに対応するサービス ファイルのコンテンツには、次の情報が記述されています。  
  
    ```  
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2.  IIS でのホスト[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : IIS で WCF サービスをホストする](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)」を参照してください。  
  
### サービスを呼び出すには  
  
1.  エンドポイントは .svc ファイルを基準にした空のアドレスの位置に構成されているので、サービスは使用可能であり、service.svc\/\<操作\> に対して要求を送信することで、サービスを呼び出すことができます。たとえば、service.svc\/Add では `Add` 操作を呼び出します。これは、ASP.NET AJAX Script Manager コントロールのスクリプト コレクションにエンドポイント URL を入力することで使用できます。例については、「[HTTP POST を使用する AJAX サービス](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)」を参照してください。  
  
## 参照  
 [ASP.NET AJAX 用の WCF サービスの作成](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)   
 [方法 : AJAX 対応 ASP.NET Web サービスを WCF に移行する](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
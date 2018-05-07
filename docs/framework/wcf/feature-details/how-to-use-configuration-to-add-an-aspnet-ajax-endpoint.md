---
title: '方法 : 構成を使用して ASP.NET AJAX エンドポイントを追加する'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: f14b441ead7c701aa4f794370fc5f54ad3b4a4e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a>方法 : 構成を使用して ASP.NET AJAX エンドポイントを追加する
Windows Communication Foundation (WCF) では、ASP.NET AJAX 対応エンドポイントをクライアントの Web サイトの JavaScript から呼び出すことが使用できるようにするサービスを作成することができます。 このようなエンドポイントを作成するには、他のすべての Windows Communication Foundation (WCF) エンドポイントと同様に、構成ファイルを使用するか、または、構成要素を必要としないメソッドを使用できます。 ここでは、構成を使用する方法について説明します。  
  
 ASP.NET AJAX 対応になるするサービス エンドポイントを有効にするプロシージャの部分で使用するエンドポイントを構成するは、<xref:System.ServiceModel.WebHttpBinding>を追加して、 [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)エンドポイントの動作です。 エンドポイントを構成した後を実装して、サービスをホストする手順は、すべての WCF サービスで使用されるものと似ています。 実際の例では、次を参照してください。、 [HTTP POST を使用して AJAX サービス](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)です。  
  
 構成を使用せずに ASP.NET AJAX エンドポイントを構成する方法の詳細については、次を参照してください。[する方法: ASP.NET AJAX エンドポイントなしを使用して構成を追加](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)です。  
  
### <a name="to-create-a-basic-wcf-service"></a>基本的な WCF サービスを作成するには  
  
1.  マークされたインターフェイスを持つ基本的な WCF サービス コントラクトを定義、<xref:System.ServiceModel.ServiceContractAttribute>属性。 各操作を <xref:System.ServiceModel.OperationContractAttribute> でマークします。 <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> プロパティが設定されていることを確認します。  
  
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
  
2.  `ICalculator` を使用して、`CalculatorService` サービス コントラクトを実装します。  
  
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
  
### <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a>サービスに ASP.NET AJAX エンドポイントを作成するには  
  
1.  動作の構成を作成し、指定、 [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)サービスの ASP.NET AJAX 対応エンドポイントの動作です。  
  
    ```xml  
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
  
    ```xml  
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
  
### <a name="to-host-the-service-in-iis"></a>IIS でサービスをホストするには  
  
1.  IIS でサービスをホストするには、アプリケーションで .svc 拡張子の新しいサービス ファイルを作成します。 適切なを追加してこのファイルを編集[ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)ディレクティブ、サービスの情報です。 たとえば、`CalculatorService` サンプルに対応するサービス ファイルのコンテンツには、次の情報が記述されています。  
  
    ```  
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2.  IIS でホストの詳細については、次を参照してください。[する方法: IIS で WCF サービスをホスト](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)です。  
  
### <a name="to-call-the-service"></a>サービスを呼び出すには  
  
1.  .Svc ファイルに相対する空のアドレスでエンドポイントが構成されているサービスが利用できるようになりましたされ、に対してに要求を送信することによって呼び出すことができますので\<操作 > たとえば、service.svc/Add の`Add`操作します。 これは、ASP.NET AJAX Script Manager コントロールのスクリプト コレクションにエンドポイント URL を入力することで使用できます。 例については、次を参照してください。、 [HTTP POST を使用して AJAX サービス](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)です。  
  
## <a name="see-also"></a>関連項目  
 [ASP.NET AJAX 用の WCF サービスの作成](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [方法 : AJAX 対応 ASP.NET Web サービスを WCF に移行する](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)

---
title: "方法 : 構成を使用せずに ASP.NET AJAX エンドポイントを追加する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# 方法 : 構成を使用せずに ASP.NET AJAX エンドポイントを追加する
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、クライアント Web サイトの JavaScript から呼び出される ASP.NET AJAX 対応のエンドポイントを公開するサービスを作成できます。 このようなエンドポイントを作成するには、他のすべての WCF エンドポイントと同様に、構成ファイルを使用するか、または構成要素を必要としないメソッドを使用することができます。 ここでは、2 番目の方法について説明します。  
  
 構成を使用せずに ASP.NET AJAX エンドポイントを持つサービスを作成するには、サービスがインターネット インフォメーション サービス (IIS) でホストされている必要があります。 このアプローチを使用して ASP.NET AJAX エンドポイントを有効にするには指定、 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>にある Factory パラメーターとして、 [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) .svc ファイル ディレクティブです。 このカスタム ファクトリは自動的に ASP.NET AJAX エンドポイントを構成するコンポーネントであるため、クライアント Web サイトの JavaScript から呼び出すことができます。  
  
 実施例については、次を参照してください。、[サービスを構成せず AJAX](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md)します。  
  
 構成要素を使用して ASP.NET AJAX エンドポイントを構成する方法の概要を参照してください。[方法: ASP.NET AJAX エンドポイントを追加する構成を使用して](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)します。  
  
### <a name="to-create-a-basic-wcf-service"></a>基本的な WCF サービスを作成するには  
  
1.  基本的な定義[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]でマークされたサービス コントラクト インターフェイスを<xref:System.ServiceModel.ServiceContractAttribute>属性です。 各操作にマークを付ける、 <xref:System.ServiceModel.OperationContractAttribute>します。 設定して、 <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A>プロパティです。  
  
    ```  
    [ServiceContract(Namespace = "MyService")]]  
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
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a>構成を使用せずにインターネット インフォメーション サービスでサービスをホストするには  
  
1.  アプリケーションで、.svc という拡張子を付けて新しい service ファイルを作成します。 このファイルを編集するには、追加、適切な[ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)ディレクティブ情報をサービスします。 指定する、 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>で使用するのには、 [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)ディレクティブで使用すると、自動的に ASP.NET AJAX エンドポイントを構成します。  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2.  サービスをビルドしてクライアントから呼び出します。 呼び出されたサービスがインターネット インフォメーション サービス (IIS) によってアクティブ化されます。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]IIS では、ホストを参照してください[方法: IIS で WCF サービスをホスト](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)します。  
  
### <a name="to-call-the-service"></a>サービスを呼び出すには  
  
1.  .Svc ファイルに相対する空のアドレスでエンドポイントが構成されて、サービスを使用できるよう、に対してに要求を送信することによって呼び出すことがため<>\> - たとえば、service.svc/Add の`Add`操作します。 これは、ASP.NET AJAX Script Manager コントロールのスクリプト コレクションにサービス URL を入力することで使用できます。 例については、次を参照してください。、[サービスを構成せず AJAX](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md)します。  
  
## <a name="example"></a>例  
<!-- TODO: review snippet reference  [!CODE [Microsoft.Win32.RegistryKey#4](Microsoft.Win32.RegistryKey#4)]  -->  
  
 自動的に構成されたエンドポイントは、ベース URL に対して相対的に空のアドレスの位置に作成されます。 この方法では、構成ファイルを追加して使用することもできます。 構成ファイルにエンドポイントの定義がある場合、これらのエンドポイントは自動的に構成されたエンドポイントに追加されます。  
  
 たとえば、service.svc が使用して、 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>サービス ディレクトリを使用して同じサービスのエンドポイントを定義する Web.config ファイルが含まれている、 <xref:System.ServiceModel.BasicHttpBinding> "soap"の相対アドレスにします。 この場合、サービスには、service.svc に含まれるエンドポイント (ASP.NET AJAX 要求に応答) と、service.svc/soap にあるもう&1; つのエンドポイント (SOAP 要求に応答) の&2; つのエンドポイントが含まれることになります。  
  
 構成ファイルが空の相対アドレスにエンドポイントを定義するかどうか、 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>は、使用、例外がスローされ、サービスの開始に失敗します。  
  
 自動的に構成されるエンドポイントの設定を変更するために構成を使用することはできません。 リーダーのクォータなど、設定の有効期限があります変更されると、使用しないでください構成を必要としないアプローチを削除して、 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> .svc ファイルと、エンドポイントの構成エントリを作成するからです。  
  
 サービスが必要な場合 ASP.NET 互換モード - たとえば、使用されている場合、 <xref:System.Web.HttpContext>クラスや ASP.NET 承認機構構成ファイルは、このモードを有効にするために必要です。 必要な構成要素は、 [ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)要素は、次のように追加する必要があります。  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled=”true” /> </system.serviceModel>`  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][WCF サービスと ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)トピックです。  
  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>クラスの派生クラスは、 <xref:System.ServiceModel.Activation.ServiceHostFactory>します。 サービス ホスト ファクトリ機構の詳細については、次を参照してください。、[を使用して ServiceHostFactory のホストを拡張する](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)トピックです。  
  
## <a name="see-also"></a>関連項目  
 [ASP.NET AJAX の WCF サービスを作成します。](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)   
 [方法: AJAX 対応 ASP.NET Web サービスを WCF に移行します。](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
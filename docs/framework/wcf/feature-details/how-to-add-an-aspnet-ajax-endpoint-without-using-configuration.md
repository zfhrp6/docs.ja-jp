---
title: '方法 : 構成を使用せずに ASP.NET AJAX エンドポイントを追加する'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d82febd776bfc51e3e9725701253ed19996349b5
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a>方法 : 構成を使用せずに ASP.NET AJAX エンドポイントを追加する
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、クライアント Web サイトの JavaScript から呼び出される ASP.NET AJAX 対応のエンドポイントを公開するサービスを作成できます。 このようなエンドポイントを作成するには、他のすべての WCF エンドポイントと同様に、構成ファイルを使用するか、または構成要素を必要としないメソッドを使用することができます。 ここでは、2 番目の方法について説明します。  
  
 構成を使用せずに ASP.NET AJAX エンドポイントを持つサービスを作成するには、サービスがインターネット インフォメーション サービス (IIS) でホストされている必要があります。 このアプローチを使用する ASP.NET AJAX エンドポイントをアクティブ化するには指定、<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>工場出荷時のパラメーターとして、 [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) .svc ファイルでディレクティブです。 このカスタム ファクトリは自動的に ASP.NET AJAX エンドポイントを構成するコンポーネントであるため、クライアント Web サイトの JavaScript から呼び出すことができます。  
  
 実際の例では、次を参照してください。、 [AJAX サービスのない構成](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md)です。  
  
 構成要素を使用して ASP.NET AJAX エンドポイントを構成する方法の概要については、次を参照してください。[する方法: ASP.NET AJAX エンドポイントを追加する構成を使用する](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)です。  
  
### <a name="to-create-a-basic-wcf-service"></a>基本的な WCF サービスを作成するには  
  
1.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 属性でマークされたインターフェイスを使用して、基本的な <xref:System.ServiceModel.ServiceContractAttribute> サービス コントラクトを定義します。 各操作を <xref:System.ServiceModel.OperationContractAttribute> でマークします。 <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> プロパティが設定されていることを確認します。  
  
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
  
2.  `ICalculator` を使用して、`CalculatorService` サービス コントラクトを実装します。  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  名前空間ブロック内にラップすることにより、`ICalculator` と `CalculatorService` の実装の名前空間を定義します。  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a>構成を使用せずにインターネット インフォメーション サービスでサービスをホストするには  
  
1.  アプリケーションで、.svc という拡張子を付けて新しい service ファイルを作成します。 適切なを追加してこのファイルを編集[ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)ディレクティブ、サービスの情報です。 指定する、<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>で使用するのには、 [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)ディレクティブを自動的に ASP.NET AJAX エンドポイントを構成します。  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2.  サービスをビルドしてクライアントから呼び出します。 呼び出されたサービスがインターネット インフォメーション サービス (IIS) によってアクティブ化されます。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] IIS では、ホストを参照してください[する方法: IIS で WCF サービスをホスト](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)です。  
  
### <a name="to-call-the-service"></a>サービスを呼び出すには  
  
1.  .Svc ファイルに相対する空のアドレスでエンドポイントが構成されているサービスが利用できるようになりましたされ、に対してに要求を送信することによって呼び出すことができますので\<操作 > たとえば、service.svc/Add の`Add`操作します。 これは、ASP.NET AJAX Script Manager コントロールのスクリプト コレクションにサービス URL を入力することで使用できます。 例については、次を参照してください。、 [AJAX サービスのない構成](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md)です。  
  
## <a name="example"></a>例  
  
 自動的に構成されたエンドポイントは、ベース URL に対して相対的に空のアドレスの位置に作成されます。 この方法では、構成ファイルを追加して使用することもできます。 構成ファイルにエンドポイントの定義がある場合、これらのエンドポイントは自動的に構成されたエンドポイントに追加されます。  
  
 たとえば、service.svc が <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> を使用していて、そのサービス ディレクトリには、<xref:System.ServiceModel.BasicHttpBinding> を使用して "soap" という相対アドレスで同じサービスのエンドポイントを定義する Web.config ファイルが含まれているとします。 この場合、サービスには、service.svc に含まれるエンドポイント (ASP.NET AJAX 要求に応答) と、service.svc/soap にあるもう 1 つのエンドポイント (SOAP 要求に応答) の 2 つのエンドポイントが含まれることになります。  
  
 構成ファイルで空の相対アドレスにエンドポイントを定義した場合は、<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> が使用されると例外がスローされ、サービスの開始に失敗します。  
  
 自動的に構成されるエンドポイントの設定を変更するために構成を使用することはできません。 リーダーのクォータなど、設定の変更が必要な場合は、.svc ファイルから <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> を削除し、エンドポイントの構成エントリを作成することで、構成を使用しない方法の採用を中止します。  
  
 <xref:System.Web.HttpContext> クラスや ASP.NET 承認機構を使用するなど、サービスで ASP.NET 互換モードが必要な場合は、このモードを有効にするために引き続き構成ファイルが必要です。 必要な構成要素は、 [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)要素は、次のように追加する必要があります。  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 詳細については、次を参照してください。、 [WCF サービスと ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)トピックです。  
  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> クラスは、<xref:System.ServiceModel.Activation.ServiceHostFactory> の派生クラスです。 サービス ホスト ファクトリ メカニズムの詳細については、次を参照してください。、[ホストを使用して ServiceHostFactory の拡張](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)トピックです。  
  
## <a name="see-also"></a>関連項目  
 [ASP.NET AJAX 用の WCF サービスの作成](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [方法 : AJAX 対応 ASP.NET Web サービスを WCF に移行する](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)

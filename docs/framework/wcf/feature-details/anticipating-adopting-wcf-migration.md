---
title: 'Windows Communication Foundation の採用: 将来の移行の簡略化'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: aeafc164d16d9dc60ad0b3012da292e9b0bb38b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490046"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>Windows Communication Foundation の採用: 将来の移行の簡略化
新しい ASP.NET アプリケーションの WCF への簡単に将来の移行には、次の推奨事項と同様に、前の推奨事項に従います。  
  
## <a name="protocols"></a>プロトコル  
 ASP.NET 2.0 の SOAP 1.2 サポートを無効にします。  
  
```xml  
<configuration>  
     <system.web>  
      <webServices >  
          <protocols>  
           <remove name="HttpSoap12"/>  
          </protocols>    
      </webServices>  
     </system.web>   
</configuration>  
```  
  
 これは、WCF には、メッセージが SOAP 1.1 と SOAP 1.2 のように、さまざまなプロトコルに準拠している別のエンドポイントを使用して、移動が必要とするために推奨されます。 ASP.NET 2.0 Web サービスが SOAP 1.1 と SOAP 1.2 では、ことはできませんが、既定の構成の両方をサポートするために構成されている転送を確実になる元のアドレスで単一の WCF エンドポイントに移行する場合はすべての ASP.NET Web と互換性があります。サービスの既存のクライアントです。 また、SOAP 1.1 ではなく 1.2 を選択すると、サービスの利用者がさらに厳しく制限されます。  
  
## <a name="service-development"></a>サービスの開発  
 WCF では、適用することでサービス コントラクトを定義することができます、<xref:System.ServiceModel.ServiceContractAttribute>インターフェイスまたはクラスのいずれか。 この属性は、クラスではなくインターフェイスに適用することをお勧めします。これにより、任意の数のクラスでさまざまに実装できるコントラクト定義が作成されます。 ASP.NET 2.0 では、<xref:System.Web.Services.WebService> 属性をクラスだけでなくインターフェイスに適用することもできます。 ただし、既に説明したように ASP.NET 2.0 には不具合があり、<xref:System.Web.Services.WebService> 属性をクラスではなくインターフェイスに適用した場合、この属性の名前空間パラメーターが有効化されません。 あるため、既定値からサービスの名前空間を変更することをお勧めhttp://tempuri.orgの Namespace パラメーターを使用して、<xref:System.Web.Services.WebService>を適用して ASP.NET Web サービスを定義する 1 つ続行、属性、 <xref:System.ServiceModel.ServiceContractAttribute>インターフェイスまたはクラスのいずれかの属性です。  
  
-   これらのインターフェイスを定義するメソッドに含めるコードは、できるだけ少なくします。 これらのメソッドの作業を他のクラスに委任します。 新しい WCF サービスの種類にし、それらのクラス、実質的な作業委任も可能性があります。  
  
-   `MessageName` の <xref:System.Web.Services.WebMethodAttribute> パラメーターを使用して、サービスの動作の明示的な名前を指定します。  
  
    ```  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     そうは、重要なは、ASP.NET での操作の既定の名前は、WCF によって提供される既定の名前と異なるためです。 明示的な名前を指定することで、既定の名前への依存を避けることができます。  
  
-   WCF が実装する操作を多様メソッドをサポートしていないためにを多様メソッドで ASP.NET Web サービスの操作を実装しませんしないでください。  
  
-   <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> を使用して、HTTP 要求をメソッドにルーティングする SOAPAction HTTP ヘッダーの明示的な値を指定します。  
  
    ```  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     このアプローチを ASP.NET および WCF の同じによって使用される SOAPAction の値を既定値に依存することは回避します。  
  
-   SOAP 拡張機能は使用しないでください。 SOAP 拡張機能が必要な場合は、検討されている対象の目的は、WCF によって既に提供されている機能するかどうかを決定します。 そのような場合は実際に場合、考え直して WCF を導入しないすぐにします。  
  
## <a name="state-management"></a>状態管理  
 サービスで状態を維持する必要がないようにします。 だけでなく、アプリケーションのスケーラビリティを侵害する傾向がある状態を維持するは、WCF は、ASP.NET 互換モードで ASP.NET のメカニズムをサポートしていますが、ASP.NET および WCF の状態管理メカニズムが大きく異なります。  
  
## <a name="exception-handling"></a>例外処理  
 サービスで送受信するデータ型の構造を設計するときは、クライアントに伝達する必要があり、サービス内で発生する可能性のあるさまざまな種類の例外を表現する構造も設計します。  
  
```  
[Serializable]  
[XmlRoot(  
     Namespace="ExplicitNamespace", IsNullable=true)]  
    public partial class AnticipatedException {  
  
     private string anticipatedExceptionInformationField;  
  
     public string AnticipatedExceptionInformation {  
      get {  
          return this.anticipatedExceptionInformationField;  
          }  
      set {  
          this.anticipatedExceptionInformationField = value;  
          }  
     }  
}  
```  
  
 これらのクラスには、自分自身を XML にシリアル化する機能を与えます。  
  
```  
public XmlNode ToXML()  
{  
     XmlSerializer serializer = new XmlSerializer(  
      typeof(AnticipatedException));  
     MemoryStream memoryStream = new MemoryStream();  
     XmlTextWriter writer = new XmlTextWriter(  
     memoryStream, UnicodeEncoding.UTF8);  
     serializer.Serialize(writer, this);  
     XmlDocument document = new XmlDocument();  
     document.LoadXml(new string(  
     UnicodeEncoding.UTF8.GetChars(  
     memoryStream.GetBuffer())).Trim());  
    return document.DocumentElement;  
}  
```  
  
 これでこのクラスを使用して、明示的にスローされた <xref:System.Web.Services.Protocols.SoapException> インスタンスの詳細を指定できます。  
  
```  
AnctipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 これらの例外クラスは、WCF で簡単に再利用されます<xref:System.ServiceModel.FaultException%601>新しいをスローするクラス `FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>セキュリティ  
 セキュリティに関する推奨事項を次にいくつか示します。  
  
-   回避としてこれらを使用して ASP.NET 2.0 のプロファイルを使用して使用が制限 ASP.NET 統合モードの場合は、サービスは、WCF に移行されました。  
  
-   Acl を使用して、インターネット インフォメーション サービス (IIS) を使用して Acl をサポートする ASP.NET Web サービスとしてのサービスへのアクセスを制御するを回避するため、WCF はをホストするため、ASP.NET Web サービスが IIS に依存し、WCF は必ずしもありませんを IIS でホストするためです。  
  
-   サービスのリソースへのアクセスを承認するには、ASP.NET 2.0 ロール プロバイダーの使用を検討してください。  
  
## <a name="see-also"></a>関連項目  
 [Windows Communication Foundation 導入の準備: 将来的な統合の容易化](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)

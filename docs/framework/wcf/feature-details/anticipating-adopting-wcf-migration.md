---
title: "Windows Communication Foundation の採用: 将来の移行の簡略化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 375274cd1b67b6dc71d3e66e1c1f063a81db7d8e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a><span data-ttu-id="39434-102">Windows Communication Foundation の採用: 将来の移行の簡略化</span><span class="sxs-lookup"><span data-stu-id="39434-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>
<span data-ttu-id="39434-103">将来、新しい ASP.NET アプリケーションを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] へ簡単に移行できるようにするには、前述の推奨事項および次の推奨事項に従います。</span><span class="sxs-lookup"><span data-stu-id="39434-103">To ensure an easier future migration of new ASP.NET applications to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], follow the preceding recommendations as well as the following recommendations.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="39434-104">プロトコル</span><span class="sxs-lookup"><span data-stu-id="39434-104">Protocols</span></span>  
 <span data-ttu-id="39434-105">ASP.NET 2.0 の SOAP 1.2 サポートを無効にします。</span><span class="sxs-lookup"><span data-stu-id="39434-105">Disable ASP.NET 2.0’s support for SOAP 1.2:</span></span>  
  
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
  
 <span data-ttu-id="39434-106">このような処理を行うのは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ではさまざまなエンドポイントを介してメッセージを交換するため、SOAP 1.1 や SOAP 1.2 など各種プロトコルに対応する必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="39434-106">Doing so is advisable because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires messages conforming to different protocols, like SOAP 1.1 and SOAP 1.2, to go by using different endpoints.</span></span> <span data-ttu-id="39434-107">ASP.NET 2.0 Web サービスが SOAP 1.1 と SOAP 1.2 を両方ともサポートするように構成されている場合 (既定の構成)、その ASP.NET Web サービスの既存の全クライアントと確実に互換性のある、元のアドレスの単一の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] エンドポイントに移行することはできません。</span><span class="sxs-lookup"><span data-stu-id="39434-107">If an ASP.NET 2.0 Web service is configured to support both SOAP 1.1 and SOAP 1.2, which is the default configuration, then it cannot be migrated forward to a single [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint at the original address that would be certainly be compatible with all of the ASP.NET Web service’s existing clients.</span></span> <span data-ttu-id="39434-108">また、SOAP 1.1 ではなく 1.2 を選択すると、サービスの利用者がさらに厳しく制限されます。</span><span class="sxs-lookup"><span data-stu-id="39434-108">Also choosing SOAP 1.2 instead of 1.1 will more severely restrict the clientele of the service.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="39434-109">サービスの開発</span><span class="sxs-lookup"><span data-stu-id="39434-109">Service Development</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="39434-110"> では、<xref:System.ServiceModel.ServiceContractAttribute> をインターフェイスまたはクラスのいずれかに適用することでサービス コントラクトを定義できます。</span><span class="sxs-lookup"><span data-stu-id="39434-110"> allows you to define service contracts by applying the <xref:System.ServiceModel.ServiceContractAttribute> either to interfaces or to classes.</span></span> <span data-ttu-id="39434-111">この属性は、クラスではなくインターフェイスに適用することをお勧めします。これにより、任意の数のクラスでさまざまに実装できるコントラクト定義が作成されます。</span><span class="sxs-lookup"><span data-stu-id="39434-111">It is recommended to apply the attribute to an interface rather than to a class, because doing so creates a definition of a contract that can be variously implemented by any number of classes.</span></span> <span data-ttu-id="39434-112">ASP.NET 2.0 では、<xref:System.Web.Services.WebService> 属性をクラスだけでなくインターフェイスに適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="39434-112">ASP.NET 2.0 supports the option of applying the <xref:System.Web.Services.WebService> attribute to interfaces as well as classes.</span></span> <span data-ttu-id="39434-113">ただし、既に説明したように ASP.NET 2.0 には不具合があり、<xref:System.Web.Services.WebService> 属性をクラスではなくインターフェイスに適用した場合、この属性の名前空間パラメーターが有効化されません。</span><span class="sxs-lookup"><span data-stu-id="39434-113">However, as mentioned already, there is a defect in ASP.NET 2.0, by which the Namespace parameter of the <xref:System.Web.Services.WebService> attribute has no effect when that attribute is applied to an interface rather than a class.</span></span> <span data-ttu-id="39434-114">一般に、<xref:System.Web.Services.WebService> 属性の名前空間パラメーターを使用して、サービスの名前空間を既定値の http://tempuri.org から変更することが望ましので、引き続き <xref:System.ServiceModel.ServiceContractAttribute> 属性をインターフェイスまたはクラスに適用して ASP.NET Web サービスを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39434-114">Since it is generally advisable to modify the namespace of a service from the default value, http://tempuri.org, using the Namespace parameter of the <xref:System.Web.Services.WebService> attribute, one should continue defining ASP.NET Web Services by applying the <xref:System.ServiceModel.ServiceContractAttribute> attribute either to interfaces or to classes.</span></span>  
  
-   <span data-ttu-id="39434-115">これらのインターフェイスを定義するメソッドに含めるコードは、できるだけ少なくします。</span><span class="sxs-lookup"><span data-stu-id="39434-115">Have as little code as possible in the methods by which those interfaces are defined.</span></span> <span data-ttu-id="39434-116">これらのメソッドの作業を他のクラスに委任します。</span><span class="sxs-lookup"><span data-stu-id="39434-116">Have them delegate their work to other classes.</span></span> <span data-ttu-id="39434-117">その際、新しい [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの型も、実質的な作業をそのクラスに委任できます。</span><span class="sxs-lookup"><span data-stu-id="39434-117">New [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service types could then also delegate their substantive work to those classes.</span></span>  
  
-   <span data-ttu-id="39434-118">`MessageName` の <xref:System.Web.Services.WebMethodAttribute> パラメーターを使用して、サービスの動作の明示的な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="39434-118">Provide explicit names for the operations of a service using the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
    ```  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="39434-119">ASP.NET と [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では既定の動作名が異なるので、この処理は重要です。</span><span class="sxs-lookup"><span data-stu-id="39434-119">Doing so is important, because the default names for operations in ASP.NET are different from the default names supplied by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="39434-120">明示的な名前を指定することで、既定の名前への依存を避けることができます。</span><span class="sxs-lookup"><span data-stu-id="39434-120">By providing explicit names, you avoid relying on the default ones.</span></span>  
  
-   <span data-ttu-id="39434-121">ASP.NET Web サービスの動作を多様メソッドで実装しないでください。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、多様メソッドを使用した動作の実装がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="39434-121">Do not implement ASP.NET Web service operations with polymorphic methods, because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not support implementing operations with polymorphic methods.</span></span>  
  
-   <span data-ttu-id="39434-122"><xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> を使用して、HTTP 要求をメソッドにルーティングする SOAPAction HTTP ヘッダーの明示的な値を指定します。</span><span class="sxs-lookup"><span data-stu-id="39434-122">Use the <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> to provide explicit values for the SOAPAction HTTP headers by which HTTP requests will be routed to methods.</span></span>  
  
    ```  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="39434-123">この方法により、ASP.NET と [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で SOAPAction の同じ既定値を使用する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="39434-123">Taking this approach will circumvent having to rely on the default SOAPAction values used by ASP.NET and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] being the same.</span></span>  
  
-   <span data-ttu-id="39434-124">SOAP 拡張機能は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="39434-124">Avoid using SOAP extensions.</span></span> <span data-ttu-id="39434-125">SOAP 拡張機能が必要な場合は、それを検討する目的の機能が [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で既に提供されていないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="39434-125">If SOAP extensions are required, then determine whether the purpose for which they are being considered is a feature that is already provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="39434-126">目的の機能が備わっている場合は、"すぐには [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を導入しない" という方針を考え直してください。</span><span class="sxs-lookup"><span data-stu-id="39434-126">If that is indeed the case, then reconsider the choice to not adopt [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] right away.</span></span>  
  
## <a name="state-management"></a><span data-ttu-id="39434-127">状態管理</span><span class="sxs-lookup"><span data-stu-id="39434-127">State Management</span></span>  
 <span data-ttu-id="39434-128">サービスで状態を維持する必要がないようにします。</span><span class="sxs-lookup"><span data-stu-id="39434-128">Avoid having to maintain state in services.</span></span> <span data-ttu-id="39434-129">状態を維持すると、アプリケーションのスケーラビリティが損なわれるだけではありません。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の ASP.NET 互換モードを使用すれば ASP.NET のメカニズムに対応できるとはいえ、ASP.NET と [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] とでは状態管理メカニズムが大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="39434-129">Not only does maintaining state tend to compromise the scalability of an application, but the state management mechanisms of ASP.NET and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are very different, although [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does support the ASP.NET mechanisms in ASP.NET compatibility mode.</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="39434-130">例外処理</span><span class="sxs-lookup"><span data-stu-id="39434-130">Exception Handling</span></span>  
 <span data-ttu-id="39434-131">サービスで送受信するデータ型の構造を設計するときは、クライアントに伝達する必要があり、サービス内で発生する可能性のあるさまざまな種類の例外を表現する構造も設計します。</span><span class="sxs-lookup"><span data-stu-id="39434-131">In designing the structures of the data types to be sent and received by a service, also design structures to represent the various types of exceptions that might occur within a service that one might wish to convey to a client.</span></span>  
  
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
  
 <span data-ttu-id="39434-132">これらのクラスには、自分自身を XML にシリアル化する機能を与えます。</span><span class="sxs-lookup"><span data-stu-id="39434-132">Give such classes the ability to serialize themselves to XML:</span></span>  
  
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
  
 <span data-ttu-id="39434-133">これでこのクラスを使用して、明示的にスローされた <xref:System.Web.Services.Protocols.SoapException> インスタンスの詳細を指定できます。</span><span class="sxs-lookup"><span data-stu-id="39434-133">The classes can then be used to provide the details for explicitly thrown <xref:System.Web.Services.Protocols.SoapException> instances:</span></span>  
  
```  
AnctipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 <span data-ttu-id="39434-134">この例外クラスは、新しい [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] をスローするのに、<xref:System.ServiceModel.FaultException%601>`FaultException<AnticipatedException>(anticipatedException);` クラスと共に簡単に再利用できます。</span><span class="sxs-lookup"><span data-stu-id="39434-134">These exception classes will be readily reusable with the[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<xref:System.ServiceModel.FaultException%601> class to throw a new `FaultException<AnticipatedException>(anticipatedException);`</span></span>  
  
## <a name="security"></a><span data-ttu-id="39434-135">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="39434-135">Security</span></span>  
 <span data-ttu-id="39434-136">セキュリティに関する推奨事項を次にいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="39434-136">The following are some security recommendations.</span></span>  
  
-   <span data-ttu-id="39434-137">ASP.NET 2.0 のプロファイルは使用しないでください。サービスを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] へ移行した場合、ASP.NET 統合モードの使用が制限されます。</span><span class="sxs-lookup"><span data-stu-id="39434-137">Avoid using ASP.NET 2.0 Profiles, as using them would restrict the use of ASP.NET Integration Mode if the service was migrated to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
-   <span data-ttu-id="39434-138">サービスへのアクセスを制御する目的で ACL を使用しないでください。ASP.NET Web サービスはインターネット インフォメーション サービス (IIS) を使用して ACL を サポートしますが、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] はサポートしません。これは、ASP.NET Web サービスはホスティングを IIS に依存しますが、WCF は IIS でホストされる必要がないためです。</span><span class="sxs-lookup"><span data-stu-id="39434-138">Avoid using ACLs to control access to services, as ASP.NET Web services supports ACLs using Internet Information Services (IIS), [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not—because ASP.NET Web services depend on IIS for hosting, and WCF does not necessarily have to be hosted in IIS.</span></span>  
  
-   <span data-ttu-id="39434-139">サービスのリソースへのアクセスを承認するには、ASP.NET 2.0 ロール プロバイダーの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="39434-139">Do consider using ASP.NET 2.0 Role Providers for authorizing access to the resources of a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39434-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="39434-140">See Also</span></span>  
 [<span data-ttu-id="39434-141">Windows Communication Foundation の採用: 将来的な統合の容易化</span><span class="sxs-lookup"><span data-stu-id="39434-141">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)

---
title: "Windows Communication Foundation 導入の準備: 将来的な統合の容易化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ccf6e5363da872d3902c12713bd19f5820370428
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a><span data-ttu-id="ac417-102">Windows Communication Foundation 導入の準備: 将来的な統合の容易化</span><span class="sxs-lookup"><span data-stu-id="ac417-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>
<span data-ttu-id="ac417-103">現在 ASP.NET を使用しており、将来 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を採用する予定である場合、このトピックは、新規の ASP.NET Web サービスが [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションと共に問題なく動作するためのガイダンスになります。</span><span class="sxs-lookup"><span data-stu-id="ac417-103">If you use ASP.NET today, and anticipate using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in the future, this topic provides guidance to ensure that new ASP.NET Web services will work well together with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="general-recommendations"></a><span data-ttu-id="ac417-104">一般的な推奨事項</span><span class="sxs-lookup"><span data-stu-id="ac417-104">General Recommendations</span></span>  
 <span data-ttu-id="ac417-105">ASP.NET 2.0 を使用して、すべての新規サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="ac417-105">Adopt ASP.NET 2.0 for any new services.</span></span> <span data-ttu-id="ac417-106">こうすることで、拡張および強化された新バージョンの機能にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="ac417-106">Doing so will provide access to the improvements and enhancements of the new version.</span></span> <span data-ttu-id="ac417-107">またこれにより、ASP.NET 2.0 コンポーネントと [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] コンポーネントとを同じアプリケーション内で使用する可能性にも対応できます。</span><span class="sxs-lookup"><span data-stu-id="ac417-107">However, it will also allow for the possibility of using ASP.NET 2.0 components together with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] components in the same application.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="ac417-108">プロトコル</span><span class="sxs-lookup"><span data-stu-id="ac417-108">Protocols</span></span>  
 <span data-ttu-id="ac417-109">WS-I Basic Profile 1.1 への準拠を検証するには、次のように ASP.NET 2.0 の新機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="ac417-109">Use ASP.NET 2.0’s new facility for validating conformity to the WS-I Basic Profile 1.1:</span></span>  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 <span data-ttu-id="ac417-110">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の定義済みバインディングである [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用することによって、WS-I Basic Profile 1.1 準拠の ASP.NET Web サービスは <xref:System.ServiceModel.BasicHttpBinding> クライアントと相互運用できます。</span><span class="sxs-lookup"><span data-stu-id="ac417-110">ASP.NET Web services that conform to WS-I Basic Profile 1.1 will be interoperable with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients by using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] predefined binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="ac417-111">サービスの開発</span><span class="sxs-lookup"><span data-stu-id="ac417-111">Service Development</span></span>  
 <span data-ttu-id="ac417-112">SOAPAction HTTP ヘッダーではなく、SOAP メッセージの本文要素の完全修飾名に基づいてメッセージをメソッドにルーティングする場合は、<xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> 属性の使用を避けます。</span><span class="sxs-lookup"><span data-stu-id="ac417-112">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the SOAPAction HTTP header.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ac417-113"> は、SOAPAction HTTP ヘッダーを使用してメッセージをルーティングします。</span><span class="sxs-lookup"><span data-stu-id="ac417-113"> uses the SOAPAction HTTP header for routing messages.</span></span>  
  
## <a name="data-representation"></a><span data-ttu-id="ac417-114">データ表現</span><span class="sxs-lookup"><span data-stu-id="ac417-114">Data Representation</span></span>  
 <span data-ttu-id="ac417-115"><xref:System.Xml.Serialization.XmlSerializer> によって既定で型のシリアル化が行われる XML は、XML の名前空間が明示的に定義されている場合、<xref:System.Runtime.Serialization.DataContractSerializer> によって型のシリアル化が行われる XML と意味的に同一です。</span><span class="sxs-lookup"><span data-stu-id="ac417-115">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="ac417-116">将来 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を採用する予定の場合、ASP.NET Web サービスで使用するデータ型を定義するには、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="ac417-116">When defining a data type for use with ASP.NET Web services in anticipation of adopting [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in the future, do the following:</span></span>  
  
1.  <span data-ttu-id="ac417-117">XML スキーマではなく、.NET Framework クラスを使用して型を定義します。</span><span class="sxs-lookup"><span data-stu-id="ac417-117">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
2.  <span data-ttu-id="ac417-118"><xref:System.SerializableAttribute> と <xref:System.Xml.Serialization.XmlRootAttribute> だけをそのクラスに追加します。後者を使用して型の名前空間を明示的に定義してください。</span><span class="sxs-lookup"><span data-stu-id="ac417-118">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="ac417-119">.NET Framework クラスを XML に変換する方法を制御する目的で、<xref:System.Xml.Serialization> 名前空間の属性を追加しないでください。</span><span class="sxs-lookup"><span data-stu-id="ac417-119">Do no add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
 <span data-ttu-id="ac417-120">この手法を採用すると、後から <xref:System.Runtime.Serialization.DataContractAttribute> および <xref:System.Runtime.Serialization.DataMemberAttribute> を追加することで、転送のためにクラスをシリアル化する XML に大きな変更を加えることなく .NET クラスをデータ コントラクトにすることができます。</span><span class="sxs-lookup"><span data-stu-id="ac417-120">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="ac417-121">ASP.NET Web サービスがメッセージ内で使用する型は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションによってデータ コントラクトとして処理することが可能です。これにはさまざまな利点がありますが、特に [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションではより高いパフォーマンスを引き出すことができます。</span><span class="sxs-lookup"><span data-stu-id="ac417-121">The types used in messages by ASP.NET Web services will be able to be processed as data contracts by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications, yielding, amongst other benefits, better performance in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="security"></a><span data-ttu-id="ac417-122">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="ac417-122">Security</span></span>  
 <span data-ttu-id="ac417-123">インターネット インフォメーション サービス (IIS) に用意されている認証オプションは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="ac417-123">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ac417-124"> クライアントではこれらの認証オプションはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="ac417-124"> clients do not support them.</span></span> <span data-ttu-id="ac417-125">サービスをセキュリティで保護する必要がある場合は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で提供されるオプションを使用します。こちらのオプションの方が選択の幅が広く、標準プロトコルに基づいているためです。</span><span class="sxs-lookup"><span data-stu-id="ac417-125">If a service needs to be secured, use the options provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], because these options are richer and are based on standard protocols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac417-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac417-126">See Also</span></span>  
 [<span data-ttu-id="ac417-127">Windows Communication Foundation の採用: 将来の移行の容易化</span><span class="sxs-lookup"><span data-stu-id="ac417-127">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)

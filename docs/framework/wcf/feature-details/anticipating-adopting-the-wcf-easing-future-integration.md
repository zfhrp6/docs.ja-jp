---
title: 'Windows Communication Foundation 導入の準備: 将来的な統合の容易化'
ms.date: 03/30/2017
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
ms.openlocfilehash: f81e158a5e7f897307c0c6d376dfe01dac127ead
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489597"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a><span data-ttu-id="5f5b4-102">Windows Communication Foundation 導入の準備: 将来的な統合の容易化</span><span class="sxs-lookup"><span data-stu-id="5f5b4-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>
<span data-ttu-id="5f5b4-103">現在 ASP.NET を使用して WCF を使用して、将来を予測して、このトピック指針を WCF アプリケーションと共に、新しい ASP.NET Web サービスが動作することを確認します。</span><span class="sxs-lookup"><span data-stu-id="5f5b4-103">If you use ASP.NET today, and anticipate using WCF in the future, this topic provides guidance to ensure that new ASP.NET Web services will work well together with WCF applications.</span></span>  
  
## <a name="general-recommendations"></a><span data-ttu-id="5f5b4-104">一般的な推奨事項</span><span class="sxs-lookup"><span data-stu-id="5f5b4-104">General Recommendations</span></span>  
 <span data-ttu-id="5f5b4-105">ASP.NET 2.0 を使用して、すべての新規サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="5f5b4-105">Adopt ASP.NET 2.0 for any new services.</span></span> <span data-ttu-id="5f5b4-106">こうすることで、拡張および強化された新バージョンの機能にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="5f5b4-106">Doing so will provide access to the improvements and enhancements of the new version.</span></span> <span data-ttu-id="5f5b4-107">ただし、同じアプリケーションで WCF コンポーネントと共に、ASP.NET 2.0 コンポーネントを使用する可能性はこともできます。</span><span class="sxs-lookup"><span data-stu-id="5f5b4-107">However, it will also allow for the possibility of using ASP.NET 2.0 components together with WCF components in the same application.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="5f5b4-108">プロトコル</span><span class="sxs-lookup"><span data-stu-id="5f5b4-108">Protocols</span></span>  
 <span data-ttu-id="5f5b4-109">WS-I Basic Profile 1.1 への準拠を検証するには、次のように ASP.NET 2.0 の新機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="5f5b4-109">Use ASP.NET 2.0’s new facility for validating conformity to the WS-I Basic Profile 1.1:</span></span>  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 <span data-ttu-id="5f5b4-110">WS に準拠する ASP.NET Web サービスのバインド、定義済みの WCF を使用して WCF クライアントと相互運用可能な基本プロファイル 1.1 なります<xref:System.ServiceModel.BasicHttpBinding>です。</span><span class="sxs-lookup"><span data-stu-id="5f5b4-110">ASP.NET Web services that conform to WS-I Basic Profile 1.1 will be interoperable with WCF clients by using WCF predefined binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="5f5b4-111">サービスの開発</span><span class="sxs-lookup"><span data-stu-id="5f5b4-111">Service Development</span></span>  
 <span data-ttu-id="5f5b4-112">SOAPAction HTTP ヘッダーではなく、SOAP メッセージの本文要素の完全修飾名に基づいてメッセージをメソッドにルーティングする場合は、<xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> 属性の使用を避けます。</span><span class="sxs-lookup"><span data-stu-id="5f5b4-112">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the SOAPAction HTTP header.</span></span> <span data-ttu-id="5f5b4-113">WCF では、メッセージのルーティングの SOAPAction HTTP ヘッダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="5f5b4-113">WCF uses the SOAPAction HTTP header for routing messages.</span></span>  
  
## <a name="data-representation"></a><span data-ttu-id="5f5b4-114">データ表現</span><span class="sxs-lookup"><span data-stu-id="5f5b4-114">Data Representation</span></span>  
 <span data-ttu-id="5f5b4-115"><xref:System.Xml.Serialization.XmlSerializer> によって既定で型のシリアル化が行われる XML は、XML の名前空間が明示的に定義されている場合、<xref:System.Runtime.Serialization.DataContractSerializer> によって型のシリアル化が行われる XML と意味的に同一です。</span><span class="sxs-lookup"><span data-stu-id="5f5b4-115">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="5f5b4-116">ASP.NET Web サービスで使用するためのデータ型を定義する、今後の予定の導入 WCF で、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="5f5b4-116">When defining a data type for use with ASP.NET Web services in anticipation of adopting WCF in the future, do the following:</span></span>  
  
1.  <span data-ttu-id="5f5b4-117">XML スキーマではなく、.NET Framework クラスを使用して型を定義します。</span><span class="sxs-lookup"><span data-stu-id="5f5b4-117">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
2.  <span data-ttu-id="5f5b4-118"><xref:System.SerializableAttribute> と <xref:System.Xml.Serialization.XmlRootAttribute> だけをそのクラスに追加します。後者を使用して型の名前空間を明示的に定義してください。</span><span class="sxs-lookup"><span data-stu-id="5f5b4-118">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="5f5b4-119">.NET Framework クラスを XML に変換する方法を制御する目的で、<xref:System.Xml.Serialization> 名前空間の属性を追加しないでください。</span><span class="sxs-lookup"><span data-stu-id="5f5b4-119">Do no add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
 <span data-ttu-id="5f5b4-120">この手法を採用すると、後から <xref:System.Runtime.Serialization.DataContractAttribute> および <xref:System.Runtime.Serialization.DataMemberAttribute> を追加することで、転送のためにクラスをシリアル化する XML に大きな変更を加えることなく .NET クラスをデータ コントラクトにすることができます。</span><span class="sxs-lookup"><span data-stu-id="5f5b4-120">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="5f5b4-121">ASP.NET Web サービスがメッセージで使用される型は引き出す、他の利点は、WCF アプリケーションでパフォーマンスの向上は入力が、WCF アプリケーションでデータ コントラクトとして処理することができます。</span><span class="sxs-lookup"><span data-stu-id="5f5b4-121">The types used in messages by ASP.NET Web services will be able to be processed as data contracts by WCF applications, yielding, amongst other benefits, better performance in WCF applications.</span></span>  
  
## <a name="security"></a><span data-ttu-id="5f5b4-122">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="5f5b4-122">Security</span></span>  
 <span data-ttu-id="5f5b4-123">インターネット インフォメーション サービス (IIS) に用意されている認証オプションは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="5f5b4-123">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> <span data-ttu-id="5f5b4-124">WCF クライアントでは、そのサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="5f5b4-124">WCF clients do not support them.</span></span> <span data-ttu-id="5f5b4-125">保護されるように、サービスに必要な場合は、これらのオプションが豊富なは、標準プロトコルに基づいているため、WCF が提供するオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="5f5b4-125">If a service needs to be secured, use the options provided by WCF, because these options are richer and are based on standard protocols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f5b4-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f5b4-126">See Also</span></span>  
 [<span data-ttu-id="5f5b4-127">Windows Communication Foundation の採用: 将来の移行の簡略化</span><span class="sxs-lookup"><span data-stu-id="5f5b4-127">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)

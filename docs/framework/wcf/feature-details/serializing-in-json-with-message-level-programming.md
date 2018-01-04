---
title: "メッセージ レベルのプログラミングによる JSON 形式でのシリアル化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfa8952c54f29d88cb4975c1924b9c3e94c1c226
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="serializing-in-json-with-message-level-programming"></a><span data-ttu-id="85b3d-102">メッセージ レベルのプログラミングによる JSON 形式でのシリアル化</span><span class="sxs-lookup"><span data-stu-id="85b3d-102">Serializing in Json with Message Level Programming</span></span>
<span data-ttu-id="85b3d-103">WCF は、JSON 形式でのデータのシリアル化をサポートします。</span><span class="sxs-lookup"><span data-stu-id="85b3d-103">WCF supports serializing data in JSON format.</span></span> <span data-ttu-id="85b3d-104">このトピックでは、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> を使用して型をシリアル化することを WCF に命令する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="85b3d-104">This topic describes how to tell WCF to serialize your types using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
## <a name="typed-message-programming"></a><span data-ttu-id="85b3d-105">型指定されたメッセージのプログラミング</span><span class="sxs-lookup"><span data-stu-id="85b3d-105">Typed Message Programming</span></span>  
 <span data-ttu-id="85b3d-106"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> は、<xref:System.ServiceModel.Web.WebGetAttribute> または <xref:System.ServiceModel.Web.WebInvokeAttribute> がサービス操作に適用されるときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="85b3d-106">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is used when the <xref:System.ServiceModel.Web.WebGetAttribute> or the <xref:System.ServiceModel.Web.WebInvokeAttribute> is applied to a service operation.</span></span> <span data-ttu-id="85b3d-107">どちらの属性でも、`RequestFormat` と `ResponseFormat` を指定できます。</span><span class="sxs-lookup"><span data-stu-id="85b3d-107">Both of these attributes allow you to specify the `RequestFormat` and `ResponseFormat`.</span></span> <span data-ttu-id="85b3d-108">要求と応答に JSON を使用するには、両方の属性を `WebMessageFormat.Json` に設定します。</span><span class="sxs-lookup"><span data-stu-id="85b3d-108">To use JSON for requests and responses set both of these to `WebMessageFormat.Json`.</span></span>  <span data-ttu-id="85b3d-109">JSON を使用するには、<xref:System.ServiceModel.WebHttpBinding> を使用する必要があります。これにより、<xref:System.ServiceModel.Description.WebHttpBehavior> が自動的に構成されます。</span><span class="sxs-lookup"><span data-stu-id="85b3d-109">In order to use JSON you must use the <xref:System.ServiceModel.WebHttpBinding> which automatically configures the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span> <span data-ttu-id="85b3d-110">WCF のシリアル化の詳細についてを参照してください:[シリアル化および逆シリアル化](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)、 [Windows Communication Foundation でのシリアル化](http://msdn.microsoft.com/magazine/cc163569.aspx)です。</span><span class="sxs-lookup"><span data-stu-id="85b3d-110">For more information about WCF serialization, see: [Serialization and Deserialization](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md), [Serialization in Windows Communication Foundation](http://msdn.microsoft.com/magazine/cc163569.aspx).</span></span> <span data-ttu-id="85b3d-111">JSON と WCF の詳細については、次を参照してください[An Introduction to WCF を使用した RESTfull サービス](http://msdn.microsoft.com/magazine/dd315413.aspx)、 [.NET 3.5 で WCF サービスを作成する JSON が有効な](http://www.pluralsight-training.net/community/blogs/fritz/archive/2008/01/31/50121.aspx)、および[WCFでRESTの概要](http://msdn.microsoft.com/netframework/dd547388).</span><span class="sxs-lookup"><span data-stu-id="85b3d-111">For more information about JSON and WCF see [An Introduction to RESTfull Services with WCF](http://msdn.microsoft.com/magazine/dd315413.aspx), [Creating JSON-enabled WCF Services in .NET 3.5](http://www.pluralsight-training.net/community/blogs/fritz/archive/2008/01/31/50121.aspx), and [Overview of REST in WCF](http://msdn.microsoft.com/netframework/dd547388).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="85b3d-112">JSON を使用するには、SOAP 通信をサポートしていない <xref:System.ServiceModel.WebHttpBinding> と <xref:System.ServiceModel.Description.WebHttpBehavior> を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="85b3d-112">Using JSON requires use of <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior> which do not support SOAP communication.</span></span> <span data-ttu-id="85b3d-113">サービスと通信する、<xref:System.ServiceModel.WebHttpBinding>サービス メタデータの公開をサポートしないため、クライアント側プロキシを生成する Visual Studio の サービス参照の追加の機能または svcutil コマンド ライン ツールを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="85b3d-113">Services that communicate with the <xref:System.ServiceModel.WebHttpBinding> do not support exposing service metadata so you will not be able to use Visual Studio’s Add Service Reference functionality or the svcutil command-line tool to generate a client-side proxy.</span></span> <span data-ttu-id="85b3d-114">使用するサービス プログラムでの呼び出し方法の詳細<xref:System.ServiceModel.WebHttpBinding>を参照してください[wcf REST サービスを使用する方法](http://blogs.msdn.com/b/pedram/archive/2008/04/21/how-to-consume-rest-services-with-wcf.aspx)です。</span><span class="sxs-lookup"><span data-stu-id="85b3d-114">For more information how you can programmatically call services that use <xref:System.ServiceModel.WebHttpBinding>, see [How to Consume REST Services with WCF](http://blogs.msdn.com/b/pedram/archive/2008/04/21/how-to-consume-rest-services-with-wcf.aspx).</span></span>  
  
## <a name="untyped-message-programming"></a><span data-ttu-id="85b3d-115">型指定されていないメッセージのプログラミング</span><span class="sxs-lookup"><span data-stu-id="85b3d-115">Untyped Message Programming</span></span>  
 <span data-ttu-id="85b3d-116">型指定されていないメッセージ オブジェクトを直接操作する場合は、型指定されていないメッセージのプロパティを明示的に設定して JSON としてシリアル化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="85b3d-116">When working directly with untyped Message objects, you must explicitly set the properties on the untyped message to serialize it as JSON.</span></span> <span data-ttu-id="85b3d-117">これを行う方法を次のコード スニペットに示します。</span><span class="sxs-lookup"><span data-stu-id="85b3d-117">The following code snippet shows how to do this.</span></span>  
  
```  
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,   
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
```  
  
## <a name="see-also"></a><span data-ttu-id="85b3d-118">参照</span><span class="sxs-lookup"><span data-stu-id="85b3d-118">See Also</span></span>  
 [<span data-ttu-id="85b3d-119">AJAX の統合と JSON のサポート</span><span class="sxs-lookup"><span data-stu-id="85b3d-119">AJAX Integration and JSON Support</span></span>](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [<span data-ttu-id="85b3d-120">スタンドアロン JSON のシリアル化</span><span class="sxs-lookup"><span data-stu-id="85b3d-120">Stand-Alone JSON Serialization</span></span>](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)  
 [<span data-ttu-id="85b3d-121">JSON シリアル化</span><span class="sxs-lookup"><span data-stu-id="85b3d-121">JSON Serialization</span></span>](../../../../docs/framework/wcf/samples/json-serialization.md)

---
title: "方法 : コントラクトを SOAP クライアントおよび Web クライアントに公開する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0f13ba797b0c0e5c8b0d1eef271baf62f920f199
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-expose-a-contract-to-soap-and-web-clients"></a><span data-ttu-id="cb38b-102">方法 : コントラクトを SOAP クライアントおよび Web クライアントに公開する</span><span class="sxs-lookup"><span data-stu-id="cb38b-102">How to: Expose a Contract to SOAP and Web Clients</span></span>
<span data-ttu-id="cb38b-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、既定でエンドポイントは SOAP クライアントでのみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="cb38b-103">By default, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] makes endpoints available only to SOAP clients.</span></span> <span data-ttu-id="cb38b-104">[する方法: 基本的な WCF Web HTTP サービスを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)エンドポイントが SOAP 以外のクライアントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="cb38b-104">In [How to: Create a Basic WCF Web HTTP Service](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md), an endpoint is made available to non-SOAP clients.</span></span> <span data-ttu-id="cb38b-105">状況によっては、同じコントラクトを Web エンドポイントと SOAP エンドポイントのどちらとしても利用できることが望ましい場合があります。</span><span class="sxs-lookup"><span data-stu-id="cb38b-105">There may be times when you want to make the same contract available both ways, as a Web endpoint and as a SOAP endpoint.</span></span> <span data-ttu-id="cb38b-106">ここでは、これを実現する方法の例について示します。</span><span class="sxs-lookup"><span data-stu-id="cb38b-106">This topic shows an example of how to do this.</span></span>  
  
### <a name="to-define-the-service-contract"></a><span data-ttu-id="cb38b-107">サービス コントラクトを定義するには</span><span class="sxs-lookup"><span data-stu-id="cb38b-107">To define the service contract</span></span>  
  
1.  <span data-ttu-id="cb38b-108">次のコードのように、<xref:System.ServiceModel.ServiceContractAttribute>、<xref:System.ServiceModel.Web.WebInvokeAttribute> および <xref:System.ServiceModel.Web.WebGetAttribute> の各属性でマークされたインターフェイスを使用して、サービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="cb38b-108">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> and the <xref:System.ServiceModel.Web.WebGetAttribute> attributes, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
     [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="cb38b-109">既定では、<xref:System.ServiceModel.Web.WebInvokeAttribute> は POST 呼び出しを操作にマッピングします。</span><span class="sxs-lookup"><span data-stu-id="cb38b-109">By default <xref:System.ServiceModel.Web.WebInvokeAttribute> maps POST calls to the operation.</span></span> <span data-ttu-id="cb38b-110">ただし、"method=" パラメーターを指定することで、操作にマッピングするメソッドを指定できます。</span><span class="sxs-lookup"><span data-stu-id="cb38b-110">You can, however, specify the method to map to the operation by specifying a "method=" parameter.</span></span> <span data-ttu-id="cb38b-111"><xref:System.ServiceModel.Web.WebGetAttribute> には "method=" パラメーターがないため、サービス操作には GET 呼び出しのみがマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="cb38b-111"><xref:System.ServiceModel.Web.WebGetAttribute> does not have a "method=" parameter and only maps GET calls to the service operation.</span></span>  
  
2.  <span data-ttu-id="cb38b-112">次のコードに示すように、サービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="cb38b-112">Implement the service contract, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="cb38b-113">サービスをホストするには</span><span class="sxs-lookup"><span data-stu-id="cb38b-113">To host the service</span></span>  
  
1.  <span data-ttu-id="cb38b-114">次のコードに示すように、<xref:System.ServiceModel.ServiceHost> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="cb38b-114">Create a <xref:System.ServiceModel.ServiceHost> object, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#2)]
     [!code-vb[htSoapWeb#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#2)]  
  
2.  <span data-ttu-id="cb38b-115">次のコードに示すように、SOAP 以外のエンドポイント用に、<xref:System.ServiceModel.Description.ServiceEndpoint> に <xref:System.ServiceModel.BasicHttpBinding> を追加します。</span><span class="sxs-lookup"><span data-stu-id="cb38b-115">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.BasicHttpBinding> for the SOAP endpoint, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#3)]
     [!code-vb[htSoapWeb#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#3)]  
  
3.  <span data-ttu-id="cb38b-116">次のコードに示すように、SOAP 以外のエンドポイント用に、<xref:System.ServiceModel.Description.ServiceEndpoint> に <xref:System.ServiceModel.WebHttpBinding> を追加し、エンドポイントに <xref:System.ServiceModel.Description.WebHttpBehavior> を追加します。</span><span class="sxs-lookup"><span data-stu-id="cb38b-116">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.WebHttpBinding> for the non-SOAP endpoint and add the <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#4)]
     [!code-vb[htSoapWeb#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#4)]  
  
4.  <span data-ttu-id="cb38b-117">次のコードに示すように、`Open()` を <xref:System.ServiceModel.ServiceHost> インスタンスで呼び出して、サービス ホストを開きます。</span><span class="sxs-lookup"><span data-stu-id="cb38b-117">Call `Open()` on a <xref:System.ServiceModel.ServiceHost> instance to open the service host, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#5)]
     [!code-vb[htSoapWeb#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#5)]  
  
### <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a><span data-ttu-id="cb38b-118">Internet Explorer で GET にマッピングされたサービス操作を呼び出すには</span><span class="sxs-lookup"><span data-stu-id="cb38b-118">To call service operations mapped to GET in Internet Explorer</span></span>  
  
1.  <span data-ttu-id="cb38b-119">Internet Explorer を開き「"`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`"し、ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="cb38b-119">Open Internet Explorer and type "`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`" and press ENTER.</span></span> <span data-ttu-id="cb38b-120">この URL には、サービスのベース アドレス ("http://localhost:8000/") が含まれており、エンドポイントの相対アドレス ("")、呼び出すサービス操作 ("EchoWithGet")、疑問符の後にアンパサンド (&) で区切られた名前付きパラメーターのリストが続きます。</span><span class="sxs-lookup"><span data-stu-id="cb38b-120">The URL contains the base address of the service ("http://localhost:8000/"), the relative address of the endpoint (""), the service operation to call ("EchoWithGet"), and a question mark followed by a list of named parameters separated by an ampersand (&).</span></span>  
  
### <a name="to-call-service-operations-on-the-web-endpoint-in-code"></a><span data-ttu-id="cb38b-121">コードから Web エンドポイントにあるサービス操作を呼び出すには</span><span class="sxs-lookup"><span data-stu-id="cb38b-121">To call service operations on the Web endpoint in code</span></span>  
  
1.  <span data-ttu-id="cb38b-122">次のコードに示すように、<xref:System.ServiceModel.Web.WebChannelFactory%601> のインスタンスを `using` ブロック内に作成します。</span><span class="sxs-lookup"><span data-stu-id="cb38b-122">Create an instance of <xref:System.ServiceModel.Web.WebChannelFactory%601> within a `using` block, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]  
  
> [!NOTE]
>  <span data-ttu-id="cb38b-123">`Close()` は `using` ブロックの末尾のチャネルで自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="cb38b-123">`Close()` is automatically called on the channel at the end of the `using` block.</span></span>  
  
1.  <span data-ttu-id="cb38b-124">次のコードに示すように、チャネルを作成してサービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="cb38b-124">Create the channel and call the service, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]  
  
### <a name="to-call-service-operations-on-the-soap-endpoint"></a><span data-ttu-id="cb38b-125">SOAP エンドポイントにあるサービス操作を呼び出すには</span><span class="sxs-lookup"><span data-stu-id="cb38b-125">To call service operations on the SOAP endpoint</span></span>  
  
1.  <span data-ttu-id="cb38b-126">次のコードに示すように、<xref:System.ServiceModel.ChannelFactory> のインスタンスを `using` ブロック内に作成します。</span><span class="sxs-lookup"><span data-stu-id="cb38b-126">Create an instance of <xref:System.ServiceModel.ChannelFactory> within a `using` block, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
     [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]  
  
2.  <span data-ttu-id="cb38b-127">次のコードに示すように、チャネルを作成してサービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="cb38b-127">Create the channel and call the service, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
     [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]  
  
### <a name="to-close-the-service-host"></a><span data-ttu-id="cb38b-128">サービス ホストを閉じるは</span><span class="sxs-lookup"><span data-stu-id="cb38b-128">To close the service host</span></span>  
  
1.  <span data-ttu-id="cb38b-129">次のコードに示すように、サービス ホストを閉じます。</span><span class="sxs-lookup"><span data-stu-id="cb38b-129">Close the service host, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
     [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="cb38b-130">例</span><span class="sxs-lookup"><span data-stu-id="cb38b-130">Example</span></span>  
 <span data-ttu-id="cb38b-131">このトピックの完全なコードの一覧を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="cb38b-131">The following is the full code listing for this topic.</span></span>  
  
 [!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
 [!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cb38b-132">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="cb38b-132">Compiling the Code</span></span>  
 <span data-ttu-id="cb38b-133">Service.cs のコンパイル時には、System.ServiceModel.dll と System.ServiceModel.Web.dll を参照します。</span><span class="sxs-lookup"><span data-stu-id="cb38b-133">When compiling Service.cs, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb38b-134">参照</span><span class="sxs-lookup"><span data-stu-id="cb38b-134">See Also</span></span>  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Web.WebServiceHost>  
 <xref:System.ServiceModel.ChannelFactory>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [<span data-ttu-id="cb38b-135">WCF Web HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="cb38b-135">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)

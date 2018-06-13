---
title: '方法 : 基本的な RSS フィードを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 431879b8-a5f8-4947-ad1e-4768c726aca8
ms.openlocfilehash: d5b62d968c38401a19fc9009954450bef210e5a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493283"
---
# <a name="how-to-create-a-basic-rss-feed"></a><span data-ttu-id="74786-102">方法 : 基本的な RSS フィードを作成する</span><span class="sxs-lookup"><span data-stu-id="74786-102">How to: Create a Basic RSS Feed</span></span>
<span data-ttu-id="74786-103">Windows Communication Foundation (WCF) では、配信フィードを公開するサービスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="74786-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="74786-104">ここでは、RSS 配信フィードを公開する配信サービスを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="74786-104">This topic discusses how to create a syndication service that exposes an RSS syndication feed.</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="74786-105">基本的な配信サービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="74786-105">To create a basic syndication service</span></span>  
  
1.  <span data-ttu-id="74786-106"><xref:System.ServiceModel.Web.WebGetAttribute> 属性でマークされたインターフェイスを使用して、サービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="74786-106">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="74786-107">配信フィードとして公開される各操作は、<xref:System.ServiceModel.Syndication.Rss20FeedFormatter> オブジェクトを返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="74786-107">Each operation that is exposed as a syndication feed should return a <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> object.</span></span>  
  
     [!code-csharp[htRssBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#0)]
     [!code-vb[htRssBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="74786-108"><xref:System.ServiceModel.Web.WebGetAttribute> 属性を適用するすべてのサービス操作は、HTTP GET 要求にマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="74786-108">All service operations that apply the <xref:System.ServiceModel.Web.WebGetAttribute> attribute are mapped to HTTP GET requests.</span></span> <span data-ttu-id="74786-109">他の HTTP メソッドに操作をマッピングするには、代わりに <xref:System.ServiceModel.Web.WebInvokeAttribute> を使用します。</span><span class="sxs-lookup"><span data-stu-id="74786-109">To map your operation to a different HTTP method, use the <xref:System.ServiceModel.Web.WebInvokeAttribute> instead.</span></span> <span data-ttu-id="74786-110">詳細については、次を参照してください。[する方法: 基本的な WCF Web HTTP サービスを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)です。</span><span class="sxs-lookup"><span data-stu-id="74786-110">For more information, see [How to: Create a Basic WCF Web HTTP Service](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).</span></span>  
  
2.  <span data-ttu-id="74786-111">サービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="74786-111">Implement the service contract.</span></span>  
  
     [!code-csharp[htRssBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#1)]
     [!code-vb[htRssBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#1)]  
  
3.  <span data-ttu-id="74786-112"><xref:System.ServiceModel.Syndication.SyndicationFeed> オブジェクトを作成し、作成者、カテゴリ、および説明を追加します。</span><span class="sxs-lookup"><span data-stu-id="74786-112">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htRssBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#2)]
     [!code-vb[htRssBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#2)]  
  
4.  <span data-ttu-id="74786-113">複数の <xref:System.ServiceModel.Syndication.SyndicationItem> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="74786-113">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htRssBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#3)]
     [!code-vb[htRssBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#3)]  
  
5.  <span data-ttu-id="74786-114"><xref:System.ServiceModel.Syndication.SyndicationItem> をフィードに追加します。</span><span class="sxs-lookup"><span data-stu-id="74786-114">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> to the feed.</span></span>  
  
     [!code-csharp[htRssBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#4)]
     [!code-vb[htRssBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#4)]  
  
6.  <span data-ttu-id="74786-115">フィードを返します。</span><span class="sxs-lookup"><span data-stu-id="74786-115">Return the feed.</span></span>  
  
     [!code-csharp[htRssBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#5)]
     [!code-vb[htRssBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#5)]  
  
### <a name="to-host-a-service"></a><span data-ttu-id="74786-116">サービスをホストするには</span><span class="sxs-lookup"><span data-stu-id="74786-116">To host a service</span></span>  
  
1.  <span data-ttu-id="74786-117"><xref:System.ServiceModel.Web.WebServiceHost> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="74786-117">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>  
  
     [!code-csharp[htRssBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#6)]
     [!code-vb[htRssBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#6)]  
  
2.  <span data-ttu-id="74786-118">サービス ホストを開き、ユーザーが Enter キーを押すのを待ちます。</span><span class="sxs-lookup"><span data-stu-id="74786-118">Open the service host and wait until the user presses ENTER.</span></span>  
  
     [!code-csharp[htRssBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#8)]
     [!code-vb[htRssBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="74786-119">HTTP GET で GetBlog() を呼び出すには</span><span class="sxs-lookup"><span data-stu-id="74786-119">To call GetBlog() with an HTTP GET</span></span>  
  
1.  <span data-ttu-id="74786-120">Internet Explorer を開き、次の URL を入力して ENTER キーを押します。http://localhost:8000/BlogService/GetBlogです。</span><span class="sxs-lookup"><span data-stu-id="74786-120">Open Internet Explorer, type the following URL, and press ENTER: http://localhost:8000/BlogService/GetBlog.</span></span> <span data-ttu-id="74786-121">URL には、サービスのベース アドレスが含まれています (http://localhost:8000/BlogService)エンドポイント、およびを呼び出すサービス操作の相対アドレス。</span><span class="sxs-lookup"><span data-stu-id="74786-121">The URL contains the base address of the service (http://localhost:8000/BlogService), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="74786-122">コードから GetBlog() を呼び出すには</span><span class="sxs-lookup"><span data-stu-id="74786-122">To call GetBlog() from code</span></span>  
  
1.  <span data-ttu-id="74786-123">ベース アドレスと呼び出すメソッドを使用して <xref:System.Xml.XmlReader> を作成します。</span><span class="sxs-lookup"><span data-stu-id="74786-123">Create an <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htRssBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#9)]
     [!code-vb[htRssBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#9)]  
  
2.  <span data-ttu-id="74786-124">静的な <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> メソッドを呼び出し、作成した <xref:System.Xml.XmlReader> を渡します。</span><span class="sxs-lookup"><span data-stu-id="74786-124">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htRssBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#10)]
     [!code-vb[htRssBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#10)]  
  
     <span data-ttu-id="74786-125">これにより、サービス操作が呼び出され、サービス操作から返されたフォーマッタが新しい <xref:System.ServiceModel.Syndication.SyndicationFeed> に設定されます。</span><span class="sxs-lookup"><span data-stu-id="74786-125">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3.  <span data-ttu-id="74786-126">フィード オブジェクトにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="74786-126">Access the feed object.</span></span>  
  
     [!code-csharp[htRssBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#11)]
     [!code-vb[htRssBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="74786-127">例</span><span class="sxs-lookup"><span data-stu-id="74786-127">Example</span></span>  
 <span data-ttu-id="74786-128">この例の完全なコードの一覧を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="74786-128">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htRssBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#12)]
 [!code-vb[htRssBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="74786-129">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="74786-129">Compiling the Code</span></span>  
 <span data-ttu-id="74786-130">上記のコードのコンパイル時には、System.ServiceModel.dll と System.ServiceModel.Web.dll が参照されます。</span><span class="sxs-lookup"><span data-stu-id="74786-130">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74786-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="74786-131">See Also</span></span>  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>

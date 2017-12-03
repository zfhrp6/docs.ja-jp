---
title: "方法 : カスタムの信頼できるセッションによる HTTPS を使用したバインディングを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 87a27bb3e33b0dd78fdb2dfa206bbde098c8b769
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a><span data-ttu-id="0eaab-102">方法 : カスタムの信頼できるセッションによる HTTPS を使用したバインディングを作成する</span><span class="sxs-lookup"><span data-stu-id="0eaab-102">How to: Create a Custom Reliable Session Binding with HTTPS</span></span>

<span data-ttu-id="0eaab-103">ここでは、信頼できるセッションを使用した SSL (Secure Sockets Layer) トランスポート セキュリティの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0eaab-103">This topic demonstrates the use of Secure Sockets Layer (SSL) transport security with reliable sessions.</span></span> <span data-ttu-id="0eaab-104">HTTPS 上で信頼できるセッションを使用するには、信頼できるセッションと HTTPS トランスポートを使用するカスタム バインドを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0eaab-104">To use a reliable session over HTTPS, you must create a custom binding that uses a reliable session and the HTTPS transport.</span></span> <span data-ttu-id="0eaab-105">信頼できるセッションを有効にする場合、コードを使用して強制的に行う、または構成ファイルで宣言します。</span><span class="sxs-lookup"><span data-stu-id="0eaab-105">You enable the reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="0eaab-106">この手順では、クライアントとサービスの構成ファイルを使用して、信頼できるセッションを有効にして、 [  **\<httpsTransport >** ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md)要素。</span><span class="sxs-lookup"><span data-stu-id="0eaab-106">This procedure uses the client and service configuration files to enable the reliable session and the [**\<httpsTransport>**](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) element.</span></span>

<span data-ttu-id="0eaab-107">この手順の重要な部分は、 **\<エンドポイント >**構成要素を含む、`bindingConfiguration`という名前のカスタム バインド構成を参照する属性を`reliableSessionOverHttps`です。</span><span class="sxs-lookup"><span data-stu-id="0eaab-107">The key part of this procedure is that the **\<endpoint>** configuration element contain a `bindingConfiguration` attribute that references a custom binding configuration named `reliableSessionOverHttps`.</span></span> <span data-ttu-id="0eaab-108">[ **\<バインディング >** ](../../../../docs/framework/misc/binding.md)構成要素を含めることによって、信頼できるセッションと HTTPS トランスポートを使用することを指定するには、この名前を参照して **\<reliableSession >**と **\<httpsTransport >**要素。</span><span class="sxs-lookup"><span data-stu-id="0eaab-108">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element references this name to specify that a reliable session and the HTTPS transport are used by including **\<reliableSession>** and **\<httpsTransport>** elements.</span></span>

<span data-ttu-id="0eaab-109">この例の元のコピーを次を参照してください。[カスタム バインド信頼できるセッションが HTTPS 経由で](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md)です。</span><span class="sxs-lookup"><span data-stu-id="0eaab-109">For the source copy of this example, see [Custom Binding Reliable Session over HTTPS](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).</span></span>

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="0eaab-110">HTTPS で信頼できるセッションを使用する CustomBinding でサービスを構成します。</span><span class="sxs-lookup"><span data-stu-id="0eaab-110">Configure the service with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="0eaab-111">サービスの種類にサービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="0eaab-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. <span data-ttu-id="0eaab-112">サービス クラスにサービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="0eaab-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="0eaab-113">サービスの実装の内部アドレスやバインディングの情報が指定されていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0eaab-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="0eaab-114">構成ファイルから、アドレス情報とバインディング情報を取得するコードを記述する必要はないです。</span><span class="sxs-lookup"><span data-stu-id="0eaab-114">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. <span data-ttu-id="0eaab-115">作成、 *Web.config*のエンドポイントを構成するファイル、`CalculatorService`という名前のカスタム バインディングで`reliableSessionOverHttps`信頼できるセッションと HTTPS トランスポートを使用します。</span><span class="sxs-lookup"><span data-stu-id="0eaab-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` with a custom binding named `reliableSessionOverHttps` that uses a reliable session and the HTTPS transport.</span></span>

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. <span data-ttu-id="0eaab-116">作成、 *Service.svc*行を含むファイル。</span><span class="sxs-lookup"><span data-stu-id="0eaab-116">Create a *Service.svc* file that contains the line:</span></span>

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. <span data-ttu-id="0eaab-117">場所、 *Service.svc*インターネット インフォメーション サービス (IIS) 仮想ディレクトリのファイルです。</span><span class="sxs-lookup"><span data-stu-id="0eaab-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="0eaab-118">HTTPS で信頼できるセッションを使用する CustomBinding でクライアントを構成します。</span><span class="sxs-lookup"><span data-stu-id="0eaab-118">Configure the client with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="0eaab-119">使用して、 [ServiceModel メタデータ ユーティリティ ツール (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)サービス メタデータからコードを生成するためのコマンドラインからです。</span><span class="sxs-lookup"><span data-stu-id="0eaab-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="0eaab-120">生成されたクライアントが含まれています、`ICalculator`クライアントの実装が満たす必要があるサービス コントラクトを定義するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="0eaab-120">The client that's generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. <span data-ttu-id="0eaab-121">生成されたクライアント アプリケーションは `ClientCalculator` も実装します。</span><span class="sxs-lookup"><span data-stu-id="0eaab-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="0eaab-122">サービスの実装内のアドレスとバインディング情報が指定されていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0eaab-122">Note that the address and binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="0eaab-123">構成ファイルからアドレスとバインディング情報を取得するコードを記述するために必要でないです。</span><span class="sxs-lookup"><span data-stu-id="0eaab-123">You aren't required to write code to retrieve the address and binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. <span data-ttu-id="0eaab-124">という名前のカスタム バインディングを構成する`reliableSessionOverHttps`HTTPS トランスポートと信頼できるセッションを使用します。</span><span class="sxs-lookup"><span data-stu-id="0eaab-124">Configure a custom binding named `reliableSessionOverHttps` to use the HTTPS transport and reliable sessions.</span></span>

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. <span data-ttu-id="0eaab-125">アプリケーションで `ClientCalculator` のインスタンスを作成し、サービス操作を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0eaab-125">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. <span data-ttu-id="0eaab-126">クライアントをコンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="0eaab-126">Compile and run the client.</span></span>  

## <a name="net-framework-security"></a><span data-ttu-id="0eaab-127">.NET Framework のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="0eaab-127">.NET Framework security</span></span>

<span data-ttu-id="0eaab-128">このサンプルで使用する証明書はテスト証明書で作成されたため*Makecert.exe*などの HTTPS アドレスにアクセスしようとするときに、セキュリティ警告が表示されます`https://localhost/servicemodelsamples/service.svc`、お使いのブラウザーからです。</span><span class="sxs-lookup"><span data-stu-id="0eaab-128">Because the certificate used in this sample is a test certificate created with *Makecert.exe*, a security alert appears when you try to access an HTTPS address, such as `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="0eaab-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="0eaab-129">See also</span></span>

[<span data-ttu-id="0eaab-130">信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="0eaab-130">Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)

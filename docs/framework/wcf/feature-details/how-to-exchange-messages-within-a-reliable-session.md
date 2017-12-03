---
title: "方法 : 信頼されたセッション内のメッセージを変換する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c0465f50de37d7276cad5920c4b9fb9e544caf57
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a><span data-ttu-id="142f1-102">方法 : 信頼されたセッション内のメッセージを変換する</span><span class="sxs-lookup"><span data-stu-id="142f1-102">How to: Exchange Messages Within a Reliable Session</span></span>

<span data-ttu-id="142f1-103">このトピックでは、信頼できるセッションを有効にするために必要な手順について説明します。ここでは、信頼できるセッションを (既定ではなく) オプションでサポートするシステム指定のバインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="142f1-103">This topic outlines the steps required to enable a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="142f1-104">強制的にコードを使用して、信頼できるセッションを有効にするか、構成ファイルで宣言します。</span><span class="sxs-lookup"><span data-stu-id="142f1-104">You enable a reliable session imperatively using code or declaratively in your configuration file.</span></span> <span data-ttu-id="142f1-105">この手順は、信頼できるセッションを有効にして、送信された順序と同じ順序でメッセージが到達するを規定するために、クライアントとサービス構成ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="142f1-105">This procedure uses the client and service configuration files to enable the reliable session and to stipulate that the messages arrive in the same order in which they were sent.</span></span>

<span data-ttu-id="142f1-106">この手順の重要な部分は、エンドポイント構成要素が含まれている、`bindingConfiguration`という名前のバインディング構成を参照する属性を`Binding1`です。</span><span class="sxs-lookup"><span data-stu-id="142f1-106">The key part of this procedure is that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="142f1-107">[ **\<バインディング >** ](../../../../docs/framework/misc/binding.md)構成要素を設定して、信頼できるセッションを有効にするには、この名前の参照、`enabled`の属性、 [ **\<reliableSession >** ](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)要素を`true`です。</span><span class="sxs-lookup"><span data-stu-id="142f1-107">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) element to `true`.</span></span> <span data-ttu-id="142f1-108">信頼できるセッションで順序付き配信の保証を指定するには、`ordered` 属性を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="142f1-108">You specify the ordered delivery assurances for the reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="142f1-109">この例の元のコピーを次を参照してください。 [WS 信頼できるセッション](../../../../docs/framework/wcf/samples/ws-reliable-session.md)です。</span><span class="sxs-lookup"><span data-stu-id="142f1-109">For the source copy of this example, see [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="142f1-110">信頼できるセッションを使用する WSHttpBinding でサービスを構成します。</span><span class="sxs-lookup"><span data-stu-id="142f1-110">Configure the service with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="142f1-111">サービスの種類にサービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="142f1-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. <span data-ttu-id="142f1-112">サービス クラスにサービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="142f1-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="142f1-113">サービスの実装の内部アドレスやバインディングの情報が指定されていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="142f1-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="142f1-114">構成ファイルからアドレスとバインディング情報を取得するコードを記述する必要はないです。</span><span class="sxs-lookup"><span data-stu-id="142f1-114">You aren't required to write code to retrieve the address or binding information information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. <span data-ttu-id="142f1-115">作成、 *Web.config*のエンドポイントを構成するファイル、`CalculatorService`を使用して、<xref:System.ServiceModel.WSHttpBinding>有効になっているし、順次配送のために必要なメッセージの信頼できるセッションでします。</span><span class="sxs-lookup"><span data-stu-id="142f1-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding> with reliable session enabled and ordered delivery of messages required.</span></span>

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. <span data-ttu-id="142f1-116">作成、 *Service.svc*行を含むファイル。</span><span class="sxs-lookup"><span data-stu-id="142f1-116">Create a *Service.svc* file that contains the line:</span></span>

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1.  <span data-ttu-id="142f1-117">場所、 *Service.svc*インターネット インフォメーション サービス (IIS) 仮想ディレクトリのファイルです。</span><span class="sxs-lookup"><span data-stu-id="142f1-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="142f1-118">信頼できるセッションを使用する WSHttpBinding でクライアントを構成します。</span><span class="sxs-lookup"><span data-stu-id="142f1-118">Configure the client with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="142f1-119">使用して、 [ServiceModel メタデータ ユーティリティ ツール (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)サービス メタデータからコードを生成するためのコマンドラインから。</span><span class="sxs-lookup"><span data-stu-id="142f1-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata:</span></span>

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="142f1-120">生成されたクライアントが含まれています、`ICalculator`クライアントの実装が満たす必要があるサービス コントラクトを定義するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="142f1-120">The generated client contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. <span data-ttu-id="142f1-121">生成されたクライアント アプリケーションは `ClientCalculator` も実装します。</span><span class="sxs-lookup"><span data-stu-id="142f1-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="142f1-122">アドレスとバインディング情報が、サービスの実装で任意の位置指定されていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="142f1-122">Note that the address and binding information isn't specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="142f1-123">構成ファイルからアドレスとバインディング情報を取得するコードを記述する必要はないです。</span><span class="sxs-lookup"><span data-stu-id="142f1-123">You aren't required to write code to retrieve the address or binding information information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. <span data-ttu-id="142f1-124">*Svcutil.exe*もを使用するクライアントの構成を生成、<xref:System.ServiceModel.WSHttpBinding>クラスです。</span><span class="sxs-lookup"><span data-stu-id="142f1-124">*Svcutil.exe* also generates the configuration for the client that uses the <xref:System.ServiceModel.WSHttpBinding> class.</span></span> <span data-ttu-id="142f1-125">構成ファイルの名前*App.config*を使用する場合[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="142f1-125">Name the configuration file *App.config* when using [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. <span data-ttu-id="142f1-126">インスタンスを作成、`ClientCalculator`アプリケーションでサービス操作を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="142f1-126">Create an instance of the `ClientCalculator` in an application and call the service operations.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. <span data-ttu-id="142f1-127">クライアントをコンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="142f1-127">Compile and run the client.</span></span>

## <a name="example"></a><span data-ttu-id="142f1-128">例</span><span class="sxs-lookup"><span data-stu-id="142f1-128">Example</span></span>

<span data-ttu-id="142f1-129">システム指定のバインディングの中には、信頼できるセッションを既定でサポートするものがあります。</span><span class="sxs-lookup"><span data-stu-id="142f1-129">Several of the system-provided bindings support reliable sessions by default.</span></span> <span data-ttu-id="142f1-130">以下に例を示します。</span><span class="sxs-lookup"><span data-stu-id="142f1-130">These include:</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

<span data-ttu-id="142f1-131">信頼できるセッションをサポートするカスタム バインディングを作成する方法の例は、次を参照してください。[する方法: HTTPS で、カスタムの信頼できるセッション バインドを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md)です。</span><span class="sxs-lookup"><span data-stu-id="142f1-131">For an example of how to create a custom binding that supports reliable sessions, see [How to: Create a Custom Reliable Session Binding with HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="142f1-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="142f1-132">See also</span></span>

[<span data-ttu-id="142f1-133">信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="142f1-133">Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)

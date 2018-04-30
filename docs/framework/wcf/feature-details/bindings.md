---
title: Windows Communication Foundation バインディング
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF [WCF], bindings
- Windows Communication Foundation [WCF], bindings
- bindings [WCF]
ms.assetid: 83639133-89f7-43f0-b4ef-8d9e57c08d25
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 926cdab8b835aa170fc0cdc0046c3fef579c3fec
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="windows-communcation-foundation-bindings"></a><span data-ttu-id="273b5-102">Windows Communication Foundation バインディング</span><span class="sxs-lookup"><span data-stu-id="273b5-102">Windows Communcation Foundation Bindings</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="273b5-103"> では、アプリケーション ソフトウェアを作成する方法と、アプリケーション ソフトウェアが他のソフトウェアと通信する方法は分離されています。</span><span class="sxs-lookup"><span data-stu-id="273b5-103"> separates how the software for an application is written from how it communicates with other software.</span></span> <span data-ttu-id="273b5-104">バインディングを使用して、クライアントとサービスが相互に通信するために必要なトランスポート、エンコーディング、およびプロトコルの詳細を指定します。</span><span class="sxs-lookup"><span data-stu-id="273b5-104">Bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="273b5-105"> は、バインディングを使用してエンドポイントの基になるネットワーク上の表現を生成します。このため、バインディングの詳細の大半について通信している双方が合意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="273b5-105"> uses bindings to generate the underlying wire representation of the endpoint, so most of the binding details must be agreed upon by the parties that are communicating.</span></span> <span data-ttu-id="273b5-106">これを実現する最も簡単な方法は、サービスのクライアントがサービスのエンドポイントと同じバインディングを使用することです。</span><span class="sxs-lookup"><span data-stu-id="273b5-106">The easiest way to achieve this is for clients of a service to use the same binding that the endpoint for the service uses.</span></span> <span data-ttu-id="273b5-107">これを行う方法の詳細については、次を参照してください。 [Windows Communication Foundation サービスを構成してクライアントを使用してバインド](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)です。</span><span class="sxs-lookup"><span data-stu-id="273b5-107">For more information about how to do this, see [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb).</span></span>  
  
 <span data-ttu-id="273b5-108">バインディングは、バインド要素のコレクションで構成されます。</span><span class="sxs-lookup"><span data-stu-id="273b5-108">A binding is made up of a collection of binding elements.</span></span> <span data-ttu-id="273b5-109">各要素は、エンドポイントがクライアントと通信する方法の一部分を記述します。</span><span class="sxs-lookup"><span data-stu-id="273b5-109">Each element describes some aspect of how the endpoint communicates with clients.</span></span> <span data-ttu-id="273b5-110">バインディングには、1 つ以上のトランスポート バインド要素、1 つ以上のメッセージ エンコーディング バインド要素 (既定では、トランスポート バインド要素によって提供されます)、および任意の数の他のプロトコル バインド要素が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="273b5-110">A binding must include at least one transport binding element, at least one message-encoding binding element (which the transport binding element can provide by default), and any number of other protocol binding elements.</span></span> <span data-ttu-id="273b5-111">このように、ランタイムをビルドするプロセスでは、各バインド要素からランタイムにコードを提供できます。</span><span class="sxs-lookup"><span data-stu-id="273b5-111">The process that builds a runtime out of this description allows each binding element to contribute code to that runtime.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="273b5-112"> には、一般的なバインド要素を含むさまざまなバインディングが用意されています。</span><span class="sxs-lookup"><span data-stu-id="273b5-112"> provides bindings that contain common selections of binding elements.</span></span> <span data-ttu-id="273b5-113">これらのバインディングは、既定の設定で使用することも、ユーザーの要件に応じて既定値を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="273b5-113">These can be used with their default settings or you can modify those default values according to user requirements.</span></span> <span data-ttu-id="273b5-114">これらのシステム指定のバインディングには、バインド要素およびその設定を直接制御できるプロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="273b5-114">These system-provided bindings have properties that allow direct control over the binding elements and their settings.</span></span> <span data-ttu-id="273b5-115">また、バインディングの各バージョンに独自の名前を付けることで、複数のバージョンを同時に使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="273b5-115">You can also easily work side-by-side with multiple versions of a binding by giving each version of the binding its own name.</span></span> <span data-ttu-id="273b5-116">詳細については、「 [Configuring System-Provided バインド](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)です。</span><span class="sxs-lookup"><span data-stu-id="273b5-116">For details, see [Configuring System-Provided Bindings](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md).</span></span>  
  
 <span data-ttu-id="273b5-117">システム指定のバインディングに用意されていないバインド要素のコレクションが必要になった場合には、その必要なバインド要素のコレクションで構成されるカスタム バインドを作成できます。</span><span class="sxs-lookup"><span data-stu-id="273b5-117">If you need a collection of binding elements not provided by one of these system-provided bindings, you can create a custom binding that consists of the collection of binding elements required.</span></span> <span data-ttu-id="273b5-118">このようなカスタム バインドは簡単に作成でき、新しいクラスも必要ありませんが、バインド要素およびその設定を制御するためのプロパティは提供されません。</span><span class="sxs-lookup"><span data-stu-id="273b5-118">These custom bindings are easy to create and do not require a new class, but they do not provide properties for controlling the binding elements or their settings.</span></span> <span data-ttu-id="273b5-119">バインド要素へのアクセスと設定の変更は、バインド要素を含むコレクションを通じて行います。</span><span class="sxs-lookup"><span data-stu-id="273b5-119">You can access the binding elements and modify their settings through the collection that contains them.</span></span> <span data-ttu-id="273b5-120">詳細については、「[カスタム バインディング](../../../../docs/framework/wcf/extending/custom-bindings.md)です。</span><span class="sxs-lookup"><span data-stu-id="273b5-120">For details, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="273b5-121">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="273b5-121">In This Section</span></span>  
 [<span data-ttu-id="273b5-122">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="273b5-122">Configuring System-Provided Bindings</span></span>](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 <span data-ttu-id="273b5-123">一般的なシナリオをサポートするために [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に用意されたバインディングを使用および変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="273b5-123">Describes how to use and modify the bindings that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides to support common scenarios.</span></span>  
  
 [<span data-ttu-id="273b5-124">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="273b5-124">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 <span data-ttu-id="273b5-125">サービスおよびクライアントで使用する [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] バインディングをコードで強制的に定義する方法と、構成を使用して宣言によって定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="273b5-125">Describes how to define [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bindings for services and clients imperatively in code and declaratively using configuration.</span></span>  
  
 [<span data-ttu-id="273b5-126">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="273b5-126">Custom Bindings</span></span>](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 <span data-ttu-id="273b5-127"><xref:System.ServiceModel.Channels.CustomBinding> の概要と使用する状況について説明します。</span><span class="sxs-lookup"><span data-stu-id="273b5-127">Describes what a <xref:System.ServiceModel.Channels.CustomBinding> is and when it is used.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="273b5-128">参照</span><span class="sxs-lookup"><span data-stu-id="273b5-128">Reference</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
  
 <xref:System.ServiceModel.Channels.BindingElement>  
  
 <xref:System.ServiceModel.Channels.CustomBinding>  
  
## <a name="related-sections"></a><span data-ttu-id="273b5-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="273b5-129">Related Sections</span></span>  
 [<span data-ttu-id="273b5-130">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="273b5-130">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)

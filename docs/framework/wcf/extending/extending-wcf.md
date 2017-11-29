---
title: "WCF の拡張"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3faa09a550bdc32437aeac864f09ec7711bdaf97
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="extending-wcf"></a><span data-ttu-id="add99-102">WCF の拡張</span><span class="sxs-lookup"><span data-stu-id="add99-102">Extending WCF</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="add99-103"> では、実行時コンポーネントを変更し、拡張することによって、サービス ベースのアプリケーションを正確に制御および拡張できます。</span><span class="sxs-lookup"><span data-stu-id="add99-103"> allows you to modify and extend run time components to precisely control and extend service-based applications.</span></span> <span data-ttu-id="add99-104">このセクションのトピックでは、その拡張アーキテクチャについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="add99-104">The topics in this section go in depth about the extensibility architecture.</span></span> <span data-ttu-id="add99-105">基本的なプログラミングの詳細については、次を参照してください。[基本的な WCF プログラミング](../../../../docs/framework/wcf/basic-wcf-programming.md)です。</span><span class="sxs-lookup"><span data-stu-id="add99-105">For more information about basic programming, see [Basic WCF Programming](../../../../docs/framework/wcf/basic-wcf-programming.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="add99-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="add99-106">In This Section</span></span>  
 [<span data-ttu-id="add99-107">拡張 ServiceHost とサービス モデル レイヤー</span><span class="sxs-lookup"><span data-stu-id="add99-107">Extending ServiceHost and the Service Model Layer</span></span>](../../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md)  
 <span data-ttu-id="add99-108">サービス モデル レイヤーには、基になるチャネルから受信メッセージを取得し、そのメッセージをアプリケーション コードでのメソッド呼び出しに変換し、結果を呼び出し元に送信するという役割があります。</span><span class="sxs-lookup"><span data-stu-id="add99-108">The service model layer is responsible for pulling incoming messages out of the underlying channels, translating them into method invocations in application code, and sending the results back to the caller.</span></span>  <span data-ttu-id="add99-109">サービス モデル拡張は、ディスパッチャーの機能、カスタム動作、メッセージとパラメーターの途中受信、およびその他の拡張機能に関連する実行や通信の動作と機能を変更または実装します。</span><span class="sxs-lookup"><span data-stu-id="add99-109">Service model extensions modify or implement execution or communication behavior and features involving dispatcher functionality, custom behaviors, message and parameter interception, and other extensibility functionality.</span></span>  
  
 [<span data-ttu-id="add99-110">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="add99-110">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)  
 <span data-ttu-id="add99-111">バインディングはエンドポイントに接続するために必要な通信の詳細設定を記述するオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="add99-111">Bindings are objects that describe the communication details required to connect to an endpoint.</span></span> <span data-ttu-id="add99-112">バインディングの拡張やカスタム バインディングは、アプリケーションの各種機能をサポートするために必要なカスタム通信機能を実装します。</span><span class="sxs-lookup"><span data-stu-id="add99-112">Binding extensions or custom bindings implement custom communication functionality required to support application features.</span></span>  
  
 [<span data-ttu-id="add99-113">チャネル レイヤーの拡張</span><span class="sxs-lookup"><span data-stu-id="add99-113">Extending the Channel Layer</span></span>](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)  
 <span data-ttu-id="add99-114">チャネル レイヤーは、サービス モデル レイヤーより下に位置し、クライアントとサービス間のメッセージの交換を担います。</span><span class="sxs-lookup"><span data-stu-id="add99-114">The channel layer sits beneath the service model layer and is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="add99-115">チャネル拡張は、セキュリティなどの新しいプロトコル機能を実装できます。</span><span class="sxs-lookup"><span data-stu-id="add99-115">Channel extensions can implement new protocol functionality, such as security.</span></span> <span data-ttu-id="add99-116">また、SOAP メッセージを伝達する新しいネットワーク トランスポートの実装など、トランスポート機能も実装できます。</span><span class="sxs-lookup"><span data-stu-id="add99-116">Channel extensions also transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
 [<span data-ttu-id="add99-117">セキュリティの拡張</span><span class="sxs-lookup"><span data-stu-id="add99-117">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
 <span data-ttu-id="add99-118">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のセキュリティは、転送セキュリティ (整合性、機密性、および認証)、アクセス制御 (承認)、および監査で構成されます。</span><span class="sxs-lookup"><span data-stu-id="add99-118">Security in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] consists of transfer security (integrity, confidentiality, and authentication), access control (authorization) and auditing.</span></span> <span data-ttu-id="add99-119">`IdentityModel` 名前空間にある各クラスは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でアクセス制御のために使用されます。</span><span class="sxs-lookup"><span data-stu-id="add99-119">The classes found in the `IdentityModel` namespace are used by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] for access control.</span></span> <span data-ttu-id="add99-120">セキュリティ アーキテクチャを理解することによって、カスタムのアクセス制御システムに対応したカスタムのクレーム タイプを作成できます。</span><span class="sxs-lookup"><span data-stu-id="add99-120">Understanding the security architecture allows you to create custom claim types to accommodate custom access control systems.</span></span>  
  
 [<span data-ttu-id="add99-121">メタデータ システムの拡張</span><span class="sxs-lookup"><span data-stu-id="add99-121">Extending the Metadata System</span></span>](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)  
 <span data-ttu-id="add99-122">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のメタデータ システムは複数のクラスのグループおよびインターフェイスで、サービス ベースのアプリケーションを実装するために必要なメタデータを表します。</span><span class="sxs-lookup"><span data-stu-id="add99-122">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="add99-123">クラスを変更または拡張するか、WSDL (Web サービス記述言語) の拡張子やカスタム WS-PolicyAttachments アサーションなどのカスタム メタデータをエクスポート/インポートするインターフェイスを実装して構成します。</span><span class="sxs-lookup"><span data-stu-id="add99-123">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
 [<span data-ttu-id="add99-124">拡張エンコーダーとシリアライザー</span><span class="sxs-lookup"><span data-stu-id="add99-124">Extending Encoders and Serializers</span></span>](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
 <span data-ttu-id="add99-125">エンコーダーとシリアライザーは、データをある形式から別の形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="add99-125">Encoders and serializers translate data from one form to another.</span></span> <span data-ttu-id="add99-126">このセクションのトピックでは、提供されたクラスを特別な要件に合わせて拡張する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="add99-126">The topics in this section discuss how to extend the supplied classes to meet special requirements.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="add99-127">参照</span><span class="sxs-lookup"><span data-stu-id="add99-127">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a><span data-ttu-id="add99-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="add99-128">Related Sections</span></span>  
 [<span data-ttu-id="add99-129">基本的な WCF プログラミング</span><span class="sxs-lookup"><span data-stu-id="add99-129">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [<span data-ttu-id="add99-130">WCF 機能の詳細</span><span class="sxs-lookup"><span data-stu-id="add99-130">WCF Feature Details</span></span>](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [<span data-ttu-id="add99-131">ガイドラインとベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="add99-131">Guidelines and Best Practices</span></span>](../../../../docs/framework/wcf/guidelines-and-best-practices.md)

---
title: "ServiceHost とサービス モデル レイヤーの拡張"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extending service models [WCF]
ms.assetid: 954c138a-1cd0-45a0-8abe-e4d2b8ff5400
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1a1a439735375d96bee2d09f13d50e43783df964
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="extending-servicehost-and-the-service-model-layer"></a><span data-ttu-id="c51dc-102">ServiceHost とサービス モデル レイヤーの拡張</span><span class="sxs-lookup"><span data-stu-id="c51dc-102">Extending ServiceHost and the Service Model Layer</span></span>
<span data-ttu-id="c51dc-103">サービス モデル レイヤーには、基になるチャネルから受信メッセージを取得し、そのメッセージをアプリケーション コードでのメソッド呼び出しに変換し、結果を呼び出し元に送信するという役割があります。</span><span class="sxs-lookup"><span data-stu-id="c51dc-103">The service model layer is responsible for pulling incoming messages out of the underlying channels, translating them into method invocations in application code, and sending the results back to the caller.</span></span> <span data-ttu-id="c51dc-104">サービス モデル拡張は、クライアントやディスパッチャーの機能、カスタム動作、メッセージとパラメーターの途中受信、およびその他の拡張機能に関連する実行や通信の動作と機能を変更または実装します。</span><span class="sxs-lookup"><span data-stu-id="c51dc-104">Service model extensions modify or implement execution or communication behavior and features involving client or dispatcher functionality, custom behaviors, message and parameter interception, and other extensibility functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c51dc-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c51dc-105">In This Section</span></span>  
 [<span data-ttu-id="c51dc-106">クライアントの拡張</span><span class="sxs-lookup"><span data-stu-id="c51dc-106">Extending Clients</span></span>](../../../../docs/framework/wcf/extending/extending-clients.md)  
 <span data-ttu-id="c51dc-107">クライアント ランタイムを途中受信して変更できるインターフェイス、およびクライアント アプリケーションのカスタム拡張を挿入できるクラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c51dc-107">Describes the interfaces that can intercept and modify the client runtime, as well as the classes into which you can insert your custom extensions in client applications.</span></span> <span data-ttu-id="c51dc-108">たとえば、カスタム クライアント メッセージ ログやカスタム メッセージ シリアル化などを実行できます。</span><span class="sxs-lookup"><span data-stu-id="c51dc-108">For example, you can perform custom client message logging, perform custom message serialization, and so on.</span></span>  
  
 [<span data-ttu-id="c51dc-109">ディスパッチャーの拡張</span><span class="sxs-lookup"><span data-stu-id="c51dc-109">Extending Dispatchers</span></span>](../../../../docs/framework/wcf/extending/extending-dispatchers.md)  
 <span data-ttu-id="c51dc-110">サービス ランタイムを途中受信して変更できるインターフェイス、およびサービス アプリケーションのカスタム拡張を挿入できるクラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c51dc-110">Describes the interfaces that can intercept and modify the service runtime, as well as the classes into which you can insert your custom extensions in service applications.</span></span> <span data-ttu-id="c51dc-111">たとえば、カスタム サービス ログ、サービス側でのメッセージ検証、カスタム ディスパッチなどを実行できます。</span><span class="sxs-lookup"><span data-stu-id="c51dc-111">For example, you can perform custom service logging, service-side message validation, custom dispatching, and so on.</span></span>  
  
 [<span data-ttu-id="c51dc-112">拡張可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="c51dc-112">Extensible Objects</span></span>](../../../../docs/framework/wcf/extending/extensible-objects.md)  
 <span data-ttu-id="c51dc-113">5 つの拡張可能オブジェクトと、<xref:System.ServiceModel.IExtensibleObject%601> パターンについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c51dc-113">Describes the five extensible objects and the <xref:System.ServiceModel.IExtensibleObject%601> pattern.</span></span> <span data-ttu-id="c51dc-114">拡張可能オブジェクト パターンは、既存のランタイム クラスに新しい機能を付加して拡張したり、オブジェクトに新しい状態を追加するために使用します。</span><span class="sxs-lookup"><span data-stu-id="c51dc-114">The extensible object pattern is used to either extend existing runtime classes with new functionality or to add new state to an object.</span></span> <span data-ttu-id="c51dc-115">このようなオブジェクトを実際に拡張することにより、処理の段階に応じて、共通の拡張可能オブジェクトに定義された共有の状態や機能にアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="c51dc-115">Extensions, attached to one of the extensible objects, enable behaviors at very different stages in processing to access shared state and functionality attached to a common extensible object that they can access.</span></span>  
  
 [<span data-ttu-id="c51dc-116">構成して、ランタイムのビヘイビアーの使用を拡張します。</span><span class="sxs-lookup"><span data-stu-id="c51dc-116">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)  
 <span data-ttu-id="c51dc-117">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ランタイムで設定を変更したり、拡張機能を挿入したりするには、動作を使用します。</span><span class="sxs-lookup"><span data-stu-id="c51dc-117">To change settings on or insert extensions in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime, you use Behaviors.</span></span> <span data-ttu-id="c51dc-118">WCF には、調整機能、インスタンス化、およびサービスと操作に関するその他のさまざまな側面を制御するための、システムに実装済みの動作が用意されています。</span><span class="sxs-lookup"><span data-stu-id="c51dc-118">WCF includes system-implemented behaviors for controlling throttling, instancing, and many other aspects of services and operations.</span></span> <span data-ttu-id="c51dc-119">ここでは、独自のカスタム動作を作成し、プログラムおよび構成ファイルにより、作成したカスタム動作を使用できるようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c51dc-119">This section describes how to create your own custom behaviors and how to make them available for use both programmatically and using configuration files.</span></span>  
  
 [<span data-ttu-id="c51dc-120">ServiceHostFactory を使用したホストの拡張</span><span class="sxs-lookup"><span data-stu-id="c51dc-120">Extending Hosting Using ServiceHostFactory</span></span>](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 <span data-ttu-id="c51dc-121"><xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> および <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> を拡張し、<xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> クラスを使用してホスト環境をカスタマイズする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c51dc-121">Describes how to extend <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>, and use the <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> classes to customize the host environment.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c51dc-122">参照</span><span class="sxs-lookup"><span data-stu-id="c51dc-122">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c51dc-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="c51dc-123">Related Sections</span></span>

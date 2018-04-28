---
title: 拡張機能の概要
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
- WCF [WCF], extensibility
- Windows Communication Foundation [WCF], extensibility
- extensibility [WCF]
ms.assetid: ef56c251-d63c-4b3f-944f-b0c67bfb0f68
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 331e71f26b1c703f7df27086d943e799b4eb13e2
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="introduction-to-extensibility"></a><span data-ttu-id="ef1da-102">拡張機能の概要</span><span class="sxs-lookup"><span data-stu-id="ef1da-102">Introduction to Extensibility</span></span>
<span data-ttu-id="ef1da-103">[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] のアプリケーション モデルは、分散アプリケーションの大部分の通信要件に対応するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="ef1da-103">The [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] application model is designed to solve the greater part of the communication requirements of any distributed application.</span></span> <span data-ttu-id="ef1da-104">ただし、既定のアプリケーション モデルとシステム提供の実装でサポートされないシナリオが必ず存在します。</span><span class="sxs-lookup"><span data-stu-id="ef1da-104">But there are always scenarios that the default application model and system-provided implementations do not support.</span></span> <span data-ttu-id="ef1da-105">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] の拡張モデルでは、アプリケーション モデル全体の置き換えに至るまでのすべてのレベルでシステム動作を変更できるようにすることによって、カスタム シナリオをサポートします。</span><span class="sxs-lookup"><span data-stu-id="ef1da-105">The [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] extensibility model is intended to support custom scenarios by enabling you to modify system behavior at every level, even to the point of replacing the entire application model.</span></span> <span data-ttu-id="ef1da-106">ここでは、拡張のさまざまな領域を提示し、各領域の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="ef1da-106">This topic outlines the various areas of extension and points to more information about each.</span></span>  
  
## <a name="areas-to-extend"></a><span data-ttu-id="ef1da-107">拡張する領域</span><span class="sxs-lookup"><span data-stu-id="ef1da-107">Areas to Extend</span></span>  
 <span data-ttu-id="ef1da-108">次の領域を拡張できます。</span><span class="sxs-lookup"><span data-stu-id="ef1da-108">You can extend:</span></span>  
  
-   <span data-ttu-id="ef1da-109">アプリケーション ランタイム。</span><span class="sxs-lookup"><span data-stu-id="ef1da-109">The application runtime.</span></span> <span data-ttu-id="ef1da-110">ここでは、アプリケーションについて、メッセージのディスパッチと処理を拡張します。</span><span class="sxs-lookup"><span data-stu-id="ef1da-110">This extends the dispatching and the processing of messages for the application.</span></span> <span data-ttu-id="ef1da-111">この領域には、セキュリティ システム、メタデータ システム、シリアル化システム、およびアプリケーションを基になるチャネル システムに接続するためのバインディングとバインド要素も含まれます。</span><span class="sxs-lookup"><span data-stu-id="ef1da-111">This area also includes extending the security system, the metadata system, the serialization system, and the bindings and binding elements that connect the application with the underlying channel system.</span></span>  
  
-   <span data-ttu-id="ef1da-112">チャネルとチャネル ランタイム。</span><span class="sxs-lookup"><span data-stu-id="ef1da-112">The channel and channel runtime.</span></span> <span data-ttu-id="ef1da-113">ここでは、メッセージ レベルで機能するシステムを拡張し、プロトコル、トランスポート、およびエンコーディングのサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="ef1da-113">This extends the system that functions at the message level, providing protocol, transport, and encoding support.</span></span>  
  
-   <span data-ttu-id="ef1da-114">ホスト ランタイム。</span><span class="sxs-lookup"><span data-stu-id="ef1da-114">The host runtime.</span></span> <span data-ttu-id="ef1da-115">ここでは、チャネルおよびアプリケーション ランタイムとのホスト アプリケーション ドメインの関係を拡張します。</span><span class="sxs-lookup"><span data-stu-id="ef1da-115">This extends the relationship of the hosting application domain to the channel and application runtime.</span></span>  
  
### <a name="extending-the-application-runtime"></a><span data-ttu-id="ef1da-116">アプリケーション ランタイムの拡張</span><span class="sxs-lookup"><span data-stu-id="ef1da-116">Extending the Application Runtime</span></span>  
 <span data-ttu-id="ef1da-117">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーションでは、対応するチャネル宛てのメッセージとアプリケーション宛てのメッセージを区別します。</span><span class="sxs-lookup"><span data-stu-id="ef1da-117">In [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] applications, there is a distinction between messages that are destined for a corresponding channel and messages that are destined for the application itself.</span></span> <span data-ttu-id="ef1da-118">チャネル メッセージは、セキュリティで保護されたメッセージ交換の確立や、信頼できるセッションの確立など、特定のチャネル関連の機能をサポートします。</span><span class="sxs-lookup"><span data-stu-id="ef1da-118">Channel messages support some channel-related functionality, such as establishing a secure conversation or establishing a reliable session.</span></span> <span data-ttu-id="ef1da-119">このメッセージは、アプリケーション ランタイムでは使用できません。このメッセージは、アプリケーション層が関係する前に処理されます。</span><span class="sxs-lookup"><span data-stu-id="ef1da-119">These messages are not available to the application runtime; they are processed before the application layer is involved.</span></span>  
  
 <span data-ttu-id="ef1da-120">アプリケーション メッセージは、ユーザーまたはユーザーの顧客が作成したクライアントまたはサービスの操作向けのデータを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="ef1da-120">Application messages contain data that is destined for a client or service operation that you or your customer has created.</span></span> <span data-ttu-id="ef1da-121">このメッセージは、必要に応じて、メッセージまたはオブジェクトの形でアプリケーション レベルの拡張システムで使用できます。</span><span class="sxs-lookup"><span data-stu-id="ef1da-121">These messages are available to the application-level extension system in message or object form, depending upon your needs.</span></span>  
  
 <span data-ttu-id="ef1da-122">すべてのメッセージはチャネル システムを通過しますが、アプリケーション メッセージだけがチャネル システムからアプリケーションに渡されます。</span><span class="sxs-lookup"><span data-stu-id="ef1da-122">All messages pass through the channel system; only application messages are passed from the channel system into the application.</span></span> <span data-ttu-id="ef1da-123">新しいチャネル レベルの機能を作成するには、チャネル システムを拡張する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef1da-123">To create new channel-level functionality, you must extend the channel system.</span></span> <span data-ttu-id="ef1da-124">新しいアプリケーション レベルの機能を作成するには、サービスまたはクライアントのランタイム (それぞれディスパッチャーとチャネル ファクトリ) を拡張する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef1da-124">To create new application-level functionality, you must extend the service or client runtime (dispatchers and channel factories, respectively).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="ef1da-125"> アプリケーション ランタイムを拡張するを参照してください[ServiceHost を拡張して、サービス モデル レイヤー](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md)です。</span><span class="sxs-lookup"><span data-stu-id="ef1da-125"> extending the application runtime, see [Extending ServiceHost and the Service Model Layer](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).</span></span>  
  
#### <a name="extending-security"></a><span data-ttu-id="ef1da-126">セキュリティの拡張</span><span class="sxs-lookup"><span data-stu-id="ef1da-126">Extending Security</span></span>  
 <span data-ttu-id="ef1da-127">トークンや資格情報などのカスタム セキュリティ機構を作成するには、セキュリティ システムを拡張する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef1da-127">To build custom security mechanisms such as tokens and credentials, you must extend the security system.</span></span> <span data-ttu-id="ef1da-128">詳細については、次を参照してください。[拡張セキュリティ](../../../docs/framework/wcf/extending/extending-security.md)です。</span><span class="sxs-lookup"><span data-stu-id="ef1da-128">For more information, see [Extending Security](../../../docs/framework/wcf/extending/extending-security.md).</span></span>  
  
#### <a name="extending-metadata"></a><span data-ttu-id="ef1da-129">メタデータの拡張</span><span class="sxs-lookup"><span data-stu-id="ef1da-129">Extending Metadata</span></span>  
 <span data-ttu-id="ef1da-130">メタデータを既定以外の方法で公開するには、メタデータ システムを拡張する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef1da-130">To expose your metadata in differently than the default, you must extend the metadata system.</span></span> <span data-ttu-id="ef1da-131">詳細については、次を参照してください。[メタデータ システムの拡張](../../../docs/framework/wcf/extending/extending-the-metadata-system.md)です。</span><span class="sxs-lookup"><span data-stu-id="ef1da-131">For more information, see [Extending the Metadata System](../../../docs/framework/wcf/extending/extending-the-metadata-system.md).</span></span>  
  
#### <a name="extending-serialization"></a><span data-ttu-id="ef1da-132">シリアル化の拡張</span><span class="sxs-lookup"><span data-stu-id="ef1da-132">Extending Serialization</span></span>  
 <span data-ttu-id="ef1da-133">カスタム エンコーダーの作成、データ サロゲートの提供、または転送されるデータのカスタマイズに関するその他の作業を行うには、シリアル化システムを拡張する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef1da-133">To build custom encoders, provide data surrogates, or other work involving the customization of transferred data, you must extend the serialization system.</span></span> <span data-ttu-id="ef1da-134">詳細については、次を参照してください。[を拡張するエンコーダーとシリアライザー](../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)です。</span><span class="sxs-lookup"><span data-stu-id="ef1da-134">For more information, see [Extending Encoders and Serializers](../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md).</span></span>  
  
#### <a name="extending-bindings"></a><span data-ttu-id="ef1da-135">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="ef1da-135">Extending Bindings</span></span>  
 <span data-ttu-id="ef1da-136">トランスポート チャネルまたはプロトコル チャネルをアプリケーション層に関連付けるには、バインディング システムを拡張する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef1da-136">To associate transport or protocol channels with the application layer, you must extend the binding system.</span></span> <span data-ttu-id="ef1da-137">詳細については、次を参照してください。[バインディングの拡張](../../../docs/framework/wcf/extending/extending-bindings.md)です。</span><span class="sxs-lookup"><span data-stu-id="ef1da-137">For more information, see [Extending Bindings](../../../docs/framework/wcf/extending/extending-bindings.md).</span></span>  
  
### <a name="extending-the-channel-system"></a><span data-ttu-id="ef1da-138">チャネル システムの拡張</span><span class="sxs-lookup"><span data-stu-id="ef1da-138">Extending the Channel System</span></span>  
 <span data-ttu-id="ef1da-139">プロトコルの機能またはカスタム トランスポートをサポートするチャネルを作成するを参照してください。 [、チャネル レイヤの拡張](../../../docs/framework/wcf/extending/extending-the-channel-layer.md)です。</span><span class="sxs-lookup"><span data-stu-id="ef1da-139">To create channels that support custom transports or protocol functionality, see [Extending the Channel Layer](../../../docs/framework/wcf/extending/extending-the-channel-layer.md).</span></span>  
  
### <a name="extending-the-service-hosting-system"></a><span data-ttu-id="ef1da-140">サービス ホスト システムの拡張</span><span class="sxs-lookup"><span data-stu-id="ef1da-140">Extending the Service Hosting System</span></span>  
 <span data-ttu-id="ef1da-141">サービス全体のアプリケーション モデルを変更するには、<xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> クラスを拡張する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef1da-141">To modify the service-wide application model, you must extend <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="ef1da-142">詳細については、次を参照してください。 [ServiceHost を拡張すると、サービス モデル レイヤー](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md)です。</span><span class="sxs-lookup"><span data-stu-id="ef1da-142">For more information, see [Extending ServiceHost and the Service Model Layer](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).</span></span>  
  
 <span data-ttu-id="ef1da-143">ホスト アプリケーション ドメインとサービス ホストとの関係を変更するには、<xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> クラスを拡張する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef1da-143">To modify the relationship between the hosting application domain and the service host, you must extend the <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="ef1da-144">詳細については、次を参照してください。[ホストを使用して ServiceHostFactory の拡張](../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)です。</span><span class="sxs-lookup"><span data-stu-id="ef1da-144">For more information, see [Extending Hosting Using ServiceHostFactory](../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef1da-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="ef1da-145">See Also</span></span>  
 [<span data-ttu-id="ef1da-146">WCF の拡張</span><span class="sxs-lookup"><span data-stu-id="ef1da-146">Extending WCF</span></span>](../../../docs/framework/wcf/extending/index.md)

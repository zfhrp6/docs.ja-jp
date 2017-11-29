---
title: "サービスおよびクライアントのセキュリティ保護"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: ed37992b5488d33b9292bdd54eef47f9eb12f225
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="securing-services-and-clients"></a><span data-ttu-id="0e98d-102">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="0e98d-102">Securing Services and Clients</span></span>
<span data-ttu-id="0e98d-103">ここでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] でのセキュリティのプログラミングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="0e98d-103">The information in this section focuses on programming security in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="0e98d-104">一般に、これには、システムが提供する適切なバインディングを選択すること、セキュリティ要素のプロパティを適切に設定すること、サービス側/クライアント側で使う資格情報の検索方法にまつわる、サービスの動作に関するプロパティを適切に設定することなどが含まれます。</span><span class="sxs-lookup"><span data-stu-id="0e98d-104">Generally, this includes selecting an appropriate system-provided binding, setting the properties of the security element, and then setting properties of the service behaviors that govern how credentials are retrieved for use by either the service or the client.</span></span> <span data-ttu-id="0e98d-105">ように、これらの手法はほとんどのシナリオでは、ほとんどのユーザーのセキュリティ要件をカバー[一般的なセキュリティ シナリオ](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)です。</span><span class="sxs-lookup"><span data-stu-id="0e98d-105">These techniques cover the security requirements of most users for most scenarios, as shown in [Common Security Scenarios](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span></span> <span data-ttu-id="0e98d-106">シナリオには、多くの機能が必要とする場合が初めて表示[のカスタム バインディングのセキュリティ機能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); ソリューションが明らかなかどうかは、次を参照してください。[拡張セキュリティ](../../../../docs/framework/wcf/extending/extending-security.md)です。</span><span class="sxs-lookup"><span data-stu-id="0e98d-106">If your scenario requires more capabilities, first see [Security Capabilities with Custom Bindings](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); if a solution is not apparent, see [Extending Security](../../../../docs/framework/wcf/extending/extending-security.md).</span></span> <span data-ttu-id="0e98d-107">作成する (またはとの相互運用) は豊富な要求を使用するシステムでは、トピックを参照してください。[承認](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)です。</span><span class="sxs-lookup"><span data-stu-id="0e98d-107">If you are creating (or interoperating with) a system that uses rich claims, see the topics in [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0e98d-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="0e98d-108">In This Section</span></span>  
 [<span data-ttu-id="0e98d-109">WCF セキュリティのプログラミング</span><span class="sxs-lookup"><span data-stu-id="0e98d-109">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 <span data-ttu-id="0e98d-110">メッセージを保護するために使うプログラミング モデルの概要</span><span class="sxs-lookup"><span data-stu-id="0e98d-110">An overview of the programming model used to secure messages.</span></span>  
  
 [<span data-ttu-id="0e98d-111">トランスポート セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="0e98d-111">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 <span data-ttu-id="0e98d-112">トランスポート層を介してやり取りするメッセージを保護する方法の概要</span><span class="sxs-lookup"><span data-stu-id="0e98d-112">An overview of how to secure messages through the transport layer.</span></span>  
  
 [<span data-ttu-id="0e98d-113">メッセージ セキュリティ</span><span class="sxs-lookup"><span data-stu-id="0e98d-113">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 <span data-ttu-id="0e98d-114">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のメッセージ レベル セキュリティを使用する理由の要約</span><span class="sxs-lookup"><span data-stu-id="0e98d-114">Summarizes reasons for using message-level security in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
 [<span data-ttu-id="0e98d-115">セキュリティで保護されたセッション</span><span class="sxs-lookup"><span data-stu-id="0e98d-115">Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 <span data-ttu-id="0e98d-116">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] セッションのセキュリティを保護する際の考慮事項</span><span class="sxs-lookup"><span data-stu-id="0e98d-116">A discussion of the considerations required when securing a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] session.</span></span>  
  
 [<span data-ttu-id="0e98d-117">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="0e98d-117">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 <span data-ttu-id="0e98d-118">X.509 証明書を使用する際に必要となる主なタスクの解説</span><span class="sxs-lookup"><span data-stu-id="0e98d-118">An explanation of some of the common tasks required when using X.509 certificates.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0e98d-119">参照</span><span class="sxs-lookup"><span data-stu-id="0e98d-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="0e98d-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="0e98d-120">Related Sections</span></span>  
 [<span data-ttu-id="0e98d-121">セキュリティの基本概念</span><span class="sxs-lookup"><span data-stu-id="0e98d-121">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [<span data-ttu-id="0e98d-122">セキュリティの拡張</span><span class="sxs-lookup"><span data-stu-id="0e98d-122">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="0e98d-123">一般的なセキュリティ シナリオ</span><span class="sxs-lookup"><span data-stu-id="0e98d-123">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [<span data-ttu-id="0e98d-124">バインディングとセキュリティ</span><span class="sxs-lookup"><span data-stu-id="0e98d-124">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [<span data-ttu-id="0e98d-125">カスタム バインドのセキュリティ機能</span><span class="sxs-lookup"><span data-stu-id="0e98d-125">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [<span data-ttu-id="0e98d-126">セキュリティの拡張</span><span class="sxs-lookup"><span data-stu-id="0e98d-126">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="0e98d-127">承認</span><span class="sxs-lookup"><span data-stu-id="0e98d-127">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="0e98d-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="0e98d-128">See Also</span></span>  
 [<span data-ttu-id="0e98d-129">基本的な WCF プログラミング</span><span class="sxs-lookup"><span data-stu-id="0e98d-129">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="0e98d-130">Windows Server App Fabric のセキュリティ モデル</span><span class="sxs-lookup"><span data-stu-id="0e98d-130">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)

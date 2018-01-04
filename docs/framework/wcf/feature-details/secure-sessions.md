---
title: "セキュリティで保護されたセッション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 65a54c06efffb2e3167c77bd109a50a31b971add
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="secure-sessions"></a><span data-ttu-id="857ea-102">セキュリティで保護されたセッション</span><span class="sxs-lookup"><span data-stu-id="857ea-102">Secure Sessions</span></span>
<span data-ttu-id="857ea-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] の機能の 1 つに、送信された順序でメッセージが受信されることを保証する "信頼できるセッション" があります。</span><span class="sxs-lookup"><span data-stu-id="857ea-103">A feature of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is reliable sessions that guarantee messages are received in the order they were sent.</span></span> <span data-ttu-id="857ea-104">このセクションの各トピックでは、信頼できるセッションを作成する際に考慮する必要のあるセキュリティへの影響について説明します。</span><span class="sxs-lookup"><span data-stu-id="857ea-104">The topics in this section discuss the security implications to consider when creating a reliable session.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="857ea-105">信頼できるセッションを参照してください[セッションを使用した](../../../../docs/framework/wcf/using-sessions.md)です。</span><span class="sxs-lookup"><span data-stu-id="857ea-105"> reliable sessions, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="857ea-106">Windows XP で偽装が必要な場合は、ステートフルなセキュリティ コンテキスト トークン (SCT: Security Context Token) を使用しない、セキュリティで保護されたセッションを使用します。</span><span class="sxs-lookup"><span data-stu-id="857ea-106">When impersonation is required on Windows XP, use a secure session without a stateful security context token (SCT).</span></span> <span data-ttu-id="857ea-107">ステートフル SCT が偽装と共に使用されると、<xref:System.InvalidOperationException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="857ea-107">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="857ea-108">[サポートされていないシナリオ](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)です。</span><span class="sxs-lookup"><span data-stu-id="857ea-108"> [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="857ea-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="857ea-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="857ea-110">セキュリティ保護されたメッセージ交換とセッション</span><span class="sxs-lookup"><span data-stu-id="857ea-110">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|<span data-ttu-id="857ea-111">セキュリティで保護されたメッセージ交換とセキュリティで保護されたセッションは、同じ意味で使用されます。</span><span class="sxs-lookup"><span data-stu-id="857ea-111">Secure conversations and secure sessions are synonymous.</span></span> <span data-ttu-id="857ea-112">ここでは、セキュリティで保護されたメッセージ交換のしくみ、およびこのパターンを使用する状況と理由について説明します。</span><span class="sxs-lookup"><span data-stu-id="857ea-112">This topic explains the way a secure conversation works, and when and why to use the pattern.</span></span>|  
|[<span data-ttu-id="857ea-113">方法 : セキュリティで保護されたセッションを作成する</span><span class="sxs-lookup"><span data-stu-id="857ea-113">How to: Create a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|<span data-ttu-id="857ea-114">セキュリティで保護されたセッションの基本的な作成手順を説明するチュートリアルです。</span><span class="sxs-lookup"><span data-stu-id="857ea-114">Walks through of the basics of creating a secure session.</span></span>|  
|[<span data-ttu-id="857ea-115">方法 : セキュリティで保護されたセッションに対しセキュリティ コンテキスト トークンを作成する</span><span class="sxs-lookup"><span data-stu-id="857ea-115">How to: Create a Security Context Token for a Secure Session</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|<span data-ttu-id="857ea-116">クライアントの状態とセッションを保持する Web ファームを作成する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="857ea-116">Walks through the steps of creating a Web farm that will maintain state and sessions with clients.</span></span>|  
|[<span data-ttu-id="857ea-117">セキュリティで保護されたセッションに関するセキュリティの検討</span><span class="sxs-lookup"><span data-stu-id="857ea-117">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|<span data-ttu-id="857ea-118">セキュリティで保護されたセッションに関する特別な考慮事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="857ea-118">Describes special considerations for secure sessions.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="857ea-119">参照</span><span class="sxs-lookup"><span data-stu-id="857ea-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="857ea-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="857ea-120">Related Sections</span></span>  
 [<span data-ttu-id="857ea-121">セッション、インスタンス化、および同時実行</span><span class="sxs-lookup"><span data-stu-id="857ea-121">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [<span data-ttu-id="857ea-122">サービスの設計と実装</span><span class="sxs-lookup"><span data-stu-id="857ea-122">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="857ea-123">参照</span><span class="sxs-lookup"><span data-stu-id="857ea-123">See Also</span></span>  
 [<span data-ttu-id="857ea-124">方法 : メッセージ リプレイ検出を有効にする</span><span class="sxs-lookup"><span data-stu-id="857ea-124">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 [<span data-ttu-id="857ea-125">リプレイ攻撃</span><span class="sxs-lookup"><span data-stu-id="857ea-125">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [<span data-ttu-id="857ea-126">方法 : セッションを必要とするサービスを作成する</span><span class="sxs-lookup"><span data-stu-id="857ea-126">How to: Create a Service That Requires Sessions</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)

---
title: "WCF でのセキュリティの考慮事項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
caps.latest.revision: "49"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: c0af5a5d96f20b2ba5118909a3f0c5ba405bdb11
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="security-considerations-in-wcf"></a><span data-ttu-id="27ff3-102">WCF でのセキュリティの考慮事項</span><span class="sxs-lookup"><span data-stu-id="27ff3-102">Security Considerations in WCF</span></span>
<span data-ttu-id="27ff3-103">このセクションの各トピックでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] アプリケーションの設計時に考慮する必要のあるセキュリティ関連の各種項目を示します。</span><span class="sxs-lookup"><span data-stu-id="27ff3-103">The topics in this section list various security-related items to consider when designing a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27ff3-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="27ff3-104">In This Section</span></span>  
 [<span data-ttu-id="27ff3-105">情報漏えいが起こる</span><span class="sxs-lookup"><span data-stu-id="27ff3-105">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 <span data-ttu-id="27ff3-106">情報が開示または攻撃されるさまざまな方法、およびそれを軽減する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="27ff3-106">Discusses the various ways that information can be disclosed or attacked, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="27ff3-107">特権の昇格</span><span class="sxs-lookup"><span data-stu-id="27ff3-107">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 <span data-ttu-id="27ff3-108">最初に付与されたものよりも高い承認アクセス許可を攻撃者に与えることの影響、およびそれを軽減する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="27ff3-108">Discusses the effects of giving an attacker authorization permissions beyond those initially granted and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="27ff3-109">サービス拒否が起こる</span><span class="sxs-lookup"><span data-stu-id="27ff3-109">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 <span data-ttu-id="27ff3-110">システムがメッセージを適切に処理できない場合の影響、およびそれを軽減する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="27ff3-110">Discusses what happens when a system is unable to process messages appropriately and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="27ff3-111">改ざん</span><span class="sxs-lookup"><span data-stu-id="27ff3-111">Tampering</span></span>](../../../../docs/framework/wcf/feature-details/tampering.md)  
 <span data-ttu-id="27ff3-112">メッセージの改ざんやメッセージの配信先の変更、およびそれを軽減する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="27ff3-112">Discusses the altering of messages or the delivery of messages and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="27ff3-113">リプレイ攻撃</span><span class="sxs-lookup"><span data-stu-id="27ff3-113">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 <span data-ttu-id="27ff3-114">攻撃者がメッセージのストリームを送受信者間でコピーし、そのストリームを 1 つ以上の第三者に対してリプレイすることによる影響、およびそれを軽減する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="27ff3-114">Discusses what happens when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="27ff3-115">セキュリティで保護されたセッションに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="27ff3-115">Security Considerations for Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)  
 <span data-ttu-id="27ff3-116">セキュリティで保護されたセッションを実装する場合に、セキュリティに影響を及ぼす次の項目について説明します。</span><span class="sxs-lookup"><span data-stu-id="27ff3-116">Discusses the following items that affect security when implementing secure sessions.</span></span>  
  
 [<span data-ttu-id="27ff3-117">サポートされていないシナリオ</span><span class="sxs-lookup"><span data-stu-id="27ff3-117">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 <span data-ttu-id="27ff3-118">セキュリティの特定の側面がサポートされないため、避けたり配慮したりする必要のあるさまざまなシナリオを示します。</span><span class="sxs-lookup"><span data-stu-id="27ff3-118">Lists various scenarios that do not support a particular aspect of security and should be avoided or considered.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="27ff3-119">参照</span><span class="sxs-lookup"><span data-stu-id="27ff3-119">Reference</span></span>  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="27ff3-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="27ff3-120">Related Sections</span></span>  
 [<span data-ttu-id="27ff3-121">セキュリティ ガイダンスとベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="27ff3-121">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a><span data-ttu-id="27ff3-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="27ff3-122">See Also</span></span>  
 [<span data-ttu-id="27ff3-123">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="27ff3-123">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)

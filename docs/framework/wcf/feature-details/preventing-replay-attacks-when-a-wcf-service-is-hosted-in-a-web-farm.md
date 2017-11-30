---
title: "WCF サービスが Web ファームでホストされている場合のリプレイ攻撃の回避"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c2ed695-7a31-4257-92bd-9e9731b886a5
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4ecf37ffb87ddfdd483cebcac3f5892bab43dcd6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="preventing-replay-attacks-when-a-wcf-service-is-hosted-in-a-web-farm"></a><span data-ttu-id="4ca6c-102">WCF サービスが Web ファームでホストされている場合のリプレイ攻撃の回避</span><span class="sxs-lookup"><span data-stu-id="4ca6c-102">Preventing Replay Attacks When a WCF Service is Hosted in a Web Farm</span></span>
<span data-ttu-id="4ca6c-103">メッセージ セキュリティ WCF の使用により、受信メッセージから NONCE を作成し、生成された NONCE が内部 `InMemoryNonceCache` にあるかどうかを確認することで、リプレイ攻撃が防止される場合。</span><span class="sxs-lookup"><span data-stu-id="4ca6c-103">When using message security WCF prevents replay attacks by creating a NONCE out of the incoming message and checking the internal `InMemoryNonceCache` to see if the generated NONCE is present.</span></span> <span data-ttu-id="4ca6c-104">その場合、メッセージはリプレイとして破棄されます。</span><span class="sxs-lookup"><span data-stu-id="4ca6c-104">If it is, the message is discarded as a replay.</span></span> <span data-ttu-id="4ca6c-105">WCF サービスが Web ファームでホストされている場合、`InMemoryNonceCache` は Web ファームのノード間で共有されていないため、サービスはリプレイ攻撃に対して脆弱です。</span><span class="sxs-lookup"><span data-stu-id="4ca6c-105">When a WCF service is hosted in a web farm, since the `InMemoryNonceCache` is not shared across the nodes in the web farm, the service is vulnerable to replay attacks.</span></span>  <span data-ttu-id="4ca6c-106">このシナリオの危険性を軽減するために、WCF 4.5 では抽象クラス <xref:System.ServiceModel.Security.NonceCache> からクラスを派生させることによって独自の共有 NONCE キャッシュを実装する機能拡張ポイントを提供しています。</span><span class="sxs-lookup"><span data-stu-id="4ca6c-106">To mitigate this scenario WCF 4.5 provides an extensibility point that allows you to implement your own shared NONCE cache by deriving a class from the abstract class <xref:System.ServiceModel.Security.NonceCache>.</span></span>  
  
## <a name="noncecache-implementation"></a><span data-ttu-id="4ca6c-107">NonceCache 実装</span><span class="sxs-lookup"><span data-stu-id="4ca6c-107">NonceCache Implementation</span></span>  
 <span data-ttu-id="4ca6c-108">独自の共有 NONCE キャッシュを実装するには、<xref:System.ServiceModel.Security.NonceCache> からクラスを派生させ、<xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> メソッドと <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="4ca6c-108">To implement your own shared NONCE cache, derive a class from <xref:System.ServiceModel.Security.NonceCache> and override the <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> and <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> methods.</span></span> <span data-ttu-id="4ca6c-109"><xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> は、指定された NONCE がキャッシュに存在するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="4ca6c-109"><xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> will check to see if the specified NONCE exists in the cache.</span></span> <span data-ttu-id="4ca6c-110"><xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> は NONCE をキャッシュに追加しようとします。</span><span class="sxs-lookup"><span data-stu-id="4ca6c-110"><xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> will attempt to add a NONCE to the cache.</span></span> <span data-ttu-id="4ca6c-111">クラスを実装したら、インスタンスを作成して、そのインスタンスをクライアント側でのリプレイ検出用には <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.NonceCache%2A>、サーバー側でのリプレイ検出用には <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NonceCache%2A> に割り当てて準備します。</span><span class="sxs-lookup"><span data-stu-id="4ca6c-111">Once the class is implemented, you hook it up by instantiating an instance and assigning it to <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.NonceCache%2A> for client-side replay detection and <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NonceCache%2A> for server-side replay detection.</span></span> <span data-ttu-id="4ca6c-112">この機能のためにすぐに使用できる構成サポートはありません。</span><span class="sxs-lookup"><span data-stu-id="4ca6c-112">There is no out of the box configuration support for this feature.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ca6c-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ca6c-113">See Also</span></span>  
 [<span data-ttu-id="4ca6c-114">メッセージ セキュリティ</span><span class="sxs-lookup"><span data-stu-id="4ca6c-114">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [<span data-ttu-id="4ca6c-115">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="4ca6c-115">SymmetricSecurityBindingElement</span></span>](../../../../docs/framework/wcf/diagnostics/wmi/symmetricsecuritybindingelement.md)

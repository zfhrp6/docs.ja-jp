---
title: "フェデレーション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation [WCF]
ms.assetid: 2f1e646f-8361-48d4-9d5d-1b961f31ede4
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c9b707108d5849db57dcebfb4cb1f7b18378bff0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="federation"></a><span data-ttu-id="585b1-102">フェデレーション</span><span class="sxs-lookup"><span data-stu-id="585b1-102">Federation</span></span>
<span data-ttu-id="585b1-103">ここでは、フェデレーション セキュリティの概念について簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="585b1-103">This topic provides a brief overview of the concept of federated security.</span></span> <span data-ttu-id="585b1-104">また、フェデレーション セキュリティ アーキテクチャを展開する際の [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のサポートについても説明します。</span><span class="sxs-lookup"><span data-stu-id="585b1-104">It also describes [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] support for deploying federated security architectures.</span></span> <span data-ttu-id="585b1-105">フェデレーションを示すサンプル アプリケーションを参照してください。[フェデレーション サンプル](../../../../docs/framework/wcf/samples/federation-sample.md)です。</span><span class="sxs-lookup"><span data-stu-id="585b1-105">For a sample application that demonstrates federation, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="definition-of-federated-security"></a><span data-ttu-id="585b1-106">フェデレーション セキュリティの定義</span><span class="sxs-lookup"><span data-stu-id="585b1-106">Definition of Federated Security</span></span>  
 <span data-ttu-id="585b1-107">フェデレーション セキュリティにより、クライアントがアクセスするサービスと、関連する認証および承認の手順を明確に分離できます。</span><span class="sxs-lookup"><span data-stu-id="585b1-107">Federated security allows for clean separation between the service a client is accessing and the associated authentication and authorization procedures.</span></span> <span data-ttu-id="585b1-108">また、フェデレーション セキュリティを使用すると、異なる信頼レルムに属する複数のシステム、ネットワーク、および組織間のコラボレーションが可能になります。</span><span class="sxs-lookup"><span data-stu-id="585b1-108">Federated security also enables collaboration across multiple systems, networks, and organizations in different trust realms.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="585b1-109"> は、フェデレーション セキュリティを使用する分散システムの構築と展開をサポートします。</span><span class="sxs-lookup"><span data-stu-id="585b1-109"> provides support for building and deploying distributed systems that employ federated security.</span></span>  
  
### <a name="elements-of-a-federated-security-architecture"></a><span data-ttu-id="585b1-110">フェデレーション セキュリティ アーキテクチャの要素</span><span class="sxs-lookup"><span data-stu-id="585b1-110">Elements of a Federated Security Architecture</span></span>  
 <span data-ttu-id="585b1-111">次の表に示すように、フェデレーション セキュリティ アーキテクチャには 3 つの主要な要素があります。</span><span class="sxs-lookup"><span data-stu-id="585b1-111">The federated security architecture has three key elements, as described in the following table.</span></span>  
  
|<span data-ttu-id="585b1-112">要素</span><span class="sxs-lookup"><span data-stu-id="585b1-112">Element</span></span>|<span data-ttu-id="585b1-113">説明</span><span class="sxs-lookup"><span data-stu-id="585b1-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="585b1-114">ドメイン/レルム</span><span class="sxs-lookup"><span data-stu-id="585b1-114">Domain/realm</span></span>|<span data-ttu-id="585b1-115">セキュリティ管理または信頼の単位。</span><span class="sxs-lookup"><span data-stu-id="585b1-115">A single unit of security administration or trust.</span></span> <span data-ttu-id="585b1-116">ドメインには通常、1 つの組織が含まれます。</span><span class="sxs-lookup"><span data-stu-id="585b1-116">A typical domain might include a single organization.</span></span>|  
|<span data-ttu-id="585b1-117">フェデレーション</span><span class="sxs-lookup"><span data-stu-id="585b1-117">Federation</span></span>|<span data-ttu-id="585b1-118">信頼が確立されたドメインのコレクション。</span><span class="sxs-lookup"><span data-stu-id="585b1-118">A collection of domains that have established trust.</span></span> <span data-ttu-id="585b1-119">信頼のレベルはさまざまですが、通常は認証レベルが含まれ、ほとんどの場合に承認レベルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="585b1-119">The level of trust may vary, but typically includes authentication and almost always includes authorization.</span></span> <span data-ttu-id="585b1-120">典型的なフェデレーションには、一連のリソースへの共有アクセスを可能にする信頼を確立した多くの組織が含まれます。</span><span class="sxs-lookup"><span data-stu-id="585b1-120">A typical federation might include a number of organizations that have established trust for shared access to a set of resources.</span></span>|  
|<span data-ttu-id="585b1-121">STS (セキュリティ トークン サービス)</span><span class="sxs-lookup"><span data-stu-id="585b1-121">Security Token Service (STS)</span></span>|<span data-ttu-id="585b1-122">セキュリティ トークンを発行する Web サービス。つまり、信頼できる証拠に基づいて、サービスを信頼する任意の相手に対してアサーションを行います。</span><span class="sxs-lookup"><span data-stu-id="585b1-122">A Web service that issues security tokens; that is, it makes assertions based on evidence that it trusts, to whomever trusts it.</span></span> <span data-ttu-id="585b1-123">これによりドメイン間における信頼の橋渡しの基礎が形成されます。</span><span class="sxs-lookup"><span data-stu-id="585b1-123">This forms the basis of trust brokering between domains.</span></span>|  
  
### <a name="example-scenario"></a><span data-ttu-id="585b1-124">サンプル シナリオ</span><span class="sxs-lookup"><span data-stu-id="585b1-124">Example Scenario</span></span>  
 <span data-ttu-id="585b1-125">フェデレーション セキュリティの例を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="585b1-125">The following illustration shows an example of federated security.</span></span>  
  
 <span data-ttu-id="585b1-126">![フェデレーション](../../../../docs/framework/wcf/feature-details/media/typicalfederatedsecurityscenario.gif "TypicalFederatedSecurityScenario")</span><span class="sxs-lookup"><span data-stu-id="585b1-126">![Federation](../../../../docs/framework/wcf/feature-details/media/typicalfederatedsecurityscenario.gif "TypicalFederatedSecurityScenario")</span></span>  
  
 <span data-ttu-id="585b1-127">このシナリオでは、A と B の 2 つの組織があります。組織 B には、組織 A の一部のユーザーにとって有用な Web リソース (Web サービス) があります。</span><span class="sxs-lookup"><span data-stu-id="585b1-127">This scenario includes two organizations: A and B. Organization B has a Web resource (a Web service) that some users in organization A find valuable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="585b1-128">このセクションでは、用語を使用*リソース*、*サービス*、および*Web サービス*同義です。</span><span class="sxs-lookup"><span data-stu-id="585b1-128">This section uses the terms *resource*, *service*, and *Web service* interchangeably.</span></span>  
  
 <span data-ttu-id="585b1-129">通常、組織 B は、組織 A のユーザーに対して、サービスにアクセスする前になんらかの有効な形式の認証を行うことを要求します。</span><span class="sxs-lookup"><span data-stu-id="585b1-129">Typically, organization B requires that a user from organization A provide some valid form of authentication before accessing the service.</span></span> <span data-ttu-id="585b1-130">さらに、組織 B では、当該の特定リソースにアクセスするためにユーザーが承認されることを要求する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="585b1-130">In addition, the organization may also require that the user be authorized to access the specific resource in question.</span></span> <span data-ttu-id="585b1-131">この問題に対処し、組織 A のユーザーが組織 B のリソースにアクセスできるようにする 1 つの方法として、次のような方法があります。</span><span class="sxs-lookup"><span data-stu-id="585b1-131">One way to address this problem and enable users in organization A to access the resource in organization B is as follows:</span></span>  
  
-   <span data-ttu-id="585b1-132">組織 A のユーザーは、各自の資格情報 (ユーザー名とパスワード) を組織 B に登録します。</span><span class="sxs-lookup"><span data-stu-id="585b1-132">Users from organization A register their credentials (a user name and password) with organization B.</span></span>  
  
-   <span data-ttu-id="585b1-133">組織 A のユーザーがリソースにアクセスするには、リソースにアクセスする前に自分の資格情報を組織 B に提示して認証を受けます。</span><span class="sxs-lookup"><span data-stu-id="585b1-133">During the resource access, users from organization A present their credentials to organization B and are authenticated before accessing the resource.</span></span>  
  
 <span data-ttu-id="585b1-134">この方法には、次の 3 つの重大な欠点があります。</span><span class="sxs-lookup"><span data-stu-id="585b1-134">This approach has three significant drawbacks:</span></span>  
  
-   <span data-ttu-id="585b1-135">組織 B では、ローカル ユーザーの資格情報の管理に加えて、組織 A のユーザーの資格情報の管理も必要になります。</span><span class="sxs-lookup"><span data-stu-id="585b1-135">Organization B has to manage the credentials for users from organization A in addition to managing the credentials of its local users.</span></span>  
  
-   <span data-ttu-id="585b1-136">組織 A のユーザーは、組織 A 内のリソースにアクセスするために通常使用する資格情報以外に、別の資格情報セットを保持する (つまり、別のユーザー名とパスワードを覚えておく) 必要があります。通常、これは、複数のサービス サイトで同じユーザー名とパスワードが使用される可能性を高めるため、脆弱なセキュリティ対策と言えます。</span><span class="sxs-lookup"><span data-stu-id="585b1-136">Users in organization A need to maintain an additional set of credentials (that is, remember an additional user name and password) apart from the credentials they normally use to gain access to resources within organization A. This usually encourages the practice of using the same user name and password at multiple service sites, which is a weak security measure.</span></span>  
  
-   <span data-ttu-id="585b1-137">組織 B にあるリソースの価値を認識する組織の数が増えても、アーキテクチャを拡張できません。</span><span class="sxs-lookup"><span data-stu-id="585b1-137">The architecture does not scale as more organizations perceive the resource at organization B as being of some value.</span></span>  
  
 <span data-ttu-id="585b1-138">上記の欠点に対処する別の方法として、フェデレーション セキュリティの使用があります。</span><span class="sxs-lookup"><span data-stu-id="585b1-138">An alternative approach, which addresses the previously mentioned drawbacks, is to employ federated security.</span></span> <span data-ttu-id="585b1-139">この方法では、組織 A と組織 B が信頼関係を確立し、セキュリティ トークン サービス (STS: Security Token Service) を使用して、確立された信頼を仲介できるようにします。</span><span class="sxs-lookup"><span data-stu-id="585b1-139">In this approach, organizations A and B establish a trust relationship and employ Security Token Service (STS) to enable brokering of the established trust.</span></span>  
  
 <span data-ttu-id="585b1-140">フェデレーション セキュリティ アーキテクチャでは、組織 A のユーザーが、組織 B の Web サービスにアクセスする場合に、組織 B の STS から発行された有効なセキュリティ トークンを提示する必要があることを認識しています。この STS が、特定のサービスへのアクセスを認証および承認します。</span><span class="sxs-lookup"><span data-stu-id="585b1-140">In a federated security architecture, users from organization A know that if they want to access the Web service in organization B that they must present a valid security token from the STS at organization B, which authenticates and authorizes their access to the specific service.</span></span>  
  
 <span data-ttu-id="585b1-141">STS B に接続したユーザーは、STS に関連付けられたポリシーから別のレベルの間接指定を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="585b1-141">On contacting the STS B, the users receive another level of indirection from the policy associated with the STS.</span></span> <span data-ttu-id="585b1-142">このユーザーは、STS B がセキュリティ トークンを発行する前に、STS A (クライアントの信頼レルム) の有効なセキュリティ トークンを提示しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="585b1-142">They must present a valid security token from the STS A (that is, the client trust realm) before the STS B can issue them a security token.</span></span> <span data-ttu-id="585b1-143">これは、2 つの組織間で確立された信頼関係の推論であり、組織 A. からユーザーの id を管理する組織 B がないことを意味します。実際には、STS B 通常 null に`issuerAddress`と`issuerMetadataAddress`です。</span><span class="sxs-lookup"><span data-stu-id="585b1-143">This is a corollary of the trust relationship established between the two organizations and implies that organization B does not have to manage identities for users from organization A. In practice, STS B typically has a null `issuerAddress` and `issuerMetadataAddress`.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="585b1-144">[する方法: ローカル発行者を構成する](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)です。</span><span class="sxs-lookup"><span data-stu-id="585b1-144"> [How to: Configure a Local Issuer](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span> <span data-ttu-id="585b1-145">クライアントが STS A. を検索するローカル ポリシーを参照している場合は、この構成を呼び出す*ホーム レルム フェデレーション*STS B は STS A. に関する情報を保持する必要はありませんので、拡張性が、</span><span class="sxs-lookup"><span data-stu-id="585b1-145">In that case, the client consults a local policy to locate STS A. This configuration is called *home realm federation* and it scales better because STS B does not have to maintain information about STS A.</span></span>  
  
 <span data-ttu-id="585b1-146">ユーザーは、組織 A の STS に接続し、組織 A 内の他のリソースにアクセスする際に通常使用する認証資格情報を提示して、セキュリティ トークンを取得します。これにより、ユーザーが複数の資格情報セットを保持する必要があるという問題や、複数のサービス サイトで同じ資格情報セットを使用するという問題が、ある程度解決されます。</span><span class="sxs-lookup"><span data-stu-id="585b1-146">The users then contact the STS at organization A and obtain a security token by presenting authentication credentials that they normally use to gain access to any other resource within organization A. This also alleviates the problem of users having to maintain multiple sets of credentials or using the same set of credentials at multiple service sites.</span></span>  
  
 <span data-ttu-id="585b1-147">STS A からセキュリティ トークンを取得したユーザーは、このトークンを STS B に提示します。組織 B はユーザーの要求の承認手順を進め、独自のセキュリティ トークン セットからユーザーにセキュリティ トークンを発行します。</span><span class="sxs-lookup"><span data-stu-id="585b1-147">Once the users obtain a security token from the STS A, they present the token to the STS B. Organization B proceeds to perform authorization of the users' requests and issues a security token to the users from its own set of security tokens.</span></span> <span data-ttu-id="585b1-148">ユーザーは、このトークンを組織 B のリソースに提示し、サービスにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="585b1-148">The users can then present their token to the resource at organization B and access the service.</span></span>  
  
## <a name="support-for-federated-security-in-wcf"></a><span data-ttu-id="585b1-149">WCF におけるフェデレーション セキュリティのサポート</span><span class="sxs-lookup"><span data-stu-id="585b1-149">Support for Federated Security in WCF</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="585b1-150">では、ターンキーを通じてフェデレーション セキュリティ アーキテクチャを展開する、 [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="585b1-150"> provides turnkey support for deploying federated security architectures through the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="585b1-151">[ \<WsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)要素は、要求/応答通信のスタイル、基になるトランスポート機構として HTTP を使用する必要があります、信頼性が高く、相互運用可能なセキュリティで保護されたバインディングのエンコードするためのワイヤ形式として、テキスト、XML を採用することです。</span><span class="sxs-lookup"><span data-stu-id="585b1-151">The [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element provides for a secure, reliable, interoperable binding that entails the use of HTTP as the underlying transport mechanism for request-reply communication style, employing text and XML as the wire format for encoding.</span></span>  
  
 <span data-ttu-id="585b1-152">使用[ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)フェデレーション セキュリティ シナリオ切り離すことができますに 2 つの論理的に独立したフェーズでは、次のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="585b1-152">The use of [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) in a federated security scenario can be decoupled into two logically independent phases, as described in the following sections.</span></span>  
  
### <a name="phase-1-design-phase"></a><span data-ttu-id="585b1-153">第 1 フェーズ : 設計</span><span class="sxs-lookup"><span data-stu-id="585b1-153">Phase 1: Design Phase</span></span>  
 <span data-ttu-id="585b1-154">設計フェーズでは、クライアントを使用して、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)サービス エンドポイントを公開するポリシーを読み取ると、サービスの認証と承認の要件を収集します。</span><span class="sxs-lookup"><span data-stu-id="585b1-154">During the design phase, the client uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to read the policy the service endpoint exposes and to collect the service's authentication and authorization requirements.</span></span> <span data-ttu-id="585b1-155">次のフェデレーション セキュリティの通信パターンをクライアントで作成するために、適切なプロキシが構築されます。</span><span class="sxs-lookup"><span data-stu-id="585b1-155">The appropriate proxies are constructed to create the following federated security communication pattern at the client:</span></span>  
  
-   <span data-ttu-id="585b1-156">クライアント信頼レルムにある STS からセキュリティ トークンを取得する。</span><span class="sxs-lookup"><span data-stu-id="585b1-156">Obtain a security token from the STS in the client trust realm.</span></span>  
  
-   <span data-ttu-id="585b1-157">サービス信頼レルムにある STS にトークンを提示する。</span><span class="sxs-lookup"><span data-stu-id="585b1-157">Present the token to the STS in the service trust realm.</span></span>  
  
-   <span data-ttu-id="585b1-158">サービス信頼レルムにある STS からセキュリティ トークンを取得する。</span><span class="sxs-lookup"><span data-stu-id="585b1-158">Obtain a security token from the STS in the service trust realm.</span></span>  
  
-   <span data-ttu-id="585b1-159">サービスにトークンを提示してサービスにアクセスする。</span><span class="sxs-lookup"><span data-stu-id="585b1-159">Present the token to the service to access the service.</span></span>  
  
### <a name="phase-2-run-time-phase"></a><span data-ttu-id="585b1-160">第 2 フェーズ : 実行時</span><span class="sxs-lookup"><span data-stu-id="585b1-160">Phase 2: Run-Time Phase</span></span>  
 <span data-ttu-id="585b1-161">実行時フェーズでは、クライアントは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント クラスのオブジェクトをインスタンス化し、この [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントを使用して呼び出しを行います。</span><span class="sxs-lookup"><span data-stu-id="585b1-161">During the run-time phase, the client instantiates an object of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class and makes a call using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client.</span></span> <span data-ttu-id="585b1-162">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の基盤となるフレームワークにより、フェデレーション セキュリティの通信パターンにおける前述の手順が処理され、クライアントがシームレスにサービスを利用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="585b1-162">The underlying framework of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] handles the previously mentioned steps in the federated security communication pattern and enables the client to seamlessly consume the service.</span></span>  
  
## <a name="sample-implementation-using-wcf"></a><span data-ttu-id="585b1-163">WCF を使用した実装のサンプル</span><span class="sxs-lookup"><span data-stu-id="585b1-163">Sample Implementation Using WCF</span></span>  
 <span data-ttu-id="585b1-164">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のネイティブ サポートを使用したフェデレーション セキュリティ アーキテクチャの実装サンプルを次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="585b1-164">The following illustration shows a sample implementation for a federated security architecture using native support from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="585b1-165">![WCF のフェデレーション セキュリティ](../../../../docs/framework/wcf/feature-details/media/federatedsecurityinwcf.gif "FederatedSecurityInWCF")</span><span class="sxs-lookup"><span data-stu-id="585b1-165">![Federation security in WCF](../../../../docs/framework/wcf/feature-details/media/federatedsecurityinwcf.gif "FederatedSecurityInWCF")</span></span>  
  
### <a name="example-myservice"></a><span data-ttu-id="585b1-166">MyService の例</span><span class="sxs-lookup"><span data-stu-id="585b1-166">Example MyService</span></span>  
 <span data-ttu-id="585b1-167">`MyService` サービスは、`MyServiceEndpoint` を介して単一のエンドポイントを公開します。</span><span class="sxs-lookup"><span data-stu-id="585b1-167">The service `MyService` exposes a single endpoint through `MyServiceEndpoint`.</span></span> <span data-ttu-id="585b1-168">このエンドポイントに関連付けられたアドレス、バインディング、およびコントラクトを次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="585b1-168">The following illustration shows the address, binding, and contract associated with the endpoint.</span></span>  
  
 <span data-ttu-id="585b1-169">![フェデレーション](../../../../docs/framework/wcf/feature-details/media/myservice.gif "MyService")</span><span class="sxs-lookup"><span data-stu-id="585b1-169">![Federation](../../../../docs/framework/wcf/feature-details/media/myservice.gif "MyService")</span></span>  
  
 <span data-ttu-id="585b1-170">サービス エンドポイント`MyServiceEndpoint`を使用して、 [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)で有効なセキュリティ アサーション マークアップ言語 (SAML) トークンを必要とし、 `accessAuthorized` STS B. によって発行された要求これは、サービスの構成で宣言によって指定します。</span><span class="sxs-lookup"><span data-stu-id="585b1-170">The service endpoint `MyServiceEndpoint` uses the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and requires a valid Security Assertions Markup Language (SAML) token with an `accessAuthorized` claim issued by STS B. This is declaratively specified in the service configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.MyService"      
        behaviorConfiguration='MyServiceBehavior'>  
        <endpoint address=""  
            binding=" wsFederationHttpBinding"  
            bindingConfiguration='MyServiceBinding'  
            contract="Federation.IMyService" />  
   </service>  
  </services>  
  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by MyService. It redirects   
    clients to STS-B. -->  
      <binding name='MyServiceBinding'>  
        <security mode="Message">  
           <message issuedTokenType=  
"http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
           <issuer address="http://localhost/FederationSample/STS-B/STS.svc" />  
            <issuerMetadata   
           address=  
"http://localhost/FederationSample/STS-B/STS.svc/mex" />  
         <requiredClaimTypes>  
            <add claimType="http://tempuri.org:accessAuthorized" />  
         </requiredClaimTypes>  
        </message>  
      </security>  
      </binding>  
    </wsFederationHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <behavior name='MyServiceBehavior'>  
      <serviceAuthorization   
operationRequirementType="FederationSample.MyServiceOperationRequirement, MyService" />  
       <serviceCredentials>  
         <serviceCertificate findValue="CN=FederationSample.com"  
         x509FindType="FindBySubjectDistinguishedName"  
         storeLocation='LocalMachine'  
         storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
>  <span data-ttu-id="585b1-171">`MyService` が要求するクレームについては、細かい点に注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="585b1-171">A subtle point should be noted about the claims required by `MyService`.</span></span> <span data-ttu-id="585b1-172">2 番目の図は、`MyService` が `accessAuthorized` クレームを含む SAML トークンを要求していることを示しています。</span><span class="sxs-lookup"><span data-stu-id="585b1-172">The second figure indicates that `MyService` requires a SAML token with the `accessAuthorized` claim.</span></span> <span data-ttu-id="585b1-173">より正確には、これで、`MyService` が必要とするクレームの種類が指定されます。</span><span class="sxs-lookup"><span data-stu-id="585b1-173">To be more precise, this specifies the claim type that `MyService` requires.</span></span> <span data-ttu-id="585b1-174">このクレームの種類の完全修飾名は http://tempuri.org:accessAuthorized (関連する名前空間を含みます) で、この名前がサービス構成ファイルで使用されます。</span><span class="sxs-lookup"><span data-stu-id="585b1-174">The fully-qualified name of this claim type is http://tempuri.org:accessAuthorized (along with the associated namespace), which is used in the service configuration file.</span></span> <span data-ttu-id="585b1-175">このクレームの値は、このクレームが存在することが示しており、STS B によって `true` に設定されると想定されます。</span><span class="sxs-lookup"><span data-stu-id="585b1-175">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS B.</span></span>  
  
 <span data-ttu-id="585b1-176">このポリシーは、`MyServiceOperationRequirement` の一部として実装されている `MyService` クラスによって実行時に適用されます。</span><span class="sxs-lookup"><span data-stu-id="585b1-176">At runtime, this policy is enforced by the `MyServiceOperationRequirement` class that is implemented as part of the `MyService`.</span></span>  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a><span data-ttu-id="585b1-177">STS B</span><span class="sxs-lookup"><span data-stu-id="585b1-177">STS B</span></span>  
 <span data-ttu-id="585b1-178">STS B を次の図に示します。前述のように、セキュリティ トークン サービス (STS) も Web サービスであり、エンドポイントやポリシーなどを関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="585b1-178">The following illustration shows the STS B. As stated earlier, a security token service (STS) is also a Web service and can have its associated endpoints, policy, and so on.</span></span>  
  
 <span data-ttu-id="585b1-179">![フェデレーション](../../../../docs/framework/wcf/feature-details/media/msservicestsb.gif "MsServiceSTSB")</span><span class="sxs-lookup"><span data-stu-id="585b1-179">![Federation](../../../../docs/framework/wcf/feature-details/media/msservicestsb.gif "MsServiceSTSB")</span></span>  
  
 <span data-ttu-id="585b1-180">STS B は、セキュリティ トークンを要求する際に使用できる `STSEndpoint` という単一のエンドポイントを公開します。</span><span class="sxs-lookup"><span data-stu-id="585b1-180">STS B exposes a single endpoint, called `STSEndpoint` that can be use to request security tokens.</span></span> <span data-ttu-id="585b1-181">具体的には、STS B は、`accessAuthorized` クレームを含む SAML トークンを発行します。このトークンは、サービスにアクセスするために `MyService` サービス サイトで提示できます。</span><span class="sxs-lookup"><span data-stu-id="585b1-181">Specifically, STS B issues SAML tokens with the `accessAuthorized` claim, which can be presented at the `MyService` service site for accessing the service.</span></span> <span data-ttu-id="585b1-182">ただし、STS B は、STS A によって発行された `userAuthenticated` クレームを含む有効な SAML トークンを提示することをユーザーに要求します。</span><span class="sxs-lookup"><span data-stu-id="585b1-182">However, STS B requires users to present a valid SAML token issued by STS A that contains the `userAuthenticated` claim.</span></span> <span data-ttu-id="585b1-183">これは、STS 構成で宣言によって指定されます。</span><span class="sxs-lookup"><span data-stu-id="585b1-183">This is declaratively specified in the STS configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_B" behaviorConfiguration=  
     "STS-B_Behavior">  
    <endpoint address=""  
              binding="wsFederationHttpBinding"  
              bindingConfiguration='STS-B_Binding'  
      contract="FederationSample.ISts" />  
    </service>  
  </services>  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by STS-B. It redirects clients to   
         STS-A. -->  
      <binding name='STS-B_Binding'>  
        <security mode='Message'>  
          <message issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
          <issuer address='http://localhost/FederationSample/STS-A/STS.svc' />  
          <issuerMetadata address='http://localhost/FederationSample/STS-A/STS.svc/mex'/>  
          <requiredClaimTypes>  
            <add claimType='http://tempuri.org:userAuthenticated'/>  
          </requiredClaimTypes>  
          </message>  
        </security>  
    </binding>  
   </wsFederationHttpBinding>  
  </bindings>  
  <behaviors>  
  <behavior name='STS-B_Behavior'>  
    <serviceAuthorization   operationRequirementType='FederationSample.STS_B_OperationRequirement, STS_B' />  
    <serviceCredentials>  
      <serviceCertificate findValue='CN=FederationSample.com'  
      x509FindType='FindBySubjectDistinguishedName'  
       storeLocation='LocalMachine'  
       storeName='My' />  
     </serviceCredentials>  
   </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
>  <span data-ttu-id="585b1-184">この場合も、`userAuthenticated` クレームは、STS B が必要とするクレームの種類です。このクレームの種類の完全修飾名は http://tempuri.org:userAuthenticated (関連する名前空間を含みます) で、この名前が STS 構成ファイルで使用されます。</span><span class="sxs-lookup"><span data-stu-id="585b1-184">Again, the `userAuthenticated` claim is the claim type that is required by STS B. The fully-qualified name of this claim type is http://tempuri.org:userAuthenticated (along with the associated namespace), which is used in the STS configuration file.</span></span> <span data-ttu-id="585b1-185">このクレームの値は、このクレームが存在することを示しており、STS A によって `true` に設定されると想定されます。</span><span class="sxs-lookup"><span data-stu-id="585b1-185">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS A.</span></span>  
  
 <span data-ttu-id="585b1-186">STS B の一部として実装されているこのポリシーは、`STS_B_OperationRequirement` クラスによって実行時に適用されます。</span><span class="sxs-lookup"><span data-stu-id="585b1-186">At runtime, the `STS_B_OperationRequirement` class enforces this policy, which is implemented as part of STS B.</span></span>  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 <span data-ttu-id="585b1-187">アクセス チェックで問題がなければ、STS B は、`accessAuthorized` クレームを含む SAML トークンを発行します。</span><span class="sxs-lookup"><span data-stu-id="585b1-187">If the access check is clear, STS B issues a SAML token with the `accessAuthorized` claim.</span></span>  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a><span data-ttu-id="585b1-188">STS A</span><span class="sxs-lookup"><span data-stu-id="585b1-188">STS A</span></span>  
 <span data-ttu-id="585b1-189">STS A を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="585b1-189">The following illustration shows the STS A.</span></span>  
  
 <span data-ttu-id="585b1-190">![フェデレーション](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span><span class="sxs-lookup"><span data-stu-id="585b1-190">![Federation](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span></span>  
  
 <span data-ttu-id="585b1-191">STS B と同様に、STS A もセキュリティ トークンを発行する Web サービスであり、そのための単一のエンドポイントを公開します。</span><span class="sxs-lookup"><span data-stu-id="585b1-191">Similar to the STS B, the STS A is also a Web service that issues security tokens and exposes a single endpoint for this purpose.</span></span> <span data-ttu-id="585b1-192">ただし、STS A は別のバインディング (`wsHttpBinding`) を使用し、[!INCLUDE[infocard](../../../../includes/infocard-md.md)] クレームを含む有効な `emailAddress` を提示することをユーザーに要求します。</span><span class="sxs-lookup"><span data-stu-id="585b1-192">However, it uses a different binding (`wsHttpBinding`) and requires users to present a valid [!INCLUDE[infocard](../../../../includes/infocard-md.md)] with an `emailAddress` claim.</span></span> <span data-ttu-id="585b1-193">応答で、STS A は `userAuthenticated` クレームを含む SAML トークンを発行します。</span><span class="sxs-lookup"><span data-stu-id="585b1-193">In response, it issues SAML tokens with the `userAuthenticated` claim.</span></span> <span data-ttu-id="585b1-194">これは、サービス構成で宣言によって指定されます。</span><span class="sxs-lookup"><span data-stu-id="585b1-194">This is declaratively specified in the service configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_A" behaviorConfiguration="STS-A_Behavior">  
      <endpoint address=""  
                binding="wsHttpBinding"  
                bindingConfiguration="STS-A_Binding"  
                contract="FederationSample.ISts">  
       <identity>  
       <certificateReference findValue="CN=FederationSample.com"    
                       x509FindType="FindBySubjectDistinguishedName"  
                       storeLocation="LocalMachine"   
                       storeName="My" />  
       </identity>  
    <endpoint>  
  </service>  
</services>  
  
<bindings>  
  <wsHttpBinding>  
  <!-- This is the binding used by STS-A. It requires users to present  
   a CardSpace. -->  
    <binding name='STS-A_Binding'>  
      <security mode='Message'>  
        <message clientCredentialType="CardSpace" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
  
<behaviors>  
  <behavior name='STS-A_Behavior'>  
    <serviceAuthorization operationRequirementType=  
     "FederationSample.STS_A_OperationRequirement, STS_A" />  
      <serviceCredentials>  
  <serviceCertificate findValue="CN=FederationSample.com"  
                     x509FindType='FindBySubjectDistinguishedName'  
                     storeLocation='LocalMachine'  
                     storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="585b1-195">STS A の一部として実装されているこのポリシーは、`STS_A_OperationRequirement` クラスによって実行時に適用されます。</span><span class="sxs-lookup"><span data-stu-id="585b1-195">At runtime, the `STS_A_OperationRequirement` class enforces this policy, which is implemented as part of STS A.</span></span>  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 <span data-ttu-id="585b1-196">アクセスが `true` であれば、STS A は、`userAuthenticated` クレームを含む SAML トークンを発行します。</span><span class="sxs-lookup"><span data-stu-id="585b1-196">If the access is `true`, STS A issues a SAML token with `userAuthenticated` claim.</span></span>  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a><span data-ttu-id="585b1-197">組織 A のクライアント</span><span class="sxs-lookup"><span data-stu-id="585b1-197">Client at Organization A</span></span>  
 <span data-ttu-id="585b1-198">`MyService` サービスの呼び出しに必要な手順と共に、組織 A のクライアントを次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="585b1-198">The following illustration shows the client at organization A, along with the steps involved in making a `MyService` service call.</span></span> <span data-ttu-id="585b1-199">全体の処理を示すために、他の機能コンポーネントも示します。</span><span class="sxs-lookup"><span data-stu-id="585b1-199">The other functional components are also included for completeness.</span></span>  
  
 <span data-ttu-id="585b1-200">![フェデレーション](../../../../docs/framework/wcf/feature-details/media/federationclienta.gif "FederationClientA")</span><span class="sxs-lookup"><span data-stu-id="585b1-200">![Federation](../../../../docs/framework/wcf/feature-details/media/federationclienta.gif "FederationClientA")</span></span>  
  
## <a name="summary"></a><span data-ttu-id="585b1-201">概要</span><span class="sxs-lookup"><span data-stu-id="585b1-201">Summary</span></span>  
 <span data-ttu-id="585b1-202">フェデレーション セキュリティを使用すると、役割を明確に分離できるため、安全で拡張性のあるサービス アーキテクチャを構築できます。</span><span class="sxs-lookup"><span data-stu-id="585b1-202">Federated security provides a clean division of responsibility and helps to build secure, scalable service architectures.</span></span> <span data-ttu-id="585b1-203">分散アプリケーションの構築と展開を行うためのプラットフォームとして、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ではフェデレーション セキュリティの実装をネイティブにサポートをしています。</span><span class="sxs-lookup"><span data-stu-id="585b1-203">As a platform for building and deploying distributed applications, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides native support for implementing federated security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="585b1-204">関連項目</span><span class="sxs-lookup"><span data-stu-id="585b1-204">See Also</span></span>  
 [<span data-ttu-id="585b1-205">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="585b1-205">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)

---
title: "フェデレーションと発行済みトークン"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 017d3e51022ad9980dc8f058415697c80a2a6b35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="federation-and-issued-tokens"></a><span data-ttu-id="c79a2-102">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="c79a2-102">Federation and Issued Tokens</span></span>
<span data-ttu-id="c79a2-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を使用すれば、WS-Federation および WS-Trust 仕様を実装したサービスとセキュリティで保護された通信を行うクライアントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c79a2-103">With [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], you can create clients that communicate securely with services that implement the WS-Federation and WS-Trust specifications.</span></span> <span data-ttu-id="c79a2-104">これらの仕様では、異なる信頼領域間での認証と承認を可能にする機構を提供するために、XML、SOAP、および Web サービス記述言語 (WSDL: Web Services Description Language) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c79a2-104">The specifications use XML, SOAP, and Web Services Description Language (WSDL) to provide mechanisms that enable authentication and authorization across different trust realms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c79a2-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c79a2-105">In This Section</span></span>  
 [<span data-ttu-id="c79a2-106">フェデレーション</span><span class="sxs-lookup"><span data-stu-id="c79a2-106">Federation</span></span>](../../../../docs/framework/wcf/feature-details/federation.md)  
 <span data-ttu-id="c79a2-107">フェデレーションの概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="c79a2-107">Provides an overview of federation.</span></span>  
  
 [<span data-ttu-id="c79a2-108">フェデレーションと信頼</span><span class="sxs-lookup"><span data-stu-id="c79a2-108">Federation and Trust</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)  
 <span data-ttu-id="c79a2-109">フェデレーション サービスまたはクライアントを作成するときに注意する必要がある設計上の問題を示します。</span><span class="sxs-lookup"><span data-stu-id="c79a2-109">Lists the design issues to be aware of when creating federated services or clients.</span></span>  
  
 [<span data-ttu-id="c79a2-110">方法 : フェデレーション クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="c79a2-110">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 <span data-ttu-id="c79a2-111">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でフェデレーション クライアントを作成するための基本を説明します。</span><span class="sxs-lookup"><span data-stu-id="c79a2-111">Describes the basics of creating a federated client with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="c79a2-112">方法 : フェデレーション サービスで資格情報を設定する</span><span class="sxs-lookup"><span data-stu-id="c79a2-112">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 <span data-ttu-id="c79a2-113">フェデレーション サービスを作成する手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="c79a2-113">Describes the steps of creating a federated service.</span></span>  
  
 [<span data-ttu-id="c79a2-114">方法 : WSFederationHttpBinding を作成する</span><span class="sxs-lookup"><span data-stu-id="c79a2-114">How to: Create a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="c79a2-115">`WSFederationHttpBinding` を使用するクライアントおよびサービスを構成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="c79a2-115">Describes how to configure clients and services that use the `WSFederationHttpBinding`.</span></span>  
  
 [<span data-ttu-id="c79a2-116">方法 : セキュリティ トークン サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="c79a2-116">How to: Create a Security Token Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-token-service.md)  
 <span data-ttu-id="c79a2-117">セキュリティ トークン サービスを作成する手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="c79a2-117">Describes the steps of creating a security token service.</span></span>  
  
 [<span data-ttu-id="c79a2-118">SAML (Security Assertions Markup Language) トークンとクレーム</span><span class="sxs-lookup"><span data-stu-id="c79a2-118">Security Assertions Markup Language (SAML) Tokens and Claims</span></span>](../../../../docs/framework/wcf/feature-details/saml-tokens-and-claims.md)  
 <span data-ttu-id="c79a2-119">多様なクレームの種類を作成できる拡張可能な SAML (Security Assertions Markup Language) トークンについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c79a2-119">Describes Security Assertions Markup Language (SAML) tokens, which are extensible and enable you to create rich claim types.</span></span>  
  
 [<span data-ttu-id="c79a2-120">方法 : ローカル発行者を設定する</span><span class="sxs-lookup"><span data-stu-id="c79a2-120">How to: Configure a Local Issuer</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 <span data-ttu-id="c79a2-121">セキュリティ トークンのローカル発行者の作成方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="c79a2-121">Describes how to create a local issuer of security tokens.</span></span>  
  
 [<span data-ttu-id="c79a2-122">方法 : WSFederationHttpBinding のセキュリティで保護されたセッションを無効にする</span><span class="sxs-lookup"><span data-stu-id="c79a2-122">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="c79a2-123">`WSFederationHttpBinding` のセキュリティで保護されたセッションを無効にする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="c79a2-123">Describes how to disable secure sessions on a `WSFederationHttpBinding`.</span></span> <span data-ttu-id="c79a2-124">クライアントごとにセッションが必要になる Web ファームを作成する場合には、セキュリティで保護されたセッションを無効化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c79a2-124">Disabling secure sessions is necessary when creating a Web farm that requires a session for each client.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c79a2-125">参照</span><span class="sxs-lookup"><span data-stu-id="c79a2-125">Reference</span></span>  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenProvider>  
  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
  
## <a name="see-also"></a><span data-ttu-id="c79a2-126">参照</span><span class="sxs-lookup"><span data-stu-id="c79a2-126">See Also</span></span>  
 [<span data-ttu-id="c79a2-127">承認</span><span class="sxs-lookup"><span data-stu-id="c79a2-127">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [<span data-ttu-id="c79a2-128">カスタム トークン</span><span class="sxs-lookup"><span data-stu-id="c79a2-128">Custom Tokens</span></span>](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 [<span data-ttu-id="c79a2-129">Windows Server App Fabric のセキュリティ モデル</span><span class="sxs-lookup"><span data-stu-id="c79a2-129">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)

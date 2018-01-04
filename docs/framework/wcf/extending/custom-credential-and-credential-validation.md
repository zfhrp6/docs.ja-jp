---
title: "カスタム資格情報と資格情報の検証"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- credentials [WCF], custom
- credentials [WCF]
- custom credentials [WCF]
- credential validation [WCF]
- credentials [WCF], validation
ms.assetid: da831bec-e281-4d44-b343-437b5eef688e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bdfd50253c71bfc9edd737964e771546cb797b9e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="custom-credential-and-credential-validation"></a><span data-ttu-id="a14ab-102">カスタム資格情報と資格情報の検証</span><span class="sxs-lookup"><span data-stu-id="a14ab-102">Custom Credential and Credential Validation</span></span>
<span data-ttu-id="a14ab-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のセキュリティは、サービスとクライアント間の資格情報の交換に基づきます。</span><span class="sxs-lookup"><span data-stu-id="a14ab-103">Security in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is based on the exchange of credentials between services and clients.</span></span> <span data-ttu-id="a14ab-104">セキュリティ シナリオの多くは、Windows (Kerberos)、ユーザー名とパスワード、証明書などの共通の資格情報の種類を使用して満たされます。</span><span class="sxs-lookup"><span data-stu-id="a14ab-104">Most security scenarios can be satisfied using common credential types, such as Windows (Kerberos), username and passwords, and certificates.</span></span> <span data-ttu-id="a14ab-105">ただし、新しい種類の資格情報が必要な場合があります。このセクションのこのトピックでは、その新しい種類の処理方法と検証方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a14ab-105">However, if a new type of credential is required, the topics in this section explain how to handle and validate new types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a14ab-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a14ab-106">In This Section</span></span>  
 [<span data-ttu-id="a14ab-107">方法 : カスタム証明書検証を使用するサービスを作成する</span><span class="sxs-lookup"><span data-stu-id="a14ab-107">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 <span data-ttu-id="a14ab-108">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クラスを継承することで <xref:System.IdentityModel.Selectors.X509CertificateValidator> の検証をカスタマイズする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a14ab-108">Explains how to customize [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] validation by inheriting from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span>  
  
 [<span data-ttu-id="a14ab-109">チュートリアル: カスタム クライアントおよびサービスの資格情報を作成する</span><span class="sxs-lookup"><span data-stu-id="a14ab-109">Walkthrough: Creating Custom Client and Service Credentials</span></span>](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 <span data-ttu-id="a14ab-110">拡張する方法を示します、<xref:System.ServiceModel.Description.ClientCredentials>と<xref:System.ServiceModel.Description.ServiceCredentials>資格情報の種類を新規に対応するクラス。</span><span class="sxs-lookup"><span data-stu-id="a14ab-110">Demonstrates how to extend the <xref:System.ServiceModel.Description.ClientCredentials> and <xref:System.ServiceModel.Description.ServiceCredentials> classes to accommodate new credential types.</span></span> <span data-ttu-id="a14ab-111">これは、カスタム資格情報の種類の作成を実現するトピック シリーズの 1 番目です。</span><span class="sxs-lookup"><span data-stu-id="a14ab-111">This is first in a series of topics that enable creation of custom credential types.</span></span>  
  
 [<span data-ttu-id="a14ab-112">方法 : カスタム セキュリティ トークン プロバイダーを作成する</span><span class="sxs-lookup"><span data-stu-id="a14ab-112">How to: Create a Custom Security Token Provider</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 <span data-ttu-id="a14ab-113">セキュリティ トークン プロバイダーを作成して新しい資格情報の種類を処理し、その資格情報の新しいトークンを返す方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a14ab-113">Explains how to create a security token provider to handle new credential types and return new tokens for the credential.</span></span> <span data-ttu-id="a14ab-114">これは、シリーズの 2 番目のトピックです。</span><span class="sxs-lookup"><span data-stu-id="a14ab-114">This is the second topic in the series.</span></span>  
  
 [<span data-ttu-id="a14ab-115">方法 : カスタム セキュリティ トークン認証システムを作成する</span><span class="sxs-lookup"><span data-stu-id="a14ab-115">How to: Create a Custom Security Token Authenticator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 <span data-ttu-id="a14ab-116">カスタム認証システムを作成して新しい資格情報の種類を認証する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a14ab-116">Explains how to create a custom authenticator to authenticate a new credential type.</span></span> <span data-ttu-id="a14ab-117">これは、シリーズの 3 番目のトピックです。</span><span class="sxs-lookup"><span data-stu-id="a14ab-117">This is the third topic in the series.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a14ab-118">参照</span><span class="sxs-lookup"><span data-stu-id="a14ab-118">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a><span data-ttu-id="a14ab-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="a14ab-119">Related Sections</span></span>  
 [<span data-ttu-id="a14ab-120">認証</span><span class="sxs-lookup"><span data-stu-id="a14ab-120">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [<span data-ttu-id="a14ab-121">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="a14ab-121">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="a14ab-122">承認</span><span class="sxs-lookup"><span data-stu-id="a14ab-122">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="a14ab-123">参照</span><span class="sxs-lookup"><span data-stu-id="a14ab-123">See Also</span></span>  
 [<span data-ttu-id="a14ab-124">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="a14ab-124">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)

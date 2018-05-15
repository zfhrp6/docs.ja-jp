---
title: カスタム資格情報と資格情報の検証
ms.date: 03/30/2017
helpviewer_keywords:
- credentials [WCF], custom
- credentials [WCF]
- custom credentials [WCF]
- credential validation [WCF]
- credentials [WCF], validation
ms.assetid: da831bec-e281-4d44-b343-437b5eef688e
ms.openlocfilehash: 9b340c01a9eb4ce4007e93f2b38e292cd6543ba1
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="custom-credential-and-credential-validation"></a><span data-ttu-id="eba4e-102">カスタム資格情報と資格情報の検証</span><span class="sxs-lookup"><span data-stu-id="eba4e-102">Custom Credential and Credential Validation</span></span>
<span data-ttu-id="eba4e-103">Windows Communication Foundation (WCF) でのセキュリティは、サービスとクライアント間で資格情報の交換に基づいています。</span><span class="sxs-lookup"><span data-stu-id="eba4e-103">Security in Windows Communication Foundation (WCF) is based on the exchange of credentials between services and clients.</span></span> <span data-ttu-id="eba4e-104">セキュリティ シナリオの多くは、Windows (Kerberos)、ユーザー名とパスワード、証明書などの共通の資格情報の種類を使用して満たされます。</span><span class="sxs-lookup"><span data-stu-id="eba4e-104">Most security scenarios can be satisfied using common credential types, such as Windows (Kerberos), username and passwords, and certificates.</span></span> <span data-ttu-id="eba4e-105">ただし、新しい種類の資格情報が必要な場合があります。このセクションのこのトピックでは、その新しい種類の処理方法と検証方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eba4e-105">However, if a new type of credential is required, the topics in this section explain how to handle and validate new types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eba4e-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="eba4e-106">In This Section</span></span>  
 [<span data-ttu-id="eba4e-107">方法 : カスタム証明書検証を使用するサービスを作成する</span><span class="sxs-lookup"><span data-stu-id="eba4e-107">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 <span data-ttu-id="eba4e-108">継承することで WCF の検証をカスタマイズする方法について説明します、<xref:System.IdentityModel.Selectors.X509CertificateValidator>クラスです。</span><span class="sxs-lookup"><span data-stu-id="eba4e-108">Explains how to customize WCF validation by inheriting from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span>  
  
 [<span data-ttu-id="eba4e-109">チュートリアル: カスタム クライアントおよびサービスの資格情報を作成する</span><span class="sxs-lookup"><span data-stu-id="eba4e-109">Walkthrough: Creating Custom Client and Service Credentials</span></span>](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 <span data-ttu-id="eba4e-110">拡張する方法を示します、<xref:System.ServiceModel.Description.ClientCredentials>と<xref:System.ServiceModel.Description.ServiceCredentials>資格情報の種類を新規に対応するクラス。</span><span class="sxs-lookup"><span data-stu-id="eba4e-110">Demonstrates how to extend the <xref:System.ServiceModel.Description.ClientCredentials> and <xref:System.ServiceModel.Description.ServiceCredentials> classes to accommodate new credential types.</span></span> <span data-ttu-id="eba4e-111">これは、カスタム資格情報の種類の作成を実現するトピック シリーズの 1 番目です。</span><span class="sxs-lookup"><span data-stu-id="eba4e-111">This is first in a series of topics that enable creation of custom credential types.</span></span>  
  
 [<span data-ttu-id="eba4e-112">方法 : カスタム セキュリティ トークン プロバイダーを作成する</span><span class="sxs-lookup"><span data-stu-id="eba4e-112">How to: Create a Custom Security Token Provider</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 <span data-ttu-id="eba4e-113">セキュリティ トークン プロバイダーを作成して新しい資格情報の種類を処理し、その資格情報の新しいトークンを返す方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="eba4e-113">Explains how to create a security token provider to handle new credential types and return new tokens for the credential.</span></span> <span data-ttu-id="eba4e-114">これは、シリーズの 2 番目のトピックです。</span><span class="sxs-lookup"><span data-stu-id="eba4e-114">This is the second topic in the series.</span></span>  
  
 [<span data-ttu-id="eba4e-115">方法 : カスタム セキュリティ トークン認証システムを作成する</span><span class="sxs-lookup"><span data-stu-id="eba4e-115">How to: Create a Custom Security Token Authenticator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 <span data-ttu-id="eba4e-116">カスタム認証システムを作成して新しい資格情報の種類を認証する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="eba4e-116">Explains how to create a custom authenticator to authenticate a new credential type.</span></span> <span data-ttu-id="eba4e-117">これは、シリーズの 3 番目のトピックです。</span><span class="sxs-lookup"><span data-stu-id="eba4e-117">This is the third topic in the series.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="eba4e-118">参照</span><span class="sxs-lookup"><span data-stu-id="eba4e-118">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a><span data-ttu-id="eba4e-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="eba4e-119">Related Sections</span></span>  
 [<span data-ttu-id="eba4e-120">認証</span><span class="sxs-lookup"><span data-stu-id="eba4e-120">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [<span data-ttu-id="eba4e-121">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="eba4e-121">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="eba4e-122">承認</span><span class="sxs-lookup"><span data-stu-id="eba4e-122">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="eba4e-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="eba4e-123">See Also</span></span>  
 [<span data-ttu-id="eba4e-124">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="eba4e-124">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)

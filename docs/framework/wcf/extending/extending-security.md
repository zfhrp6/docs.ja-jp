---
title: "セキュリティの拡張"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
caps.latest.revision: "23"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: a3950b156ede806382bbe4e013db5d94a8b20a23
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="extending-security"></a><span data-ttu-id="e70aa-102">セキュリティの拡張</span><span class="sxs-lookup"><span data-stu-id="e70aa-102">Extending Security</span></span>
<span data-ttu-id="e70aa-103">新しいクレームの種類やカスタム トークンに対応するために、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のセキュリティ インフラストラクチャを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="e70aa-103">To accommodate new claim types and custom tokens, you can extend the security infrastructure of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="e70aa-104">このセクションの各トピックでは、この方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e70aa-104">The topics in this section show you how this is done.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e70aa-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e70aa-105">In This Section</span></span>  
 [<span data-ttu-id="e70aa-106">セキュリティ アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="e70aa-106">Security Architecture</span></span>](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f)  
 <span data-ttu-id="e70aa-107">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のセキュリティ システムのアーキテクチャについて解説します。</span><span class="sxs-lookup"><span data-stu-id="e70aa-107">Walks through the architecture of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security system.</span></span>  
  
 [<span data-ttu-id="e70aa-108">カスタム資格情報と資格情報の検証</span><span class="sxs-lookup"><span data-stu-id="e70aa-108">Custom Credential and Credential Validation</span></span>](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md)  
 <span data-ttu-id="e70aa-109">カスタム資格情報の検証中に ID モデルを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e70aa-109">Explains how the Identity Model is used when validating custom credentials.</span></span>  
  
 [<span data-ttu-id="e70aa-110">カスタム トークン</span><span class="sxs-lookup"><span data-stu-id="e70aa-110">Custom Tokens</span></span>](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 <span data-ttu-id="e70aa-111">通常、セキュリティ トークン サービス (STS) から発行されるトークンは SAML トークンです。</span><span class="sxs-lookup"><span data-stu-id="e70aa-111">Issued tokens from a Security Token Service (STS) are typically SAML tokens.</span></span> <span data-ttu-id="e70aa-112">ここでは、カスタムのトークンの種類を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e70aa-112">This topic explains how to create a custom token type.</span></span>  
  
 [<span data-ttu-id="e70aa-113">カスタム承認</span><span class="sxs-lookup"><span data-stu-id="e70aa-113">Custom Authorization</span></span>](../../../../docs/framework/wcf/extending/custom-authorization.md)  
 <span data-ttu-id="e70aa-114">カスタム承認を実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e70aa-114">Explains how to implement custom authorization.</span></span>  
  
 [<span data-ttu-id="e70aa-115">認証サービスの Id をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="e70aa-115">Overriding the Identity of a Service for Authentication</span></span>](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)  
 <span data-ttu-id="e70aa-116">認証のためにサービスの ID をオーバーライドする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e70aa-116">Describes how to override the identity of a service for authentication.</span></span>  
  
 [<span data-ttu-id="e70aa-117">方法: カスタムのクライアント Id 検証機能を作成します。</span><span class="sxs-lookup"><span data-stu-id="e70aa-117">How to: Create a Custom Client Identity Verifier</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 <span data-ttu-id="e70aa-118">カスタム エンドポイント ID を検証する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e70aa-118">Demonstrates how to validate a custom endpoint identity.</span></span>  
  
 [<span data-ttu-id="e70aa-119">方法: 個別の X.509 証明書の署名を使用して暗号化</span><span class="sxs-lookup"><span data-stu-id="e70aa-119">How to: Use Separate X.509 Certificates for Signing and Encryption</span></span>](../../../../docs/framework/wcf/extending/how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 <span data-ttu-id="e70aa-120">通常、メッセージの署名および暗号化は 1 つの証明書を使用して行われます。</span><span class="sxs-lookup"><span data-stu-id="e70aa-120">Messages are typically signed and encrypted with a single certificate.</span></span> <span data-ttu-id="e70aa-121">ここでは、必要に応じて 2 つの証明書を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e70aa-121">This topic explains how two certificates can be used, when required.</span></span>  
  
 [<span data-ttu-id="e70aa-122">方法: X.509 証明書の秘密キーの暗号化サービス プロバイダーを変更します。</span><span class="sxs-lookup"><span data-stu-id="e70aa-122">How to: Change the Cryptographic Provider for an X.509 Certificate's Private Key</span></span>](../../../../docs/framework/wcf/extending/change-cryptographic-provider-x509-certificate-private-key.md)  
 <span data-ttu-id="e70aa-123">X.509 証明書の秘密キーを提供するために使用する暗号化プロバイダーを変更する方法、およびそのプロバイダーを [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] フレームワークに統合する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e70aa-123">Explains how to change the cryptographic provider used to provide an X.509 certificate's private key and how to integrate the provider into the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] framework.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e70aa-124">参照</span><span class="sxs-lookup"><span data-stu-id="e70aa-124">Reference</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a><span data-ttu-id="e70aa-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="e70aa-125">Related Sections</span></span>  
 [<span data-ttu-id="e70aa-126">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e70aa-126">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [<span data-ttu-id="e70aa-127">基本的な WCF プログラミング</span><span class="sxs-lookup"><span data-stu-id="e70aa-127">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
## <a name="see-also"></a><span data-ttu-id="e70aa-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="e70aa-128">See Also</span></span>  
 [<span data-ttu-id="e70aa-129">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="e70aa-129">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)

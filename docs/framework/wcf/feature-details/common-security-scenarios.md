---
title: 一般的なセキュリティ シナリオ
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], scenarios
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0fb51ea0624c4fa686e4e99ffb9c30decedfea10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490904"
---
# <a name="common-security-scenarios"></a><span data-ttu-id="870de-102">一般的なセキュリティ シナリオ</span><span class="sxs-lookup"><span data-stu-id="870de-102">Common Security Scenarios</span></span>
<span data-ttu-id="870de-103">ここでは、考えられるさまざまなクライアントおよびサービスのセキュリティ構成の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="870de-103">The topics in this section catalog a number of possible client and service security configurations.</span></span> <span data-ttu-id="870de-104">構成はさまざまな要因により異なります。</span><span class="sxs-lookup"><span data-stu-id="870de-104">Configurations vary according to a number of factors.</span></span> <span data-ttu-id="870de-105">たとえば、サービスやクライアントがイントラネット上にあるかどうか、また、セキュリティが Windows とトランスポート (HTTPS など) のどちらで提供されるかなどが考えられます。</span><span class="sxs-lookup"><span data-stu-id="870de-105">For example, whether a service or client is on an intranet, or whether the security is provided by Windows or transport (such as HTTPS).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="870de-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="870de-106">In This Section</span></span>  
 [<span data-ttu-id="870de-107">セキュリティで保護されていないインターネット環境のクライアントとサービス</span><span class="sxs-lookup"><span data-stu-id="870de-107">Internet Unsecured Client and Service</span></span>](../../../../docs/framework/wcf/feature-details/internet-unsecured-client-and-service.md)  
 <span data-ttu-id="870de-108">セキュリティで保護されていないパブリックなクライアントとサービスの例です。</span><span class="sxs-lookup"><span data-stu-id="870de-108">An example of a public, unsecured client and service.</span></span>  
  
 [<span data-ttu-id="870de-109">セキュリティで保護されていないイントラネットのクライアントとサービス</span><span class="sxs-lookup"><span data-stu-id="870de-109">Intranet Unsecured Client and Service</span></span>](../../../../docs/framework/wcf/feature-details/intranet-unsecured-client-and-service.md)  
 <span data-ttu-id="870de-110">WCF アプリケーションをセキュリティで保護されたプライベート ネットワーク上の情報を提供する基本的な Windows Communication Foundation (WCF) サービスを開発しました。</span><span class="sxs-lookup"><span data-stu-id="870de-110">A basic Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span>  
  
 [<span data-ttu-id="870de-111">基本認証を使用する場合のトランスポート セキュリティ</span><span class="sxs-lookup"><span data-stu-id="870de-111">Transport Security with Basic Authentication</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 <span data-ttu-id="870de-112">アプリケーションは、カスタム認証を使用して、クライアントにログオンを許可します。</span><span class="sxs-lookup"><span data-stu-id="870de-112">The application allows clients to log on using custom authentication.</span></span>  
  
 [<span data-ttu-id="870de-113">Windows 認証を使用する場合のトランスポート セキュリティ</span><span class="sxs-lookup"><span data-stu-id="870de-113">Transport Security with Windows Authentication</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md)  
 <span data-ttu-id="870de-114">Windows セキュリティによってセキュリティ保護されたクライアントとサービスを示します。</span><span class="sxs-lookup"><span data-stu-id="870de-114">Shows a client and service secured by Windows security.</span></span>  
  
 [<span data-ttu-id="870de-115">トランスポート セキュリティと匿名クライアント</span><span class="sxs-lookup"><span data-stu-id="870de-115">Transport Security with an Anonymous Client</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-an-anonymous-client.md)  
 <span data-ttu-id="870de-116">このシナリオでは HTTPS などのようなトランスポート セキュリティを使用して、機密性と整合性を強化します。</span><span class="sxs-lookup"><span data-stu-id="870de-116">This scenario uses transport security (such as HTTPS) to ensure confidentiality and integrity.</span></span>  
  
 [<span data-ttu-id="870de-117">トランスポート セキュリティと証明書認証</span><span class="sxs-lookup"><span data-stu-id="870de-117">Transport Security with Certificate Authentication</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-certificate-authentication.md)  
 <span data-ttu-id="870de-118">証明書によってセキュリティ保護されたクライアントとサービスを示します。</span><span class="sxs-lookup"><span data-stu-id="870de-118">Shows a client and service secured by a certificate.</span></span>  
  
 [<span data-ttu-id="870de-119">メッセージ セキュリティと匿名クライアント</span><span class="sxs-lookup"><span data-stu-id="870de-119">Message Security with an Anonymous Client</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-an-anonymous-client.md)  
 <span data-ttu-id="870de-120">クライアントと WCF メッセージ セキュリティによって保護されたサービスを示します。</span><span class="sxs-lookup"><span data-stu-id="870de-120">Shows a client and service secured by WCF message security.</span></span>  
  
 [<span data-ttu-id="870de-121">ユーザー名クライアントを使用したメッセージ セキュリティ</span><span class="sxs-lookup"><span data-stu-id="870de-121">Message Security with a User Name Client</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-a-user-name-client.md)  
 <span data-ttu-id="870de-122">クライアントは、ドメイン ユーザー名とパスワードを使用してクライアントのログオンを許可する Windows フォーム アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="870de-122">The client is a Windows Forms application that allows clients to log on using a domain user name and password.</span></span>  
  
 [<span data-ttu-id="870de-123">メッセージ セキュリティと証明書クライアント</span><span class="sxs-lookup"><span data-stu-id="870de-123">Message Security with a Certificate Client</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-a-certificate-client.md)  
 <span data-ttu-id="870de-124">サーバー側の証明書は複数あり、クライアント側の証明書はそれぞれ 1 つです。</span><span class="sxs-lookup"><span data-stu-id="870de-124">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="870de-125">セキュリティのコンテキストは、トランスポート層セキュリティ (TLS: Transport Layer Security) ネゴシエーションを介して確立されます。</span><span class="sxs-lookup"><span data-stu-id="870de-125">A security context is established through Transport Layer Security (TLS) negotiation.</span></span>  
  
 [<span data-ttu-id="870de-126">Windows クライアントを使用する場合のメッセージ セキュリティ</span><span class="sxs-lookup"><span data-stu-id="870de-126">Message Security with a Windows Client</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md)  
 <span data-ttu-id="870de-127">証明書クライアントのバリエーションの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="870de-127">A variation of the certificate client.</span></span> <span data-ttu-id="870de-128">サーバー側の証明書は複数あり、クライアント側の証明書はそれぞれ 1 つです。</span><span class="sxs-lookup"><span data-stu-id="870de-128">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="870de-129">セキュリティのコンテキストは TLS ネゴシエーションを介して確立されます。</span><span class="sxs-lookup"><span data-stu-id="870de-129">A security context is established through TLS negotiation.</span></span>  
  
 [<span data-ttu-id="870de-130">資格情報ネゴシエーションを使用しない Windows クライアントを使用するメッセージ セキュリティ</span><span class="sxs-lookup"><span data-stu-id="870de-130">Message Security with a Windows Client without Credential Negotiation</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client-without-credential-negotiation.md)  
 <span data-ttu-id="870de-131">Kerberos ドメインによってセキュリティ保護されたクライアントとサービスを示します。</span><span class="sxs-lookup"><span data-stu-id="870de-131">Shows a client and service secured by a Kerberos domain.</span></span>  
  
 [<span data-ttu-id="870de-132">相互の証明書を使用する場合のメッセージ セキュリティ</span><span class="sxs-lookup"><span data-stu-id="870de-132">Message Security with Mutual Certificates</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-mutual-certificates.md)  
 <span data-ttu-id="870de-133">サーバー側の証明書は複数あり、クライアント側の証明書はそれぞれ 1 つです。</span><span class="sxs-lookup"><span data-stu-id="870de-133">Servers have certificates, and each client has a certificate.</span></span> <span data-ttu-id="870de-134">サーバーの証明書はアプリケーションと共に配布され、帯域外でも使用可能です。</span><span class="sxs-lookup"><span data-stu-id="870de-134">The server certificate is distributed with the application and is available out of band.</span></span>  
  
 [<span data-ttu-id="870de-135">発行済みトークンを使用したメッセージ セキュリティ</span><span class="sxs-lookup"><span data-stu-id="870de-135">Message Security with Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/message-security-with-issued-tokens.md)  
 <span data-ttu-id="870de-136">フェデレーション セキュリティにより独立したドメイン間で信頼を確立できます。</span><span class="sxs-lookup"><span data-stu-id="870de-136">Federated security that enables the establishment of trust between independent domains.</span></span>  
  
 [<span data-ttu-id="870de-137">信頼できるサブシステム</span><span class="sxs-lookup"><span data-stu-id="870de-137">Trusted Subsystem</span></span>](../../../../docs/framework/wcf/feature-details/trusted-subsystem.md)  
 <span data-ttu-id="870de-138">クライアントは、ネットワーク全体に分散している 1 つ以上の Web サービスにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="870de-138">A client accesses one or more Web services that are distributed across a network.</span></span> <span data-ttu-id="870de-139">Web サービスは、セキュリティで保護する必要がある追加のリソース (データベースや他の Web サービスなど) にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="870de-139">The Web services access additional resources (such as databases or other Web services) that must be secured.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="870de-140">参照</span><span class="sxs-lookup"><span data-stu-id="870de-140">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="870de-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="870de-141">Related Sections</span></span>  
 [<span data-ttu-id="870de-142">承認</span><span class="sxs-lookup"><span data-stu-id="870de-142">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [<span data-ttu-id="870de-143">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="870de-143">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
 [<span data-ttu-id="870de-144">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="870de-144">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [<span data-ttu-id="870de-145">バインディングとセキュリティ</span><span class="sxs-lookup"><span data-stu-id="870de-145">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [<span data-ttu-id="870de-146">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="870de-146">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
 [<span data-ttu-id="870de-147">認証</span><span class="sxs-lookup"><span data-stu-id="870de-147">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [<span data-ttu-id="870de-148">承認</span><span class="sxs-lookup"><span data-stu-id="870de-148">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [<span data-ttu-id="870de-149">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="870de-149">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="870de-150">監査</span><span class="sxs-lookup"><span data-stu-id="870de-150">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
  
## <a name="see-also"></a><span data-ttu-id="870de-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="870de-151">See Also</span></span>  
 [<span data-ttu-id="870de-152">セキュリティ ガイドラインとベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="870de-152">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 [<span data-ttu-id="870de-153">Windows Server App Fabric のセキュリティ モデル</span><span class="sxs-lookup"><span data-stu-id="870de-153">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)

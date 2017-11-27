---
title: "セキュリティ プロトコル バージョン 1.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: f40c79ad1a6eedc2b1de4dffa9de5b48aeb8e6f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="security-protocols-version-10"></a><span data-ttu-id="546ea-102">セキュリティ プロトコル バージョン 1.0</span><span class="sxs-lookup"><span data-stu-id="546ea-102">Security Protocols version 1.0</span></span>
<span data-ttu-id="546ea-103">Web サービス セキュリティ プロトコルには、既存のエンタープライズ メッセージング セキュリティのあらゆる要件に対応する Web サービス セキュリティ機構が用意されています。</span><span class="sxs-lookup"><span data-stu-id="546ea-103">The Web Services Security Protocols provide Web services security mechanisms that cover all existing enterprise messaging security requirements.</span></span> <span data-ttu-id="546ea-104">ここでは、以下の Web サービス セキュリティ プロトコルについて、([!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] で実装される) <xref:System.ServiceModel.Channels.SecurityBindingElement> バージョン 1.0 の詳細を説明します。</span><span class="sxs-lookup"><span data-stu-id="546ea-104">This section describes the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] version 1.0 details (implemented in the <xref:System.ServiceModel.Channels.SecurityBindingElement>) for the following Web services security protocols.</span></span>  
  
|<span data-ttu-id="546ea-105">仕様/ドキュメント</span><span class="sxs-lookup"><span data-stu-id="546ea-105">Specification/Document</span></span>|<span data-ttu-id="546ea-106">Link</span><span class="sxs-lookup"><span data-stu-id="546ea-106">Link</span></span>|  
|-|-|  
|<span data-ttu-id="546ea-107">WSS SOAP Message Security 1.0</span><span class="sxs-lookup"><span data-stu-id="546ea-107">WSS: SOAP Message Security 1.0</span></span>|<span data-ttu-id="546ea-108">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf</span><span class="sxs-lookup"><span data-stu-id="546ea-108">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf</span></span>|  
|<span data-ttu-id="546ea-109">WSS: Username Token Profile 1.0</span><span class="sxs-lookup"><span data-stu-id="546ea-109">WSS: Username Token Profile 1.0</span></span>|<span data-ttu-id="546ea-110">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf</span><span class="sxs-lookup"><span data-stu-id="546ea-110">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf</span></span>|  
|<span data-ttu-id="546ea-111">WSS: X509 Token Profile 1.0</span><span class="sxs-lookup"><span data-stu-id="546ea-111">WSS: X509 Token Profile 1.0</span></span>|<span data-ttu-id="546ea-112">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf</span><span class="sxs-lookup"><span data-stu-id="546ea-112">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf</span></span>|  
|<span data-ttu-id="546ea-113">WSS: SAML 1.1 Token Profile 1.0</span><span class="sxs-lookup"><span data-stu-id="546ea-113">WSS: SAML 1.1 Token Profile 1.0</span></span>|<span data-ttu-id="546ea-114">http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf</span><span class="sxs-lookup"><span data-stu-id="546ea-114">http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf</span></span>|  
|<span data-ttu-id="546ea-115">WSS SOAP Message Security 1.1</span><span class="sxs-lookup"><span data-stu-id="546ea-115">WSS: SOAP Message Security 1.1</span></span>|<span data-ttu-id="546ea-116">http://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf</span><span class="sxs-lookup"><span data-stu-id="546ea-116">http://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf</span></span>|  
|<span data-ttu-id="546ea-117">WSS Username Token Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="546ea-117">WSS Username Token Profile 1.1</span></span>|<span data-ttu-id="546ea-118">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf</span><span class="sxs-lookup"><span data-stu-id="546ea-118">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf</span></span>|  
|<span data-ttu-id="546ea-119">WSS: X.509 Token Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="546ea-119">WSS: X.509 Token Profile 1.1</span></span>|<span data-ttu-id="546ea-120">http://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf</span><span class="sxs-lookup"><span data-stu-id="546ea-120">http://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf</span></span>|  
|<span data-ttu-id="546ea-121">WSS: Kerberos Token Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="546ea-121">WSS: Kerberos Token Profile 1.1</span></span>|<span data-ttu-id="546ea-122">http://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf</span><span class="sxs-lookup"><span data-stu-id="546ea-122">http://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf</span></span>|  
|<span data-ttu-id="546ea-123">WSS: SAML 1.1 Token Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="546ea-123">WSS: SAML 1.1 Token Profile 1.1</span></span>|<span data-ttu-id="546ea-124">http://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf</span><span class="sxs-lookup"><span data-stu-id="546ea-124">http://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf</span></span>|  
|<span data-ttu-id="546ea-125">WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="546ea-125">WS-Secure Conversation</span></span>|<span data-ttu-id="546ea-126">http://msdn.microsoft.com/ws/2005/02/ws-secure-conversation/</span><span class="sxs-lookup"><span data-stu-id="546ea-126">http://msdn.microsoft.com/ws/2005/02/ws-secure-conversation/</span></span>|  
|<span data-ttu-id="546ea-127">WS-Trust</span><span class="sxs-lookup"><span data-stu-id="546ea-127">WS-Trust</span></span>|<span data-ttu-id="546ea-128">http://msdn.microsoft.com/ws/2005/02/ws-trust/</span><span class="sxs-lookup"><span data-stu-id="546ea-128">http://msdn.microsoft.com/ws/2005/02/ws-trust/</span></span>|  
|<span data-ttu-id="546ea-129">Application Note:</span><span class="sxs-lookup"><span data-stu-id="546ea-129">Application Note:</span></span><br /><br /> <span data-ttu-id="546ea-130">Using WS-Trust for TLS Handshake</span><span class="sxs-lookup"><span data-stu-id="546ea-130">Using WS-Trust for TLS Handshake</span></span>|<span data-ttu-id="546ea-131">公開予定</span><span class="sxs-lookup"><span data-stu-id="546ea-131">To be published</span></span>|  
|<span data-ttu-id="546ea-132">Application Note:</span><span class="sxs-lookup"><span data-stu-id="546ea-132">Application Note:</span></span><br /><br /> <span data-ttu-id="546ea-133">Using WS-Trust for SPNEGO</span><span class="sxs-lookup"><span data-stu-id="546ea-133">Using WS-Trust for SPNEGO</span></span>|<span data-ttu-id="546ea-134">公開予定</span><span class="sxs-lookup"><span data-stu-id="546ea-134">To be published</span></span>|  
|<span data-ttu-id="546ea-135">Application Note:</span><span class="sxs-lookup"><span data-stu-id="546ea-135">Application Note:</span></span><br /><br /> <span data-ttu-id="546ea-136">Web Services Addressing Endpoint References And Identity</span><span class="sxs-lookup"><span data-stu-id="546ea-136">Web Services Addressing Endpoint References And Identity</span></span>|<span data-ttu-id="546ea-137">公開予定</span><span class="sxs-lookup"><span data-stu-id="546ea-137">To be published</span></span>|  
|<span data-ttu-id="546ea-138">WS-SecurityPolicy 1.1</span><span class="sxs-lookup"><span data-stu-id="546ea-138">WS-SecurityPolicy 1.1</span></span><br /><br /> <span data-ttu-id="546ea-139">(2005/07)</span><span class="sxs-lookup"><span data-stu-id="546ea-139">(2005/07)</span></span>|<span data-ttu-id="546ea-140">http://msdn.microsoft.com/ws/2005/07/ws-security-policy/</span><span class="sxs-lookup"><span data-stu-id="546ea-140">http://msdn.microsoft.com/ws/2005/07/ws-security-policy/</span></span><br /><br /> <span data-ttu-id="546ea-141">OASIS WS-SX 技術委員会 http://www.oasis-open.org/archives/ws-sx/200512/msg00017.html に提出された正誤表によって修正済み</span><span class="sxs-lookup"><span data-stu-id="546ea-141">as amended by errata submitted to OASIS WS-SX Technical Committee http://www.oasis-open.org/archives/ws-sx/200512/msg00017.html</span></span>|  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="546ea-142"> Version 1 には、Web サービス セキュリティ構成の基礎として使用できる 17 個の認証モードが用意されています。</span><span class="sxs-lookup"><span data-stu-id="546ea-142">, version 1, provides 17 authentication modes that can be used as the basis for Web services security configuration.</span></span> <span data-ttu-id="546ea-143">各モードは、次のような一般的な展開要件について最適化されています。</span><span class="sxs-lookup"><span data-stu-id="546ea-143">Each mode is optimized for a common set of deployment requirements, such as:</span></span>  
  
-   <span data-ttu-id="546ea-144">クライアントとサービスの認証に使用する資格情報</span><span class="sxs-lookup"><span data-stu-id="546ea-144">Credentials used to authenticate client and service.</span></span>  
  
-   <span data-ttu-id="546ea-145">メッセージまたはトランスポートのセキュリティ保護機構</span><span class="sxs-lookup"><span data-stu-id="546ea-145">Message or transport security protection mechanisms.</span></span>  
  
-   <span data-ttu-id="546ea-146">メッセージ交換パターン</span><span class="sxs-lookup"><span data-stu-id="546ea-146">Message exchange patterns.</span></span>  
  
|<span data-ttu-id="546ea-147">認証モード</span><span class="sxs-lookup"><span data-stu-id="546ea-147">Authentication Mode</span></span>|<span data-ttu-id="546ea-148">クライアント認証</span><span class="sxs-lookup"><span data-stu-id="546ea-148">Client Authentication</span></span>|<span data-ttu-id="546ea-149">サーバー認証</span><span class="sxs-lookup"><span data-stu-id="546ea-149">Server Authentication</span></span>|<span data-ttu-id="546ea-150">モード</span><span class="sxs-lookup"><span data-stu-id="546ea-150">Mode</span></span>|  
|-------------------------|---------------------------|---------------------------|----------|  
|<span data-ttu-id="546ea-151">UserNameOverTransport</span><span class="sxs-lookup"><span data-stu-id="546ea-151">UserNameOverTransport</span></span>|<span data-ttu-id="546ea-152">ユーザー名/パスワード</span><span class="sxs-lookup"><span data-stu-id="546ea-152">User name/password</span></span>|<span data-ttu-id="546ea-153">X509</span><span class="sxs-lookup"><span data-stu-id="546ea-153">X509</span></span>|<span data-ttu-id="546ea-154">Transport</span><span class="sxs-lookup"><span data-stu-id="546ea-154">Transport</span></span>|  
|<span data-ttu-id="546ea-155">CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="546ea-155">CertificateOverTransport</span></span>|<span data-ttu-id="546ea-156">X509</span><span class="sxs-lookup"><span data-stu-id="546ea-156">X509</span></span>|<span data-ttu-id="546ea-157">X509</span><span class="sxs-lookup"><span data-stu-id="546ea-157">X509</span></span>|<span data-ttu-id="546ea-158">Transport</span><span class="sxs-lookup"><span data-stu-id="546ea-158">Transport</span></span>|  
|<span data-ttu-id="546ea-159">KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="546ea-159">KerberosOverTransport</span></span>|<span data-ttu-id="546ea-160">Windows</span><span class="sxs-lookup"><span data-stu-id="546ea-160">Windows</span></span>|<span data-ttu-id="546ea-161">X509</span><span class="sxs-lookup"><span data-stu-id="546ea-161">X509</span></span>|<span data-ttu-id="546ea-162">Transport</span><span class="sxs-lookup"><span data-stu-id="546ea-162">Transport</span></span>|  
|<span data-ttu-id="546ea-163">IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="546ea-163">IssuedTokenOverTransport</span></span>|<span data-ttu-id="546ea-164">フェデレーション</span><span class="sxs-lookup"><span data-stu-id="546ea-164">Federated</span></span>|<span data-ttu-id="546ea-165">X509</span><span class="sxs-lookup"><span data-stu-id="546ea-165">X509</span></span>|<span data-ttu-id="546ea-166">Transport</span><span class="sxs-lookup"><span data-stu-id="546ea-166">Transport</span></span>|  
|<span data-ttu-id="546ea-167">SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="546ea-167">SspiNegotiatedOverTransport</span></span>|<span data-ttu-id="546ea-168">Windows SSPI ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="546ea-168">Windows Sspi Negotiated</span></span>|<span data-ttu-id="546ea-169">Windows SSPI ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="546ea-169">Windows Sspi Negotiated</span></span>|<span data-ttu-id="546ea-170">Transport</span><span class="sxs-lookup"><span data-stu-id="546ea-170">Transport</span></span>|  
|<span data-ttu-id="546ea-171">AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="546ea-171">AnonymousForCertificate</span></span>|<span data-ttu-id="546ea-172">なし</span><span class="sxs-lookup"><span data-stu-id="546ea-172">None</span></span>|<span data-ttu-id="546ea-173">X509</span><span class="sxs-lookup"><span data-stu-id="546ea-173">X509</span></span>|<span data-ttu-id="546ea-174">メッセージ</span><span class="sxs-lookup"><span data-stu-id="546ea-174">Message</span></span>|  
|<span data-ttu-id="546ea-175">UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="546ea-175">UserNameForCertificate</span></span>|<span data-ttu-id="546ea-176">ユーザー名/パスワード</span><span class="sxs-lookup"><span data-stu-id="546ea-176">User name/password</span></span>|<span data-ttu-id="546ea-177">X509</span><span class="sxs-lookup"><span data-stu-id="546ea-177">X509</span></span>|<span data-ttu-id="546ea-178">メッセージ</span><span class="sxs-lookup"><span data-stu-id="546ea-178">Message</span></span>|  
|<span data-ttu-id="546ea-179">MutualCertificate</span><span class="sxs-lookup"><span data-stu-id="546ea-179">MutualCertificate</span></span>|<span data-ttu-id="546ea-180">X509</span><span class="sxs-lookup"><span data-stu-id="546ea-180">X509</span></span>|<span data-ttu-id="546ea-181">X509</span><span class="sxs-lookup"><span data-stu-id="546ea-181">X509</span></span>|<span data-ttu-id="546ea-182">メッセージ</span><span class="sxs-lookup"><span data-stu-id="546ea-182">Message</span></span>|  
|<span data-ttu-id="546ea-183">MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="546ea-183">MutualCertificateDuplex</span></span>|<span data-ttu-id="546ea-184">X509</span><span class="sxs-lookup"><span data-stu-id="546ea-184">X509</span></span>|<span data-ttu-id="546ea-185">X509</span><span class="sxs-lookup"><span data-stu-id="546ea-185">X509</span></span>|<span data-ttu-id="546ea-186">メッセージ</span><span class="sxs-lookup"><span data-stu-id="546ea-186">Message</span></span>|  
|<span data-ttu-id="546ea-187">IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="546ea-187">IssuedTokenForCertificate</span></span>|<span data-ttu-id="546ea-188">フェデレーション</span><span class="sxs-lookup"><span data-stu-id="546ea-188">Federated</span></span>|<span data-ttu-id="546ea-189">X509</span><span class="sxs-lookup"><span data-stu-id="546ea-189">X509</span></span>|<span data-ttu-id="546ea-190">メッセージ</span><span class="sxs-lookup"><span data-stu-id="546ea-190">Message</span></span>|  
|<span data-ttu-id="546ea-191">Kerberos</span><span class="sxs-lookup"><span data-stu-id="546ea-191">Kerberos</span></span>|<span data-ttu-id="546ea-192">Windows</span><span class="sxs-lookup"><span data-stu-id="546ea-192">Windows</span></span>|<span data-ttu-id="546ea-193">Windows</span><span class="sxs-lookup"><span data-stu-id="546ea-193">Windows</span></span>|<span data-ttu-id="546ea-194">メッセージ</span><span class="sxs-lookup"><span data-stu-id="546ea-194">Message</span></span>|  
|<span data-ttu-id="546ea-195">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="546ea-195">IssuedToken</span></span>|<span data-ttu-id="546ea-196">フェデレーション</span><span class="sxs-lookup"><span data-stu-id="546ea-196">Federated</span></span>|<span data-ttu-id="546ea-197">フェデレーション</span><span class="sxs-lookup"><span data-stu-id="546ea-197">Federated</span></span>|<span data-ttu-id="546ea-198">メッセージ</span><span class="sxs-lookup"><span data-stu-id="546ea-198">Message</span></span>|  
|<span data-ttu-id="546ea-199">SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="546ea-199">SspiNegotiated</span></span>|<span data-ttu-id="546ea-200">Windows SSPI ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="546ea-200">Windows Sspi Negotiated</span></span>|<span data-ttu-id="546ea-201">Windows SSPI ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="546ea-201">Windows Sspi Negotiated</span></span>|<span data-ttu-id="546ea-202">メッセージ</span><span class="sxs-lookup"><span data-stu-id="546ea-202">Message</span></span>|  
|<span data-ttu-id="546ea-203">AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="546ea-203">AnonymousForSslNegotiated</span></span>|<span data-ttu-id="546ea-204">なし</span><span class="sxs-lookup"><span data-stu-id="546ea-204">None</span></span>|<span data-ttu-id="546ea-205">X509、TLS ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="546ea-205">X509, TLS-Nego</span></span>|<span data-ttu-id="546ea-206">メッセージ</span><span class="sxs-lookup"><span data-stu-id="546ea-206">Message</span></span>|  
|<span data-ttu-id="546ea-207">UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="546ea-207">UserNameForSslNegotiated</span></span>|<span data-ttu-id="546ea-208">ユーザー名/パスワード</span><span class="sxs-lookup"><span data-stu-id="546ea-208">User name/password</span></span>|<span data-ttu-id="546ea-209">X509、TLS ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="546ea-209">X509, TLS-Nego</span></span>|<span data-ttu-id="546ea-210">メッセージ</span><span class="sxs-lookup"><span data-stu-id="546ea-210">Message</span></span>|  
|<span data-ttu-id="546ea-211">MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="546ea-211">MutualSslNegotiated</span></span>|<span data-ttu-id="546ea-212">X509</span><span class="sxs-lookup"><span data-stu-id="546ea-212">X509</span></span>|<span data-ttu-id="546ea-213">X509、TLS ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="546ea-213">X509, TLS-Nego</span></span>|<span data-ttu-id="546ea-214">メッセージ</span><span class="sxs-lookup"><span data-stu-id="546ea-214">Message</span></span>|  
|<span data-ttu-id="546ea-215">IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="546ea-215">IssuedTokenForSslNegotiated</span></span>|<span data-ttu-id="546ea-216">フェデレーション</span><span class="sxs-lookup"><span data-stu-id="546ea-216">Federated</span></span>|<span data-ttu-id="546ea-217">X509、TLS ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="546ea-217">X509, TLS-Nego</span></span>|<span data-ttu-id="546ea-218">メッセージ</span><span class="sxs-lookup"><span data-stu-id="546ea-218">Message</span></span>|  
  
 <span data-ttu-id="546ea-219">このような認証モードを使用するエンドポイントは、WS-SecurityPolicy (WS-SP) を使用してセキュリティ要件を表現できます。</span><span class="sxs-lookup"><span data-stu-id="546ea-219">Endpoints using such authentication modes can express their security requirements using WS-SecurityPolicy (WS-SP).</span></span> <span data-ttu-id="546ea-220">ここでは、各認証モードのセキュリティ ヘッダーとインフラストラクチャ メッセージの構造について説明します。また、ポリシーとメッセージの例も示します。</span><span class="sxs-lookup"><span data-stu-id="546ea-220">This document describes the structure of security header and infrastructure messages for each authentication mode and provides examples of policies and messages.</span></span>  
  
 <span data-ttu-id="546ea-221">アプリケーション間での複数のメッセージ交換を保護するために、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では WS-SecureConversation を使用してセキュリティで保護されたセッションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="546ea-221">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] leverages WS-SecureConversation to provide secure sessions support to protect multi-message exchanges between applications.</span></span>  <span data-ttu-id="546ea-222">実装の詳細については、後述の「セキュリティで保護されたセッション」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="546ea-222">See "Secure Sessions" below for implementation details.</span></span>  
  
 <span data-ttu-id="546ea-223">認証モードに加え、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、メッセージ セキュリティ ベースのほとんどの認証モードに適用される一般的な保護機構を制御するための設定 (署名と暗号化操作の順序、アルゴリズム スイート、キー派生、署名確認など) も用意されています。</span><span class="sxs-lookup"><span data-stu-id="546ea-223">In addition to authentication modes, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides settings to control common protection mechanisms that apply to most message security-based authentication modes, for example: order of signature versus encryption operations, algorithm suites, key derivation, and signature confirmation.</span></span>  
  
 <span data-ttu-id="546ea-224">このドキュメントでは、以下のプレフィックスと名前空間を使用します。</span><span class="sxs-lookup"><span data-stu-id="546ea-224">The following prefixes and namespaces are used in this document.</span></span>  
  
|<span data-ttu-id="546ea-225">プレフィックス</span><span class="sxs-lookup"><span data-stu-id="546ea-225">Prefix</span></span>|<span data-ttu-id="546ea-226">Namespace</span><span class="sxs-lookup"><span data-stu-id="546ea-226">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="546ea-227">s</span><span class="sxs-lookup"><span data-stu-id="546ea-227">s</span></span>|<span data-ttu-id="546ea-228">http://www.w3.org/2003/05/soap-envelope</span><span class="sxs-lookup"><span data-stu-id="546ea-228">http://www.w3.org/2003/05/soap-envelope</span></span>|  
|<span data-ttu-id="546ea-229">sp</span><span class="sxs-lookup"><span data-stu-id="546ea-229">sp</span></span>|<span data-ttu-id="546ea-230">http://schemas.xmlsoap.org/ws/2005/07/securitypolicy</span><span class="sxs-lookup"><span data-stu-id="546ea-230">http://schemas.xmlsoap.org/ws/2005/07/securitypolicy</span></span>|  
|<span data-ttu-id="546ea-231">a</span><span class="sxs-lookup"><span data-stu-id="546ea-231">a</span></span>|<span data-ttu-id="546ea-232">http://www.w3.org/2005/08/addressing</span><span class="sxs-lookup"><span data-stu-id="546ea-232">http://www.w3.org/2005/08/addressing</span></span>|  
|<span data-ttu-id="546ea-233">wsse</span><span class="sxs-lookup"><span data-stu-id="546ea-233">wsse</span></span>|<span data-ttu-id="546ea-234">未定 - OASIS WSS 1.0 の URI</span><span class="sxs-lookup"><span data-stu-id="546ea-234">TBD – OASIS WSS 1.0 URI</span></span>|  
|<span data-ttu-id="546ea-235">wsse11</span><span class="sxs-lookup"><span data-stu-id="546ea-235">wsse11</span></span>|<span data-ttu-id="546ea-236">未定 - OASIS WSS 1.1 の URI</span><span class="sxs-lookup"><span data-stu-id="546ea-236">TBD – OASIS WSS 1.1 URI</span></span>|  
|<span data-ttu-id="546ea-237">wsu</span><span class="sxs-lookup"><span data-stu-id="546ea-237">wsu</span></span>|<span data-ttu-id="546ea-238">未定 - OASIS WSS 1.0 Utility の URI</span><span class="sxs-lookup"><span data-stu-id="546ea-238">TBD – OASIS WSS 1.0 Utility URI</span></span>|  
|<span data-ttu-id="546ea-239">ds</span><span class="sxs-lookup"><span data-stu-id="546ea-239">ds</span></span>|<span data-ttu-id="546ea-240">未定 - W3C XMLDSig の URI</span><span class="sxs-lookup"><span data-stu-id="546ea-240">TBD – W3C XMLDSig URI</span></span>|  
|<span data-ttu-id="546ea-241">wst</span><span class="sxs-lookup"><span data-stu-id="546ea-241">wst</span></span>|<span data-ttu-id="546ea-242">未定 - WS-Trust 2005/02 の URI</span><span class="sxs-lookup"><span data-stu-id="546ea-242">TBD – WS-Trust 2005/02 URI</span></span>|  
|<span data-ttu-id="546ea-243">wssc</span><span class="sxs-lookup"><span data-stu-id="546ea-243">wssc</span></span>|<span data-ttu-id="546ea-244">未定 - WS-SecureConversation 2005/02 の URI</span><span class="sxs-lookup"><span data-stu-id="546ea-244">TBD – WS-SecureConversation 2005/02 URI</span></span>|  
|<span data-ttu-id="546ea-245">wsaw</span><span class="sxs-lookup"><span data-stu-id="546ea-245">wsaw</span></span>|<span data-ttu-id="546ea-246">未定 - WS-Addressing ポリシーの名前空間</span><span class="sxs-lookup"><span data-stu-id="546ea-246">TBD - WS-Addressing policy namespace</span></span>|  
|<span data-ttu-id="546ea-247">wsp</span><span class="sxs-lookup"><span data-stu-id="546ea-247">wsp</span></span>|<span data-ttu-id="546ea-248">http://schemas.xmlsoap.org/ws/2004/09/policy </span><span class="sxs-lookup"><span data-stu-id="546ea-248">http://schemas.xmlsoap.org/ws/2004/09/policy</span></span>|  
|<span data-ttu-id="546ea-249">mssp</span><span class="sxs-lookup"><span data-stu-id="546ea-249">mssp</span></span>|<span data-ttu-id="546ea-250">http://schemas.microsoft.com/ws/2005/07/securitypolicy</span><span class="sxs-lookup"><span data-stu-id="546ea-250">http://schemas.microsoft.com/ws/2005/07/securitypolicy</span></span>|  
  
## <a name="1-token-profiles"></a><span data-ttu-id="546ea-251">1.トークン プロファイル</span><span class="sxs-lookup"><span data-stu-id="546ea-251">1. Token Profiles</span></span>  
 <span data-ttu-id="546ea-252">Web サービス セキュリティ仕様では、資格情報をセキュリティ トークンとして表します。</span><span class="sxs-lookup"><span data-stu-id="546ea-252">Web Services Security specifications represent credential as security tokens.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="546ea-253"> では、以下のトークンの種類をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="546ea-253"> supports the following token types:</span></span>  
  
### <a name="11-usernametoken"></a><span data-ttu-id="546ea-254">1.1 UsernameToken</span><span class="sxs-lookup"><span data-stu-id="546ea-254">1.1 UsernameToken</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="546ea-255"> は、以下の制約で UsernameToken10 プロファイルおよび UsernameToken11 プロファイルに従います。</span><span class="sxs-lookup"><span data-stu-id="546ea-255"> follows UsernameToken10 and UsernameToken11 profiles with the following constraints:</span></span>  
  
 <span data-ttu-id="546ea-256">R1101 : UsernameToken\Password 要素の PasswordType 属性では、#PasswordText (既定値) を省略するか、指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="546ea-256">R1101 PasswordType attribute on UsernameToken\Password element MUST be either omitted or have value #PasswordText (default).</span></span>  
  
 <span data-ttu-id="546ea-257">機能拡張を使用すると、#PasswordDigest を実装できます。</span><span class="sxs-lookup"><span data-stu-id="546ea-257">One can implement the #PasswordDigest using extensibility.</span></span> <span data-ttu-id="546ea-258">#PasswordDigest は、十分に安全性の高いパスワード保護機構であると誤解されがちであることが報告されています。</span><span class="sxs-lookup"><span data-stu-id="546ea-258">It has been observed that #PasswordDigest was often mistaken to be a secure enough password protection mechanism.</span></span> <span data-ttu-id="546ea-259">しかし、#PasswordDigest は、UsernameToken の暗号化の代替として使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="546ea-259">But #PasswordDigest cannot serve as a substitute for encryption of the UsernameToken.</span></span> <span data-ttu-id="546ea-260">#PasswordDigest の第一の目的は、リプレイ攻撃から保護することです。</span><span class="sxs-lookup"><span data-stu-id="546ea-260">The primary goal of #PasswordDigest is protection against replay attacks.</span></span> <span data-ttu-id="546ea-261">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の各認証モードでは、メッセージ署名を使用することで、リプレイ攻撃の脅威が軽減されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-261">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] authentication modes, replay attack threats are mitigated by using message signatures.</span></span>  
  
 <span data-ttu-id="546ea-262">B1102 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、Nonce および UsernameToken の作成済みサブ要素を出力することはありません。</span><span class="sxs-lookup"><span data-stu-id="546ea-262">B1102 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] never emits Nonce and Created sub-elements of the UsernameToken.</span></span>  
  
 <span data-ttu-id="546ea-263">これらのサブ要素は、リプレイ検出を支援するためのものです。</span><span class="sxs-lookup"><span data-stu-id="546ea-263">These sub-elements are intended to help replay detection.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="546ea-264"> では、代わりにメッセージ署名を使用します。</span><span class="sxs-lookup"><span data-stu-id="546ea-264"> uses message signatures instead.</span></span>  
  
 <span data-ttu-id="546ea-265">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) では、パスワードからのキー派生機能が導入されています。</span><span class="sxs-lookup"><span data-stu-id="546ea-265">OASIS WSS SOAP Message Security UsernameToken Profile 1.1 (UsernameToken11) introduced key derivation from password feature.</span></span>  
  
 <span data-ttu-id="546ea-266">B1103 : UsernameToken のパスワードをキー派生に使用することはできません。したがって、暗号化操作では使用できません。</span><span class="sxs-lookup"><span data-stu-id="546ea-266">B1103 UsernameToken password MUST not be used for key derivation and therefore for cryptographic operations.</span></span>  
  
 <span data-ttu-id="546ea-267">理由 : パスワードは、一般に暗号化操作に使用するには脆弱すぎると見なされています。</span><span class="sxs-lookup"><span data-stu-id="546ea-267">Rationale: passwords are generally considered too weak to be used for cryptographic operations.</span></span>  
  
### <a name="12-x509-token"></a><span data-ttu-id="546ea-268">1.2 X509 トークン</span><span class="sxs-lookup"><span data-stu-id="546ea-268">1.2 X509 Token</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="546ea-269"> は、資格情報の種類として X509v3 証明書をサポートしており、以下の制約で X509TokenProfile1.0 と X509TokenProfile1.1 に従います。</span><span class="sxs-lookup"><span data-stu-id="546ea-269"> supports X509v3 certificates as a credential type and follows X509TokenProfile1.0 and X509TokenProfile1.1 with the following constraints:</span></span>  
  
 <span data-ttu-id="546ea-270">R1201 : BinarySecurityToken 要素に X509v3 証明書が含まれている場合、この要素の ValueType 属性の値は #X509v3 であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="546ea-270">R1201 The ValueType attribute on the BinarySecurityToken element must have value #X509v3 when it contains an X509v3 certificate.</span></span>  
  
 <span data-ttu-id="546ea-271">WSS X509 Token Profile 1.0 および 1.1 では、値の種類として #X509PKIPathv1 と #PKCS7 も定義されています。</span><span class="sxs-lookup"><span data-stu-id="546ea-271">WSS X509 Token Profile 1.0 and 1.1 define also #X509PKIPathv1 and #PKCS7 as value types.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="546ea-272"> では、これらの種類をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="546ea-272"> does not support these types.</span></span>  
  
 <span data-ttu-id="546ea-273">R1202 : X509 証明書に SubjectKeyIdentifier (SKI) 拡張が含まれている場合、トークンへの外部参照に wsse:KeyIdentifier を使用する必要があります。この場合、ValueType 属性に #X509SubjectKeyIdentifier を指定し、証明書の SKI 拡張の Base64 でエンコードされた値を含めます。</span><span class="sxs-lookup"><span data-stu-id="546ea-273">R1202 If a SubjectKeyIdentifier (SKI) extension is present in an X509 certificate, wsse:KeyIdentifier should be used for external references to the token, with the ValueType attribute as #X509SubjectKeyIdentifier and its content the base64-encoded value of certificate's SKI extension.</span></span>  
  
 <span data-ttu-id="546ea-274">SKI 参照は幅広く実装されており、相互運用性の高い外部参照型であることが証明されています。</span><span class="sxs-lookup"><span data-stu-id="546ea-274">SKI references are widely implemented and proven to be a highly interoperable external reference type.</span></span>  
  
 <span data-ttu-id="546ea-275">R1203 : X509 セキュリティ トークンへの外部参照では、ds:X509IssuerSerial を使用できません。</span><span class="sxs-lookup"><span data-stu-id="546ea-275">R1203 An external Reference to X509 Security Token SHOULD NOT use ds:X509IssuerSerial.</span></span>  
  
 <span data-ttu-id="546ea-276">R1204 : X509TokenProfile1.1 を使用している場合、X509 セキュリティ トークンへの外部参照では、WS-Security 1.1 で導入された拇印を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="546ea-276">R1204 If X509TokenProfile1.1 is in use, an external reference to X509 Security Token SHOULD use the thumbprint introduced by WS-Security 1.1.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="546ea-277"> は、X509IssuerSerial をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="546ea-277"> supports X509IssuerSerial.</span></span> <span data-ttu-id="546ea-278">ただし、X509IssuerSerial には相互運用性の問題があります。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、文字列を使用して X509IssuerSerial の 2 つの値を比較します。</span><span class="sxs-lookup"><span data-stu-id="546ea-278">However There are interoperability issues with X509IssuerSerial: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses a string to compare two values of X509IssuerSerial.</span></span> <span data-ttu-id="546ea-279">したがって、サブジェクト名の構成要素を並べ替えて、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスに証明書への参照を送信した場合、参照が見つからないことがあります。</span><span class="sxs-lookup"><span data-stu-id="546ea-279">Therefore if one reorders components of the Subject Name and sends to an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service a reference to a certificate, it may not be found.</span></span>  
  
### <a name="13-kerberos-token"></a><span data-ttu-id="546ea-280">1.3 Kerberos トークン</span><span class="sxs-lookup"><span data-stu-id="546ea-280">1.3 Kerberos Token</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="546ea-281"> は、Windows 認証のために、以下の制約で KerberosTokenProfile1.1 をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="546ea-281"> supports KerberosTokenProfile1.1 for the purpose of Windows authentication with the following constraints:</span></span>  
  
 <span data-ttu-id="546ea-282">R1301 : GSS_API と Kerberos 仕様で定義されているように、Kerberos トークンは GSS によってラップされた Kerberos v4 AP_REQ の値を伝達する必要があります。また、値 #GSS_Kerberosv5_AP_REQ が指定された ValueType 属性を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="546ea-282">R1301 A Kerberos Token must carry the value of a GSS wrapped Kerberos v4 AP_REQ as defined in GSS_API and the Kerberos specification, and must have the ValueType attribute with the value #GSS_Kerberosv5_AP_REQ.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="546ea-283"> は、ベア AP-REQ ではなく、GSS によってラップされた Kerberos AP-REQ を使用します。</span><span class="sxs-lookup"><span data-stu-id="546ea-283"> uses GSS wrapped Kerberos AP-REQ, not a bare AP-REQ.</span></span> <span data-ttu-id="546ea-284">これは、セキュリティのベスト プラクティスです。</span><span class="sxs-lookup"><span data-stu-id="546ea-284">This is a security best practice.</span></span>  
  
### <a name="14-saml-v11-token"></a><span data-ttu-id="546ea-285">1.4 SAML v1.1 トークン</span><span class="sxs-lookup"><span data-stu-id="546ea-285">1.4 SAML v1.1 Token</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="546ea-286"> は、SAML v1.1 トークンの WSS SAML Token Profile 1.0 および 1.1 をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="546ea-286"> supports WSS SAML Token profiles 1.0 and 1.1 for SAML v1.1 tokens.</span></span> <span data-ttu-id="546ea-287">SAML トークンの形式のその他のバージョンも実装できます。</span><span class="sxs-lookup"><span data-stu-id="546ea-287">It is possible to implement other versions of SAML token formats.</span></span>  
  
### <a name="15-security-context-token"></a><span data-ttu-id="546ea-288">1.5 セキュリティ コンテキスト トークン</span><span class="sxs-lookup"><span data-stu-id="546ea-288">1.5 Security Context Token</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="546ea-289"> は、WS-SecureCoversation に導入されたセキュリティ コンテキスト トークン (SCT) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="546ea-289"> supports the Security Context Token (SCT) introduced in WS-SecureCoversation.</span></span> <span data-ttu-id="546ea-290">SCT は、SecureConversation と、後述する TLS および SSPI の各バイナリ ネゴシエーション プロトコルで確立されたセキュリティ コンテキストを表すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-290">SCT is used to represent a security context established in SecureConversation as well as the binary negotiation protocols TLS and SSPI, described below.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="546ea-291">2.一般的なメッセージ セキュリティ パラメーター</span><span class="sxs-lookup"><span data-stu-id="546ea-291">2. Common Message Security Parameters</span></span>  
  
### <a name="21-timestamp"></a><span data-ttu-id="546ea-292">2.1 タイムスタンプ</span><span class="sxs-lookup"><span data-stu-id="546ea-292">2.1 TimeStamp</span></span>  
 <span data-ttu-id="546ea-293">タイムスタンプの有無は、<xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> クラスの <xref:System.ServiceModel.Channels.SecurityBindingElement> プロパティを使用して制御します。</span><span class="sxs-lookup"><span data-stu-id="546ea-293">Timestamp presence is controlled using the <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> property of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="546ea-294"> は、常に wsse:Created および wsse:Expires の各フィールドと共に wsse:TimeStamp をシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="546ea-294"> always serializes wsse:TimeStamp with wsse:Created and wsse:Expires fields.</span></span> <span data-ttu-id="546ea-295">署名を使用する場合、wsse:TimeStamp は必ず署名されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-295">The wsse:TimeStamp is always signed when signing is used.</span></span>  
  
### <a name="22-protection-order"></a><span data-ttu-id="546ea-296">2.2 保護の順序</span><span class="sxs-lookup"><span data-stu-id="546ea-296">2.2 Protection Order</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="546ea-297"> は、メッセージ保護の順序として、"暗号化前に署名" と "署名前に暗号化" をサポートしています (Security Policy 1.1)。</span><span class="sxs-lookup"><span data-stu-id="546ea-297"> supports the message protection order "Sign Before Encrypt" and "Encrypt Before Sign" (Security Policy 1.1).</span></span> <span data-ttu-id="546ea-298">WS-Security 1.1 の SignatureConfirmation 機構を使用していない場合、"署名前に暗号化" を使用して保護されたメッセージを開くと、置き換え攻撃への署名が行われます。また、暗号化された内容に署名すると監査が困難になります。これらの理由から、"暗号化前に署名" を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="546ea-298">"Sign Before Encrypt" is recommended for reasons including: messages protected with Encrypt Before Sign are open to signature substitution attacks unless the WS-Security 1.1 SignatureConfirmation mechanism is used, and a signature over encrypted content makes auditing harder.</span></span>  
  
### <a name="23-signature-protection"></a><span data-ttu-id="546ea-299">2.3 署名の保護</span><span class="sxs-lookup"><span data-stu-id="546ea-299">2.3 Signature Protection</span></span>  
 <span data-ttu-id="546ea-300">"署名前に暗号化" を使用する場合、暗号化された内容や署名キー (特に、脆弱なキー マテリアルでカスタム トークンを使用する場合) を推測するブルート フォース攻撃を防ぐために、署名を保護することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="546ea-300">When Encrypt Before Sign is used, it is recommended to protect the signature to prevent brute force attacks for guessing the encrypted content or the signing key (especially when a custom token is used with weak key material).</span></span>  
  
### <a name="24-algorithm-suite"></a><span data-ttu-id="546ea-301">2.4 アルゴリズム スイート</span><span class="sxs-lookup"><span data-stu-id="546ea-301">2.4 Algorithm Suite</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="546ea-302"> は、Security Policy 1.1 に記載されたすべてのアルゴリズム スイートをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="546ea-302"> supports all algorithm suites listed in Security Policy 1.1.</span></span>  
  
### <a name="25-key-derivation"></a><span data-ttu-id="546ea-303">2.5 キー派生</span><span class="sxs-lookup"><span data-stu-id="546ea-303">2.5 Key Derivation</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="546ea-304"> では、WS-SecureConversation に記載された "対称キーのキー派生" を使用します。</span><span class="sxs-lookup"><span data-stu-id="546ea-304"> uses "Key Derivation for symmetric keys" as described in WS-SecureConversation.</span></span>  
  
### <a name="26-signature-confirmation"></a><span data-ttu-id="546ea-305">2.6 署名確認</span><span class="sxs-lookup"><span data-stu-id="546ea-305">2.6 Signature Confirmation</span></span>  
 <span data-ttu-id="546ea-306">署名確認によって "man-in-the-middle" 攻撃から保護することで、署名セットを保護できます。</span><span class="sxs-lookup"><span data-stu-id="546ea-306">Signature confirmation can be as protection from middle man attacks to protect the set of signatures.</span></span>  
  
### <a name="27-security-header-layout"></a><span data-ttu-id="546ea-307">2.7 セキュリティ ヘッダーのレイアウト</span><span class="sxs-lookup"><span data-stu-id="546ea-307">2.7 Security Header Layout</span></span>  
 <span data-ttu-id="546ea-308">各認証モードでは、セキュリティ ヘッダーの特定のレイアウトが使用されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-308">Each authentication mode describes a certain layout for the security header.</span></span> <span data-ttu-id="546ea-309">セキュリティ ヘッダー内の要素は、部分的に順序付けられています。</span><span class="sxs-lookup"><span data-stu-id="546ea-309">Elements within the security header are semi-ordered.</span></span> <span data-ttu-id="546ea-310">セキュリティ ヘッダーの子要素の順序を定義するために、WS-Security Policy では、以下のセキュリティ ヘッダー レイアウト モードが定義されています。</span><span class="sxs-lookup"><span data-stu-id="546ea-310">To define the order of security header child elements, WS-Security Policy defines the following security header layout modes:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="546ea-311">Strict</span><span class="sxs-lookup"><span data-stu-id="546ea-311">Strict</span></span>|<span data-ttu-id="546ea-312">"使用前に宣言する" という一般的原則に基づき、Security Policy のセクション 7.7.1 に記載された番号付きレイアウト ルールに従って、項目がセキュリティ ヘッダーに追加されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-312">Items are added to the security header following the numbered layout rules described in Security Policy section 7.7.1 according to a general principle of "declare before use".</span></span>|  
|<span data-ttu-id="546ea-313">Lax</span><span class="sxs-lookup"><span data-stu-id="546ea-313">Lax</span></span>|<span data-ttu-id="546ea-314">WSS: SOAP Message Security に準拠した任意の順序で、項目がセキュリティ ヘッダーに追加されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-314">Items are added to the security header in any order that conforms to WSS: SOAP Message Security.</span></span>|  
|<span data-ttu-id="546ea-315">LaxTimestampFirst</span><span class="sxs-lookup"><span data-stu-id="546ea-315">LaxTimestampFirst</span></span>|<span data-ttu-id="546ea-316">セキュリティ ヘッダー内の最初の項目が wsse:Timestamp でなければならないという点を除き、Lax と同じです。</span><span class="sxs-lookup"><span data-stu-id="546ea-316">Same as Lax except that the first item in the security header must be a wsse:Timestamp</span></span>|  
|<span data-ttu-id="546ea-317">LaxTimestampLast</span><span class="sxs-lookup"><span data-stu-id="546ea-317">LaxTimestampLast</span></span>|<span data-ttu-id="546ea-318">セキュリティ ヘッダー内の最後の項目が wsse:Timestamp でなければならないという点を除き、Lax と同じです。</span><span class="sxs-lookup"><span data-stu-id="546ea-318">Same as lax except that the last item in the security header must be a wsse:Timestamp</span></span>|  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="546ea-319"> は、セキュリティ ヘッダーの 4 つのレイアウト モードをすべてサポートしています。</span><span class="sxs-lookup"><span data-stu-id="546ea-319"> supports all four modes for security header layout.</span></span> <span data-ttu-id="546ea-320">後ほど示す各認証モードのセキュリティ ヘッダーの構造とメッセージの例では、"Strict" モードに従っています。</span><span class="sxs-lookup"><span data-stu-id="546ea-320">Security header structure and message examples for authentication modes below follow the "Strict" mode.</span></span>  
  
## <a name="2-common-message-security-parameters"></a><span data-ttu-id="546ea-321">2.一般的なメッセージ セキュリティ パラメーター</span><span class="sxs-lookup"><span data-stu-id="546ea-321">2. Common Message Security Parameters</span></span>  
 <span data-ttu-id="546ea-322">このセクションでは、各認証モードのポリシーの例、およびクライアントとサービスによって交換されるメッセージのセキュリティ ヘッダーの構造を示す例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="546ea-322">This section provides example policies for each authentication mode along with examples showing security header structure in messages exchanged by client and service.</span></span>  
  
### <a name="61-transport-protection"></a><span data-ttu-id="546ea-323">6.1 トランスポートの保護</span><span class="sxs-lookup"><span data-stu-id="546ea-323">6.1 Transport Protection</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="546ea-324"> に用意された UserNameOverTransport、CertificateOverTransport、KerberosOverTransport、IssuedTokenOverTransport、および SspiNegotiatedOverTransport の 5 つの認証モードでは、セキュリティで保護されたトランスポートを使用してメッセージを保護します。</span><span class="sxs-lookup"><span data-stu-id="546ea-324"> provides five authentication modes that use secure transport to protect messages; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport and SspiNegotiatedOverTransport.</span></span>  
  
 <span data-ttu-id="546ea-325">これらの認証モードは、SecurityPolicy に記載されたトランスポート バインディングを使用して構築されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-325">These authentication modes are constructed using the transport binding described in SecurityPolicy.</span></span> <span data-ttu-id="546ea-326">UserNameOverTransport 認証モードの場合、UsernameToken は署名付きサポート トークンです。</span><span class="sxs-lookup"><span data-stu-id="546ea-326">For the UserNameOverTransport authentication mode the UsernameToken is a signed supporting token.</span></span> <span data-ttu-id="546ea-327">その他の認証モードでは、トークンは署名付き保証トークンとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-327">For the other authentication modes the token appears as a signed endorsing token.</span></span> <span data-ttu-id="546ea-328">SecurityPolicy の Appendix C.1.2 および C.1.3 には、セキュリティ ヘッダーのレイアウトの詳細が記載されています。</span><span class="sxs-lookup"><span data-stu-id="546ea-328">Appendix C.1.2 and C.1.3 of SecurityPolicy describe the security header layout in detail.</span></span> <span data-ttu-id="546ea-329">以降のセキュリティ ヘッダーの例は、指定の認証モードの Strict レイアウトを示しています。</span><span class="sxs-lookup"><span data-stu-id="546ea-329">The following example security headers show the Strict layout for a given authentication mode.</span></span>  
  
 <span data-ttu-id="546ea-330">すべてのケースで、トークンの "派生キー" プロパティの値は "false" です。</span><span class="sxs-lookup"><span data-stu-id="546ea-330">The value of the "Derived Keys" property for the tokens in all cases is "false".</span></span>  
  
 <span data-ttu-id="546ea-331">トランスポート バインディングの各プロパティの値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="546ea-331">The values of the various properties of the transport binding are as follows:</span></span>  
  
 <span data-ttu-id="546ea-332">タイムスタンプ : true</span><span class="sxs-lookup"><span data-stu-id="546ea-332">Timestamp: true</span></span>  
  
 <span data-ttu-id="546ea-333">セキュリティ ヘッダーのレイアウト : Strict</span><span class="sxs-lookup"><span data-stu-id="546ea-333">Security Header Layout: Strict</span></span>  
  
 <span data-ttu-id="546ea-334">アルゴリズム スイート : Basic256</span><span class="sxs-lookup"><span data-stu-id="546ea-334">Algorithm Suite: Basic256</span></span>  
  
#### <a name="611-usernameovertransport"></a><span data-ttu-id="546ea-335">6.1.1 UsernameOverTransport</span><span class="sxs-lookup"><span data-stu-id="546ea-335">6.1.1 UsernameOverTransport</span></span>  
 <span data-ttu-id="546ea-336">この認証モードでは、クライアントはユーザー名トークンを使用して認証を行います。ユーザー名トークンは、イニシエーターから受信者に必ず送信される署名付きサポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-336">With this authentication mode, the client authenticates with a Username Token which appears at the SOAP layer as a signed supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="546ea-337">サービスはトランスポート層で X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-337">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="546ea-338">使用するバインディングは、トランスポート バインディングです。</span><span class="sxs-lookup"><span data-stu-id="546ea-338">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="546ea-339">ポリシー</span><span class="sxs-lookup"><span data-stu-id="546ea-339">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='UsernameOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:SignedSupportingTokens >  
        <wsp:Policy>  
          <sp:UsernameToken   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy>  
              <sp:WssUsernameToken10 />   
            </wsp:Policy>  
          </sp:UsernameToken>  
        </wsp:Policy>  
      </sp:SignedSupportingTokens>  
      <sp:Wss11 >  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10 >  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="546ea-340">セキュリティ ヘッダーのレイアウト</span><span class="sxs-lookup"><span data-stu-id="546ea-340">Security Header Layout</span></span>  
  
 <span data-ttu-id="546ea-341">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-341">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:UsernameToken ... >  
  ...  
  </wsse:UsernameToken>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-342">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-342">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a><span data-ttu-id="546ea-343">6.1.2 CertificateOverTransport</span><span class="sxs-lookup"><span data-stu-id="546ea-343">6.1.2 CertificateOverTransport</span></span>  
 <span data-ttu-id="546ea-344">この認証モードでは、クライアントは X.509 証明書を使用して認証を行います。X.509 証明書は、イニシエーターから受信者に必ず送信される保証サポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-344">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="546ea-345">サービスはトランスポート層で X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-345">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="546ea-346">使用するバインディングは、トランスポート バインディングです。</span><span class="sxs-lookup"><span data-stu-id="546ea-346">The binding used is a transport binding.</span></span>  
  
 <span data-ttu-id="546ea-347">ポリシー</span><span class="sxs-lookup"><span data-stu-id="546ea-347">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CertificateOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding xmlns:sp='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy' >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
             <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy>  
              <sp:RequireThumbprintReference />   
              <sp:WssX509V3Token10 />   
            </wsp:Policy>  
          </sp:X509Token>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="546ea-348">セキュリティ ヘッダーのレイアウト</span><span class="sxs-lookup"><span data-stu-id="546ea-348">Security Header Layout</span></span>  
  
 <span data-ttu-id="546ea-349">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-349">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wse:Timestamp u:Id="_0">  
  ...  
  </wse:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-350">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-350">Response</span></span>  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a><span data-ttu-id="546ea-351">6.1.3 IssuedTokenOverTransport</span><span class="sxs-lookup"><span data-stu-id="546ea-351">6.1.3 IssuedTokenOverTransport</span></span>  
 <span data-ttu-id="546ea-352">この認証モードでは、クライアントはサービスに対する認証を行わず、セキュリティ トークン サービス (STS) により発行されたトークンを示すことで、共有キーの有無を示します。</span><span class="sxs-lookup"><span data-stu-id="546ea-352">With this authentication mode the client does not authenticate to the service, as such, but rather presents a token issued by a Security Token Service (STS) and proves knowledge of a shared key.</span></span> <span data-ttu-id="546ea-353">発行されたトークンは、イニシエーターから受信者に必ず送信される保証サポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-353">The issued token appears at the SOAP layer as an endorsing supporting token that is always sent from the initiator to the recipient.</span></span> <span data-ttu-id="546ea-354">サービスはトランスポート層で X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-354">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="546ea-355">バインディングはトランスポート バインディングです。</span><span class="sxs-lookup"><span data-stu-id="546ea-355">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="546ea-356">ポリシー</span><span class="sxs-lookup"><span data-stu-id="546ea-356">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='IssuedTokenOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:IssuedToken   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <sp:RequestSecurityTokenTemplate>  
              <wst:KeyType>  
              http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
              </wst:KeyType>   
            </sp:RequestSecurityTokenTemplate>  
            <wsp:Policy>  
              <sp:RequireInternalReference />   
            </wsp:Policy>  
          </sp:IssuedToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="546ea-357">セキュリティ ヘッダーのレイアウト</span><span class="sxs-lookup"><span data-stu-id="546ea-357">Security Header Layout</span></span>  
  
 <span data-ttu-id="546ea-358">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-358">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion ...>  
  ...  
  </saml:Assertion>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-359">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-359">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a><span data-ttu-id="546ea-360">6.1.4 KerberosOverTransport</span><span class="sxs-lookup"><span data-stu-id="546ea-360">6.1.4 KerberosOverTransport</span></span>  
 <span data-ttu-id="546ea-361">この認証モードを使用すると、クライアントは Kerberos チケットを使用してサービスに対する認証を行います。</span><span class="sxs-lookup"><span data-stu-id="546ea-361">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="546ea-362">Kerberos トークンは、保証サポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-362">The Kerberos token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="546ea-363">サービスはトランスポート層で X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-363">The service is authenticated using an X.509 certificate at the transport layer.</span></span> <span data-ttu-id="546ea-364">バインディングはトランスポート バインディングです。</span><span class="sxs-lookup"><span data-stu-id="546ea-364">The binding is a transport binding.</span></span>  
  
 <span data-ttu-id="546ea-365">ポリシー</span><span class="sxs-lookup"><span data-stu-id="546ea-365">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='KerberosOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding>  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic128 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:KerberosToken  
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Once' >  
            <wsp:Policy>  
              <sp:WssGssKerberosV5ApReqToken11 />   
            </wsp:Policy>  
          </sp:KerberosToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="546ea-366">セキュリティ ヘッダーのレイアウト</span><span class="sxs-lookup"><span data-stu-id="546ea-366">Security Header Layout</span></span>  
  
 <span data-ttu-id="546ea-367">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-367">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken ValueType="...#GSS_Kerberosv5_AP_REQ">  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-368">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-368">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a><span data-ttu-id="546ea-369">6.1.5 SspiNegotiatedOverTransport</span><span class="sxs-lookup"><span data-stu-id="546ea-369">6.1.5 SspiNegotiatedOverTransport</span></span>  
 <span data-ttu-id="546ea-370">このモードでは、ネゴシエーション プロトコルを使用して、クライアントとサーバーの認証を行います。</span><span class="sxs-lookup"><span data-stu-id="546ea-370">With this mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="546ea-371">Kerberos を使用できる場合は Kerberos が使用され、それ以外の場合は NTLM が使用されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-371">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="546ea-372">発行された SCT は、イニシエーターから受信者に必ず送信される保証サポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-372">The resulting SCT appears at the SOAP layer as an endorsing supporting token that is always sent from initiator to recipient.</span></span> <span data-ttu-id="546ea-373">サービスは、トランスポート層で X.509 証明書により追加的に認証されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-373">The service is additionally authenticated at the transport layer by an X.509 certificate.</span></span> <span data-ttu-id="546ea-374">使用するバインディングは、トランスポート バインディングです。</span><span class="sxs-lookup"><span data-stu-id="546ea-374">The binding used is a transport binding.</span></span> <span data-ttu-id="546ea-375">"SPNEGO" (ネゴシエーション) には、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が WS-Trust で SSPI バイナリ ネゴシエーション プロトコルを使用する方法が記述されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-375">"SPNEGO" (negotiation) describes how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses SSPI binary negotiation protocol with WS-Trust.</span></span> <span data-ttu-id="546ea-376">このセクションで示すセキュリティ ヘッダーの例は、SPNEGO ハンドシェイクによって SCT が確立された後の状態を示しています。</span><span class="sxs-lookup"><span data-stu-id="546ea-376">Security header examples in this section are after the SCT has been established through the SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="546ea-377">ポリシー</span><span class="sxs-lookup"><span data-stu-id="546ea-377">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SspiNegotiatedOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding>  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:SpnegoContextToken   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy />   
          </sp:SpnegoContextToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples"></a><span data-ttu-id="546ea-378">セキュリティ ヘッダーの例</span><span class="sxs-lookup"><span data-stu-id="546ea-378">Security Header Examples</span></span>  
 <span data-ttu-id="546ea-379">WS-Trust バイナリ ネゴシエーションを使用して、SPNEGO ハンドシェイクによってセキュリティ コンテキスト トークンが確立されると、アプリケーション メッセージのセキュリティ ヘッダーは、次のような構造になります。</span><span class="sxs-lookup"><span data-stu-id="546ea-379">Once the Security Context Token is established through SPNEGO handshake using WS-Trust Binary Negotiation, the application messages have security headers with the following structure.</span></span>  
  
 <span data-ttu-id="546ea-380">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-380">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:SecurityContextToken u:Id="uuid-2202746a-7725-453d-8747-809cb718dab0-29" >  
  ...  
  </wssc:SecurityContextToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-381">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-381">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a><span data-ttu-id="546ea-382">6.2 X.509 証明書を使用したサービス認証</span><span class="sxs-lookup"><span data-stu-id="546ea-382">6.2 Using X.509 Certificates for Service Authentication</span></span>  
 <span data-ttu-id="546ea-383">このセクションでは、MutualCertificate WSS1.0、Mutual CertificateDuplex、MutualCertificate WSS1.1、AnonymousForCertificate、UserNameForCertificate、および IssuedTokenForCertificate の各認証モードについて説明します。</span><span class="sxs-lookup"><span data-stu-id="546ea-383">This section describes the following authentication modes: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate and IssuedTokenForCertificate.</span></span>  
  
#### <a name="621-mutualcertificate-wss10"></a><span data-ttu-id="546ea-384">6.2.1 MutualCertificate WSS1.0</span><span class="sxs-lookup"><span data-stu-id="546ea-384">6.2.1 MutualCertificate WSS1.0</span></span>  
 <span data-ttu-id="546ea-385">この認証モードでは、クライアントは X.509 証明書を使用して認証を行います。X.509 証明書は、イニシエーター トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-385">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="546ea-386">また、サービスは X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-386">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="546ea-387">使用するバインディングは、次のプロパティ値が設定された非対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="546ea-387">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="546ea-388">イニシエーター トークン : インクルード モードが .../IncludeToken/AlwaysToRecipient に設定されたクライアントの X.509 証明書</span><span class="sxs-lookup"><span data-stu-id="546ea-388">Initiator Token: the client’s X.509 certificate, with inclusion mode set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="546ea-389">受信者トークン : インクルード モードが …/IncludeToken/Never に設定されたサーバーの X.509 証明書</span><span class="sxs-lookup"><span data-stu-id="546ea-389">Recipient Token: Server’s X.509 Certificate, with inclusion mode is set …/IncludeToken/Never</span></span>  
  
 <span data-ttu-id="546ea-390">トークンの保護 : False</span><span class="sxs-lookup"><span data-stu-id="546ea-390">Token Protection: False</span></span>  
  
 <span data-ttu-id="546ea-391">ヘッダーと本文全体の署名 : True</span><span class="sxs-lookup"><span data-stu-id="546ea-391">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="546ea-392">保護の順序 : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="546ea-392">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="546ea-393">署名の暗号化 : True</span><span class="sxs-lookup"><span data-stu-id="546ea-393">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="546ea-394">ポリシー</span><span class="sxs-lookup"><span data-stu-id="546ea-394">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='MutualCertificate_WSS10_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:AsymmetricBinding>  
        <wsp:Policy>  
          <sp:InitiatorToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:InitiatorToken>  
          <sp:RecipientToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Never' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:RecipientToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:AsymmetricBinding>  
      <sp:Wss10>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
        </wsp:Policy>  
      </sp:Wss10>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="546ea-395">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="546ea-395">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="546ea-396">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-396">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-397">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-397">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-398">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="546ea-398">Security Header Examples: EncryptBeforeSign</span></span>  
  
 <span data-ttu-id="546ea-399">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-399">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-400">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-400">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="622-mutualcertificateduplex"></a><span data-ttu-id="546ea-401">6.2.2 MutualCertificateDuplex</span><span class="sxs-lookup"><span data-stu-id="546ea-401">6.2.2 MutualCertificateDuplex</span></span>  
 <span data-ttu-id="546ea-402">この認証モードでは、クライアントは X.509 証明書を使用して認証を行います。X.509 証明書は、イニシエーター トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-402">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as the initiator token.</span></span> <span data-ttu-id="546ea-403">また、サービスは X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-403">The service is also authenticated using an X.509 certificate.</span></span>  
  
 <span data-ttu-id="546ea-404">使用するバインディングは、次のプロパティ値が設定された非対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="546ea-404">The binding used is an asymmetric binding with the following property values:</span></span>  
  
 <span data-ttu-id="546ea-405">イニシエーター トークン : インクルード モードが .../IncludeToken/AlwaysToRecipient に設定されたクライアントの X.509 証明書</span><span class="sxs-lookup"><span data-stu-id="546ea-405">Initiator Token: Client’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToRecipient</span></span>  
  
 <span data-ttu-id="546ea-406">受信者トークン : インクルード モードが .../IncludeToken/AlwaysToInitiator に設定されたサーバーの X509 証明書</span><span class="sxs-lookup"><span data-stu-id="546ea-406">Recipient Token: Server’s X509 Certificate, inclusion mode is set to …/IncludeToken/AlwaysToInitiator</span></span>  
  
 <span data-ttu-id="546ea-407">トークンの保護 : False</span><span class="sxs-lookup"><span data-stu-id="546ea-407">Token Protection: False</span></span>  
  
 <span data-ttu-id="546ea-408">ヘッダーと本文全体の署名 : True</span><span class="sxs-lookup"><span data-stu-id="546ea-408">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="546ea-409">保護の順序 : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="546ea-409">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="546ea-410">署名の暗号化 : True</span><span class="sxs-lookup"><span data-stu-id="546ea-410">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="546ea-411">ポリシー</span><span class="sxs-lookup"><span data-stu-id="546ea-411">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='MutualCertificateDuplex_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:AsymmetricBinding>  
        <wsp:Policy>  
          <sp:InitiatorToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:InitiatorToken>  
          <sp:RecipientToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToInitiator' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:RecipientToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:AsymmetricBinding>  
      <sp:Wss10>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
        </wsp:Policy>  
      </sp:Wss10>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="546ea-412">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="546ea-412">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="546ea-413">要求と応答</span><span class="sxs-lookup"><span data-stu-id="546ea-413">Request and Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="546ea-414">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="546ea-414">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="546ea-415">要求と応答</span><span class="sxs-lookup"><span data-stu-id="546ea-415">Request and Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a><span data-ttu-id="546ea-416">6.2.3 X.509 サービス認証での SymmetricBinding の使用</span><span class="sxs-lookup"><span data-stu-id="546ea-416">6.2.3 Using SymmetricBinding with X.509 Service Authentication</span></span>  
 <span data-ttu-id="546ea-417">"WSS10" では、X509 トークンを使用するシナリオのサポートが制限されていました。</span><span class="sxs-lookup"><span data-stu-id="546ea-417">"WSS10" provided limited support for scenarios with X509 tokens.</span></span> <span data-ttu-id="546ea-418">たとえば、サービスの X509 トークンだけを使用して、メッセージの署名と暗号化を保護することはできませんでした。</span><span class="sxs-lookup"><span data-stu-id="546ea-418">For example, there was no way to provide signature and encryption protection for messages using only service X509 token.</span></span> <span data-ttu-id="546ea-419">"WSS11" では、EncryptedKey を共通鍵トークンとして使用する方法が導入されています。</span><span class="sxs-lookup"><span data-stu-id="546ea-419">"WSS11" introduced the usage of EncryptedKey as a symmetric token.</span></span> <span data-ttu-id="546ea-420">これにより、サービスの X.509 証明書の暗号化された一時キーを使用して、要求メッセージと応答メッセージの両方を保護できるようになります。</span><span class="sxs-lookup"><span data-stu-id="546ea-420">Now a temporary key encrypted for the service's X.509 certificate could be used for both request and response messages protection.</span></span> <span data-ttu-id="546ea-421">セクション 6.4 で説明する認証モードでは、このパターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="546ea-421">The authentication modes described in the section 6.4 below use this pattern.</span></span>  
  
 <span data-ttu-id="546ea-422">WS-SecurityPolicy には、サービスの X509 トークンを保護トークンとして使用して SymmetricBinding を使用するこのパターンが記載されています。</span><span class="sxs-lookup"><span data-stu-id="546ea-422">WS-SecurityPolicy describes this pattern using SymmetricBinding with Service X509 token as the protection token.</span></span>  
  
 <span data-ttu-id="546ea-423">AnonymousForCertificate、UsernameForCertificate、MutualCertificate WSS11、および IssuedTokenForCertificate の各認証モードはすべて、以下のプロパティ値が設定された sp:SymmetricBinding の同様のインスタンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="546ea-423">Authentication modes AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 and IssuedTokenForCertificate all use a similar instance of sp:SymmetricBinding with the following property values:</span></span>  
  
 <span data-ttu-id="546ea-424">保護トークン: インクルード モードが .../IncludeToken/Never に設定されたサーバーの X509 証明書</span><span class="sxs-lookup"><span data-stu-id="546ea-424">Protection Token: Server’s X509 Certificate, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="546ea-425">トークンの保護 : False</span><span class="sxs-lookup"><span data-stu-id="546ea-425">Token Protection: False</span></span>  
  
 <span data-ttu-id="546ea-426">ヘッダーと本文全体の署名 : True</span><span class="sxs-lookup"><span data-stu-id="546ea-426">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="546ea-427">保護の順序 : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="546ea-427">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="546ea-428">署名の暗号化 : True</span><span class="sxs-lookup"><span data-stu-id="546ea-428">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="546ea-429">前述の各認証モードは、使用するサポート トークンだけが異なります。</span><span class="sxs-lookup"><span data-stu-id="546ea-429">The above authentication modes only differ by the supporting tokens they use.</span></span> <span data-ttu-id="546ea-430">AnonymousForCertificate はサポート トークンをまったく使用せず、MutualCertificate WSS 1.1 は保証サポート トークンとしてクライアントの X509 証明書を使用します。また、UserNameForCertificate は署名付きサポート トークンとしてユーザー名トークンを使用し、IssuedTokenForCertificate は保証サポート トークンとして発行済みトークンを使用します。</span><span class="sxs-lookup"><span data-stu-id="546ea-430">AnonymousForCertificate does not have any supporting tokens, MutualCertificate WSS 1.1 has the client’s X509 certificate as an endorsing supporting tokens, UserNameForCertificate has a UserName Token as a signed supporting token and IssuedTokenForCertificate has the issued token as an endorsing supporting token.</span></span>  
  
 <span data-ttu-id="546ea-431">ポリシー</span><span class="sxs-lookup"><span data-stu-id="546ea-431">Policy</span></span>  
  
 <span data-ttu-id="546ea-432">対称バインディング</span><span class="sxs-lookup"><span data-stu-id="546ea-432">Symmetric Binding</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SymmetricCert_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Never' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:RequireThumbprintReference />   
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />  
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <!-- Supporting Token Assertions appear here -->  
      ...  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
          <sp:RequireSignatureConfirmation />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
#### <a name="624-anonymousforcertificate"></a><span data-ttu-id="546ea-433">6.2.4 AnonymousForCertificate</span><span class="sxs-lookup"><span data-stu-id="546ea-433">6.2.4 AnonymousForCertificate</span></span>  
 <span data-ttu-id="546ea-434">この認証モードでは、クライアントは匿名になり、X.509 証明書を使用してサービスが認証されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-434">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="546ea-435">使用するバインディングは、6.4.2 で説明する対称バインディングのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="546ea-435">The binding used is an instance of symmetric binding as described in 6.4.2.</span></span>  
  
 <span data-ttu-id="546ea-436">ポリシー</span><span class="sxs-lookup"><span data-stu-id="546ea-436">Policy</span></span>  
  
 <span data-ttu-id="546ea-437">バインディングの詳細については、前述の 6.2.3 の「ポリシー」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="546ea-437">See "Policy" in 6.2.3 above for binding details</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="546ea-438">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="546ea-438">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="546ea-439">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-439">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-440">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-440">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="546ea-441">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="546ea-441">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="546ea-442">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-442">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-443">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-443">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="625-usernameforcertificate"></a><span data-ttu-id="546ea-444">6.2.5 UserNameForCertificate</span><span class="sxs-lookup"><span data-stu-id="546ea-444">6.2.5 UserNameForCertificate</span></span>  
 <span data-ttu-id="546ea-445">この認証モードでは、クライアントはユーザー名トークンを使用してサーバーに対する認証を行います。ユーザー名トークンは、署名付きサポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-445">With this authentication mode the client authenticates to the service using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="546ea-446">X.509 証明書を使用したクライアントに対するサービス認証。</span><span class="sxs-lookup"><span data-stu-id="546ea-446">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="546ea-447">使用するバインディングは、クライアントによって生成され、サービスの公開キーで暗号化されたキーを保護トークンとして使用する対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="546ea-447">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="546ea-448">ポリシー</span><span class="sxs-lookup"><span data-stu-id="546ea-448">Policy</span></span>  
  
 <span data-ttu-id="546ea-449">バインディングの詳細については、前述の 6.2.3 の「ポリシー」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="546ea-449">See "Policy" in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="546ea-450">署名付きサポート トークン</span><span class="sxs-lookup"><span data-stu-id="546ea-450">Signed Supporting Token</span></span>  
  
```xml  
<sp:SignedSupportingTokens>  
  <wsp:Policy>  
    <sp:UsernameToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:WssUsernameToken10 />   
      </wsp:Policy>  
    </sp:UsernameToken>  
  </wsp:Policy>  
</sp:SignedSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="546ea-451">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="546ea-451">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="546ea-452">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-452">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-453">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-453">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="546ea-454">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="546ea-454">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="546ea-455">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-455">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-456">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-456">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="626-mutualcertificate-wss-11"></a><span data-ttu-id="546ea-457">6.2.6 MutualCertificate (WSS 1.1)</span><span class="sxs-lookup"><span data-stu-id="546ea-457">6.2.6 MutualCertificate (WSS 1.1)</span></span>  
 <span data-ttu-id="546ea-458">この認証モードでは、クライアントは X.509 証明書を使用して認証を行います。X.509 証明書は、保証サポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-458">With this authentication mode the client authenticates using an X.509 certificate which appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="546ea-459">また、サービスは X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-459">The service is also authenticated using an X.509 certificate.</span></span> <span data-ttu-id="546ea-460">使用するバインディングは、クライアントによって生成され、サービスの公開キーで暗号化されたキーを保護トークンとして使用する対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="546ea-460">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="546ea-461">ポリシー</span><span class="sxs-lookup"><span data-stu-id="546ea-461">Policy</span></span>  
  
 <span data-ttu-id="546ea-462">バインディングの詳細については、前述の 6.2.3 の「ポリシー」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="546ea-462">See Policy in 6.2.3 for binding details</span></span>  
  
 <span data-ttu-id="546ea-463">保証サポート トークン</span><span class="sxs-lookup"><span data-stu-id="546ea-463">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:X509Token sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:RequireThumbprintReference />   
        <sp:WssX509V3Token10 />   
      </wsp:Policy>  
    </sp:X509Token>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="546ea-464">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="546ea-464">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="546ea-465">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-465">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-466">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-466">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="546ea-467">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="546ea-467">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="546ea-468">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-468">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-469">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-469">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="627-issuedtokenforcertificate"></a><span data-ttu-id="546ea-470">6.2.7 IssuedTokenForCertificate</span><span class="sxs-lookup"><span data-stu-id="546ea-470">6.2.7 IssuedTokenForCertificate</span></span>  
 <span data-ttu-id="546ea-471">この認証モードでは、クライアントはサービスに対する認証を行わず、STS により発行されたトークンを示すことで、共有キーの有無を示します。</span><span class="sxs-lookup"><span data-stu-id="546ea-471">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by a STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="546ea-472">発行済みトークンは、保証サポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-472">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="546ea-473">X.509 証明書を使用したクライアントに対するサービス認証。</span><span class="sxs-lookup"><span data-stu-id="546ea-473">The service authenticates to the client using an X.509 certificate.</span></span> <span data-ttu-id="546ea-474">使用するバインディングは、クライアントによって生成され、サービスの公開キーで暗号化されたキーを保護トークンとして使用する対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="546ea-474">The binding used is a symmetric binding with the protection token being a key generated by the client, encrypted with the public key of the service.</span></span>  
  
 <span data-ttu-id="546ea-475">ポリシー</span><span class="sxs-lookup"><span data-stu-id="546ea-475">Policy</span></span>  
  
 <span data-ttu-id="546ea-476">バインディングの詳細については、前述の 6.2.3 の「ポリシー」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="546ea-476">See Policy in 6.2.3 above for binding details</span></span>  
  
 <span data-ttu-id="546ea-477">保証サポート トークン</span><span class="sxs-lookup"><span data-stu-id="546ea-477">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <sp:RequestSecurityTokenTemplate>  
        <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
       </wst:KeyType>  
     </sp:RequestSecurityTokenTemplate>  
     <wsp:Policy>  
       <sp:RequireDerivedKeys />   
       <sp:RequireInternalReference />   
     </wsp:Policy>  
   </sp:IssuedToken>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="546ea-478">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="546ea-478">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="546ea-479">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-479">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-480">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-480">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="546ea-481">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="546ea-481">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="546ea-482">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-482">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-483">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-483">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
## <a name="63-kerberos"></a><span data-ttu-id="546ea-484">6.3 Kerberos</span><span class="sxs-lookup"><span data-stu-id="546ea-484">6.3 Kerberos</span></span>  
 <span data-ttu-id="546ea-485">この認証モードを使用すると、クライアントは Kerberos チケットを使用してサービスに対する認証を行います。</span><span class="sxs-lookup"><span data-stu-id="546ea-485">With this authentication mode the client authenticates to the service using a Kerberos ticket.</span></span> <span data-ttu-id="546ea-486">また、その同じチケットによってサーバーが認証されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-486">That same ticket also provides server authentication.</span></span> <span data-ttu-id="546ea-487">使用するバインディングは、以下のプロパティが設定された対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="546ea-487">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="546ea-488">保護トークン: インクルード モードが .../IncludeToken/Once に設定された Kerberos チケット</span><span class="sxs-lookup"><span data-stu-id="546ea-488">Protection Token: Kerberos Ticket, inclusion mode is set to .../IncludeToken/Once</span></span>  
<span data-ttu-id="546ea-489">トークンの保護 : False</span><span class="sxs-lookup"><span data-stu-id="546ea-489">Token Protection: False</span></span>  
  
 <span data-ttu-id="546ea-490">ヘッダーと本文全体の署名 : True</span><span class="sxs-lookup"><span data-stu-id="546ea-490">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="546ea-491">保護の順序 : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="546ea-491">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="546ea-492">署名の暗号化 : True</span><span class="sxs-lookup"><span data-stu-id="546ea-492">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="546ea-493">ポリシー</span><span class="sxs-lookup"><span data-stu-id="546ea-493">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='Kerberos_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:KerberosToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Once' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:WssGssKerberosV5ApReqToken11 />   
                </wsp:Policy>  
              </sp:KerberosToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic128 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="546ea-494">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="546ea-494">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="546ea-495">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-495">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-496">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-496">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="546ea-497">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="546ea-497">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="546ea-498">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-498">Request</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-499">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-499">Response</span></span>  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a><span data-ttu-id="546ea-500">6.4 IssuedToken</span><span class="sxs-lookup"><span data-stu-id="546ea-500">6.4 IssuedToken</span></span>  
 <span data-ttu-id="546ea-501">この認証モードでは、クライアントはサービスに対する認証を行わず、STS により発行されたトークンを示すことで、共有キーの有無を示します。</span><span class="sxs-lookup"><span data-stu-id="546ea-501">With this authentication mode the client does not authenticate to the service, as such, rather the client presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="546ea-502">サービスはクライアントに対する認証を行いませんが、そのサービスだけがキーを復号化できるように、STS は発行されたトークンの一部として共有キーを暗号化します。</span><span class="sxs-lookup"><span data-stu-id="546ea-502">The service is not authenticated to the client, as such, instead the STS encrypts the shared key as part of the issued token such that only the service can decrypt the key.</span></span> <span data-ttu-id="546ea-503">使用するバインディングは、以下のプロパティが設定された対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="546ea-503">The binding used is as symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="546ea-504">保護トークン: インクルード モードが .../IncludeToken/AlwaysToRecipient に設定された発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="546ea-504">Protection Token: Issued Token, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="546ea-505">トークンの保護 : False</span><span class="sxs-lookup"><span data-stu-id="546ea-505">Token Protection: False</span></span>  
  
 <span data-ttu-id="546ea-506">ヘッダーと本文全体の署名 : True</span><span class="sxs-lookup"><span data-stu-id="546ea-506">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="546ea-507">保護の順序 : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="546ea-507">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="546ea-508">署名の暗号化 : True</span><span class="sxs-lookup"><span data-stu-id="546ea-508">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="546ea-509">ポリシー</span><span class="sxs-lookup"><span data-stu-id="546ea-509">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CustomBinding_ISimple3_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <sp:RequestSecurityTokenTemplate>  
                  <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
                  </wst:KeyType>   
                </sp:RequestSecurityTokenTemplate>  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:RequireInternalReference />   
                </wsp:Policy>  
              </sp:IssuedToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="546ea-510">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="546ea-510">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="546ea-511">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-511">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-512">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-512">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="546ea-513">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="546ea-513">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="546ea-514">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-514">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-515">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-515">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a><span data-ttu-id="546ea-516">6.5 SslNegotiated を使用したサービス認証</span><span class="sxs-lookup"><span data-stu-id="546ea-516">6.5 Using SslNegotiated for Service Authentication</span></span>  
 <span data-ttu-id="546ea-517">このセクションでは、WS-SecureConversation (WS-SC) ごとのセキュリティ コンテキスト トークンである保護トークンと共に、対称バインディングを使用する認証モードのグループについて説明します。WS-SecureConversation (WS-SC) のキー値は、WS-Trust (WS-T) RST/RSTR メッセージで TLS プロトコルを実行することによりネゴシエートされます。</span><span class="sxs-lookup"><span data-stu-id="546ea-517">This section describes a group of authentication modes that use a symmetric binding with the protection token being a Security Context Token per WS-SecureConversation (WS-SC) whose key value is negotiated by executing the TLS protocol over WS-Trust (WS-T) RST/RSTR messages.</span></span> <span data-ttu-id="546ea-518">WS-Trust を使用した TLS ハンドシェイク実装の詳細は、TLSNEGO に記述されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-518">Details of the TLS handshake implementation using WS-Trust are described in TLSNEGO.</span></span> <span data-ttu-id="546ea-519">ここで示すメッセージの例は、セキュリティ コンテキストに関連付けられた SCT が、ハンドシェイクによって既に確立されていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="546ea-519">Here in the message examples we will assume that SCT with an associated security context is already established through a handshake.</span></span>  
  
 <span data-ttu-id="546ea-520">使用するバインディングは、以下のプロパティが設定された対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="546ea-520">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="546ea-521">保護トークン: インクルード モードが .../IncludeToken/Never に設定された SslContextToken</span><span class="sxs-lookup"><span data-stu-id="546ea-521">Protection Token: SslContextToken, inclusion mode is set to .../IncludeToken/Never</span></span>  
<span data-ttu-id="546ea-522">トークンの保護 : False</span><span class="sxs-lookup"><span data-stu-id="546ea-522">Token Protection: False</span></span>  
  
 <span data-ttu-id="546ea-523">ヘッダーと本文全体の署名 : True</span><span class="sxs-lookup"><span data-stu-id="546ea-523">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="546ea-524">保護の順序 : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="546ea-524">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="546ea-525">署名の暗号化 : True</span><span class="sxs-lookup"><span data-stu-id="546ea-525">Encrypt Signature: True</span></span>  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a><span data-ttu-id="546ea-526">6.5.1 SslNegotiated サービス認証のポリシー</span><span class="sxs-lookup"><span data-stu-id="546ea-526">6.5.1 Policy for SslNegotiated service authentication</span></span>  
 <span data-ttu-id="546ea-527">このセクションで説明するすべての認証モードのポリシーは、使用する署名付きサポート トークンまたは保証トークンだけが異なります。</span><span class="sxs-lookup"><span data-stu-id="546ea-527">Policy for all authentication modes in this section are similar and differ only by specific signed supporting or endorsing tokens used.</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SslNegotiated_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <mssp:SslContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' />  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                </wsp:Policy>  
              </mssp:SslContextToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <!-- Supporting token assertions go here -->  
      ..  
      <sp:Wss11>   
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
#### <a name="652-anonymousforsslnegotiated"></a><span data-ttu-id="546ea-528">6.5.2 AnonymousForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="546ea-528">6.5.2 AnonymousForSslNegotiated</span></span>  
 <span data-ttu-id="546ea-529">この認証モードでは、クライアントは匿名になり、X.509 証明書を使用してサービスが認証されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-529">With this authentication mode the client is anonymous and the service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="546ea-530">使用するバインディングは、前述の 6.5.1 に示した対称バインディングのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="546ea-530">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="546ea-531">ポリシー</span><span class="sxs-lookup"><span data-stu-id="546ea-531">Policy</span></span>  
  
 <span data-ttu-id="546ea-532">バインディングの詳細については、前述の 6.5.1 の「ポリシー」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="546ea-532">See Policy in 6.5.1 above for binding details.</span></span>  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="546ea-533">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="546ea-533">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="546ea-534">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-534">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-535">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-535">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="546ea-536">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="546ea-536">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="546ea-537">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-537">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-538">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-538">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="653-usernameforsslnegotiated"></a><span data-ttu-id="546ea-539">6.5.3 UserNameForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="546ea-539">6.5.3 UserNameForSslNegotiated</span></span>  
 <span data-ttu-id="546ea-540">この認証モードでは、クライアントはユーザー名トークンを使用して認証を行います。ユーザー名トークンは、署名付きサポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-540">With this authentication mode the client is authenticates using a Username Token which appears at the SOAP layer as a signed supporting token.</span></span> <span data-ttu-id="546ea-541">サービスは X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-541">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="546ea-542">使用するバインディングは、6.5.1 で説明した対称バインディングのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="546ea-542">The binding used is an instance of symmetric binding as described in 6.5.1.</span></span>  
  
 <span data-ttu-id="546ea-543">ポリシー</span><span class="sxs-lookup"><span data-stu-id="546ea-543">Policy</span></span>  
  
 <span data-ttu-id="546ea-544">バインディングの詳細については、前述の 6.5.1 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="546ea-544">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="546ea-545">署名付きサポート トークン</span><span class="sxs-lookup"><span data-stu-id="546ea-545">Signed Supporting Token</span></span>  
  
```xml  
<sp:SignedSupportingTokens>  
  <wsp:Policy>  
    <sp:UsernameToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:WssUsernameToken10 />   
      </wsp:Policy>  
    </sp:UsernameToken>  
  </wsp:Policy>  
</sp:SignedSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="546ea-546">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="546ea-546">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="546ea-547">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-547">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-548">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-548">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="546ea-549">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="546ea-549">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="546ea-550">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-550">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-551">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-551">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="654-issuedtokenforsslnegotiated"></a><span data-ttu-id="546ea-552">6.5.4 IssuedTokenForSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="546ea-552">6.5.4 IssuedTokenForSslNegotiated</span></span>  
 <span data-ttu-id="546ea-553">この認証モードでは、クライアントはサービスに対する認証を行わず、STS により発行されたトークンを示すことで、共有キーの有無を示します。</span><span class="sxs-lookup"><span data-stu-id="546ea-553">With this authentication mode the client does not authenticate to the service, as such, but instead presents a token issued by an STS and proves knowledge of a shared key.</span></span> <span data-ttu-id="546ea-554">発行済みトークンは、保証サポート トークンとして SOAP 層に表示されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-554">The issued token appears at the SOAP layer as an endorsing supporting token.</span></span> <span data-ttu-id="546ea-555">サービスは X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-555">The service is authenticated using an X.509 certificate.</span></span> <span data-ttu-id="546ea-556">使用するバインディングは、前述の 6.5.1 に示した対称バインディングのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="546ea-556">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="546ea-557">ポリシー</span><span class="sxs-lookup"><span data-stu-id="546ea-557">Policy</span></span>  
  
 <span data-ttu-id="546ea-558">バインディングの詳細については、前述の 6.5.1 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="546ea-558">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="546ea-559">保証サポート トークン</span><span class="sxs-lookup"><span data-stu-id="546ea-559">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <sp:RequestSecurityTokenTemplate>  
        <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
        </wst:KeyType>   
      </sp:RequestSecurityTokenTemplate>  
      <wsp:Policy>  
        <sp:RequireDerivedKeys />   
        <sp:RequireInternalReference />   
      </wsp:Policy>  
    </sp:IssuedToken>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="546ea-560">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="546ea-560">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="546ea-561">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-561">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-562">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-562">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="546ea-563">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="546ea-563">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="546ea-564">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-564">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-565">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-565">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="655-mutualsslnegotiated"></a><span data-ttu-id="546ea-566">6.5.5 MutualSslNegotiated</span><span class="sxs-lookup"><span data-stu-id="546ea-566">6.5.5 MutualSslNegotiated</span></span>  
 <span data-ttu-id="546ea-567">この認証モードでは、クライアントとサービスは X.509 証明書を使用して認証を行います。</span><span class="sxs-lookup"><span data-stu-id="546ea-567">With this authentication mode the client and the service authenticate using X.509 certificates.</span></span> <span data-ttu-id="546ea-568">使用するバインディングは、前述の 6.5.1 に示した対称バインディングのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="546ea-568">The binding used is an instance of symmetric binding as described in 6.5.1 above.</span></span>  
  
 <span data-ttu-id="546ea-569">ポリシー</span><span class="sxs-lookup"><span data-stu-id="546ea-569">Policy</span></span>  
  
 <span data-ttu-id="546ea-570">バインディングの詳細については、前述の 6.5.1 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="546ea-570">See section 6.5.1 above for binding details</span></span>  
  
 <span data-ttu-id="546ea-571">保証サポート トークン</span><span class="sxs-lookup"><span data-stu-id="546ea-571">Endorsing Supporting Token</span></span>  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:X509Token sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:RequireThumbprintReference />   
        <sp:WssX509V3Token10 />   
      </wsp:Policy>  
    </sp:X509Token>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="546ea-572">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="546ea-572">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="546ea-573">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-573">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-574">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-574">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="546ea-575">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="546ea-575">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="546ea-576">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-576">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-577">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-577">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="66-sspinegotiated"></a><span data-ttu-id="546ea-578">6.6 SspiNegotiated</span><span class="sxs-lookup"><span data-stu-id="546ea-578">6.6 SspiNegotiated</span></span>  
 <span data-ttu-id="546ea-579">この認証モードを使用すると、クライアントとサーバーの認証を実行するために、ネゴシエーション プロトコルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-579">With this authentication mode a negotiation protocol is used to perform client and server authentication.</span></span> <span data-ttu-id="546ea-580">Kerberos を使用できる場合は Kerberos が使用され、それ以外の場合は NTLM が使用されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-580">Kerberos is used if possible, otherwise NTLM.</span></span> <span data-ttu-id="546ea-581">使用するバインディングは、以下のプロパティが設定された対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="546ea-581">The binding used is a symmetric binding with the following properties;</span></span>  
  
 <span data-ttu-id="546ea-582">保護トークン: インクルード モードが .../IncludeToken/AlwaysToRecipient に設定された SpnegoContextToken</span><span class="sxs-lookup"><span data-stu-id="546ea-582">Protection Token: SpnegoContextToken, inclusion mode is set to .../IncludeToken/AlwaysToRecipient</span></span>  
<span data-ttu-id="546ea-583">トークンの保護 : False</span><span class="sxs-lookup"><span data-stu-id="546ea-583">Token Protection: False</span></span>  
  
 <span data-ttu-id="546ea-584">ヘッダーと本文全体の署名 : True</span><span class="sxs-lookup"><span data-stu-id="546ea-584">Entire Header And Body Signatures: True</span></span>  
  
 <span data-ttu-id="546ea-585">保護の順序 : SignBeforeEncrypt</span><span class="sxs-lookup"><span data-stu-id="546ea-585">Protection Order: SignBeforeEncrypt</span></span>  
  
 <span data-ttu-id="546ea-586">署名の暗号化 : True</span><span class="sxs-lookup"><span data-stu-id="546ea-586">Encrypt Signature: True</span></span>  
  
 <span data-ttu-id="546ea-587">ポリシー</span><span class="sxs-lookup"><span data-stu-id="546ea-587">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='CustomBinding_ISimple13_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:SpnegoContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                </wsp:Policy>  
              </sp:SpnegoContextToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="546ea-588">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="546ea-588">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="546ea-589">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-589">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-590">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-590">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="546ea-591">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="546ea-591">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="546ea-592">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-592">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-593">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-593">Response</span></span>  
  
```xml  
<wsse:Security>  
<wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="67-secureconversation"></a><span data-ttu-id="546ea-594">6.7 SecureConversation</span><span class="sxs-lookup"><span data-stu-id="546ea-594">6.7 SecureConversation</span></span>  
 <span data-ttu-id="546ea-595">使用するバインディングは、WS-SecureConversation (WS-SC) ごとの SCT を保護トークンとして使用する対称バインディングです。</span><span class="sxs-lookup"><span data-stu-id="546ea-595">The binding used is a symmetric binding with the protection token being a SCT per WS-SecureConversation (WS-SC).</span></span> <span data-ttu-id="546ea-596">入れ子になったバインディング (このバインディング自体も、ネゴシエーション プロトコルを使用する対称バインディングです) に従い、SCT は WS-Trust (WS-Trust) または WS-SecureConversation (WS-SC) を使用してネゴシエートされます。</span><span class="sxs-lookup"><span data-stu-id="546ea-596">The SCT is negotiated using WS-Trust (WS-Trust) or WS-SecureConversation (WS-SC) according to a nested binding, which is itself a symmetric binding that uses a negotiation protocol.</span></span> <span data-ttu-id="546ea-597">ネゴシエーション プロトコルは、可能であれば Kerberos を使用してクライアントとサーバーの認証を行います。</span><span class="sxs-lookup"><span data-stu-id="546ea-597">The negotiation protocol will use Kerberos to perform client and server authentication if possible.</span></span> <span data-ttu-id="546ea-598">Kerberos を使用できない場合は、NTLM が使用されます。</span><span class="sxs-lookup"><span data-stu-id="546ea-598">If Kerberos cannot be used, it will fall back to NTLM.</span></span>  
  
 <span data-ttu-id="546ea-599">ポリシー</span><span class="sxs-lookup"><span data-stu-id="546ea-599">Policy</span></span>  
  
```xml  
<wsp:Policy wsu:Id='SecureConversation_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:SecureConversationToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:BootstrapPolicy>  
                    <wsp:Policy>  
                      <sp:SignedParts>  
                        <sp:Body />   
                        <sp:Header Name='To' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='From' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='FaultTo' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='ReplyTo' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='MessageID' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='RelatesTo' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='Action' Namespace='http://www.w3.org/2005/08/addressing' />   
                      </sp:SignedParts>  
                      <sp:EncryptedParts>  
                        <sp:Body />   
                      </sp:EncryptedParts>  
                      <sp:SymmetricBinding>  
                        <wsp:Policy>  
                          <sp:ProtectionToken>  
                            <wsp:Policy>  
                              <sp:SpnegoContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                                <wsp:Policy>  
                                  <sp:RequireDerivedKeys />   
                                </wsp:Policy>  
                              </sp:SpnegoContextToken>  
                            </wsp:Policy>  
                          </sp:ProtectionToken>  
                          <sp:AlgorithmSuite>  
                            <wsp:Policy>  
                              <sp:Basic256 />   
                            </wsp:Policy>  
                          </sp:AlgorithmSuite>  
                          <sp:Layout>  
                            <wsp:Policy>  
                              <sp:Strict />   
                            </wsp:Policy>  
                          </sp:Layout>  
                          <sp:IncludeTimestamp />   
                          <sp:EncryptSignature />   
                          <sp:OnlySignEntireHeadersAndBody />   
                        </wsp:Policy>  
                      </sp:SymmetricBinding>  
                      <sp:Wss11>  
                        <wsp:Policy>  
                          <sp:MustSupportRefKeyIdentifier />   
                          <sp:MustSupportRefIssuerSerial />   
                          <sp:MustSupportRefThumbprint />   
                          <sp:MustSupportRefEncryptedKey />   
                        </wsp:Policy>  
                      </sp:Wss11>  
                      <sp:Trust10>  
                        <wsp:Policy>  
                          <sp:MustSupportIssuedTokens />   
                          <sp:RequireClientEntropy />   
                          <sp:RequireServerEntropy />   
                        </wsp:Policy>  
                      </sp:Trust10>  
                    </wsp:Policy>  
                  </sp:BootstrapPolicy>  
                </wsp:Policy>  
              </sp:SecureConversationToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a><span data-ttu-id="546ea-600">セキュリティ ヘッダーの例 : SignBeforeEncrypt、EncryptSignature</span><span class="sxs-lookup"><span data-stu-id="546ea-600">Security Header Examples: SignBeforeEncrypt, EncryptSignature</span></span>  
 <span data-ttu-id="546ea-601">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-601">Request</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-602">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-602">Response</span></span>  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a><span data-ttu-id="546ea-603">セキュリティ ヘッダーの例 : EncryptBeforeSign</span><span class="sxs-lookup"><span data-stu-id="546ea-603">Security Header Examples: EncryptBeforeSign</span></span>  
 <span data-ttu-id="546ea-604">要求</span><span class="sxs-lookup"><span data-stu-id="546ea-604">Request</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 <span data-ttu-id="546ea-605">応答</span><span class="sxs-lookup"><span data-stu-id="546ea-605">Response</span></span>  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```

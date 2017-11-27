---
title: "&lt;clientCertificate&gt; 要素の &lt;authentication&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4eb125727d68d1618b32d21612ecfac28eaa5b6b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltauthenticationgt-of-ltclientcertificategt-element"></a><span data-ttu-id="c66d6-102">&lt;clientCertificate&gt; 要素の &lt;authentication&gt;</span><span class="sxs-lookup"><span data-stu-id="c66d6-102">&lt;authentication&gt; of &lt;clientCertificate&gt; Element</span></span>
<span data-ttu-id="c66d6-103">サービスによって使用されるクライアント証明書の認証動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="c66d6-103">Specifies authentication behaviors for client certificates used by a service.</span></span>  
  
 <span data-ttu-id="c66d6-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c66d6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c66d6-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="c66d6-105">\<behaviors></span></span>  
<span data-ttu-id="c66d6-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="c66d6-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="c66d6-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="c66d6-107">\<behavior></span></span>  
<span data-ttu-id="c66d6-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="c66d6-108">\<serviceCredentials></span></span>  
<span data-ttu-id="c66d6-109">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="c66d6-109">\<clientCertificate></span></span>  
<span data-ttu-id="c66d6-110">\<認証 ></span><span class="sxs-lookup"><span data-stu-id="c66d6-110">\<authentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c66d6-111">構文</span><span class="sxs-lookup"><span data-stu-id="c66d6-111">Syntax</span></span>  
  
```xml  
<authentication  
customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
includeWindowsGroups="Boolean"  
mapClientCertificateToWindowsAccount="Boolean"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c66d6-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c66d6-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c66d6-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c66d6-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c66d6-114">属性</span><span class="sxs-lookup"><span data-stu-id="c66d6-114">Attributes</span></span>  
  
|<span data-ttu-id="c66d6-115">属性</span><span class="sxs-lookup"><span data-stu-id="c66d6-115">Attribute</span></span>|<span data-ttu-id="c66d6-116">説明</span><span class="sxs-lookup"><span data-stu-id="c66d6-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c66d6-117">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="c66d6-117">customCertificateValidatorType</span></span>|<span data-ttu-id="c66d6-118">省略可能な文字列。</span><span class="sxs-lookup"><span data-stu-id="c66d6-118">Optional string.</span></span> <span data-ttu-id="c66d6-119">カスタム型の検証に使用される型およびアセンブリです。</span><span class="sxs-lookup"><span data-stu-id="c66d6-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="c66d6-120">`certificateValidationMode` が `Custom` に設定されている場合は、この属性を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c66d6-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="c66d6-121">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="c66d6-121">certificateValidationMode</span></span>|<span data-ttu-id="c66d6-122">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="c66d6-122">Optional enumeration.</span></span> <span data-ttu-id="c66d6-123">資格情報の検証に使用されるモードのいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c66d6-123">Specifies one of the modes used to validate credentials.</span></span> <span data-ttu-id="c66d6-124">この属性は <xref:System.ServiceModel.Security.X509CertificateValidationMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="c66d6-124">This attribute is of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> type.</span></span> <span data-ttu-id="c66d6-125"><xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType> に設定されている場合、`customCertificateValidator` も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c66d6-125">If set to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="c66d6-126">既定値は、<xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType> です。</span><span class="sxs-lookup"><span data-stu-id="c66d6-126">The default is <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span></span>|  
|<span data-ttu-id="c66d6-127">includeWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="c66d6-127">includeWindowsGroups</span></span>|<span data-ttu-id="c66d6-128">省略可能なブール。</span><span class="sxs-lookup"><span data-stu-id="c66d6-128">Optional Boolean.</span></span> <span data-ttu-id="c66d6-129">セキュリティ コンテキストに Windows グループが含まれているかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c66d6-129">Specifies if Windows groups are included in the security context.</span></span> <span data-ttu-id="c66d6-130">この属性を `true` に設定すると、グループ全体が拡張されるため、パフォーマンスに影響が及びます。</span><span class="sxs-lookup"><span data-stu-id="c66d6-130">Setting this attribute to `true` has a performance impact, as it results in a full group expansion.</span></span> <span data-ttu-id="c66d6-131">ユーザーが属するグループの一覧を生成する必要がない場合は、この属性を `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="c66d6-131">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|<span data-ttu-id="c66d6-132">mapClientCertificateToWindowsAcccount</span><span class="sxs-lookup"><span data-stu-id="c66d6-132">mapClientCertificateToWindowsAcccount</span></span>|<span data-ttu-id="c66d6-133">ブール型。</span><span class="sxs-lookup"><span data-stu-id="c66d6-133">Boolean.</span></span> <span data-ttu-id="c66d6-134">証明書を使用してクライアントを Windows ID にマップできるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c66d6-134">Specifies whether the client can be mapped to a Windows identity using the certificate.</span></span> <span data-ttu-id="c66d6-135">これを行うには、Active Directory が有効である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c66d6-135">Active Directory must be enabled to do this.</span></span>|  
|<span data-ttu-id="c66d6-136">revocationMode</span><span class="sxs-lookup"><span data-stu-id="c66d6-136">revocationMode</span></span>|<span data-ttu-id="c66d6-137">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="c66d6-137">Optional enumeration.</span></span> <span data-ttu-id="c66d6-138">証明書失効リスト (RCL) のチェックに使用されるモードのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="c66d6-138">One of the modes used to check for a revoked certificate lists (RCL).</span></span> <span data-ttu-id="c66d6-139">既定値は、`Online` です。</span><span class="sxs-lookup"><span data-stu-id="c66d6-139">The default is `Online`.</span></span> <span data-ttu-id="c66d6-140">この値は、HTTP トランスポート セキュリティを使用する場合は無視されます。</span><span class="sxs-lookup"><span data-stu-id="c66d6-140">This value is ignored when using HTTP transport security.</span></span>|  
|<span data-ttu-id="c66d6-141">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="c66d6-141">trustedStoreLocation</span></span>|<span data-ttu-id="c66d6-142">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="c66d6-142">Optional enumeration.</span></span> <span data-ttu-id="c66d6-143">2 つのシステム格納場所 (`LocalMachine` または `CurrentUser`) のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="c66d6-143">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="c66d6-144">この値は、サービス証明書がクライアントにネゴシエートされるときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="c66d6-144">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="c66d6-145">に対して検証が実行、**信頼されたユーザー**指定されたストアの場所に格納します。</span><span class="sxs-lookup"><span data-stu-id="c66d6-145">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="c66d6-146">既定値は、`CurrentUser` です。</span><span class="sxs-lookup"><span data-stu-id="c66d6-146">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="c66d6-147">customCertificateValidatorType 属性</span><span class="sxs-lookup"><span data-stu-id="c66d6-147">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="c66d6-148">値</span><span class="sxs-lookup"><span data-stu-id="c66d6-148">Value</span></span>|<span data-ttu-id="c66d6-149">説明</span><span class="sxs-lookup"><span data-stu-id="c66d6-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c66d6-150">String</span><span class="sxs-lookup"><span data-stu-id="c66d6-150">String</span></span>|<span data-ttu-id="c66d6-151">タイプ名およびアセンブリと、タイプの検索に使用される他のデータを指定します。</span><span class="sxs-lookup"><span data-stu-id="c66d6-151">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="c66d6-152">certificateValidationMode 属性</span><span class="sxs-lookup"><span data-stu-id="c66d6-152">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="c66d6-153">値</span><span class="sxs-lookup"><span data-stu-id="c66d6-153">Value</span></span>|<span data-ttu-id="c66d6-154">説明</span><span class="sxs-lookup"><span data-stu-id="c66d6-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c66d6-155">列挙型</span><span class="sxs-lookup"><span data-stu-id="c66d6-155">Enumeration</span></span>|<span data-ttu-id="c66d6-156">None、PeerTrust、ChainTrust、PeerOrChainTrust、Custom のいずれかの値にします。</span><span class="sxs-lookup"><span data-stu-id="c66d6-156">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="c66d6-157">詳細については、次を参照してください。[証明書の使用](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)です。</span><span class="sxs-lookup"><span data-stu-id="c66d6-157">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="c66d6-158">revocationMode 属性</span><span class="sxs-lookup"><span data-stu-id="c66d6-158">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="c66d6-159">値</span><span class="sxs-lookup"><span data-stu-id="c66d6-159">Value</span></span>|<span data-ttu-id="c66d6-160">説明</span><span class="sxs-lookup"><span data-stu-id="c66d6-160">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c66d6-161">列挙型</span><span class="sxs-lookup"><span data-stu-id="c66d6-161">Enumeration</span></span>|<span data-ttu-id="c66d6-162">NoCheck、Online、Offline のいずれかの値にします。</span><span class="sxs-lookup"><span data-stu-id="c66d6-162">One of the following values: NoCheck, Online, Offline.</span></span> <span data-ttu-id="c66d6-163">詳細については、次を参照してください。[証明書の使用](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)です。</span><span class="sxs-lookup"><span data-stu-id="c66d6-163">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="c66d6-164">trustedStoreLocation 属性</span><span class="sxs-lookup"><span data-stu-id="c66d6-164">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="c66d6-165">値</span><span class="sxs-lookup"><span data-stu-id="c66d6-165">Value</span></span>|<span data-ttu-id="c66d6-166">説明</span><span class="sxs-lookup"><span data-stu-id="c66d6-166">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c66d6-167">列挙型</span><span class="sxs-lookup"><span data-stu-id="c66d6-167">Enumeration</span></span>|<span data-ttu-id="c66d6-168">`LocalMachine` または `CurrentUser` のいずれかの値にします。</span><span class="sxs-lookup"><span data-stu-id="c66d6-168">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="c66d6-169">既定値は、`CurrentUser` です。</span><span class="sxs-lookup"><span data-stu-id="c66d6-169">The default is `CurrentUser`.</span></span> <span data-ttu-id="c66d6-170">クライアント アプリケーションがシステム アカウントで実行されている場合、証明書は通常 `LocalMachine` の下にあります。</span><span class="sxs-lookup"><span data-stu-id="c66d6-170">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="c66d6-171">クライアント アプリケーションがユーザー アカウントで実行されている場合、証明書は通常 `CurrentUser` の下にあります。</span><span class="sxs-lookup"><span data-stu-id="c66d6-171">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c66d6-172">子要素</span><span class="sxs-lookup"><span data-stu-id="c66d6-172">Child Elements</span></span>  
 <span data-ttu-id="c66d6-173">なし。</span><span class="sxs-lookup"><span data-stu-id="c66d6-173">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c66d6-174">親要素</span><span class="sxs-lookup"><span data-stu-id="c66d6-174">Parent Elements</span></span>  
  
|<span data-ttu-id="c66d6-175">要素</span><span class="sxs-lookup"><span data-stu-id="c66d6-175">Element</span></span>|<span data-ttu-id="c66d6-176">説明</span><span class="sxs-lookup"><span data-stu-id="c66d6-176">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c66d6-177">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="c66d6-177">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="c66d6-178">サービスに対するクライアントの認証に使用する X.509 証明書を定義します。</span><span class="sxs-lookup"><span data-stu-id="c66d6-178">Defines an X.509 certificate used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c66d6-179">コメント</span><span class="sxs-lookup"><span data-stu-id="c66d6-179">Remarks</span></span>  
 <span data-ttu-id="c66d6-180">`<authentication>` 要素は、<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> クラスに対応します。</span><span class="sxs-lookup"><span data-stu-id="c66d6-180">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="c66d6-181">この要素を使用すると、クライアントを認証する方法をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="c66d6-181">It enables you to customize how clients are authenticated.</span></span> <span data-ttu-id="c66d6-182">`certificateValidationMode` 属性は、`None`、`ChainTrust`、`PeerOrChainTrust`、`PeerTrust`、または `Custom` に設定できます。</span><span class="sxs-lookup"><span data-stu-id="c66d6-182">You can set the `certificateValidationMode` attribute to `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, or `Custom`.</span></span> <span data-ttu-id="c66d6-183">既定では、レベルに設定が`ChainTrust`で終了する証明書の階層で各証明書を検索することを指定する、*ルート機関*チェーンの上部にあります。</span><span class="sxs-lookup"><span data-stu-id="c66d6-183">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a *root authority* at the top of the chain.</span></span> <span data-ttu-id="c66d6-184">これは最もセキュリティで保護されているモードです。</span><span class="sxs-lookup"><span data-stu-id="c66d6-184">This is the most secure mode.</span></span> <span data-ttu-id="c66d6-185">また、値を `PeerOrChainTrust` に設定することもできます。これは、信頼されたチェーン内の証明書と共に、自己発行された証明書 (ピア信頼) も受け入れるよう指定します。</span><span class="sxs-lookup"><span data-stu-id="c66d6-185">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="c66d6-186">自己発行の資格情報は信頼された証明機関から購入したものである必要はないため、この値はクライアントとサービスの開発およびデバッグに使用されます。</span><span class="sxs-lookup"><span data-stu-id="c66d6-186">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="c66d6-187">クライアントを展開するときは、代わりに `ChainTrust` 値を使用します。</span><span class="sxs-lookup"><span data-stu-id="c66d6-187">When deploying a client, use the `ChainTrust` value instead.</span></span>  
  
 <span data-ttu-id="c66d6-188">また、値を `Custom` に設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="c66d6-188">You can also set the value to `Custom`.</span></span> <span data-ttu-id="c66d6-189">`Custom` 値に設定する場合は、`customCertificateValidatorType` 属性を、証明書の検証に使用するアセンブリと型に設定する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="c66d6-189">When set to the `Custom` value, you must also set the `customCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="c66d6-190">独自のカスタム検証を作成するには、抽象 <xref:System.IdentityModel.Selectors.X509CertificateValidator> クラスを継承する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c66d6-190">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="c66d6-191">詳細については、次を参照してください。[する方法: カスタム証明書検証を使用するサービスを作成する](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)です。</span><span class="sxs-lookup"><span data-stu-id="c66d6-191">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c66d6-192">例</span><span class="sxs-lookup"><span data-stu-id="c66d6-192">Example</span></span>  
 <span data-ttu-id="c66d6-193">次のコードは、`<authentication>` 要素の X.509 証明書とカスタム検証タイプを指定します。</span><span class="sxs-lookup"><span data-stu-id="c66d6-193">The following code specifies an X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
```xml  
<serviceBehaviors>  
 <behavior name="myServiceBehavior">  
  <clientCertificate>  
   <certificate   
         findValue="www.cohowinery.com"   
         storeLocation="CurrentUser"   
         storeName="TrustedPeople"  
         x509FindType="FindByIssuerName" />  
   <authentication customCertificateValidatorType="MyTypes.Coho"  
    certificateValidationMode="Custom"   
    revocationMode="Offline"  
    includeWindowsGroups="false"   
    mapClientCertificateToWindowsAccount="true" />  
  </clientCertificate>  
 </behavior>  
</serviceBehaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c66d6-194">関連項目</span><span class="sxs-lookup"><span data-stu-id="c66d6-194">See Also</span></span>  
 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>  
 <xref:System.ServiceModel.Security.X509CertificateValidationMode>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>  
 <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>  
 [<span data-ttu-id="c66d6-195">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="c66d6-195">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="c66d6-196">方法: カスタム証明書検証を使用するサービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="c66d6-196">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [<span data-ttu-id="c66d6-197">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="c66d6-197">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)

---
title: "&lt;serviceCredentials&gt; の &lt;serviceCertificate&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 597ae6d5-4938-4950-9f5e-b2280e816182
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 23f56c85f4fbea7eb1ccc41a7b520b2166158fbc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltservicecertificategt-of-ltservicecredentialsgt"></a><span data-ttu-id="d2e0c-102">&lt;serviceCredentials&gt; の &lt;serviceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="d2e0c-102">&lt;serviceCertificate&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="d2e0c-103">メッセージ セキュリティ モードを使用しているクライアントへのサービスの認証に使用する X.509 証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-103">Specify an X.509 certificate that will be used to authenticate the service to clients using Message security mode.</span></span>  
  
 <span data-ttu-id="d2e0c-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d2e0c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d2e0c-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="d2e0c-105">\<behaviors></span></span>  
<span data-ttu-id="d2e0c-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="d2e0c-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="d2e0c-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="d2e0c-107">\<behavior></span></span>  
<span data-ttu-id="d2e0c-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="d2e0c-108">\<serviceCredentials></span></span>  
<span data-ttu-id="d2e0c-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="d2e0c-109">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2e0c-110">構文</span><span class="sxs-lookup"><span data-stu-id="d2e0c-110">Syntax</span></span>  
  
```xml  
<serviceCertificate findValue="String"   
    storeLocation="LocalMachine/CurrentUser"  
    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2e0c-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d2e0c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d2e0c-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2e0c-113">属性</span><span class="sxs-lookup"><span data-stu-id="d2e0c-113">Attributes</span></span>  
  
|<span data-ttu-id="d2e0c-114">属性</span><span class="sxs-lookup"><span data-stu-id="d2e0c-114">Attribute</span></span>|<span data-ttu-id="d2e0c-115">説明</span><span class="sxs-lookup"><span data-stu-id="d2e0c-115">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="d2e0c-116">X.509 証明書ストアで検索する値を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-116">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="d2e0c-117">属性に含まれている型は、指定された X509FindType の要件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-117">The type contained in the attribute must satisfy the requirements of the specified X509FindType.</span></span> <span data-ttu-id="d2e0c-118">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-118">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="d2e0c-119">クライアントがサーバーの証明書の検証に使用する X.509 証明書ストアの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-119">Specifies the location of the X.509 certificate store that the client uses to validate the server’s certificate against.</span></span> <span data-ttu-id="d2e0c-120">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d2e0c-121">-LocalMachine: ローカル マシンに割り当てられている証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-121">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="d2e0c-122">-CurrentUser: 現在のユーザーに割り当てられている証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-122">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="d2e0c-123">既定は LocalMachine です。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-123">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="d2e0c-124">開く X.509 証明書ストアの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-124">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="d2e0c-125">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-125">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d2e0c-126">-AddressBook: 他のユーザーのストアの証明書します。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-126">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="d2e0c-127">-AuthRoot: サードパーティ証明機関 (Ca) のストアの証明書します。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-127">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="d2e0c-128">-CertificatAuthority: 中間証明機関 (Ca) 証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-128">-   CertificatAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="d2e0c-129">-Disallowed: 失効した証明書のストアの証明書します。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-129">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="d2e0c-130">-My: 証明書しますストアの個人用証明書。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-130">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="d2e0c-131">信頼されたルート証明機関 (Ca) のルート: 証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-131">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="d2e0c-132">-TrustedPeople: 直接信頼されたユーザーやリソースのストアの証明書します。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-132">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="d2e0c-133">-TrustedPublisher: 直接信頼された発行者のストアの証明書します。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-133">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="d2e0c-134">既定値は My です。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-134">The default is My.</span></span>|  
|`x509FindType`|<span data-ttu-id="d2e0c-135">実行する X.509 検索の種類を定義します。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-135">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="d2e0c-136">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-136">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d2e0c-137">は、FindByThumbprint</span><span class="sxs-lookup"><span data-stu-id="d2e0c-137">-   FindByThumbprint</span></span><br /><span data-ttu-id="d2e0c-138">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="d2e0c-138">-   FindBySubjectName</span></span><br /><span data-ttu-id="d2e0c-139">-Findbysubjectdistinguishedname です。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-139">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="d2e0c-140">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="d2e0c-140">-   FindByIssuerName</span></span><br /><span data-ttu-id="d2e0c-141">-FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="d2e0c-141">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="d2e0c-142">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="d2e0c-142">-   FindBySerialNumber</span></span><br /><span data-ttu-id="d2e0c-143">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="d2e0c-143">-   FindByTimeValid</span></span><br /><span data-ttu-id="d2e0c-144">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="d2e0c-144">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="d2e0c-145">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="d2e0c-145">-   FindByTemplateName</span></span><br /><span data-ttu-id="d2e0c-146">-FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="d2e0c-146">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="d2e0c-147">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="d2e0c-147">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="d2e0c-148">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="d2e0c-148">-   FindByExtension</span></span><br /><span data-ttu-id="d2e0c-149">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="d2e0c-149">-   FindByKeyUsage</span></span><br /><span data-ttu-id="d2e0c-150">-Findbysubjectkeyidentifier です。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-150">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="d2e0c-151">`findValue` 属性に含まれている型は、指定された X509FindType の要件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-151">The type contained in the `findValue` attribute must satisfy the requirements of the specified X509FindType.</span></span><br /><br /> <span data-ttu-id="d2e0c-152">既定値は FindBySubjectDistinguishedName です。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-152">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2e0c-153">子要素</span><span class="sxs-lookup"><span data-stu-id="d2e0c-153">Child Elements</span></span>  
 <span data-ttu-id="d2e0c-154">なし</span><span class="sxs-lookup"><span data-stu-id="d2e0c-154">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d2e0c-155">親要素</span><span class="sxs-lookup"><span data-stu-id="d2e0c-155">Parent Elements</span></span>  
  
|<span data-ttu-id="d2e0c-156">要素</span><span class="sxs-lookup"><span data-stu-id="d2e0c-156">Element</span></span>|<span data-ttu-id="d2e0c-157">説明</span><span class="sxs-lookup"><span data-stu-id="d2e0c-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d2e0c-158">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="d2e0c-158">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="d2e0c-159">サービスの認証に使用される資格情報と、クライアントの資格情報検証関連の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-159">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2e0c-160">コメント</span><span class="sxs-lookup"><span data-stu-id="d2e0c-160">Remarks</span></span>  
 <span data-ttu-id="d2e0c-161">メッセージ セキュリティ モードを使用しているクライアントへのサービスの認証に使用する X.509 証明書を指定するには、この要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-161">Use this element to specify an X.509 certificate that will be used to authenticate the service to clients using Message security mode.</span></span> <span data-ttu-id="d2e0c-162">定期的に更新される証明書を使用している場合は、証明書のサムプリントが変更されます。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-162">If you are using a certificate that will be periodically renewed, then its thumbprint will change.</span></span> <span data-ttu-id="d2e0c-163">その場合、証明書を同じサブジェクト名で再発行できるため、`x509FindType` としてサブジェクト名を使用します。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-163">In that case, use the subject name as the `x509FindType` because the certificate can be reissued with the same subject name.</span></span>  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="d2e0c-164">参照してください、要素を使用して[する方法: クライアントの資格情報の値を指定](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)です。</span><span class="sxs-lookup"><span data-stu-id="d2e0c-164"> using the element, see [How to: Specify Client Credential Values](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2e0c-165">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2e0c-165">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>  
 <xref:System.ServiceModel.Description.ServiceCredentials.ServiceCertificate%2A>  
 [<span data-ttu-id="d2e0c-166">方法: クライアントの資格情報の値を指定する</span><span class="sxs-lookup"><span data-stu-id="d2e0c-166">How to: Specify Client Credential Values</span></span>](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)  
 [<span data-ttu-id="d2e0c-167">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="d2e0c-167">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)

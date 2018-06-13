---
title: '&lt;basicHttpBinding&gt; の &lt;transport&gt;'
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: 0111a1f0b7697caa584cd7fc45ad6347207100ea
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751270"
---
# <a name="lttransportgt-of-ltbasichttpbindinggt"></a><span data-ttu-id="89331-102">&lt;basicHttpBinding&gt; の &lt;transport&gt;</span><span class="sxs-lookup"><span data-stu-id="89331-102">&lt;transport&gt; of &lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="89331-103">HTTP トランスポートの認証パラメーターを制御するプロパティを定義します。</span><span class="sxs-lookup"><span data-stu-id="89331-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
 <span data-ttu-id="89331-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="89331-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="89331-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="89331-105">\<bindings></span></span>  
<span data-ttu-id="89331-106">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="89331-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="89331-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="89331-107">\<binding></span></span>  
<span data-ttu-id="89331-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="89331-108">\<security></span></span>  
<span data-ttu-id="89331-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="89331-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89331-110">構文</span><span class="sxs-lookup"><span data-stu-id="89331-110">Syntax</span></span>  
  
```xml  
<basicHttpBinding>  
    <binding>  
        <security  
        mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"  
             proxyCredentialType="None|Basic|Digest|Ntlm|Windows" realm="string" >  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</basicHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89331-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="89331-111">Attributes and Elements</span></span>  
 <span data-ttu-id="89331-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="89331-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89331-113">属性</span><span class="sxs-lookup"><span data-stu-id="89331-113">Attributes</span></span>  
  
|<span data-ttu-id="89331-114">属性</span><span class="sxs-lookup"><span data-stu-id="89331-114">Attribute</span></span>|<span data-ttu-id="89331-115">説明</span><span class="sxs-lookup"><span data-stu-id="89331-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="89331-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="89331-116">clientCredentialType</span></span>|<span data-ttu-id="89331-117">-HTTP 認証を使用してクライアント認証を実行するときに使用される資格情報の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="89331-117">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="89331-118">既定値は、`None` です。</span><span class="sxs-lookup"><span data-stu-id="89331-118">The default is `None`.</span></span> <span data-ttu-id="89331-119">この属性は <xref:System.ServiceModel.HttpClientCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="89331-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="89331-120">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="89331-120">proxyCredentialType</span></span>|<span data-ttu-id="89331-121">-Over HTTP プロキシを使用して、ドメイン内からクライアント認証を実行するときに使用される資格情報の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="89331-121">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="89331-122">この属性は、親 `mode` 要素の `security` 属性が `Transport` または `TransportCredentialsOnly` の場合にだけ適用されます。</span><span class="sxs-lookup"><span data-stu-id="89331-122">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="89331-123">この属性は <xref:System.ServiceModel.HttpProxyCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="89331-123">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="89331-124">realm</span><span class="sxs-lookup"><span data-stu-id="89331-124">realm</span></span>|<span data-ttu-id="89331-125">ダイジェストまたは基本認証の HTTP 認証方式によって使用されるレルムを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="89331-125">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="89331-126">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="89331-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="89331-127">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="89331-127">policyEnforcement</span></span>|<span data-ttu-id="89331-128">この列挙体は、<xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> を適用するタイミングを指定します。</span><span class="sxs-lookup"><span data-stu-id="89331-128">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="89331-129">1.Never – ポリシーが適用されることはありません (拡張保護は無効になります)。</span><span class="sxs-lookup"><span data-stu-id="89331-129">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="89331-130">2.WhenSupported – ポリシーが適用されるのは、クライアントが拡張保護をサポートしている場合のみです。</span><span class="sxs-lookup"><span data-stu-id="89331-130">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="89331-131">3.Always – ポリシーは常に適用されます。</span><span class="sxs-lookup"><span data-stu-id="89331-131">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="89331-132">拡張保護をサポートしていないクライアントは認証に失敗します。</span><span class="sxs-lookup"><span data-stu-id="89331-132">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="89331-133">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="89331-133">protectionScenario</span></span>|<span data-ttu-id="89331-134">この列挙体は、ポリシーによって適用される保護シナリオを指定します。</span><span class="sxs-lookup"><span data-stu-id="89331-134">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="89331-135">clientCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="89331-135">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="89331-136">値</span><span class="sxs-lookup"><span data-stu-id="89331-136">Value</span></span>|<span data-ttu-id="89331-137">説明</span><span class="sxs-lookup"><span data-stu-id="89331-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="89331-138">なし</span><span class="sxs-lookup"><span data-stu-id="89331-138">None</span></span>|<span data-ttu-id="89331-139">メッセージは、転送中はセキュリティで保護されません。</span><span class="sxs-lookup"><span data-stu-id="89331-139">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="89331-140">Basic</span><span class="sxs-lookup"><span data-stu-id="89331-140">Basic</span></span>|<span data-ttu-id="89331-141">基本認証を指定します。</span><span class="sxs-lookup"><span data-stu-id="89331-141">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="89331-142">Digest</span><span class="sxs-lookup"><span data-stu-id="89331-142">Digest</span></span>|<span data-ttu-id="89331-143">ダイジェスト認証を指定します。</span><span class="sxs-lookup"><span data-stu-id="89331-143">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="89331-144">Ntlm</span><span class="sxs-lookup"><span data-stu-id="89331-144">Ntlm</span></span>|<span data-ttu-id="89331-145">Windows 認証に失敗した場合で可能な場合は、NTLM 認証を指定します。</span><span class="sxs-lookup"><span data-stu-id="89331-145">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="89331-146">Windows</span><span class="sxs-lookup"><span data-stu-id="89331-146">Windows</span></span>|<span data-ttu-id="89331-147">Windows 統合認証を指定します。</span><span class="sxs-lookup"><span data-stu-id="89331-147">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="89331-148">proxyCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="89331-148">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="89331-149">値</span><span class="sxs-lookup"><span data-stu-id="89331-149">Value</span></span>|<span data-ttu-id="89331-150">説明</span><span class="sxs-lookup"><span data-stu-id="89331-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="89331-151">なし</span><span class="sxs-lookup"><span data-stu-id="89331-151">None</span></span>|<span data-ttu-id="89331-152">メッセージの数は、転送中にセキュリティ保護されていません。</span><span class="sxs-lookup"><span data-stu-id="89331-152">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="89331-153">Basic</span><span class="sxs-lookup"><span data-stu-id="89331-153">Basic</span></span>|<span data-ttu-id="89331-154">RFC 2617 『HTTP Authentication: Basic and Digest Authentication』で定義されているとおりに基本認証を指定します。</span><span class="sxs-lookup"><span data-stu-id="89331-154">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="89331-155">Digest</span><span class="sxs-lookup"><span data-stu-id="89331-155">Digest</span></span>|<span data-ttu-id="89331-156">RFC 2617 『HTTP Authentication: Basic and Digest Authentication』で定義されているとおりにダイジェスト認証を指定します。</span><span class="sxs-lookup"><span data-stu-id="89331-156">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="89331-157">Ntlm</span><span class="sxs-lookup"><span data-stu-id="89331-157">Ntlm</span></span>|<span data-ttu-id="89331-158">Windows 認証に失敗した場合で可能な場合は、NTLM 認証を指定します。</span><span class="sxs-lookup"><span data-stu-id="89331-158">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="89331-159">Windows</span><span class="sxs-lookup"><span data-stu-id="89331-159">Windows</span></span>|<span data-ttu-id="89331-160">Windows 統合認証を指定します。</span><span class="sxs-lookup"><span data-stu-id="89331-160">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="89331-161">証明書</span><span class="sxs-lookup"><span data-stu-id="89331-161">Certificate</span></span>|<span data-ttu-id="89331-162">証明書を使用したクライアント認証を実行します。</span><span class="sxs-lookup"><span data-stu-id="89331-162">Performs client authentication using a certificate.</span></span> <span data-ttu-id="89331-163">このオプションは、親要素の `Mode` の `security` 属性が Transport に設定されている場合のみ機能し、TransportCredentialOnly に設定されている場合は機能しません。</span><span class="sxs-lookup"><span data-stu-id="89331-163">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89331-164">子要素</span><span class="sxs-lookup"><span data-stu-id="89331-164">Child Elements</span></span>  
 <span data-ttu-id="89331-165">なし</span><span class="sxs-lookup"><span data-stu-id="89331-165">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89331-166">親要素</span><span class="sxs-lookup"><span data-stu-id="89331-166">Parent Elements</span></span>  
  
|<span data-ttu-id="89331-167">要素</span><span class="sxs-lookup"><span data-stu-id="89331-167">Element</span></span>|<span data-ttu-id="89331-168">説明</span><span class="sxs-lookup"><span data-stu-id="89331-168">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89331-169">\<security></span><span class="sxs-lookup"><span data-stu-id="89331-169">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="89331-170">セキュリティ機能を定義、 [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="89331-170">Defines the security capabilities for the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="89331-171">例</span><span class="sxs-lookup"><span data-stu-id="89331-171">Example</span></span>  
 <span data-ttu-id="89331-172">基本的なバインディングを使用した SSL トランスポート セキュリティの使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="89331-172">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="89331-173">既定で、基本的なバインディングは HTTP 通信をサポートします。</span><span class="sxs-lookup"><span data-stu-id="89331-173">By default, the basic binding supports HTTP communication.</span></span>  
  
```xml  
<system.serviceModel>  
   <services>  
      <service   
          type="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
         <endpoint address=""  
               binding="basicHttpBinding"  
               bindingConfiguration="Binding1"   
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
      </service>  
   </services>  
    <bindings>  
        <basicHttpBinding>  
        <!-- Configure basicHttpBinding with Transport security -- >  
        <!-- mode and clientCredentialType set to None.-->  
           <binding name="Binding1">  
               <security mode="Transport">  
                   <transport clientCredentialType="None"  
                              proxyCredentialType="None">  
                       <extendedProtectionPolicy  
                          policyEnforcement="WhenSupported"  
                          protectionScenario="TransportSelected">  
                    <customServiceNames></customServiceNames>  
                       </extendedProtectionPolicy>  
               </security>  
           </binding>  
        </basicHttpBinding>  
    </bindings>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="89331-174">関連項目</span><span class="sxs-lookup"><span data-stu-id="89331-174">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 [<span data-ttu-id="89331-175">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="89331-175">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="89331-176">バインディング</span><span class="sxs-lookup"><span data-stu-id="89331-176">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="89331-177">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="89331-177">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="89331-178">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="89331-178">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="89331-179">\<binding></span><span class="sxs-lookup"><span data-stu-id="89331-179">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

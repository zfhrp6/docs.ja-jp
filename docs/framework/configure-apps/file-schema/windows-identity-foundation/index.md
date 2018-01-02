---
title: "Windows Identity Foundation 構成スキーマ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d4f6d76-49a5-4bad-b345-097b2e2844e9
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 2000ae86f38ff2fd06dbe7424cbfdd74781c6c3c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="windows-identity-foundation-configuration-schema"></a><span data-ttu-id="59713-102">Windows Identity Foundation 構成スキーマ</span><span class="sxs-lookup"><span data-stu-id="59713-102">Windows Identity Foundation Configuration Schema</span></span>
<span data-ttu-id="59713-103">このセクションのトピックでは、Windows Identity Foundation (WIF) の構成スキーマに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="59713-103">The topics in this section provide information about the Windows Identity Foundation (WIF) configuration schema.</span></span> <span data-ttu-id="59713-104">フレームワークによって公開されたクラスを介して WIF を使用するようにアプリケーションを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="59713-104">You can also configure an application to use WIF through classes exposed by the framework,.</span></span> <span data-ttu-id="59713-105">これらのクラスは、スキーマ内の関連要素を処理するセクションに記載されています。</span><span class="sxs-lookup"><span data-stu-id="59713-105">These classes are noted in the sections that treat relevant elements in the schema.</span></span> <span data-ttu-id="59713-106">次に示すのは、WIF 構成スキーマによって公開された基本的な XML タグ構造です。</span><span class="sxs-lookup"><span data-stu-id="59713-106">The following shows the basic XML tag structure exposed by the WIF configuration schema.</span></span> <span data-ttu-id="59713-107">属性は省略されています。</span><span class="sxs-lookup"><span data-stu-id="59713-107">Attributes are omitted.</span></span> <span data-ttu-id="59713-108">強調表示したコメントは、スキーマの主要なコンポーネントを示しています。</span><span class="sxs-lookup"><span data-stu-id="59713-108">Highlighted comments indicate major components of the schema.</span></span>  
  
```xml  
<system.identityModel>  
    <!-- Service Configuration -->  
    <identityConfiguration>  
        <caches>  
            <sessionSecurityTokenCache />  
            <tokenReplayCache />  
        </caches>  
  
        <certificateValidation>  
            <certificateValidator />   
        </certificateValidation>  
  
        <claimsAuthenticationManager />  
  
        <claimsAuthorizationManager>  
            <optionalConfigurationElement>  
        </claimsAuthorizationManager>  
  
        <claimTypeRequired>  
            <claimType />   
        </claimTypeRequired>  
  
        <tokenReplayDetection />  
  
        <!-- Security Token Handler Collection Configuration -->  
        <securityTokenHandlers>  
            <add>  
                <!-- Can take an optional configuration element which can be one of  
                     the following or a custom element -->  
                <samlSecurityTokenHandlerRequirement>  
                    <nameClaimType>  
                    <roleClaimType>   
                </samlSecurityTokenHandlerRequirement>  
  
                <sessionSecurityTokenHandlerRequirement />  
                <x509SecurityTokenHandlerRequirement />  
                <userNameSecurityTokenHandlerRequirement />  
            </add>  
            <clear />  
            <remove />  
            <securityTokenHandlerConfiguration>  
                <audienceUris>  
                    <add>  
                    <clear>  
                    <remove>  
                </audienceUris>  
  
                <caches>  
                    <sessionSecurityTokenCache />  
                    <tokenReplayCache />  
                </caches>  
  
                <certificateValidation>  
                    <certificateValidator>   
                </certificateValidation>  
  
                <issuerNameRegistry>  
                    <!-- Can take an optional configuration element which can be   
                         the <trustedIssuers> element to configure a configuration-based  
                         issuer name registry or can be a custom element -->  
                    <trustedIssuers>  
                        <add>  
                        <clear>  
                        <remove>  
                    </trustedIssuers>  
                </issuerNameRegistry>  
  
                <issuerTokenResolver />  
                <serviceTokenResolver />  
                <tokenReplayDetection />  
            </securityTokenHandlerConfiguration>  
        </securityTokenHandlers>  
    </identityConfiguration>  
</system.identityModel>  
  
<system.identityModel.services>  
    <!-- Federation Authentication Configuration -->  
    <federatedAuthentication>  
        <cookieHandler>  
            <chunkedCookieHandler />  
            <customCookieHandler />  
        </cookieHandler>  
  
        <serviceCertificate>  
            <certificateReference>  
        </serviceCertificate>  
  
        <wsFederation />  
    </federatedAuthentication>  
</system.identityModel.services>  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="59713-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="59713-109">In This Section</span></span>  
 <span data-ttu-id="59713-110">[\<system.identityModel>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) アプリケーションで WIF オプションを有効にするための構成を指定します。</span><span class="sxs-lookup"><span data-stu-id="59713-110">[\<system.identityModel>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) Provides configuration for enabling WIF options in applications.</span></span>  
  
 <span data-ttu-id="59713-111">[\<system.identityModel.services>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) WIF を使用するパッシブなフェデレーションの構成を指定します。</span><span class="sxs-lookup"><span data-stu-id="59713-111">[\<system.identityModel.services>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) Provides configuration for passive federation using WIF.</span></span> <span data-ttu-id="59713-112">セッション認証モジュール (SAM) とフェデレーション認証モジュール (WSFAM) を構成します。</span><span class="sxs-lookup"><span data-stu-id="59713-112">Configures the Session Authentication Module (SAM) and the Federated Authentication Module (WSFAM).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="59713-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="59713-113">Related Sections</span></span>  
 <span data-ttu-id="59713-114">[構成と管理](http://msdn.microsoft.com/en-us/1e03c389-de2c-4096-aaff-86b087e1bea0) WIF アプリケーションおよびサービスを構成および管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="59713-114">[Configuration, Administration, And Management](http://msdn.microsoft.com/en-us/1e03c389-de2c-4096-aaff-86b087e1bea0) Describes how to configure and manage WIF applications and services.</span></span>

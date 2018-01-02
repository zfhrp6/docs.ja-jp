---
title: '&lt;system.identityModel&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: e5d26ab2ff3207b0905c33ba237bf71e623a103d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemidentitymodelgt"></a><span data-ttu-id="85184-102">&lt;system.identityModel&gt;</span><span class="sxs-lookup"><span data-stu-id="85184-102">&lt;system.identityModel&gt;</span></span>
<span data-ttu-id="85184-103">アプリケーションで Windows Identity Foundation (WIF) オプションを有効にするための構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="85184-103">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
 <span data-ttu-id="85184-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="85184-104">\<system.identityModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85184-105">構文</span><span class="sxs-lookup"><span data-stu-id="85184-105">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85184-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="85184-106">Attributes and Elements</span></span>  
 <span data-ttu-id="85184-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="85184-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85184-108">属性</span><span class="sxs-lookup"><span data-stu-id="85184-108">Attributes</span></span>  
 <span data-ttu-id="85184-109">なし</span><span class="sxs-lookup"><span data-stu-id="85184-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="85184-110">子要素</span><span class="sxs-lookup"><span data-stu-id="85184-110">Child Elements</span></span>  
  
|<span data-ttu-id="85184-111">要素</span><span class="sxs-lookup"><span data-stu-id="85184-111">Element</span></span>|<span data-ttu-id="85184-112">説明</span><span class="sxs-lookup"><span data-stu-id="85184-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85184-113">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="85184-113">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="85184-114">サービス レベルの id 設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="85184-114">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="85184-115">親要素</span><span class="sxs-lookup"><span data-stu-id="85184-115">Parent Elements</span></span>  
  
|<span data-ttu-id="85184-116">要素</span><span class="sxs-lookup"><span data-stu-id="85184-116">Element</span></span>|<span data-ttu-id="85184-117">説明</span><span class="sxs-lookup"><span data-stu-id="85184-117">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="85184-118">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="85184-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85184-119">コメント</span><span class="sxs-lookup"><span data-stu-id="85184-119">Remarks</span></span>  
 <span data-ttu-id="85184-120">追加、`<system.identityModel>`サービスまたは Windows Identity Foundation (WIF) を使用するアプリケーションを構成する構成ファイルにセクションです。</span><span class="sxs-lookup"><span data-stu-id="85184-120">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="85184-121">`<system.identityModel>`要素として表されます、<xref:System.IdentityModel.Configuration.SystemIdentityModelSection>クラスです。</span><span class="sxs-lookup"><span data-stu-id="85184-121">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85184-122">例</span><span class="sxs-lookup"><span data-stu-id="85184-122">Example</span></span>  
 <span data-ttu-id="85184-123">次の例は、追加する方法を示します、`<system.identityModel>`構成ファイルにセクションです。</span><span class="sxs-lookup"><span data-stu-id="85184-123">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="85184-124">構成セクションと名前空間の宣言を追加する必要があります最初、`<configSections>`要素。</span><span class="sxs-lookup"><span data-stu-id="85184-124">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="85184-125">追加することができ、`<system.IdentityModel>`要素を構成ファイルを 1 つまたは複数の id 構成を指定します。</span><span class="sxs-lookup"><span data-stu-id="85184-125">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
    <!--WIF 4.5 sections -->  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
  </configSections>  
  
  ...  
  
  <system.identityModel>  
    <identityConfiguration>  
      <audienceUris>  
        <add value="http://localhost/WebApplication1/" />  
      </audienceUris>  
      <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089">  
        <trustedIssuers>  
          <add thumbprint="313D3B … 9106A9EC" name="SelfSTS" />  
        </trustedIssuers>  
      </issuerNameRegistry>  
      <certificateValidation certificateValidationMode="None"/>  
    </identityConfiguration>  
  </system.identityModel>  
  
  ...  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="85184-126">参照</span><span class="sxs-lookup"><span data-stu-id="85184-126">See Also</span></span>  
 <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>

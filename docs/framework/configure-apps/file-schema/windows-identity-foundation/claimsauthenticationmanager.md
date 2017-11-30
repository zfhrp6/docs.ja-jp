---
title: '&lt;claimsAuthenticationManager&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 48e5be23b196a24a9d3e2a1dc4639d8ca9823660
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltclaimsauthenticationmanagergt"></a><span data-ttu-id="b099e-102">&lt;claimsAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="b099e-102">&lt;claimsAuthenticationManager&gt;</span></span>
<span data-ttu-id="b099e-103">入力方向の要求の要求認証マネージャーに登録します。</span><span class="sxs-lookup"><span data-stu-id="b099e-103">Registers a claims authentication manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="b099e-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="b099e-104">\<system.identityModel></span></span>  
<span data-ttu-id="b099e-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b099e-105">\<identityConfiguration></span></span>  
<span data-ttu-id="b099e-106">\<claimsAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="b099e-106">\<claimsAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b099e-107">構文</span><span class="sxs-lookup"><span data-stu-id="b099e-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b099e-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b099e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b099e-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b099e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b099e-110">属性</span><span class="sxs-lookup"><span data-stu-id="b099e-110">Attributes</span></span>  
  
|<span data-ttu-id="b099e-111">属性</span><span class="sxs-lookup"><span data-stu-id="b099e-111">Attribute</span></span>|<span data-ttu-id="b099e-112">説明</span><span class="sxs-lookup"><span data-stu-id="b099e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b099e-113">型</span><span class="sxs-lookup"><span data-stu-id="b099e-113">type</span></span>|<span data-ttu-id="b099e-114">派生するカスタム型を指定します、<xref:System.Security.Claims.ClaimsAuthenticationManager>クラスです。</span><span class="sxs-lookup"><span data-stu-id="b099e-114">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="b099e-115">指定する方法について、`type`属性 [カスタム型の参照] を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b099e-115">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b099e-116">子要素</span><span class="sxs-lookup"><span data-stu-id="b099e-116">Child Elements</span></span>  
 <span data-ttu-id="b099e-117">ある場合ありません`type`属性、または、`type`属性参照、<xref:System.Security.Claims.ClaimsAuthenticationManager>クラス、`<claimsAuthenticationManager>`要素が子要素を受け取らないです。 ただし、から派生したクラス<xref:System.Security.Claims.ClaimsAuthenticationManager>子の構成要素を定義できます。</span><span class="sxs-lookup"><span data-stu-id="b099e-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b099e-118">親要素</span><span class="sxs-lookup"><span data-stu-id="b099e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b099e-119">要素</span><span class="sxs-lookup"><span data-stu-id="b099e-119">Element</span></span>|<span data-ttu-id="b099e-120">説明</span><span class="sxs-lookup"><span data-stu-id="b099e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b099e-121">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b099e-121">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="b099e-122">サービス レベルの id 設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="b099e-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b099e-123">コメント</span><span class="sxs-lookup"><span data-stu-id="b099e-123">Remarks</span></span>  
 <span data-ttu-id="b099e-124">によって提供される既定の動作、<xref:System.Security.Claims.ClaimsAuthenticationManager>クラスには、入力方向の要求がエコーされます。</span><span class="sxs-lookup"><span data-stu-id="b099e-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="b099e-125">ない場合は`type`属性が指定されて場合、または、`type`属性を指定、<xref:System.Security.Claims.ClaimsAuthenticationManager>クラス、`<claimsAuthenticationManager>`要素は子要素を取りません。</span><span class="sxs-lookup"><span data-stu-id="b099e-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="b099e-126">指定することができます、`type`から派生した型を登録する属性、<xref:System.Security.Claims.ClaimsAuthenticationManager>カスタム動作を実装するクラス。</span><span class="sxs-lookup"><span data-stu-id="b099e-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="b099e-127">派生クラスの子要素から構成をサポートできる、`<claimsAuthenticationManager>`要素をオーバーライドすることで、<xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A>これらの要素を処理するメソッド。</span><span class="sxs-lookup"><span data-stu-id="b099e-127">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="b099e-128">子要素に定義されたスキーマは、クラスの設計者の責任です。</span><span class="sxs-lookup"><span data-stu-id="b099e-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="b099e-129">`<claimsAuthenticationManager>`要素セット、<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="b099e-129">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b099e-130">例</span><span class="sxs-lookup"><span data-stu-id="b099e-130">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</microsoft.identityModel>  
```

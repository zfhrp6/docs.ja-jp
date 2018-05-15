---
title: '&lt;remove&gt;'
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: dfea0b0eb4b133308f10b523a659cc00f87252b8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltremovegt"></a><span data-ttu-id="27d08-102">&lt;remove&gt;</span><span class="sxs-lookup"><span data-stu-id="27d08-102">&lt;remove&gt;</span></span>
<span data-ttu-id="27d08-103">トークン ハンドラー コレクションから指定したセキュリティ トークン ハンドラーを削除します。</span><span class="sxs-lookup"><span data-stu-id="27d08-103">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="27d08-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="27d08-104">\<system.identityModel></span></span>  
<span data-ttu-id="27d08-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="27d08-105">\<identityConfiguration></span></span>  
<span data-ttu-id="27d08-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="27d08-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="27d08-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="27d08-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27d08-108">構文</span><span class="sxs-lookup"><span data-stu-id="27d08-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <remove type=xs:string >  
      </remove>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27d08-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="27d08-109">Attributes and Elements</span></span>  
 <span data-ttu-id="27d08-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="27d08-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27d08-111">属性</span><span class="sxs-lookup"><span data-stu-id="27d08-111">Attributes</span></span>  
  
|<span data-ttu-id="27d08-112">属性</span><span class="sxs-lookup"><span data-stu-id="27d08-112">Attribute</span></span>|<span data-ttu-id="27d08-113">説明</span><span class="sxs-lookup"><span data-stu-id="27d08-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="27d08-114">型</span><span class="sxs-lookup"><span data-stu-id="27d08-114">type</span></span>|<span data-ttu-id="27d08-115">削除するトークン ハンドラーの CLR 型名。</span><span class="sxs-lookup"><span data-stu-id="27d08-115">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="27d08-116">指定する方法について、`type`属性は、「[カスタム型の参照](http://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24)です。</span><span class="sxs-lookup"><span data-stu-id="27d08-116">For more information about how to specify the `type` attribute, see [Custom Type References](http://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span> <span data-ttu-id="27d08-117">必須。</span><span class="sxs-lookup"><span data-stu-id="27d08-117">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="27d08-118">子要素</span><span class="sxs-lookup"><span data-stu-id="27d08-118">Child Elements</span></span>  
 <span data-ttu-id="27d08-119">なし</span><span class="sxs-lookup"><span data-stu-id="27d08-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="27d08-120">親要素</span><span class="sxs-lookup"><span data-stu-id="27d08-120">Parent Elements</span></span>  
  
|<span data-ttu-id="27d08-121">要素</span><span class="sxs-lookup"><span data-stu-id="27d08-121">Element</span></span>|<span data-ttu-id="27d08-122">説明</span><span class="sxs-lookup"><span data-stu-id="27d08-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27d08-123">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="27d08-123">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="27d08-124">エンドポイントに登録されているセキュリティ トークン ハンドラーのコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="27d08-124">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="27d08-125">例</span><span class="sxs-lookup"><span data-stu-id="27d08-125">Example</span></span>  
 <span data-ttu-id="27d08-126">次の XML の使用方法を示します、`<add>`と`<remove>`に既定のセッション トークン ハンドラーをカスタム セッション トークン ハンドラーに置き換える要素。</span><span class="sxs-lookup"><span data-stu-id="27d08-126">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="27d08-127">XML を取得、`ClaimsAwareWebFarm`サンプルです。</span><span class="sxs-lookup"><span data-stu-id="27d08-127">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```

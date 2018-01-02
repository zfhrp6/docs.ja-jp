---
title: '&lt;remove&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 15c2561487eecb44cf3542768de0a77d1dd6713d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt"></a><span data-ttu-id="87dc5-102">&lt;remove&gt;</span><span class="sxs-lookup"><span data-stu-id="87dc5-102">&lt;remove&gt;</span></span>
<span data-ttu-id="87dc5-103">トークン ハンドラー コレクションから指定したセキュリティ トークン ハンドラーを削除します。</span><span class="sxs-lookup"><span data-stu-id="87dc5-103">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="87dc5-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="87dc5-104">\<system.identityModel></span></span>  
<span data-ttu-id="87dc5-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="87dc5-105">\<identityConfiguration></span></span>  
<span data-ttu-id="87dc5-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="87dc5-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="87dc5-107">\<削除 ></span><span class="sxs-lookup"><span data-stu-id="87dc5-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87dc5-108">構文</span><span class="sxs-lookup"><span data-stu-id="87dc5-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87dc5-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="87dc5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="87dc5-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="87dc5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87dc5-111">属性</span><span class="sxs-lookup"><span data-stu-id="87dc5-111">Attributes</span></span>  
  
|<span data-ttu-id="87dc5-112">属性</span><span class="sxs-lookup"><span data-stu-id="87dc5-112">Attribute</span></span>|<span data-ttu-id="87dc5-113">説明</span><span class="sxs-lookup"><span data-stu-id="87dc5-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87dc5-114">型</span><span class="sxs-lookup"><span data-stu-id="87dc5-114">type</span></span>|<span data-ttu-id="87dc5-115">削除するトークン ハンドラーの CLR 型名。</span><span class="sxs-lookup"><span data-stu-id="87dc5-115">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="87dc5-116">指定する方法について、`type`属性は、「[カスタム型の参照](http://msdn.microsoft.com/en-us/7286d2e3-c63d-49fd-abdc-ce2705f22c24)です。</span><span class="sxs-lookup"><span data-stu-id="87dc5-116">For more information about how to specify the `type` attribute, see [Custom Type References](http://msdn.microsoft.com/en-us/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span> <span data-ttu-id="87dc5-117">必須。</span><span class="sxs-lookup"><span data-stu-id="87dc5-117">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87dc5-118">子要素</span><span class="sxs-lookup"><span data-stu-id="87dc5-118">Child Elements</span></span>  
 <span data-ttu-id="87dc5-119">なし</span><span class="sxs-lookup"><span data-stu-id="87dc5-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87dc5-120">親要素</span><span class="sxs-lookup"><span data-stu-id="87dc5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="87dc5-121">要素</span><span class="sxs-lookup"><span data-stu-id="87dc5-121">Element</span></span>|<span data-ttu-id="87dc5-122">説明</span><span class="sxs-lookup"><span data-stu-id="87dc5-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87dc5-123">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="87dc5-123">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="87dc5-124">エンドポイントに登録されているセキュリティ トークン ハンドラーのコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="87dc5-124">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="87dc5-125">例</span><span class="sxs-lookup"><span data-stu-id="87dc5-125">Example</span></span>  
 <span data-ttu-id="87dc5-126">次の XML の使用方法を示します、`<add>`と`<remove>`に既定のセッション トークン ハンドラーをカスタム セッション トークン ハンドラーに置き換える要素。</span><span class="sxs-lookup"><span data-stu-id="87dc5-126">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="87dc5-127">XML を取得、`ClaimsAwareWebFarm`サンプルです。</span><span class="sxs-lookup"><span data-stu-id="87dc5-127">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```

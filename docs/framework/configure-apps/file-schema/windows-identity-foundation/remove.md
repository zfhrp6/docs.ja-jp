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
ms.openlocfilehash: fb62bbe8b52032708dddd62dd895e61ba8c1c5e9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="ltremovegt"></a><span data-ttu-id="78a0c-102">&lt;remove&gt;</span><span class="sxs-lookup"><span data-stu-id="78a0c-102">&lt;remove&gt;</span></span>
<span data-ttu-id="78a0c-103">トークン ハンドラー コレクションから指定したセキュリティ トークン ハンドラーを削除します。</span><span class="sxs-lookup"><span data-stu-id="78a0c-103">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="78a0c-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="78a0c-104">\<system.identityModel></span></span>  
<span data-ttu-id="78a0c-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="78a0c-105">\<identityConfiguration></span></span>  
<span data-ttu-id="78a0c-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="78a0c-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="78a0c-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="78a0c-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78a0c-108">構文</span><span class="sxs-lookup"><span data-stu-id="78a0c-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78a0c-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="78a0c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="78a0c-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="78a0c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78a0c-111">属性</span><span class="sxs-lookup"><span data-stu-id="78a0c-111">Attributes</span></span>  
  
|<span data-ttu-id="78a0c-112">属性</span><span class="sxs-lookup"><span data-stu-id="78a0c-112">Attribute</span></span>|<span data-ttu-id="78a0c-113">説明</span><span class="sxs-lookup"><span data-stu-id="78a0c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="78a0c-114">型</span><span class="sxs-lookup"><span data-stu-id="78a0c-114">type</span></span>|<span data-ttu-id="78a0c-115">削除するトークン ハンドラーの CLR 型名。</span><span class="sxs-lookup"><span data-stu-id="78a0c-115">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="78a0c-116">指定する方法について、`type`属性は、「[カスタム型の参照](http://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24)です。</span><span class="sxs-lookup"><span data-stu-id="78a0c-116">For more information about how to specify the `type` attribute, see [Custom Type References](http://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span> <span data-ttu-id="78a0c-117">必須。</span><span class="sxs-lookup"><span data-stu-id="78a0c-117">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="78a0c-118">子要素</span><span class="sxs-lookup"><span data-stu-id="78a0c-118">Child Elements</span></span>  
 <span data-ttu-id="78a0c-119">なし</span><span class="sxs-lookup"><span data-stu-id="78a0c-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="78a0c-120">親要素</span><span class="sxs-lookup"><span data-stu-id="78a0c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="78a0c-121">要素</span><span class="sxs-lookup"><span data-stu-id="78a0c-121">Element</span></span>|<span data-ttu-id="78a0c-122">説明</span><span class="sxs-lookup"><span data-stu-id="78a0c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78a0c-123">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="78a0c-123">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="78a0c-124">エンドポイントに登録されているセキュリティ トークン ハンドラーのコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="78a0c-124">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="78a0c-125">例</span><span class="sxs-lookup"><span data-stu-id="78a0c-125">Example</span></span>  
 <span data-ttu-id="78a0c-126">次の XML の使用方法を示します、`<add>`と`<remove>`に既定のセッション トークン ハンドラーをカスタム セッション トークン ハンドラーに置き換える要素。</span><span class="sxs-lookup"><span data-stu-id="78a0c-126">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="78a0c-127">XML を取得、`ClaimsAwareWebFarm`サンプルです。</span><span class="sxs-lookup"><span data-stu-id="78a0c-127">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```

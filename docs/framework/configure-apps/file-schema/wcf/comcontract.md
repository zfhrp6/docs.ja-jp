---
title: '&lt;comContract&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45f4fb83478ef7061a4b14e87d2dce7f9cd9bbf8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltcomcontractgt"></a><span data-ttu-id="becef-102">&lt;comContract&gt;</span><span class="sxs-lookup"><span data-stu-id="becef-102">&lt;comContract&gt;</span></span>
<span data-ttu-id="becef-103">COM+ 統合サービス コントラクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="becef-103">Specifies a COM+ integration service contract.</span></span>  
  
 <span data-ttu-id="becef-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="becef-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="becef-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="becef-105">\<comContracts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="becef-106">構文</span><span class="sxs-lookup"><span data-stu-id="becef-106">Syntax</span></span>  
  
```xml  
<comContracts>  
  <comContract  
      contract="string"  
      namespace="string"  
      name="string"  
      requireSession="Boolean">  
      <exposedMethods>  
         <exposedMethod name="string" />  
      </exposedMethods>  
      <userDefinedTypes>  
         <userDefinedType name="string"  
            typeLibID="string"  
            typeLibVersion="string"  
            typeDefID="string">  
         </userDefinedType>  
      </userDefinedTypes>  
      <persistableTypes>  
         <persistableType id="string"  
            name="string">  
         </persistableType>  
      </persistableTypes>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="becef-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="becef-107">Attributes and Elements</span></span>  
 <span data-ttu-id="becef-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="becef-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="becef-109">属性</span><span class="sxs-lookup"><span data-stu-id="becef-109">Attributes</span></span>  
  
|<span data-ttu-id="becef-110">属性</span><span class="sxs-lookup"><span data-stu-id="becef-110">Attribute</span></span>|<span data-ttu-id="becef-111">説明</span><span class="sxs-lookup"><span data-stu-id="becef-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="becef-112">コントラクト</span><span class="sxs-lookup"><span data-stu-id="becef-112">contract</span></span>|<span data-ttu-id="becef-113">コントラクトの種類を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="becef-113">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="becef-114">name</span><span class="sxs-lookup"><span data-stu-id="becef-114">name</span></span>|<span data-ttu-id="becef-115">コントラクト名を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="becef-115">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="becef-116">namespace</span><span class="sxs-lookup"><span data-stu-id="becef-116">namespace</span></span>|<span data-ttu-id="becef-117">コントラクトの名前空間を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="becef-117">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="becef-118">requiresSession</span><span class="sxs-lookup"><span data-stu-id="becef-118">requiresSession</span></span>|<span data-ttu-id="becef-119">コントラクトをセッションの多いバインディングでのみ使用できるかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="becef-119">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="becef-120">サービスが初期化される場合、統合ランタイムは、この設定が、使用されるバインディングの種類と一貫していることを保証します。</span><span class="sxs-lookup"><span data-stu-id="becef-120">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="becef-121">コントラクト内の 1 つ以上のバインディングが競合する場合は、例外が生成されます。</span><span class="sxs-lookup"><span data-stu-id="becef-121">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="becef-122">このプロパティが `false` で、一方向のチャネルを使用し、いずれかの [out] パラメーターが存在する場合は、例外も発生します。</span><span class="sxs-lookup"><span data-stu-id="becef-122">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="becef-123">子要素</span><span class="sxs-lookup"><span data-stu-id="becef-123">Child Elements</span></span>  
  
|<span data-ttu-id="becef-124">要素</span><span class="sxs-lookup"><span data-stu-id="becef-124">Element</span></span>|<span data-ttu-id="becef-125">説明</span><span class="sxs-lookup"><span data-stu-id="becef-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="becef-126">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="becef-126">persistableTypes</span></span>|<span data-ttu-id="becef-127">すべての永続型。</span><span class="sxs-lookup"><span data-stu-id="becef-127">All the persistable types.</span></span>|  
|<span data-ttu-id="becef-128">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="becef-128">userDefinedTypes</span></span>|<span data-ttu-id="becef-129">サービス コントラクトに含まれるユーザー定義型 (UDT) のコレクション。</span><span class="sxs-lookup"><span data-stu-id="becef-129">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="becef-130">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="becef-130">exposedMethods</span></span>|<span data-ttu-id="becef-131">COM+ コンポーネントのインターフェイスが Web サービスとして公開されるときに公開される COM+ メソッドのコレクション。</span><span class="sxs-lookup"><span data-stu-id="becef-131">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="becef-132">親要素</span><span class="sxs-lookup"><span data-stu-id="becef-132">Parent Elements</span></span>  
  
|<span data-ttu-id="becef-133">要素</span><span class="sxs-lookup"><span data-stu-id="becef-133">Element</span></span>|<span data-ttu-id="becef-134">説明</span><span class="sxs-lookup"><span data-stu-id="becef-134">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="becef-135">comContracts</span><span class="sxs-lookup"><span data-stu-id="becef-135">comContracts</span></span>|<span data-ttu-id="becef-136">`comContract` 要素のコレクションを含みます。</span><span class="sxs-lookup"><span data-stu-id="becef-136">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="becef-137">コメント</span><span class="sxs-lookup"><span data-stu-id="becef-137">Remarks</span></span>  
 <span data-ttu-id="becef-138">COM + 統合サービス コントラクトは現在"http://tempuri.org"名前空間に制限されてとコントラクト名がサポートする COM インターフェイスから派生します。</span><span class="sxs-lookup"><span data-stu-id="becef-138">COM+ integration service contracts are currently restricted to the "http://tempuri.org" namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="becef-139">ただし、構成ファイルの `comContracts` セクションと `comContract` 要素を使用して代替を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="becef-139">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="becef-140">たとえば、次の構成を使用して、名前空間、コントラクト名、組み込まれるユーザー定義型、およびサービス コントラクトのその他の設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="becef-140">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
      namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"  
      name="_Broker"  
      requireSession="true">  
      <exposedMethods>  
         <exposedMethod name="BuyStock" />  
         <exposedMethod name="SellStock" />  
         <exposedMethod name="ExecuteTransaction" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
 <span data-ttu-id="becef-141">サービスが初期化される場合、指定した名前空間およびコントラクト名が、生成されるサービスの説明に適用されます。</span><span class="sxs-lookup"><span data-stu-id="becef-141">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="becef-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="becef-142">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [<span data-ttu-id="becef-143">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="becef-143">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="becef-144">COM + アプリケーションとの統合</span><span class="sxs-lookup"><span data-stu-id="becef-144">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="becef-145">方法: COM + サービス設定の構成</span><span class="sxs-lookup"><span data-stu-id="becef-145">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)

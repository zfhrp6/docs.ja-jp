---
title: '&lt;exposedMethod&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ecef8049a980f662cce4c421f62ccd3703400d69
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltexposedmethodgt"></a><span data-ttu-id="7e242-102">&lt;exposedMethod&gt;</span><span class="sxs-lookup"><span data-stu-id="7e242-102">&lt;exposedMethod&gt;</span></span>
<span data-ttu-id="7e242-103">COM+ コンポーネントのインターフェイスが Web サービスとして公開されるときに公開される COM+ メソッドを表します。</span><span class="sxs-lookup"><span data-stu-id="7e242-103">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
 <span data-ttu-id="7e242-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7e242-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7e242-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="7e242-105">\<comContracts></span></span>  
<span data-ttu-id="7e242-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="7e242-106">\<comContract></span></span>  
<span data-ttu-id="7e242-107">\<メソッド ></span><span class="sxs-lookup"><span data-stu-id="7e242-107">\<methods></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e242-108">構文</span><span class="sxs-lookup"><span data-stu-id="7e242-108">Syntax</span></span>  
  
```xml  
<comContracts>  
  <comContract>  
      <exposedMethods>  
         <exposedMethod name="string" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e242-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7e242-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7e242-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7e242-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e242-111">属性</span><span class="sxs-lookup"><span data-stu-id="7e242-111">Attributes</span></span>  
  
|<span data-ttu-id="7e242-112">属性</span><span class="sxs-lookup"><span data-stu-id="7e242-112">Attribute</span></span>|<span data-ttu-id="7e242-113">説明</span><span class="sxs-lookup"><span data-stu-id="7e242-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7e242-114">name</span><span class="sxs-lookup"><span data-stu-id="7e242-114">name</span></span>|<span data-ttu-id="7e242-115">COM+ コンポーネントのインターフェイスが Web サービスとして公開されるときに公開される COM+ メソッドを含む文字列。</span><span class="sxs-lookup"><span data-stu-id="7e242-115">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e242-116">子要素</span><span class="sxs-lookup"><span data-stu-id="7e242-116">Child Elements</span></span>  
 <span data-ttu-id="7e242-117">なし。</span><span class="sxs-lookup"><span data-stu-id="7e242-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7e242-118">親要素</span><span class="sxs-lookup"><span data-stu-id="7e242-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7e242-119">要素</span><span class="sxs-lookup"><span data-stu-id="7e242-119">Element</span></span>|<span data-ttu-id="7e242-120">説明</span><span class="sxs-lookup"><span data-stu-id="7e242-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e242-121">\<exposedMethods ></span><span class="sxs-lookup"><span data-stu-id="7e242-121">\<exposedMethods></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethods.md)|<span data-ttu-id="7e242-122">コレクション[ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)要素。</span><span class="sxs-lookup"><span data-stu-id="7e242-122">A collection of [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e242-123">コメント</span><span class="sxs-lookup"><span data-stu-id="7e242-123">Remarks</span></span>  
 <span data-ttu-id="7e242-124">COM+ 統合構成ツール (ComSvcConfig.exe) を使用して、COM インターフェイスから特定のメソッドを追加して、生成されるサービス コントラクトに表示できます。</span><span class="sxs-lookup"><span data-stu-id="7e242-124">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="7e242-125">たとえば、次のコマンドを使用して、`IFinances`.Financial コンポーネントの `ItemOrders` COM インターフェイスから、3 つの名前付きメソッドを、生成されるサービス コントラクトに追加できます。</span><span class="sxs-lookup"><span data-stu-id="7e242-125">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="7e242-126">また、ComSvcConfig.exe を実行するときとして前述のメソッドを一覧表示する次のサービス コントラクトが生成されます[ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)要素。</span><span class="sxs-lookup"><span data-stu-id="7e242-126">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" name="IFinances" namespace="http://contoso.com/services/financial">  
    <exposedMethod name="TransferFunds"/>  
    <exposedMethod name="AddFunds"/>  
    <exposedMethod name="RemoveFunds"/>  
</comContract>  
```  
  
 <span data-ttu-id="7e242-127">サービスの初期化時に、ランタイムを反映しての一覧に含まれるメソッドのみを追加するサービス コントラクトの生成を試みます[ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)要素。</span><span class="sxs-lookup"><span data-stu-id="7e242-127">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) elements.</span></span> <span data-ttu-id="7e242-128">トレースは、サービス コントラクトに含まれないインターフェイス メソッド用に作成されます。</span><span class="sxs-lookup"><span data-stu-id="7e242-128">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e242-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e242-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComMethodElementCollection>  
 <xref:System.ServiceModel.Configuration.ComMethodElement>  
 [<span data-ttu-id="7e242-130">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="7e242-130">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="7e242-131">COM + アプリケーションとの統合</span><span class="sxs-lookup"><span data-stu-id="7e242-131">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="7e242-132">方法: COM + サービス設定の構成</span><span class="sxs-lookup"><span data-stu-id="7e242-132">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)

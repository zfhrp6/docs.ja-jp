---
title: '&lt;serviceActivations&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 43461f23476d1c387cec06f9aee893defa634201
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltserviceactivationsgt"></a><span data-ttu-id="d9706-102">&lt;serviceActivations&gt;</span><span class="sxs-lookup"><span data-stu-id="d9706-102">&lt;serviceActivations&gt;</span></span>
<span data-ttu-id="d9706-103">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] サービスの種類にマップする仮想サービス アクティベーション設定を定義する設定を追加できる構成要素。</span><span class="sxs-lookup"><span data-stu-id="d9706-103">A configuration element that allows you to add settings that define virtual service activation settings that map to your [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service types.</span></span> <span data-ttu-id="d9706-104">これにより、.svc ファイルを使用せずに、WAS/IIS でホストされているサービスをアクティブ化できます。</span><span class="sxs-lookup"><span data-stu-id="d9706-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>  
  
 <span data-ttu-id="d9706-105">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d9706-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="d9706-106">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="d9706-106">\<serviceHostingEnvironment></span></span>  
<span data-ttu-id="d9706-107">\<serviceActivations ></span><span class="sxs-lookup"><span data-stu-id="d9706-107">\<serviceActivations></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9706-108">構文</span><span class="sxs-lookup"><span data-stu-id="d9706-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <serviceActivations>  
      <add factory="String"  
           service="String"/>  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9706-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d9706-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d9706-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d9706-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9706-111">属性</span><span class="sxs-lookup"><span data-stu-id="d9706-111">Attributes</span></span>  
 <span data-ttu-id="d9706-112">なし。</span><span class="sxs-lookup"><span data-stu-id="d9706-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d9706-113">子要素</span><span class="sxs-lookup"><span data-stu-id="d9706-113">Child Elements</span></span>  
  
|<span data-ttu-id="d9706-114">要素</span><span class="sxs-lookup"><span data-stu-id="d9706-114">Element</span></span>|<span data-ttu-id="d9706-115">説明</span><span class="sxs-lookup"><span data-stu-id="d9706-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9706-116">\<add></span><span class="sxs-lookup"><span data-stu-id="d9706-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-serviceactivations.md)|<span data-ttu-id="d9706-117">サービス アプリケーションのアクティベーションを指定する構成要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="d9706-117">Adds a configuration element that specifies the activation of a service application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d9706-118">親要素</span><span class="sxs-lookup"><span data-stu-id="d9706-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d9706-119">要素</span><span class="sxs-lookup"><span data-stu-id="d9706-119">Element</span></span>|<span data-ttu-id="d9706-120">説明</span><span class="sxs-lookup"><span data-stu-id="d9706-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9706-121">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="d9706-121">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="d9706-122">環境をホストするサービスがインスタンス化する特定のトランスポートの型を定義します。</span><span class="sxs-lookup"><span data-stu-id="d9706-122">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9706-123">コメント</span><span class="sxs-lookup"><span data-stu-id="d9706-123">Remarks</span></span>  
 <span data-ttu-id="d9706-124">web.config ファイルでアクティベーション設定を構成する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="d9706-124">The following example shows how to configure activation settings within your web.config file.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <serviceHostingEnvironment>  
      <serviceActivations>  
        <add service="GreetingService"/>  
      </serviceActivations>  
    </serviceHostingEnvironment>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="d9706-125">この構成を使用して、.svc ファイルを使用せずに、GreetingService をアクティブ化できます。</span><span class="sxs-lookup"><span data-stu-id="d9706-125">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>  
  
 <span data-ttu-id="d9706-126">`<serviceHostingEnvironment>` はアプリケーション レベルの構成であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d9706-126">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="d9706-127">構成を格納した `web.config` は、仮想アプリケーションのルートの下に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9706-127">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="d9706-128">また、`serviceHostingEnvironment` は machinetoApplication の継承可能なセクションです。</span><span class="sxs-lookup"><span data-stu-id="d9706-128">In addition, `serviceHostingEnvironment` is a machinetoApplication inheritable section.</span></span> <span data-ttu-id="d9706-129">コンピューターのルートに単一のサービスを登録すると、アプリケーションの各サービスはこのサービスを継承します。</span><span class="sxs-lookup"><span data-stu-id="d9706-129">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>  
  
 <span data-ttu-id="d9706-130">構成ベースのアクティベーションは、http および非 http プロトコル経由のアクティベーションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="d9706-130">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="d9706-131">relatativeAddress では、.svc、.xoml、.xamlx などの拡張子が必要です。</span><span class="sxs-lookup"><span data-stu-id="d9706-131">It requires extensions in the relatativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="d9706-132">既知の buildProviders に対して独自の拡張子をマップできます。これにより、任意の拡張子を使用してサービスをアクティブ化できるようになります。</span><span class="sxs-lookup"><span data-stu-id="d9706-132">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="d9706-133">競合が発生した場合には、`<serviceActivations>` セクションにより、.svc の登録がオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="d9706-133">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9706-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9706-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>

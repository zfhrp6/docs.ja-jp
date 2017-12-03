---
title: "&lt;serviceActivations&gt; の &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c49845169265e48b232963ed5a2e6215be75d3fd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltserviceactivationsgt"></a><span data-ttu-id="448f1-102">&lt;serviceActivations&gt; の &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="448f1-102">&lt;add&gt; of &lt;serviceActivations&gt;</span></span>
<span data-ttu-id="448f1-103">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] サービスの種類にマップする仮想サービス アクティベーション設定を定義できる構成要素。</span><span class="sxs-lookup"><span data-stu-id="448f1-103">A configuration element that allows you to define virtual service activation settings that map to your [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service types.</span></span> <span data-ttu-id="448f1-104">これにより、.svc ファイルを使用せずに、WAS/IIS でホストされているサービスをアクティブ化できます。</span><span class="sxs-lookup"><span data-stu-id="448f1-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>  
  
 <span data-ttu-id="448f1-105">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="448f1-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="448f1-106">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="448f1-106">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="448f1-107">構文</span><span class="sxs-lookup"><span data-stu-id="448f1-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <serviceActivations>  
      <add factory="String"  
           service="String"/>  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="448f1-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="448f1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="448f1-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="448f1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="448f1-110">属性</span><span class="sxs-lookup"><span data-stu-id="448f1-110">Attributes</span></span>  
  
|<span data-ttu-id="448f1-111">属性</span><span class="sxs-lookup"><span data-stu-id="448f1-111">Attribute</span></span>|<span data-ttu-id="448f1-112">説明</span><span class="sxs-lookup"><span data-stu-id="448f1-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="448f1-113">factory</span><span class="sxs-lookup"><span data-stu-id="448f1-113">factory</span></span>|<span data-ttu-id="448f1-114">サービス アクティベーション要素を生成するファクトリの CLR 型名を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="448f1-114">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|  
|<span data-ttu-id="448f1-115">service</span><span class="sxs-lookup"><span data-stu-id="448f1-115">service</span></span>|<span data-ttu-id="448f1-116">サービスを実装する ServiceType (完全修飾 Typename または省略形の Typename (App_Code フォルダーに配置されている場合))。</span><span class="sxs-lookup"><span data-stu-id="448f1-116">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|  
|<span data-ttu-id="448f1-117">relativeAddress</span><span class="sxs-lookup"><span data-stu-id="448f1-117">relativeAddress</span></span>|<span data-ttu-id="448f1-118">現在の IIS アプリケーション内の相対アドレス (たとえば "Service.svc")。</span><span class="sxs-lookup"><span data-stu-id="448f1-118">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="448f1-119">WCF 4.0 ではこの相対アドレスが 1 個の既知のファイル拡張子 (.svc、.xamlx など) を含む必要があります。relativeUrl 用の物理ファイルは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="448f1-119">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="448f1-120">子要素</span><span class="sxs-lookup"><span data-stu-id="448f1-120">Child Elements</span></span>  
 <span data-ttu-id="448f1-121">なし。</span><span class="sxs-lookup"><span data-stu-id="448f1-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="448f1-122">親要素</span><span class="sxs-lookup"><span data-stu-id="448f1-122">Parent Elements</span></span>  
  
|<span data-ttu-id="448f1-123">要素</span><span class="sxs-lookup"><span data-stu-id="448f1-123">Element</span></span>|<span data-ttu-id="448f1-124">説明</span><span class="sxs-lookup"><span data-stu-id="448f1-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="448f1-125">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="448f1-125">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="448f1-126">アクティベーション設定を記述する構成セクション。</span><span class="sxs-lookup"><span data-stu-id="448f1-126">A configuration section that describes activation settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="448f1-127">コメント</span><span class="sxs-lookup"><span data-stu-id="448f1-127">Remarks</span></span>  
 <span data-ttu-id="448f1-128">web.config ファイルでアクティベーション設定を構成する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="448f1-128">The following example shows how to configure activation settings within your web.config file.</span></span>  
  
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
  
 <span data-ttu-id="448f1-129">この構成を使用して、.svc ファイルを使用せずに、GreetingService をアクティブ化できます。</span><span class="sxs-lookup"><span data-stu-id="448f1-129">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>  
  
 <span data-ttu-id="448f1-130">`<serviceHostingEnvironment>` はアプリケーション レベルの構成であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="448f1-130">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="448f1-131">構成を格納した `web.config` は、仮想アプリケーションのルートの下に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="448f1-131">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="448f1-132">また、`serviceHostingEnvironment` は machinetoApplication の継承可能なセクションです。</span><span class="sxs-lookup"><span data-stu-id="448f1-132">In addition, `serviceHostingEnvironment` is a machinetoApplication inheritable section.</span></span> <span data-ttu-id="448f1-133">コンピューターのルートに単一のサービスを登録すると、アプリケーションの各サービスはこのサービスを継承します。</span><span class="sxs-lookup"><span data-stu-id="448f1-133">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>  
  
 <span data-ttu-id="448f1-134">構成ベースのアクティベーションは、http および非 http プロトコル経由のアクティベーションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="448f1-134">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="448f1-135">relatativeAddress では、.svc、.xoml、.xamlx などの拡張子が必要です。</span><span class="sxs-lookup"><span data-stu-id="448f1-135">It requires extensions in the relatativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="448f1-136">既知の buildProviders に対して独自の拡張子をマップできます。これにより、任意の拡張子を使用してサービスをアクティブ化できるようになります。</span><span class="sxs-lookup"><span data-stu-id="448f1-136">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="448f1-137">競合が発生した場合には、`<serviceActivations>` セクションにより、.svc の登録がオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="448f1-137">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="448f1-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="448f1-138">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceActivationElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>

---
title: '&lt;baseAddressPrefixFilters&gt;'
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 8fffcd02b1c08172b184225f13a1852414cf429a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltbaseaddressprefixfiltersgt"></a><span data-ttu-id="f868e-102">&lt;baseAddressPrefixFilters&gt;</span><span class="sxs-lookup"><span data-stu-id="f868e-102">&lt;baseAddressPrefixFilters&gt;</span></span>
<span data-ttu-id="f868e-103">指定する要素が IIS で Windows Communication Foundation (WCF) アプリケーションをホストする場合は、適切なインターネット インフォメーション サービス (IIS) バインドを選択する機構を提供するフィルターを通過する構成のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="f868e-103">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="f868e-104">\<baseAddressPrefixFilters > は"localhost"を認識ではなくコンピューターの完全修飾名を代わりに使用します。</span><span class="sxs-lookup"><span data-stu-id="f868e-104">\<baseAddressPrefixFilters> does not recognize "localhost", use the fully qualified machine name instead.</span></span>  
  
 <span data-ttu-id="f868e-105">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f868e-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="f868e-106">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="f868e-106">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f868e-107">構文</span><span class="sxs-lookup"><span data-stu-id="f868e-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="string"/>  
     </baseAddressPrefixFilters>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f868e-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f868e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f868e-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f868e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f868e-110">属性</span><span class="sxs-lookup"><span data-stu-id="f868e-110">Attributes</span></span>  
 <span data-ttu-id="f868e-111">なし。</span><span class="sxs-lookup"><span data-stu-id="f868e-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f868e-112">子要素</span><span class="sxs-lookup"><span data-stu-id="f868e-112">Child Elements</span></span>  
  
|<span data-ttu-id="f868e-113">要素</span><span class="sxs-lookup"><span data-stu-id="f868e-113">Element</span></span>|<span data-ttu-id="f868e-114">説明</span><span class="sxs-lookup"><span data-stu-id="f868e-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f868e-115">\<add></span><span class="sxs-lookup"><span data-stu-id="f868e-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddressprefixfilter.md)|<span data-ttu-id="f868e-116">サービス ホストによって使用されるベース アドレスのプレフィックス フィルターを指定する構成要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="f868e-116">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f868e-117">親要素</span><span class="sxs-lookup"><span data-stu-id="f868e-117">Parent Elements</span></span>  
  
|<span data-ttu-id="f868e-118">要素</span><span class="sxs-lookup"><span data-stu-id="f868e-118">Element</span></span>|<span data-ttu-id="f868e-119">説明</span><span class="sxs-lookup"><span data-stu-id="f868e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f868e-120">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="f868e-120">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="f868e-121">環境をホストするサービスがインスタンス化する特定のトランスポートの型を定義します。</span><span class="sxs-lookup"><span data-stu-id="f868e-121">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f868e-122">コメント</span><span class="sxs-lookup"><span data-stu-id="f868e-122">Remarks</span></span>  
 <span data-ttu-id="f868e-123">プレフィックス フィルターは、サービスによって使用される URI を、共有ホスティング プロバイダーが指定できるようにする手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="f868e-123">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="f868e-124">これにより、共有ホストは、同じサイト上の同じスキームに対して、別々のベース アドレスを使用して複数のアプリケーションをホストできるようになります。</span><span class="sxs-lookup"><span data-stu-id="f868e-124">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="f868e-125">IIS Web サイトは、仮想ディレクトリを含む仮想アプリケーションのコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="f868e-125">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="f868e-126">サイト内のアプリケーションには、1 つ以上の IIS バインディングからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f868e-126">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="f868e-127">IIS バインディングは、バインディング プロトコルとバインディング情報という 2 つの情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="f868e-127">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="f868e-128">バインディング プロトコル (HTTP など) は通信を行うスキームを定義し、バインディング情報 (IP アドレス、ポート、ホスト ヘッダーなど) にはサイトにアクセスするために使用するデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f868e-128">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="f868e-129">IIS では、サイトごとに複数の IIS バインディングを指定できるので、各スキームに複数のベース アドレスが定義されることがあります。</span><span class="sxs-lookup"><span data-stu-id="f868e-129">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="f868e-130">これに対して、サイトでホストされる [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サービスでは、スキームごとに 1 つのベース アドレスにしかバインドできません。そこで、プレフィックス フィルター機能を使用すると、ホストされるサービスの必要なベース アドレスを選択できます。</span><span class="sxs-lookup"><span data-stu-id="f868e-130">Because a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="f868e-131">IIS によって指定される受信ベース アドレスは、オプションのプレフィックス リスト フィルターに基づいてフィルター処理されます。</span><span class="sxs-lookup"><span data-stu-id="f868e-131">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="f868e-132">たとえば、サイトに次のベース アドレスが含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="f868e-132">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="f868e-133">次の構成ファイルを使用して、appdomain レベルでプレフィックス フィルターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f868e-133">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="net.tcp://test1.fabrikam.com:8000"/>  
        <add prefix="http://test2.fabrikam.com:9000"/>  
    </baseAddressPrefixFilters>  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="f868e-134">この例では、`net.tcp://test1.fabrikam.com:8000` と `http://test2.fabrikam.com:9000` が、対応するスキームに渡される唯一のベース アドレスです。</span><span class="sxs-lookup"><span data-stu-id="f868e-134">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="f868e-135">既定では、プレフィックスを指定しない場合、すべてのアドレスが渡されます。</span><span class="sxs-lookup"><span data-stu-id="f868e-135">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="f868e-136">プレフィックスだけを指定すると、そのスキームに一致するベース アドレスを渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="f868e-136">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f868e-137">フィルターでワイルドカードはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="f868e-137">The filter does not support any wildcards.</span></span> <span data-ttu-id="f868e-138">また、IIS が提供する baseAddresses には、`baseAddressPrefixFilters` リストに存在しない他のスキームにバインドされたアドレスが指定される場合があります。</span><span class="sxs-lookup"><span data-stu-id="f868e-138">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="f868e-139">これらのアドレスはフィルターで除外されません。</span><span class="sxs-lookup"><span data-stu-id="f868e-139">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f868e-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="f868e-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="f868e-141">ホスティング</span><span class="sxs-lookup"><span data-stu-id="f868e-141">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)

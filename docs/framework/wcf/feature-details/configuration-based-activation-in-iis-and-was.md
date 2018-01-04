---
title: "IIS と WAS における構成ベースのアクティブ化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc0e954ae5cadbe7e70cd8a83d3d5841f4e0d142
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="configuration-based-activation-in-iis-and-was"></a><span data-ttu-id="f2cb4-102">IIS と WAS における構成ベースのアクティブ化</span><span class="sxs-lookup"><span data-stu-id="f2cb4-102">Configuration-Based Activation in IIS and WAS</span></span>
<span data-ttu-id="f2cb4-103">インターネット インフォメーション サービス (IIS: Internet Information Services) または Windows プロセス アクティブ化サービス (WAS) で [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスをホストする場合は、.svc ファイルを用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2cb4-103">Normally when hosting a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service under Internet Information Services (IIS) or Windows Process Activation Service (WAS), you must provide a .svc file.</span></span> <span data-ttu-id="f2cb4-104">.svc ファイルには、サービスの名前と、オプションのカスタム サービス ホスト ファクトリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f2cb4-104">The .svc file contains the name of the service and an optional custom service host factory.</span></span> <span data-ttu-id="f2cb4-105">この追加ファイルによって、管理のオーバーヘッドが増加します。</span><span class="sxs-lookup"><span data-stu-id="f2cb4-105">This additional file adds manageability overhead.</span></span> <span data-ttu-id="f2cb4-106">構成ベースのアクティブ化機能により、.svc ファイルを用意する必要がなくなり、関連するオーバーヘッドも発生しません。</span><span class="sxs-lookup"><span data-stu-id="f2cb4-106">The configuration-based activation feature removes the requirement to have a .svc file and therefore the associated overhead.</span></span>  
  
## <a name="configuration-based-activation"></a><span data-ttu-id="f2cb4-107">構成ベースのアクティブ化</span><span class="sxs-lookup"><span data-stu-id="f2cb4-107">Configuration-Based Activation</span></span>  
 <span data-ttu-id="f2cb4-108">構成ベースのアクティブ化では、以前は .svc ファイルに配置されていたメタデータを受け取り、それを Web.config ファイルに配置します。</span><span class="sxs-lookup"><span data-stu-id="f2cb4-108">Configuration-based activation takes the metadata that used to be placed in the .svc file and places it in the Web.config file.</span></span> <span data-ttu-id="f2cb4-109">内で、<`serviceHostingEnvironment`> 要素は、<`serviceActivations`> 要素。</span><span class="sxs-lookup"><span data-stu-id="f2cb4-109">Within the<`serviceHostingEnvironment`> element there is a <`serviceActivations`> element.</span></span> <span data-ttu-id="f2cb4-110">内で、<`serviceActivations`> 要素が 1 つ以上 <`add`> 要素、各ホステッド サービスに 1 つです。</span><span class="sxs-lookup"><span data-stu-id="f2cb4-110">Within the <`serviceActivations`> element are one or more <`add`> elements, one for each hosted service.</span></span> <span data-ttu-id="f2cb4-111"><`add`> 要素には属性の場合、サービスおよびサービスの種類、サービス ホスト ファクトリの相対アドレスを設定することができます。</span><span class="sxs-lookup"><span data-stu-id="f2cb4-111">The <`add`> element contains attributes that let you set the relative address for the service and the service type or a service host factory.</span></span> <span data-ttu-id="f2cb4-112">次の構成コード例は、このセクションの使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f2cb4-112">The following configuration example code shows how this section is used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2cb4-113">各 <`add`> 要素には、サービスまたは factory 属性を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2cb4-113">Each <`add`> element must specify a service or a factory attribute.</span></span> <span data-ttu-id="f2cb4-114">サービスとファクトリ属性の両方を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="f2cb4-114">Specifying both service and factory attributes is allowed.</span></span>  
  
```xml  
<serviceHostingEnvironment>  
  <serviceActivations>  
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>  
  </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
 <span data-ttu-id="f2cb4-115">このコードを Web.config ファイルに含めると、サービス ソース コードをアプリケーションの App_Code ディレクトリに配置するか、コンパイル済みアセンブリをアプリケーションの Bin ディレクトリに配置することができます。</span><span class="sxs-lookup"><span data-stu-id="f2cb4-115">With this in the Web.config file, you can place the service source code in the App_Code directory of the application or a complied assembly in the Bin directory of the application.</span></span>  
  
> [!NOTE]
>  -   <span data-ttu-id="f2cb4-116">構成ベースのアクティブ化機能を使用する場合、.svc ファイルのインライン コードはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="f2cb4-116">When using configuration-based activation, inline code in .svc files is not supported.</span></span>  
> -   <span data-ttu-id="f2cb4-117">`relativeAddress`属性をなどの相対アドレスに設定する必要があります"\<サブディレクトリ >/service.svc"または"~/\<directory サブ/service.svc"です。</span><span class="sxs-lookup"><span data-stu-id="f2cb4-117">The `relativeAddress` attribute must be set to a relative address such as "\<sub-directory>/service.svc" or "~/\<sub-directory/service.svc".</span></span>  
> -   <span data-ttu-id="f2cb4-118">WCF と関連付けられている既知の拡張子を持たない相対アドレスを登録すると、構成例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f2cb4-118">A configuration exception is thrown if you register a relative address that does not have a known extension associated with WCF.</span></span>  
> -   <span data-ttu-id="f2cb4-119">指定された相対アドレスは、仮想アプリケーションのルートが基準になります。</span><span class="sxs-lookup"><span data-stu-id="f2cb4-119">The relative address specified is relative to the root of the virtual application.</span></span>  
> -   <span data-ttu-id="f2cb4-120">構成の階層的モデルにより、コンピューター レベルおよびサイト レベルの登録された相対アドレスは、仮想アプリケーションによって継承されます。</span><span class="sxs-lookup"><span data-stu-id="f2cb4-120">Due to the hierarchical model of configuration, the registered relative addresses at machine and site level are inherited by virtual applications.</span></span>  
> -   <span data-ttu-id="f2cb4-121">構成ファイル内での登録は、.svc、.xamlx、.xoml、またはその他のファイルでの設定よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="f2cb4-121">Registrations in a configuration file take precedence over settings in a .svc, .xamlx, .xoml, or other file.</span></span>  
> -   <span data-ttu-id="f2cb4-122">IIS/WAS に送信された URI 内の \ (円記号) は、自動的に / (スラッシュ) に変換されます。</span><span class="sxs-lookup"><span data-stu-id="f2cb4-122">Any ‘\’ (backslashes) in a URI sent to IIS/WAS are automatically converted to a ‘/’ (forward slash).</span></span> <span data-ttu-id="f2cb4-123">\ を含む相対アドレスが追加され、その相対アドレスを使用する URI を IIS に送信した場合は、円記号がスラッシュに変換されるため、IIS では、それを相対アドレスと一致させることができません。</span><span class="sxs-lookup"><span data-stu-id="f2cb4-123">If a relative address is added that contains a ‘\’ and you send IIS a URI that uses the relative address, the backslash is converted to a forward slash and IIS cannot match it to the relative address.</span></span> <span data-ttu-id="f2cb4-124">IIS は、一致するものが見つからなかったことを示すトレース情報を送信します。</span><span class="sxs-lookup"><span data-stu-id="f2cb4-124">IIS sends out trace information that indicates that there are no matches found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2cb4-125">参照</span><span class="sxs-lookup"><span data-stu-id="f2cb4-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>  
 [<span data-ttu-id="f2cb4-126">ホスティング サービス</span><span class="sxs-lookup"><span data-stu-id="f2cb4-126">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="f2cb4-127">ワークフロー サービスのホストの概要</span><span class="sxs-lookup"><span data-stu-id="f2cb4-127">Hosting Workflow Services Overview</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 [<span data-ttu-id="f2cb4-128">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="f2cb4-128">\<serviceHostingEnvironment></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)  
 [<span data-ttu-id="f2cb4-129">Windows Server App Fabric のホスティング機能</span><span class="sxs-lookup"><span data-stu-id="f2cb4-129">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)

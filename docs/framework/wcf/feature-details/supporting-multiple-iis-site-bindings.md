---
title: "複数の IIS サイト バインディングのサポート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ebe433d1c18d46e0868f9566a273124e6bd63f1c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="supporting-multiple-iis-site-bindings"></a><span data-ttu-id="8c983-102">複数の IIS サイト バインディングのサポート</span><span class="sxs-lookup"><span data-stu-id="8c983-102">Supporting Multiple IIS Site Bindings</span></span>
<span data-ttu-id="8c983-103">インターネット インフォメーション サービス (IIS: Internet Information Services) 7.0 で [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスをホストする場合は、同じサイトで同じプロトコルを使用する、複数のベース アドレスを提供できます。</span><span class="sxs-lookup"><span data-stu-id="8c983-103">When hosting a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service under Internet Information Services (IIS) 7.0, you may want to provide multiple base addresses that use the same protocol on the same site.</span></span> <span data-ttu-id="8c983-104">これにより、同じサービスで多数の異なる URI に応答できます。</span><span class="sxs-lookup"><span data-stu-id="8c983-104">This allows the same service to respond to a number of different URIs.</span></span> <span data-ttu-id="8c983-105">http://www.contoso.com および http://contoso.com でリッスンするサービスをホストするときには、これが役立ちます。また、内部ユーザー用に 1 つのベース アドレスを持ち、外部ユーザー用に別のベース アドレスを持つサービスを作成するのにも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8c983-105">This is useful when you want to host a service that listens on http://www.contoso.com and http://contoso.com. It is also useful to create a service that has a base address for internal users and a separate base address for external users.</span></span> <span data-ttu-id="8c983-106">たとえば、http://internal.contoso.com および http://www.contoso.com というベース アドレスを持つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="8c983-106">For example: http://internal.contoso.com and http://www.contoso.com.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c983-107">この機能は、HTTP プロトコルを使用してのみ、使用可能です。</span><span class="sxs-lookup"><span data-stu-id="8c983-107">This functionality is only available using the HTTP protocol.</span></span>  
  
## <a name="multiple-base-addresses"></a><span data-ttu-id="8c983-108">複数のベース アドレス</span><span class="sxs-lookup"><span data-stu-id="8c983-108">Multiple Base Addresses</span></span>  
 <span data-ttu-id="8c983-109">この機能は、IIS でホストされている [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="8c983-109">This feature is only available to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services that are hosted under IIS.</span></span> <span data-ttu-id="8c983-110">この機能は、既定では有効にされません。</span><span class="sxs-lookup"><span data-stu-id="8c983-110">This feature is not enabled by default.</span></span> <span data-ttu-id="8c983-111">有効にする必要がありますを追加する、`multipleSiteBindingsEnabled`属性を <`serviceHostingEnvironment`> Web.config 内の要素に設定し、ファイル`true`次の例で示すように、します。</span><span class="sxs-lookup"><span data-stu-id="8c983-111">To enable it you must add the `multipleSiteBindingsEnabled` attribute to the <`serviceHostingEnvironment`> element in your Web.config file and set it to `true`, as shown in the following example.</span></span>  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"/>  
```  
  
 <span data-ttu-id="8c983-112">IIS で [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスをホストする場合、IIS では、アプリケーションを格納している仮想ディレクトリへの URI に基づいて、1 つのベース アドレスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8c983-112">When hosting a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service under IIS, IIS creates one base address for you based on the URI to the virtual directory that contains the application.</span></span> <span data-ttu-id="8c983-113">インターネット インフォメーション サービス マネージャーを使用して、同じプロトコルを使用するベース アドレスを追加し、1 つ以上のバインディングを Web サイトに追加できます。</span><span class="sxs-lookup"><span data-stu-id="8c983-113">You can add additional base addresses that use the same protocol by using Internet Information Services Manager to add one or more bindings to your Web site.</span></span> <span data-ttu-id="8c983-114">それぞれのバインディングに対して、プロトコル (HTTP または HTTPS)、IP アドレス、ポート、およびホスト名を指定します。</span><span class="sxs-lookup"><span data-stu-id="8c983-114">For each binding specify a protocol (HTTP or HTTPS), an IP address, a port, and a host name.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="8c983-115">インターネット インフォメーション サービス マネージャーを使用する確認[IIS マネージャー (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164057)です。</span><span class="sxs-lookup"><span data-stu-id="8c983-115"> using Internet Information Services Manager, see [IIS Manager (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164057).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="8c983-116">バインドをサイトに追加するを参照してください[Web サイト (IIS 7) を作成します。](http://go.microsoft.com/fwlink/?LinkId=164060)</span><span class="sxs-lookup"><span data-stu-id="8c983-116"> adding bindings to a site, see [Create a Web Site (IIS 7)](http://go.microsoft.com/fwlink/?LinkId=164060)</span></span>  
  
 <span data-ttu-id="8c983-117">同じサイトに複数のベース アドレスを指定すると、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のヘルプ ページ、スキーマのインポート、サービスによって生成される WSDL/MEX 情報に影響が生じます。</span><span class="sxs-lookup"><span data-stu-id="8c983-117">Specifying multiple base addresses for the same site affects the content of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Help page, importing schema, and the WSDL/MEX information generated by the service.</span></span> <span data-ttu-id="8c983-118">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のヘルプ ページには、サービスと通信できる [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントの生成に使用する、コマンド ラインが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8c983-118">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Help page displays the command line to use to generate a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client that can communicate with the service.</span></span> <span data-ttu-id="8c983-119">このコマンド ラインには、その Web サイト用の IIS バインディングで指定された最初のアドレスだけが含まれています。</span><span class="sxs-lookup"><span data-stu-id="8c983-119">This command line contains only the first address specified in the IIS binding for the Web site.</span></span> <span data-ttu-id="8c983-120">同様に、スキーマをインポートするときには、IIS バインディングで指定された最初のベース アドレスだけが使用されます。</span><span class="sxs-lookup"><span data-stu-id="8c983-120">Similarly when importing schema, only the first base address specified in the IIS binding is used.</span></span> <span data-ttu-id="8c983-121">WSDL および MEX データには、IIS バインディングで指定されたすべてのベース アドレスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="8c983-121">WSDL and MEX data contain all the base addresses specified in the IIS bindings.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="8c983-122">つまり、サービスに 2 つのベース アドレス (1 つは内部ユーザー用、もう 1 つは外部ユーザー用) がある場合、サービスによって生成される WSDL/MEX 情報では、両方のベース アドレスが指定されます。</span><span class="sxs-lookup"><span data-stu-id="8c983-122">This means that if a service has two base addresses, one for internal users and one for external users, both are specified in the WSDL/MEX information generated by the service.</span></span>

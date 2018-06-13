---
title: '&lt;net.tcp&gt;'
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 9e44ddcc3a3e983abe6e36d4b6095c5c4a67529f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349884"
---
# <a name="ltnettcpgt"></a><span data-ttu-id="d7d4b-102">&lt;net.tcp&gt;</span><span class="sxs-lookup"><span data-stu-id="d7d4b-102">&lt;net.tcp&gt;</span></span>
<span data-ttu-id="d7d4b-103">複数のプロセスが同じ TCP ポートを共有できる NET.TCP ポート共有サービスの構成設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-103">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
 <span data-ttu-id="d7d4b-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="d7d4b-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="d7d4b-105">\<net.tcp></span><span class="sxs-lookup"><span data-stu-id="d7d4b-105">\<net.tcp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7d4b-106">構文</span><span class="sxs-lookup"><span data-stu-id="d7d4b-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="Integer"  
          maxPendingAccepts="Integer"  
          maxPendingConnections="Integer"  
          receiveTimeout="TimeSpan"  
          teredoEnabled="Boolean">  
          <allowAccounts>  
             <!-- LocalSystem account -->   
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->   
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Administrators account -->   
             <add securityIdentifier="S-1-5-20"/>  
             <!-- Network Service account -->   
             <add securityIdentifier="S-1-5-32-544" />  
             <!-- IIS_IUSRS account (Vista only)-->   
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.tcp>  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="d7d4b-107">型</span><span class="sxs-lookup"><span data-stu-id="d7d4b-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7d4b-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d7d4b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d7d4b-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7d4b-110">属性</span><span class="sxs-lookup"><span data-stu-id="d7d4b-110">Attributes</span></span>  
  
|<span data-ttu-id="d7d4b-111">属性</span><span class="sxs-lookup"><span data-stu-id="d7d4b-111">Attribute</span></span>|<span data-ttu-id="d7d4b-112">説明</span><span class="sxs-lookup"><span data-stu-id="d7d4b-112">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="d7d4b-113">共有接続から受け入れられます Windows Communication Foundation (WCF) サービスにまだディスパッチされていない最大の未処理の接続を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-113">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="d7d4b-114">既定値は 10 です。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-114">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="d7d4b-115">整数は、共有サービスの待機エンドポイントで同時に受け入れる未処理のスレッドの最大数を示しています。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-115">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="d7d4b-116">既定値は 2 です。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-116">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="d7d4b-117">アプリケーションによる受け入れをリスナーで待機できる最大接続数。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-117">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="d7d4b-118">このクォータ値を超過すると、新規の受信接続は受け入れられるのを待機せずに切断されます。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-118">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="d7d4b-119">メッセージ セキュリティのような接続機能では、クライアントは複数の接続を開くことがあります。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-119">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="d7d4b-120">このクォータ値を設定する場合、サービス管理者はこのような追加の接続も考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-120">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="d7d4b-121">既定値は 10 です。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-121">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="d7d4b-122">フレーム データを読み取り、基礎となる接続から接続ディスパッチを実行するタイムアウトを指定する `TimeSpan` です。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-122">A `TimeSpan` that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="d7d4b-123">既定値は "00:00:10" です。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-123">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="d7d4b-124">WCF サービスに代わって TCP ポートでリッスンするように、ポート共有サービスが Microsoft Teredo サービスを使用しているかどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-124">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of WCF services.</span></span> <span data-ttu-id="d7d4b-125">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-125">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d7d4b-126">子要素</span><span class="sxs-lookup"><span data-stu-id="d7d4b-126">Child Elements</span></span>  
  
|<span data-ttu-id="d7d4b-127">要素</span><span class="sxs-lookup"><span data-stu-id="d7d4b-127">Element</span></span>|<span data-ttu-id="d7d4b-128">説明</span><span class="sxs-lookup"><span data-stu-id="d7d4b-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7d4b-129">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="d7d4b-129">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="d7d4b-130">含む構成要素のコレクション、`securityIdentifier`属性を WCF サービスをホストし、共有サービスへの接続アクセスが許可されるプロセスのユーザー アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-130">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d7d4b-131">親要素</span><span class="sxs-lookup"><span data-stu-id="d7d4b-131">Parent Elements</span></span>  
  
|<span data-ttu-id="d7d4b-132">要素</span><span class="sxs-lookup"><span data-stu-id="d7d4b-132">Element</span></span>|<span data-ttu-id="d7d4b-133">説明</span><span class="sxs-lookup"><span data-stu-id="d7d4b-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7d4b-134">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="d7d4b-134">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="d7d4b-135">リスナー プロセス SMSvcHost.exe の設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-135">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7d4b-136">コメント</span><span class="sxs-lookup"><span data-stu-id="d7d4b-136">Remarks</span></span>  
 <span data-ttu-id="d7d4b-137">ポート共有の詳細については、次を参照してください。 [Net.TCP ポート共有](http://msdn.microsoft.com/library/f13692ee-a179-4439-ae72-50db9534eded)です。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-137">For more information on port sharing, see [Net.TCP Port Sharing](http://msdn.microsoft.com/library/f13692ee-a179-4439-ae72-50db9534eded).</span></span> <span data-ttu-id="d7d4b-138">ポート共有サービスを構成する方法を理解するには、次を参照してください。 [Net.TCP ポート共有サービスを構成する](http://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)です。</span><span class="sxs-lookup"><span data-stu-id="d7d4b-138">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](http://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7d4b-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="d7d4b-139">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>  
 [<span data-ttu-id="d7d4b-140">Net.TCP ポート共有</span><span class="sxs-lookup"><span data-stu-id="d7d4b-140">Net.TCP Port Sharing</span></span>](http://msdn.microsoft.com/library/f13692ee-a179-4439-ae72-50db9534eded)  
 [<span data-ttu-id="d7d4b-141">Net.TCP ポート共有サービスを構成する</span><span class="sxs-lookup"><span data-stu-id="d7d4b-141">Configuring the Net.TCP Port Sharing Service</span></span>](http://msdn.microsoft.com/library/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)

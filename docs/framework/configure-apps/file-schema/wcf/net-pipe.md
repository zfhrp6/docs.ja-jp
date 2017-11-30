---
title: '&lt;net.pipe&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5d68c2113b08065f7ec74ae68d7f0b5918cab0aa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltnetpipegt"></a><span data-ttu-id="4b3bb-102">&lt;net.pipe&gt;</span><span class="sxs-lookup"><span data-stu-id="4b3bb-102">&lt;net.pipe&gt;</span></span>
<span data-ttu-id="4b3bb-103">名前付きパイプ接続の有効期間を管理し、名前付きパイプを介して到着するアクティベーション要求を処理する名前付きパイプ アクティベーション サービスの構成設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="4b3bb-103">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
 <span data-ttu-id="4b3bb-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="4b3bb-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="4b3bb-105">\<net.pipe ></span><span class="sxs-lookup"><span data-stu-id="4b3bb-105">\<net.pipe></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b3bb-106">構文</span><span class="sxs-lookup"><span data-stu-id="4b3bb-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.pipe maxPendingAccepts="Integer"  
                    maxPendingConnections="Integer"  
          receiveTimeout="TimeSpan">  
          <allowAccounts>  
             // LocalSystem account  
             <add securityIdentifier="S-1-5-18"/>  
             // LocalService account  
             <add securityIdentifier="S-1-5-19"/>  
             // Administrators account  
             <add securityIdentifier="S-1-5-20"/>  
             // Network Service account  
             <add securityIdentifier="S-1-5-32-544" />  
             // IIS_IUSRS account (Vista only)  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.pipe>  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="4b3bb-107">型</span><span class="sxs-lookup"><span data-stu-id="4b3bb-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b3bb-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="4b3bb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4b3bb-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="4b3bb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b3bb-110">属性</span><span class="sxs-lookup"><span data-stu-id="4b3bb-110">Attributes</span></span>  
  
|<span data-ttu-id="4b3bb-111">属性</span><span class="sxs-lookup"><span data-stu-id="4b3bb-111">Attribute</span></span>|<span data-ttu-id="4b3bb-112">説明</span><span class="sxs-lookup"><span data-stu-id="4b3bb-112">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="4b3bb-113">整数は、共有サービスの待機エンドポイントで同時に受け入れる未処理のスレッドの最大数を示しています。</span><span class="sxs-lookup"><span data-stu-id="4b3bb-113">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="4b3bb-114">既定値は 2 です。</span><span class="sxs-lookup"><span data-stu-id="4b3bb-114">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="4b3bb-115">ディスパッチを待機できる最大接続数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="4b3bb-115">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="4b3bb-116">既定値は 100 です。</span><span class="sxs-lookup"><span data-stu-id="4b3bb-116">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="4b3bb-117">フレーム データを読み取り、基礎となる接続から接続ディスパッチを実行するタイムアウトを指定する `TimeSpan` です。</span><span class="sxs-lookup"><span data-stu-id="4b3bb-117">A `TimeSpan` that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="4b3bb-118">既定値は "00:00:10" です。</span><span class="sxs-lookup"><span data-stu-id="4b3bb-118">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b3bb-119">子要素</span><span class="sxs-lookup"><span data-stu-id="4b3bb-119">Child Elements</span></span>  
  
|<span data-ttu-id="4b3bb-120">要素</span><span class="sxs-lookup"><span data-stu-id="4b3bb-120">Element</span></span>|<span data-ttu-id="4b3bb-121">説明</span><span class="sxs-lookup"><span data-stu-id="4b3bb-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b3bb-122">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="4b3bb-122">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="4b3bb-123">`securityIdentifier` をホストするプロセスのユーザー アカウントを指定する [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 属性が含まれており、共有サービスへの接続アクセス権が付与される構成要素のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="4b3bb-123">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4b3bb-124">親要素</span><span class="sxs-lookup"><span data-stu-id="4b3bb-124">Parent Elements</span></span>  
  
|<span data-ttu-id="4b3bb-125">要素</span><span class="sxs-lookup"><span data-stu-id="4b3bb-125">Element</span></span>|<span data-ttu-id="4b3bb-126">説明</span><span class="sxs-lookup"><span data-stu-id="4b3bb-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b3bb-127">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="4b3bb-127">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="4b3bb-128">リスナー プロセス SMSvcHost.exe の設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4b3bb-128">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4b3bb-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="4b3bb-129">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>

---
title: '&lt;net.pipe&gt;'
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: 71291b1163ffb4e5fe13ff18d88d47f7d2193497
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359365"
---
# <a name="ltnetpipegt"></a><span data-ttu-id="fda59-102">&lt;net.pipe&gt;</span><span class="sxs-lookup"><span data-stu-id="fda59-102">&lt;net.pipe&gt;</span></span>
<span data-ttu-id="fda59-103">名前付きパイプ接続の有効期間を管理し、名前付きパイプを介して到着するアクティベーション要求を処理する名前付きパイプ アクティベーション サービスの構成設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="fda59-103">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
 <span data-ttu-id="fda59-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="fda59-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="fda59-105">\<net.pipe ></span><span class="sxs-lookup"><span data-stu-id="fda59-105">\<net.pipe></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fda59-106">構文</span><span class="sxs-lookup"><span data-stu-id="fda59-106">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="fda59-107">型</span><span class="sxs-lookup"><span data-stu-id="fda59-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fda59-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="fda59-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fda59-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="fda59-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fda59-110">属性</span><span class="sxs-lookup"><span data-stu-id="fda59-110">Attributes</span></span>  
  
|<span data-ttu-id="fda59-111">属性</span><span class="sxs-lookup"><span data-stu-id="fda59-111">Attribute</span></span>|<span data-ttu-id="fda59-112">説明</span><span class="sxs-lookup"><span data-stu-id="fda59-112">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="fda59-113">整数は、共有サービスの待機エンドポイントで同時に受け入れる未処理のスレッドの最大数を示しています。</span><span class="sxs-lookup"><span data-stu-id="fda59-113">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="fda59-114">既定値は 2 です。</span><span class="sxs-lookup"><span data-stu-id="fda59-114">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="fda59-115">ディスパッチを待機できる最大接続数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="fda59-115">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="fda59-116">既定値は 100 です。</span><span class="sxs-lookup"><span data-stu-id="fda59-116">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="fda59-117">フレーム データを読み取り、基礎となる接続から接続ディスパッチを実行するタイムアウトを指定する `TimeSpan` です。</span><span class="sxs-lookup"><span data-stu-id="fda59-117">A `TimeSpan` that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="fda59-118">既定値は "00:00:10" です。</span><span class="sxs-lookup"><span data-stu-id="fda59-118">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fda59-119">子要素</span><span class="sxs-lookup"><span data-stu-id="fda59-119">Child Elements</span></span>  
  
|<span data-ttu-id="fda59-120">要素</span><span class="sxs-lookup"><span data-stu-id="fda59-120">Element</span></span>|<span data-ttu-id="fda59-121">説明</span><span class="sxs-lookup"><span data-stu-id="fda59-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fda59-122">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="fda59-122">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="fda59-123">含む構成要素のコレクション、`securityIdentifier`属性を WCF サービスをホストし、共有サービスへの接続アクセスが許可されるプロセスのユーザー アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="fda59-123">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fda59-124">親要素</span><span class="sxs-lookup"><span data-stu-id="fda59-124">Parent Elements</span></span>  
  
|<span data-ttu-id="fda59-125">要素</span><span class="sxs-lookup"><span data-stu-id="fda59-125">Element</span></span>|<span data-ttu-id="fda59-126">説明</span><span class="sxs-lookup"><span data-stu-id="fda59-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fda59-127">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="fda59-127">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="fda59-128">リスナー プロセス SMSvcHost.exe の設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="fda59-128">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fda59-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="fda59-129">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>

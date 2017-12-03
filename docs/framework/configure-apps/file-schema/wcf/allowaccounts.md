---
title: '&lt;allowAccounts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 20d411fbe052940fd8fc752e74d012f28ffa441b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltallowaccountsgt"></a><span data-ttu-id="c22b3-102">&lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="c22b3-102">&lt;allowAccounts&gt;</span></span>
<span data-ttu-id="c22b3-103">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] サービスをホストするプロセスのユーザー アカウントを指定し、共有サービスへの接続アクセス権が付与されている構成要素のコレクションを含みます。</span><span class="sxs-lookup"><span data-stu-id="c22b3-103">Contains a collection of configuration elements that specify user accounts for processes that host [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="c22b3-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="c22b3-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c22b3-105">構文</span><span class="sxs-lookup"><span data-stu-id="c22b3-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c22b3-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c22b3-106">Attributes and Elements</span></span>  
 <span data-ttu-id="c22b3-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c22b3-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c22b3-108">属性</span><span class="sxs-lookup"><span data-stu-id="c22b3-108">Attributes</span></span>  
 <span data-ttu-id="c22b3-109">なし。</span><span class="sxs-lookup"><span data-stu-id="c22b3-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c22b3-110">子要素</span><span class="sxs-lookup"><span data-stu-id="c22b3-110">Child Elements</span></span>  
  
|<span data-ttu-id="c22b3-111">属性</span><span class="sxs-lookup"><span data-stu-id="c22b3-111">Attribute</span></span>|<span data-ttu-id="c22b3-112">説明</span><span class="sxs-lookup"><span data-stu-id="c22b3-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="c22b3-113">\<add></span><span class="sxs-lookup"><span data-stu-id="c22b3-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="c22b3-114">[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サービスをホストし、共有サービスへの接続アクセスが付与されているプロセスのユーザー アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="c22b3-114">Adds a user account for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c22b3-115">親要素</span><span class="sxs-lookup"><span data-stu-id="c22b3-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c22b3-116">要素</span><span class="sxs-lookup"><span data-stu-id="c22b3-116">Element</span></span>|<span data-ttu-id="c22b3-117">説明</span><span class="sxs-lookup"><span data-stu-id="c22b3-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c22b3-118">[\<net.pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md)または[ \<net.tcp >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="c22b3-118">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="c22b3-119">Net Pipe または TCP 共有サービスの構成設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="c22b3-119">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c22b3-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="c22b3-120">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>

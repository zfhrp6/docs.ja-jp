---
title: "&lt;allowAccounts&gt; の &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 09ab06bb94249e79743335da1a360f6b668b1d86
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltallowaccountsgt"></a><span data-ttu-id="73fba-102">&lt;allowAccounts&gt; の &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="73fba-102">&lt;add&gt; of &lt;allowAccounts&gt;</span></span>
<span data-ttu-id="73fba-103">[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サービスをホストし、共有サービスへの接続アクセスが付与されているプロセスのユーザー アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="73fba-103">Specifies a user account for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="73fba-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="73fba-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73fba-105">構文</span><span class="sxs-lookup"><span data-stu-id="73fba-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73fba-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="73fba-106">Attributes and Elements</span></span>  
 <span data-ttu-id="73fba-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="73fba-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73fba-108">属性</span><span class="sxs-lookup"><span data-stu-id="73fba-108">Attributes</span></span>  
  
|<span data-ttu-id="73fba-109">属性</span><span class="sxs-lookup"><span data-stu-id="73fba-109">Attribute</span></span>|<span data-ttu-id="73fba-110">説明</span><span class="sxs-lookup"><span data-stu-id="73fba-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="73fba-111">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="73fba-111">securityIdentifier</span></span>|<span data-ttu-id="73fba-112">ユーザー アカウントの識別に使用される一意の識別子を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="73fba-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="73fba-113">既定値は LocalSystem、Administrators、NS、LS、および IIS_USRS です。</span><span class="sxs-lookup"><span data-stu-id="73fba-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73fba-114">子要素</span><span class="sxs-lookup"><span data-stu-id="73fba-114">Child Elements</span></span>  
 <span data-ttu-id="73fba-115">なし。</span><span class="sxs-lookup"><span data-stu-id="73fba-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="73fba-116">親要素</span><span class="sxs-lookup"><span data-stu-id="73fba-116">Parent Elements</span></span>  
  
|<span data-ttu-id="73fba-117">要素</span><span class="sxs-lookup"><span data-stu-id="73fba-117">Element</span></span>|<span data-ttu-id="73fba-118">説明</span><span class="sxs-lookup"><span data-stu-id="73fba-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73fba-119">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="73fba-119">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="73fba-120">`securityIdentifier` をホストするプロセスのユーザー アカウントを指定する [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 属性が含まれており、共有サービスへの接続アクセス権が付与される構成要素のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="73fba-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="73fba-121">例</span><span class="sxs-lookup"><span data-stu-id="73fba-121">Example</span></span>  
 <span data-ttu-id="73fba-122">次の構成例は、このコレクションにユーザー アカウントの 5 つの既定の識別子を追加します。</span><span class="sxs-lookup"><span data-stu-id="73fba-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
```xml  
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
```  
  
## <a name="see-also"></a><span data-ttu-id="73fba-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="73fba-123">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>

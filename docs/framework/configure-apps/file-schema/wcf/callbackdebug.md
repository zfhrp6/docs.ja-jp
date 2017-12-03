---
title: '&lt;callbackDebug&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0bb730a00358f771408ff0431ff2ab77623354a4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltcallbackdebuggt"></a><span data-ttu-id="7bd54-102">&lt;callbackDebug&gt;</span><span class="sxs-lookup"><span data-stu-id="7bd54-102">&lt;callbackDebug&gt;</span></span>
<span data-ttu-id="7bd54-103">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] コールバック オブジェクトのサービス デバッグを指定します。</span><span class="sxs-lookup"><span data-stu-id="7bd54-103">Specifies service debugging for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] callback object.</span></span>  
  
 <span data-ttu-id="7bd54-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7bd54-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7bd54-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="7bd54-105">\<behaviors></span></span>  
<span data-ttu-id="7bd54-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7bd54-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="7bd54-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="7bd54-107">\<behavior></span></span>  
<span data-ttu-id="7bd54-108">\<callbackDebug ></span><span class="sxs-lookup"><span data-stu-id="7bd54-108">\<callbackDebug></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bd54-109">構文</span><span class="sxs-lookup"><span data-stu-id="7bd54-109">Syntax</span></span>  
  
```xml  
<callbackDebug  includeExceptionDetailInFaults="Boolean" />  
```  
  
## <a name="type"></a><span data-ttu-id="7bd54-110">型</span><span class="sxs-lookup"><span data-stu-id="7bd54-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7bd54-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7bd54-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7bd54-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7bd54-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7bd54-113">属性</span><span class="sxs-lookup"><span data-stu-id="7bd54-113">Attributes</span></span>  
  
|<span data-ttu-id="7bd54-114">属性</span><span class="sxs-lookup"><span data-stu-id="7bd54-114">Attribute</span></span>|<span data-ttu-id="7bd54-115">説明</span><span class="sxs-lookup"><span data-stu-id="7bd54-115">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="7bd54-116">クライアント コールバック オブジェクトが SOAP エラー内のマネージ例外情報をサービスに返すかどうかを指定する値。</span><span class="sxs-lookup"><span data-stu-id="7bd54-116">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="7bd54-117">プログラムでこの属性を `true` に設定すると、デバッグするために、クライアント コールバック オブジェクト内のマネージ例外情報がサービスに戻るフローを有効にできます。</span><span class="sxs-lookup"><span data-stu-id="7bd54-117">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="7bd54-118">**注意:**返すマネージ例外情報をクライアントにセキュリティ リスクとなることができます。</span><span class="sxs-lookup"><span data-stu-id="7bd54-118">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="7bd54-119">これは、例外の詳細が、認証されていないクライアントによって使用可能な内部サービスの実装に関する情報を公開するためです。</span><span class="sxs-lookup"><span data-stu-id="7bd54-119">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7bd54-120">子要素</span><span class="sxs-lookup"><span data-stu-id="7bd54-120">Child Elements</span></span>  
 <span data-ttu-id="7bd54-121">なし。</span><span class="sxs-lookup"><span data-stu-id="7bd54-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7bd54-122">親要素</span><span class="sxs-lookup"><span data-stu-id="7bd54-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7bd54-123">要素</span><span class="sxs-lookup"><span data-stu-id="7bd54-123">Element</span></span>|<span data-ttu-id="7bd54-124">説明</span><span class="sxs-lookup"><span data-stu-id="7bd54-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7bd54-125">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="7bd54-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="7bd54-126">エンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="7bd54-126">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7bd54-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="7bd54-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CallbackDebugElement>  
 <xref:System.ServiceModel.Description.CallbackDebugBehavior>

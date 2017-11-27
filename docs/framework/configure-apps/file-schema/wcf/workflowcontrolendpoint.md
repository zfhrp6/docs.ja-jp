---
title: '&lt;workflowControlEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8371b9180fec9877ac58026c26fb60c8ccdaa752
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltworkflowcontrolendpointgt"></a><span data-ttu-id="0d23f-102">&lt;workflowControlEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="0d23f-102">&lt;workflowControlEndpoint&gt;</span></span>
<span data-ttu-id="0d23f-103">この構成要素は、ワークフロー インスタンスの実行の制御 (作成、実行、保留、終了など) に使用する標準エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="0d23f-103">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="0d23f-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="0d23f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0d23f-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="0d23f-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d23f-106">構文</span><span class="sxs-lookup"><span data-stu-id="0d23f-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d23f-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="0d23f-107">Attributes and Elements</span></span>  
 <span data-ttu-id="0d23f-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="0d23f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d23f-109">属性</span><span class="sxs-lookup"><span data-stu-id="0d23f-109">Attributes</span></span>  
  
|<span data-ttu-id="0d23f-110">属性</span><span class="sxs-lookup"><span data-stu-id="0d23f-110">Attribute</span></span>|<span data-ttu-id="0d23f-111">説明</span><span class="sxs-lookup"><span data-stu-id="0d23f-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0d23f-112">name</span><span class="sxs-lookup"><span data-stu-id="0d23f-112">name</span></span>|<span data-ttu-id="0d23f-113">標準エンドポイントの構成名を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="0d23f-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="0d23f-114">この名前は、サービス エンドポイントの `endpointConfiguration` 属性で使用され、標準エンドポイントと構成を関連付けます。</span><span class="sxs-lookup"><span data-stu-id="0d23f-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d23f-115">子要素</span><span class="sxs-lookup"><span data-stu-id="0d23f-115">Child Elements</span></span>  
 <span data-ttu-id="0d23f-116">なし。</span><span class="sxs-lookup"><span data-stu-id="0d23f-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0d23f-117">親要素</span><span class="sxs-lookup"><span data-stu-id="0d23f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0d23f-118">要素</span><span class="sxs-lookup"><span data-stu-id="0d23f-118">Element</span></span>|<span data-ttu-id="0d23f-119">説明</span><span class="sxs-lookup"><span data-stu-id="0d23f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d23f-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="0d23f-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="0d23f-121">1 つ以上のプロパティ (アドレス、バインディング、コントラクト) が固定されている、あらかじめ定義されたエンドポイントである標準エンドポイントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="0d23f-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0d23f-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="0d23f-122">See Also</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>

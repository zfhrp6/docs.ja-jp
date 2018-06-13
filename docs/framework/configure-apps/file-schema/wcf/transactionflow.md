---
title: '&lt;トランザクション フロー&gt;'
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: c708098676e5634281e29c17639304a1a9cf5afe
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748712"
---
# <a name="lttransactionflowgt"></a><span data-ttu-id="e0765-102">&lt;トランザクション フロー&gt;</span><span class="sxs-lookup"><span data-stu-id="e0765-102">&lt;transactionFlow&gt;</span></span>
<span data-ttu-id="e0765-103">カスタム バインドのトランザクション フロー サポートを指定します。</span><span class="sxs-lookup"><span data-stu-id="e0765-103">Specifies transaction flow support for the custom binding.</span></span>  
  
 <span data-ttu-id="e0765-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e0765-104">\<system.serviceModel></span></span>  
<span data-ttu-id="e0765-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="e0765-105">\<bindings></span></span>  
<span data-ttu-id="e0765-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="e0765-106">\<customBinding></span></span>  
<span data-ttu-id="e0765-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="e0765-107">\<binding></span></span>  
<span data-ttu-id="e0765-108">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="e0765-108">\<transactionFlow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0765-109">構文</span><span class="sxs-lookup"><span data-stu-id="e0765-109">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0765-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e0765-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e0765-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e0765-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0765-112">属性</span><span class="sxs-lookup"><span data-stu-id="e0765-112">Attributes</span></span>  
  
|<span data-ttu-id="e0765-113">属性</span><span class="sxs-lookup"><span data-stu-id="e0765-113">Attribute</span></span>|<span data-ttu-id="e0765-114">説明</span><span class="sxs-lookup"><span data-stu-id="e0765-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e0765-115">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="e0765-115">transactionProtocol</span></span>|<span data-ttu-id="e0765-116">使用されるトランザクション プロトコルを指定します。</span><span class="sxs-lookup"><span data-stu-id="e0765-116">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="e0765-117">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="e0765-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e0765-118">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="e0765-118">-   OleTransactions</span></span><br /><span data-ttu-id="e0765-119">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="e0765-119">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="e0765-120">既定値は OleTransactions です。</span><span class="sxs-lookup"><span data-stu-id="e0765-120">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="e0765-121">この属性は <xref:System.ServiceModel.TransactionProtocol> 型です。</span><span class="sxs-lookup"><span data-stu-id="e0765-121">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e0765-122">子要素</span><span class="sxs-lookup"><span data-stu-id="e0765-122">Child Elements</span></span>  
 <span data-ttu-id="e0765-123">なし。</span><span class="sxs-lookup"><span data-stu-id="e0765-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e0765-124">親要素</span><span class="sxs-lookup"><span data-stu-id="e0765-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e0765-125">要素</span><span class="sxs-lookup"><span data-stu-id="e0765-125">Element</span></span>|<span data-ttu-id="e0765-126">説明</span><span class="sxs-lookup"><span data-stu-id="e0765-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e0765-127">\<binding></span><span class="sxs-lookup"><span data-stu-id="e0765-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="e0765-128">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="e0765-128">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0765-129">コメント</span><span class="sxs-lookup"><span data-stu-id="e0765-129">Remarks</span></span>  
 <span data-ttu-id="e0765-130">この要素により、受信トランザクションの目的のプロトコル形式を指定できるだけでなく、エンドポイントのバインディング設定で受信トランザクション フローを有効または無効にできます。</span><span class="sxs-lookup"><span data-stu-id="e0765-130">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="e0765-131">この構成要素を使用する方法については、次を参照してください。 [ServiceModel トランザクションの構成](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)と[トランザクション フローを有効にすると](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)です。</span><span class="sxs-lookup"><span data-stu-id="e0765-131">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="e0765-132">`OleTransactions` プロトコルを使用してエンドポイント間でトランザクションをフローさせるとき、フロー先のエンドポイントが `OleTransactions` 以外のプロトコルを使用して再びフローを試みると、トランザクション タイムアウトが失われる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e0765-132">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="e0765-133">その結果、OleTransactions ホップより後のすべてのダウンレベル ノードが、予想より遅くタイムアウトする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e0765-133">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0765-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="e0765-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransactionFlowElement>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="e0765-135">ServiceModel トランザクションの構成</span><span class="sxs-lookup"><span data-stu-id="e0765-135">ServiceModel Transaction Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)  
 [<span data-ttu-id="e0765-136">トランザクション フローの有効化</span><span class="sxs-lookup"><span data-stu-id="e0765-136">Enabling Transaction Flow</span></span>](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)  
 [<span data-ttu-id="e0765-137">バインディング</span><span class="sxs-lookup"><span data-stu-id="e0765-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="e0765-138">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="e0765-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="e0765-139">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="e0765-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="e0765-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="e0765-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
